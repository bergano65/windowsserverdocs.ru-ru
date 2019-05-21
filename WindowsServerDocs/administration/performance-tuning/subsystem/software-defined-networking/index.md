---
title: Настройка производительности программно-конфигурируемых сетей
description: Рекомендации по настройке производительности для программно-конфигурируемой сети (SDN)
ms.prod: windows-server-threshold
ms.technology: performance-tuning-guide
ms.topic: article
ms.author: grcusanz; AnPaul
author: phstee
ms.date: 10/16/2017
ms.openlocfilehash: dfb8d997c6e04381e5be0ba2c3a7ca27a851df50
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59891325"
---
# <a name="performance-tuning-software-defined-networks"></a>Настройка производительности программно-конфигурируемых сетей

Программно-конфигурируемая сеть (SDN) в Windows Server 2016 сочетает в себе сетевой контроллер, узлы Hyper-V, шлюзы подсистемы программной балансировки нагрузки и шлюзы HNV.  Настройка каждого из этих компонентов описана отдельно в следующих разделах.

## <a name="network-controller"></a>Сетевой контроллер

Сетевой контроллер — это роль сервера Windows Server, которая должна быть включена на всех виртуальных машинах, работающих на узлах, которые используют SDN, под управлением сетевого контроллера.

Для обеспечения высокого уровня доступности и максимальной производительности достаточно настроить три виртуальные машины с поддержкой сетевого контроллера.  Размер каждой виртуальной машины должен соответствовать требованиям, описанным в разделе о виртуальных машинах для инфраструктуры SDN статьи [Plan a Software Defined Network Infrastructure](../../../../networking/sdn/plan/Plan-a-Software-Defined-Network-Infrastructure.md) (Планирование инфраструктуры программно-конфигурируемой сети).

### <a name="sdn-quality-of-service-qos"></a>Качество обслуживания (QoS) для SDN

Чтобы эффективно и справедливо распределять трафик между виртуальными машинами, мы рекомендуем настроить на виртуальных машинах рабочей нагрузки параметры качества обслуживания SDN.  Дополнительные сведения о настройке качества обслуживания SDN см. в статье [Configure QoS for a Tenant VM Network Adapter](../../../../networking/sdn/manage/Configure-QoS-for-Tenant-VM-Network-Adapter.md) (Настройка качества обслуживания для сетевого адаптера виртуальной машины клиента).

## <a name="hyper-v-host-networking"></a>Сеть узлов Hyper-V

