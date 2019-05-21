---
title: Производительность и пропускная способность туннеля GRE шлюза RAS-сервера
description: В этом разделе, предназначенном для специалистов информационных технологий (ИТ), сведения пропускной способности производительности о туннели RAS Gateway протоколом (GRE).
manager: brianlic
ms.prod: windows-server-threshold
ms.date: ''
ms.technology: networking-ras
ms.topic: article
ms.assetid: c051b2ec-de0f-49d1-82b9-5742b259cd7c
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 73ae4e573d926f4a77b076c880c1d74ed69f032d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59880765"
---
# <a name="ras-gateway-gre-tunnel-throughput-and-performance"></a>Производительность и пропускная способность туннеля GRE шлюза RAS-сервера

>Относится к: Windows Server \(полугодовой канал\)

Дополнительные сведения о сервера удаленного доступа можно использовать в этом разделе \(RAS\) шлюза Generic Routing Encapsulation \(GRE\) туннеля производительности в Windows Server версии 1709, в не - программно-Конфигурируемую сеть \( SDN\) тест на основе среды.

Шлюз RAS — это программный маршрутизатор и шлюз, который можно использовать в режиме одного клиента или в мультитенантном режиме. В этом разделе рассматриваются в режиме одного клиента, Настройка высокой доступности средствами отказоустойчивой кластеризации. Статистика производительности туннель GRE, приведенных в этом разделе допустимы для шлюза RAS singele клиента и мультитенантного режима.

>[!NOTE]
>Отказоустойчивой кластеризации — это функция Windows Server, которая позволяет сгруппировать несколько серверов в отказоустойчивый кластер. Дополнительные сведения см. в разделе [отказоустойчивой кластеризации](../../../failover-clustering/failover-clustering-overview.md)

Режиме одного клиента позволяет организациям любого размера для развертывания шлюза в качестве внешним или Интернету\-с выходом edge виртуальной частной сети \(VPN\) сервера. В режиме одного клиента, вы можете развернуть шлюз RAS на физическом сервере или виртуальной машине \(виртуальной Машины\). В этом разделе описывается развертывание шлюза RAS для двух виртуальных машин \(виртуальных машин\) , настроенные в отказоустойчивом кластере.

>[!IMPORTANT]
>Так как туннели GRE обеспечивают инкапсуляции, но не шифрования, не следует использовать шлюз RAS, настроен с GRE, как шлюз edge Интернета. Чтобы узнать об оптимальных вариантов использования для шлюза RAS с туннели GRE, см. в разделе [туннелирование GRE в Windows Server](gre-tunneling-windows-server.md).

GRE является упрощенным туннельного протокола, который может инкапсулировать разнообразные протоколы сетевого уровня внутри виртуальной точки\-для\-точки ссылки за IP-сети. Реализация Майкрософт GRE инкапсулирует IPv4 и IPv6.

