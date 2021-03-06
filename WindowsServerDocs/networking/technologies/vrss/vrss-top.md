---
title: Виртуальное масштабирование на стороне приема (vRSS)
description: Узнайте о виртуальном масштабировании на стороне приема (vRSS) в Windows Server и о настройке виртуального сетевого адаптера для балансировки нагрузки входящего сетевого трафика между несколькими ядрами ядра процессора в виртуальной машине. Кроме того, можно настроить несколько физических ядер для виртуального сетевого адаптера узла (vNIC).
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 9be477b3-f81d-4e84-a6b0-ac4c1ea97715
ms.date: 09/05/2018
ms.localizationpriority: medium
manager: dougkim
ms.author: pashort
author: shortpatti
ms.openlocfilehash: b24cabe3597af35e7c7f3c6f81d360bb11675e23
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71395786"
---
# <a name="virtual-receive-side-scaling-vrss"></a>Виртуальное масштабируемое \(vRSS на стороне приема\)

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе вы узнаете о виртуальном масштабировании на стороне приема (vRSS) и о настройке виртуального сетевого адаптера для балансировки нагрузки входящего сетевого трафика между несколькими ядрами ядра процессора в виртуальной машине. Можно также использовать vRSS для настройки нескольких физических ядер для виртуального сетевого адаптера \(узла vNIC.\)

Такая конфигурация позволяет распределять нагрузку из виртуального сетевого адаптера между несколькими виртуальными процессорами на виртуальной машине виртуальной \(\)машины, позволяя виртуальной машине обрабатывать больше сетевого трафика более быстро, чем с одним логический процессор.

>[!TIP]
>VRSS можно использовать на виртуальных машинах на\-узлах Hyper V, имеющих несколько процессоров, один процессор с несколькими ядрами или несколько ядер, установленных и настроенных для использования виртуальной машины.

vRSS совместим со всеми остальными технологиями сети Hyper\--V. vRSS зависит от очередь виртуальной машины \(VMQ\) на узле Hyper\--V и RSS в виртуальной машине или на узле vNIC.

По умолчанию Windows Server поддерживает vRSS, но его можно отключить на виртуальной машине с помощью Windows PowerShell. Дополнительные сведения см. в статьях [Управление vRSS](vrss-manage.md) и [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).



## <a name="operating-system-compatibility"></a>Совместимость операционных систем

RSS можно использовать на любом многопроцессорном или многоядерном компьютере или vRSS на любой многопроцессорной или многоядерной виртуальной машине, работающей под управлением Windows Server 2016.

Многопроцессорные или многоядерные виртуальные машины, работающие под управлением следующих операционных систем Майкрософт, также поддерживают vRSS.

- Windows Server 2016
- Windows 10 профессиональная или Корпоративная
- Windows Server 2012 R2
- Windows 8.1 Pro или Enterprise
- Windows Server 2012 с установленными компонентами интеграции Windows Server 2012 R2.
- Windows 8 с установленными компонентами интеграции Windows Server 2012 R2.

Сведения о поддержке vRSS для виртуальных машин под управлением FreeBSD или Linux в качестве гостевой операционной системы в Hyper-V см. в статье [Поддерживаемые виртуальные машины Linux и FreeBSD для Hyper-v в Windows](https://docs.microsoft.com/windows-server/virtualization/hyper-v/Supported-Linux-and-FreeBSD-virtual-machines-for-Hyper-V-on-Windows).
  
## <a name="hardware-requirements"></a>Требования к оборудованию

Ниже приведены требования к оборудованию для vRSS.
 
- Физические сетевые адаптеры должны поддерживать очередь виртуальной машины \(VMQ\). Если функция VMQ отключена или не поддерживается, то для узла Hyper\-V и всех виртуальных машин, настроенных на узле, отключена функция vRSS.
- У сетевых адаптеров должна быть скорость связи 10 Гбит/с или более.
- Для\-узлов Hyper V необходимо настроить несколько процессоров или хотя бы один процессор\-с несколькими ядрами для использования vRSS.
- Виртуальные машины \(виртуальных\) машин должны быть настроены для использования двух или более логических процессоров.


## <a name="use-case-scenarios"></a>Сценарии вариантов использования

В следующих двух сценариях вариантов использования показано общее использование vRSS для балансировки нагрузки процессора и программной балансировки нагрузки.

### <a name="processor-load-balancing"></a>Балансировка нагрузки процессора
  
Энтони, сетевой администратор, настраивает новый узел Hyper-V с двумя сетевыми адаптерами, поддерживающими единый \(\)набор SR\--Output виртуализации с одним корневым входом. Он развертывает Windows Server 2016 для размещения файлового сервера виртуальной машины.

После установки оборудования и программного обеспечения Энтони настраивает виртуальную машину для использования восьми виртуальных процессоров и 4096 МБ памяти. К сожалению, Энтони не имеет возможности включить SR\-IOV, так как ее виртуальные машины полагаются на применение политик с помощью виртуального коммутатора, созданного с помощью диспетчера виртуальных коммутаторов Hyper\--V. По этой причине Энтони принимает решение использовать vRSS вместо SR\-IOV.

Изначально Энтони назначает четыре виртуальных процессора с помощью Windows PowerShell для использования с vRSS. Использование файлового сервера после недели появлялось довольно популярным, поэтому Энтони проверяет производительность виртуальной машины.  Он обнаруживает полное использование четырех виртуальных процессоров.

По этой причине Энтони решает добавить процессоры в виртуальную машину для использования vRSS.  Он назначает виртуальной машине еще два виртуальных процессора, которые автоматически доступны для vRSS, чтобы помочь справиться с большой сетевой нагрузкой. Его усилия приводят к повышению производительности файлового сервера виртуальной машины, при этом шесть процессоров эффективно обрабатывают нагрузку на сетевой трафик.


### <a name="software-load-balancing"></a>Балансировка нагрузки программного обеспечения

Сандра, сетевой администратор, настраивает одну высокопроизводительную виртуальную машину на одной из своих систем, чтобы она действовала в качестве программной подсистемы балансировки нагрузки. Ей назначены все доступные логические процессоры для этой единственной виртуальной машины.

После установки Windows Server она использует vRSS для получения параллельной обработки сетевого трафика на нескольких логических процессорах на виртуальной машине. Поскольку Windows Server поддерживает vRSS, Сандра не нужно вносить какие-либо изменения в конфигурацию.


## <a name="related-topics"></a>См. также

- [Планирование использования vRSS](vrss-plan.md)
- [Включение vRSS на виртуальном сетевом адаптере](vrss-enable.md)
- [Управление vRSS](vrss-manage.md)
- [Часто задаваемые вопросы по vRSS](vrss-faq.md)
- [Команды Windows PowerShell для RSS и vRSS](vrss-wps.md)

---