Рекомендации, содержащиеся в разделе [о производительности ввода-вывода в сети Hyper-V](#netio) руководства по [настройке производительности для серверов Hyper-V](../../role/remote-desktop/session-hosts.md), применимы при использовании SDN, но здесь мы добавили еще несколько рекомендаций для достижения наилучшей производительности при работе с SDN.

### <a name="physical-network-adapter-nic-teaming"></a>Объединение физических сетевых адаптеров (NIC)

Чтобы обеспечить оптимальную производительность и возможность отработки отказа, мы рекомендуем настроить объединение физических сетевых адаптеров.  При использовании SDN такое объединение создается с помощью объединения внедренных коммутаторов (SET).  

Для объединения лучше всего назначить двух участников, так как в этом случае виртуализованный трафик будет распределяться между двумя участниками группы во входящем и исходящем направлениях.  Вы можете назначить и более двух участников группы, но входящий трафик будет распределяться только по двум сетевым адаптерам.  Исходящий трафик всегда распределяется между всеми адаптерами, если на виртуальном коммутаторе сохраняются настройки динамической балансировки нагрузки по умолчанию.


### <a name="encapsulation-offloads"></a>Разгрузка инкапсуляции

SDN использует инкапсуляцию пакетов для виртуализации сети.  Для оптимальной производительности очень важно, чтобы сетевой адаптер поддерживал аппаратную разгрузку для используемого формата инкапсуляции.  Разные форматы инкапсуляции не имеют существенных различий в производительности.  По умолчанию при использовании сетевого контроллера применяется формат инкапсуляции VXLAN.

Чтобы определить, какой формат инкапсуляция используется для сетевого контроллера, выполните следующий командлет PowerShell:

``` syntax
    (Get-NetworkControllerVirtualNetworkConfiguration -connectionuri $uri).properties.networkvirtualizationprotocol
```

Чтобы обеспечить наилучшую производительности, если вы получите здесь значение VXLAN, убедитесь, что физические сетевые адаптеры поддерживают разгрузку задач для VXLAN.  Если в результатах указано значение NVGRE, физические сетевые адаптеры должны поддерживать разгрузку задач для NVGRE.

### <a name="mtu"></a>Максимальный передаваемый блок данных

Инкапсуляция означает, что к каждому пакету добавляются дополнительные байты.  Чтобы избежать фрагментации таких пакетов, для физической сети необходимо настроить использование кадров крупного размера.  Мы рекомендуем указать для MTU (максимальный передаваемый блок данных) значение 9234 для VXLAN или NVGRE. Его следует настроить на физическом коммутаторе для физических интерфейсов портов узла (L2) и на интерфейсах маршрутизатора (L3) для всех виртуальных локальных сетей, через которые будут отправляться инкапсулированные пакеты.  Сюда входят транспортная сеть, сеть поставщика HNV и сеть управления.

На узле Hyper-V значение MTU настраивается через сетевой адаптер, а агент узла сетевого контроллера, который работает на узле Hyper-V, автоматически применит корректировки с учетом дополнительной нагрузки инкапсуляции, если она поддерживается драйвером сетевого адаптера.  

Когда трафик покидает виртуальную сеть через шлюз, инкапсуляция удаляется и применяется исходное значение MTU, полученное от виртуальной машины.

### <a name="single-root-io-virtualization-sr-iov"></a>Виртуализация ввода-вывода с единым корнем (SR-IOV)

SDN реализуется на узле Hyper-V с помощью расширения коммутатора переадресации в виртуальном коммутаторе.  Чтобы расширение коммутатора могло обрабатывать пакеты, не следует применять SR-IOV на виртуальных сетевых интерфейсах, которые используются с этим сетевым контроллером, так как в этом случае трафик виртуальных машин будет направляться в обход виртуального коммутатора.

Если потребуется, SR-IOV можно сохранить на виртуальном коммутаторе для использования с сетевыми адаптерами виртуальной машины, которыми не управляет сетевой контроллер.  Виртуальные машины с поддержкой SR-IOV могут сосуществовать на одном виртуальном коммутаторе с другими виртуальными машинами, которые управляются сетевым контроллером и не используют SR-IOV.

Если вы используете сетевые адаптеры на 40 Гбит/с, мы рекомендуем включить SR-IOV на виртуальном коммутаторе для шлюзов программной балансировки нагрузки (SLB), чтобы добиться максимальной пропускной способности.  Это более подробно описано в статье [о шлюзах программной подсистемы балансировки нагрузки](slb-gateway-performance.md).

## <a name="hnv-gateways"></a>Шлюзы HNV

Сведения о настройке шлюзов HNV для использования с SDN вы найдете в статье [HNV Gateway Performance Tuning in Software Defined Networks](hnv-gateway-performance.md) (Настройка производительности шлюза HNV в программном обеспечении).

## <a name="software-load-balancer-slb"></a>Программная подсистема балансировки нагрузки (SLB)

Шлюзы SLB можно использовать только совместно с сетевым контроллером и SDN.  Дополнительные сведения о настройке SDN для использования с шлюзами SLB см. в статье [SLB Gateway Performance Tuning in Software Defined Networks](slb-gateway-performance.md) (Настройка производительности шлюзов программной подсистемы балансировки нагрузки в программно-конфигурируемых сетях).