Дополнительные сведения см. в разделе **сценариях развертывания шлюза RAS** в разделе [шлюза RAS](https://docs.microsoft.com/windows-server/remote/remote-access/ras-gateway/ras-gateway#bkmk_deploy). 

В этом сценарии тестирования, как показано на следующем рисунке, поток трафика, который измеряется переходит с 2 интрасети организации out 1 интрасети организации. Виртуальные машины рабочей нагрузки клиента отправлять сетевой трафик из интрасети 2 1 интрасети с помощью шлюза RAS.

![Обзор сценария тестирования туннель GRE шлюза RAS](../../media/GRE-Tunnel-Perf/Gre-Infrastructure.jpg)

## <a name="test-environment-configuration"></a>Тестовая конфигурация среды

Этот раздел содержит сведения о тестовой среде и настройки шлюза RAS.

В тестовой среде, виртуальные машины шлюза RAS развернуты на Hyper\-V узлов в отказоустойчивом кластере для обеспечения высокой доступности.

### <a name="hyper-v-host-configuration"></a>Hyper\-V конфигурация узла

Два Hyper\-V узлы настроены для поддержки сценария тестирования следующим образом. 

- Два двухъядерных\-адресацией физических компьютеров под управлением Windows Server версии 1709
- Два физических сетевых адаптеров в каждом из двух серверов подключены к другой подсети — каждый из которых представляют подсети интрасети организации. Сети и поддержки оборудования емкостью 10 Гбит/с.
- Технологию Hyper-Threading на физических серверах отключен. Это обеспечивает максимальную пропускную способность от физических сетевых адаптеров.
- Hyper\-установлен на обоих серверах и настроены два внешних Hyper V серверной роли\-V виртуальные коммутаторы, один для каждого физического сетевого адаптера.
- Поскольку оба серверы подключены к одной интрасети, серверы могут взаимодействовать друг с другом.
- Hyper\-V узлы настроены в отказоустойчивом кластере по интрасети. 

>[!NOTE]
>Дополнительные сведения см. в разделе [Виртуальный коммутатор Hyper-V](https://docs.microsoft.com/windows-server/virtualization/hyper-v-virtual-switch/hyper-v-virtual-switch).

### <a name="vm-configuration"></a>Конфигурация виртуальной Машины

Две виртуальные машины настроены для поддержки сценария тестирования следующим образом.

- На каждом сервере, то есть при установке виртуальной Машины под управлением Windows Server версии 1709. Каждая виртуальная машина настроена с 10 ядрами и 8 ГБ ОЗУ.
- Каждая виртуальная машина также настроены два виртуальных сетевых адаптеров. Один виртуальный сетевой адаптер подключен к виртуальному коммутатору 1 интрасети и виртуальный сетевой адаптер подключен к виртуальному коммутатору 2 интрасети.
- Каждая виртуальная машина имеет шлюз RAS, настроенный в качестве GRE\-на основе VPN-сервера.
- Виртуальные машины шлюза настраиваются в отказоустойчивом кластере. Когда кластерным, одна виртуальная машина активен и другой виртуальной Машины является пассивным.

### <a name="workload-hyper-v-hosts-and-vms"></a>Рабочая нагрузка Hyper\-V узлов и виртуальных машин

Для этого теста, два рабочей нагрузки Hyper\-узлов V устанавливаются в интрасети, и каждый узел имеет установлена одна виртуальная машина. При создании дубликата этот тест в тестовой среде, можно установить столько рабочей нагрузки серверов и виртуальных машин как подходит для ваших целей.

- Рабочая нагрузка Hyper\-узлов V имеет один физический сетевой адаптер установлен, то есть, подключенными к интрасети организации.
- В Hyper\-V виртуальный коммутатор, один виртуальный коммутатор можно создать на каждом узле. Параметром является внешним и привязан к одной сетевой адаптер, подключенный к интрасети.
- Нагрузки виртуальных машин настроены с ОЗУ Объемом 2 ГБ и 2 ядра.
- Виртуальные машины рабочей нагрузки, иметь один виртуальный сетевой адаптер, подключенный к виртуальному коммутатору интрасети.

### <a name="traffic-generator-tool"></a>Инструмент создания трафика

Инструмент создания трафика, который используется в этом тесте является средством ctsTraffic. Репозиторий Git для этого средства находится в [ https://github.com/Microsoft/ctsTraffic ](https://github.com/Microsoft/ctsTraffic).

## <a name="ras-gateway-performance"></a>Производительность шлюза RAS

На иллюстрациях в этом разделе описывают диспетчер задач отображает пропускной способности туннеля GRE с несколькими подключениями TCP.

Можно добиться до 2,0 Гбит/с пропускной способности с несколькими\-основы виртуальных машин, настроенных в качестве шлюзов RAS GRE.

### <a name="gre-tunnel-performance-with-multiple-tcp-sessions"></a>Производительность туннель GRE несколько сеансов TCP

С нескольких сеансов TCP использование ЦП достигает 100%, и максимальная пропускная способность на туннель GRE 2.0 Гбит/с.

На следующем рисунке показано использование ЦП на обе виртуальные машины шлюза RAS. Виртуальную Машину active #1 виртуальной Машины шлюза RAS, находится слева, даже если пассивный виртуальная машина, RAS шлюза виртуальной Машины 2, в правой части.

![Использование ЦП виртуальной Машины шлюза в диспетчере задач](../../media/GRE-Tunnel-Perf/Gre-Tunnel-01.jpg)

На следующем рисунке показана пропускная способность сети Ethernet на виртуальных машинах шлюза RAS. Виртуальную Машину active #1 виртуальной Машины шлюза RAS, находится слева, даже если пассивный виртуальная машина, RAS шлюза виртуальной Машины 2, в правой части.

![Пропускная способность сети Ethernet виртуальных Машин шлюза в диспетчере задач](../../media/GRE-Tunnel-Perf/Gre-Tunnel-02.jpg)


### <a name="gre-tunnel-performance-with-one-tcp-connection"></a>Производительность туннель GRE одно TCP-подключение

С конфигурацией тестов, изменено с нескольких сеансов TCP на одном сеансе TCP только одно ядро ЦП достигает максимальной емкости на виртуальных машинах шлюза RAS.

Максимальная пропускная способность на туннель GRE — от 400 – 500 Мбит/с.

На следующем рисунке показано использование ЦП на обе виртуальные машины шлюза RAS. Виртуальную Машину active #1 виртуальной Машины шлюза RAS, находится слева, даже если пассивный виртуальная машина, RAS шлюза виртуальной Машины 2, в правой части.

![Использование ЦП виртуальной Машины шлюза в диспетчере задач](../../media/GRE-Tunnel-Perf/Gre-Tunnel-03.jpg)


На следующем рисунке показана пропускная способность сети Ethernet на виртуальных машинах шлюза RAS. Виртуальную Машину active #1 виртуальной Машины шлюза RAS, находится слева, даже если пассивный виртуальная машина, RAS шлюза виртуальной Машины 2, в правой части.

![Пропускная способность сети Ethernet виртуальных Машин шлюза в диспетчере задач](../../media/GRE-Tunnel-Perf/Gre-Tunnel-04.jpg)

Дополнительные сведения о производительности шлюза RAS см. в разделе [оптимизация производительности HNV шлюза в сети определенных программного обеспечения](https://docs.microsoft.com/windows-server/administration/performance-tuning/subsystem/software-defined-networking/hnv-gateway-performance).