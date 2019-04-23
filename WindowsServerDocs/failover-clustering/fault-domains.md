---
ms.assetid: 56fc7f80-9558-467e-a6e9-a04c9abbee33
title: Служба сведений о домене сбоя
ms.prod: windows-server-threshold
ms.author: cosdar
ms.manager: eldenc
ms.technology: storage-failover-clustering
ms.topic: article
author: cosmosdarwin
ms.date: 09/16/2016
ms.openlocfilehash: f5c64bb8f8b7d4b8d13c76c4e94cfcf52ee32c30
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821475"
---
# <a name="fault-domain-awareness-in-windows-server-2016"></a>Информация о домене сбоя в Windows Server 2016

> Относится к: Windows Server 2016

Отказоустойчивая кластеризация позволяет нескольким серверам работать вместе с целью обеспечения высокого уровня доступности или, другими словами, отказоустойчивости узла. Но современные компании требуют все больше доступности своей инфраструктуры. Для обеспечения бесперебойной работы, свойственной облачной среде, необходимо настроить защиту даже от таких маловероятных событий, как поломки корпуса, простои стойки или стихийные бедствия. Вот почему отказоустойчивой кластеризации в Windows Server 2016 представляет корпуса, стойки или сайта отказоустойчивость.

Домены сбоя и отказоустойчивость — тесно связанные понятия. Домен сбоя — это набор аппаратных компонентов, которые совместно используют единственную точку сбоя. Чтобы достичь отказоустойчивости конкретного уровня, необходимо использовать на нем несколько доменов сбоя. Например, чтобы обеспечить отказоустойчивость стоек, серверы и данные необходимо распределить среди нескольких стоек.

Этот короткий видеоролик представляет обзор доменов сбоя в Windows Server 2016:  
[![Щелкните этот образ, чтобы просмотреть общие сведения о доменах сбоя в Windows Server 2016](media/Fault-Domains-in-Windows-Server-2016/Part-1-Fault-Domains-Overview.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-1-Overview)

## <a name="benefits"></a>Преимущества
- **Дисковых пространств, включая дисковыми пространствами, домены сбоя используются для повышения уровня безопасности данных.**  
    Устойчивость в дисковых пространствах в принципе аналогична распределенной программно определяемой системе RAID. Несколько копий всех данных синхронизируются. В случае сбоя оборудования и потери одной копии другие копируются повторно для восстановления устойчивости. Для достижения максимальной устойчивости копии следует хранить в отдельных доменах сбоя.

- **[Служба работоспособности](health-service-overview.md) использует домены, чтобы предоставлять более информативные оповещения сбоя.**  
    Каждый домен сбоя можно связать с метаданными расположения, которые будут автоматически включаться в любые последующие оповещения. Используя эти дескрипторы, рабочий или обслуживающий персонал могут различать оборудование, что поможет уменьшить количество ошибок.  

- **В растянутой кластеризации домены сбоя используются для сопоставления и хранилища.** В растянутой кластеризации можно присоединить к общему кластеру отдаленные серверы. Для повышения производительности приложения или виртуальные машины следует запускать на серверах, которые расположены недалеко от серверов, на которых хранятся данные. Информация о домене сбоя обеспечивает соответствие этого хранилища.   

## <a name="levels-of-fault-domains"></a>Уровни доменов сбоя  
Существует четыре классических уровня доменов сбоя: сайт, стойка, корпус и узел. Узлы обнаруживаются автоматически. Каждый дополнительный уровень не является обязательным. Например, если в развертывании не используются стоечные серверы, учитывать уровень корпуса не имеет смысла.  

![Схема уровни доменов сбоя](media/Fault-Domains-in-Windows-Server-2016/levels-of-fault-domains.png)

## <a name="usage"></a>Использование  
Можно использовать PowerShell или XML-разметки для определения доменов сбоев. Оба подхода эквивалентны и полнофункциональны.

>[!IMPORTANT]
> Перед включением локальных дисковых пространств по возможности укажите домены сбоя. Это позволяет автоматической конфигурации подготовить пул, уровни и такие параметры, как устойчивость и число столбцов для обеспечения отказоустойчивости корпуса или стойки. После создания пула и томов данные не будут перемещены обратно после изменения топологии домена сбоя. Чтобы переместить узлы между корпусами или стойками после включения локальных дисковых пространств, сначала следует исключить узел и его диски из пула с помощью `Remove-ClusterNode -CleanUpDisks`.

### <a name="defining-fault-domains-with-powershell"></a>Определение доменов сбоя с помощью PowerShell
Windows Server 2016 появились следующие командлеты для работы с доменами сбоя:
* `Get-ClusterFaultDomain`
* `Set-ClusterFaultDomain`
* `New-ClusterFaultDomain` 
* `Remove-ClusterFaultDomain`

Этот короткий видеоролик демонстрирует использование указанных командлетов.
[![Щелкните это изображение, чтобы ознакомьтесь с коротким видео с использованием командлетов домен сбоя кластера](media/Fault-Domains-in-Windows-Server-2016/Part-2-Using-PowerShell.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-2-Using-PowerShell)

Используйте `Get-ClusterFaultDomain` для просмотра текущей топологии домена сбоя. Появится список всех узлов в кластере, а также любых созданных корпусов, стоек или сайтов. Вы можете отфильтровать результаты с помощью таких параметров, как **-Type** или **-Name**, но это не обязательно.

```PowerShell
Get-ClusterFaultDomain
Get-ClusterFaultDomain -Type Rack
Get-ClusterFaultDomain -Name "server01.contoso.com"
```

Используйте `New-ClusterFaultDomain` создать новый корпус, стоек или сайтов. `-Type` И `-Name` параметры являются обязательными. Возможные значения `-Type` являются `Chassis`, `Rack`, и `Site`. `-Name` Может быть любой строкой. (Для `Node` домены сбоя типа, имя должно быть фактическим именем узла, как набор автоматически).

```PowerShell
New-ClusterFaultDomain -Type Chassis -Name "Chassis 007"
New-ClusterFaultDomain -Type Rack -Name "Rack A"
New-ClusterFaultDomain -Type Site -Name "Shanghai"
```

> [!IMPORTANT]  
> Windows Server не может и не проверяет соответствие любой созданный вами домен сбоя для любого элемента в мире физических. (Это может показаться очевидным, но важно понимать). Если в реальном мире все узлы размещены в одной стойке, создав два домена сбоя `-Type Rack` в программном обеспечении, вы не обеспечите волшебным образом отказоустойчивость стойки. Вы отвечаете за обеспечение соответствия топологии, созданной с помощью этих командлетов, фактическому расположению оборудования.

Используйте `Set-ClusterFaultDomain` для перемещения одного домена сбоя в другой. Обычно для описания этого отношения вложенности используются термины "родительской" и "дочерний". `-Name` И `-Parent` параметры являются обязательными. В `-Name`, укажите имя, домен сбоя, который перемещает; в `-Parent`, укажите имя назначения. Чтобы переместить сразу несколько доменов сбоя, перечислите их имена.

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent "Rack A"
Set-ClusterFaultDomain -Name "Rack A", "Rack B", "Rack C", "Rack D" -Parent "Shanghai"
```

> [!IMPORTANT]  
> При перемещении доменов сбоев их дочерние элементы перемещаются вместе с ними. Если в приведенном выше примере стойка A является родительским элементом для server01.contoso.com, этот домен не нужно отдельно перемещать на сайт Shanghai. Это уже сделано, поскольку там находится его родительский элемент: все так же, как и в реальном мире.

Вы увидите родительско дочерних отношений в выходных данных `Get-ClusterFaultDomain`в `ParentName` и `ChildrenNames` столбцов.

Можно также использовать `Set-ClusterFaultDomain` для изменения других определенных свойств доменов сбоя. Например, вы можете указать необязательные `-Location` или `-Description` метаданные для любого домена сбоя. Эти сведения будут включены в оповещения службы работоспособности, касающиеся оборудования. Вы также можете переименовать домен сбоя с помощью `-NewName` параметра. Не переименовывайте `Node` домены сбоев типа.

```PowerShell
Set-ClusterFaultDomain -Name "Rack A" -Location "Building 34, Room 4010"
Set-ClusterFaultDomain -Type Node -Description "Contoso XYZ Server"
Set-ClusterFaultDomain -Name "Shanghai" -NewName "China Region"
```

Используйте `Remove-ClusterFaultDomain` удаляемый корпусов, стоек или сайтов, которые вы создали. Параметр `-Name` обязательный. Не удается удалить домен сбоя, который содержит дочерние элементы — во-первых, удалите дочерние элементы либо переместите их за пределы с помощью `Set-ClusterFaultDomain`. Чтобы переместить домен сбоя за пределами всех других доменов сбоя, установите его `-Parent` пустая строка (»»). Не удается удалить `Node` домены сбоев типа. Чтобы удалить сразу несколько доменов сбоя, перечислите их имена.

```PowerShell
Set-ClusterFaultDomain -Name "server01.contoso.com" -Parent ""
Remove-ClusterFaultDomain -Name "Rack A"
```

### <a name="defining-fault-domains-with-xml-markup"></a>Определение доменов сбоя с помощью XML-разметки
Домены сбоя можно указать при помощи синтаксиса на основе XML. Мы рекомендуем с помощью любого текстового редактора создать XML-документ, который вы сможете сохранить и использовать потом. Например, можно использовать Visual Studio Code (загрузите его бесплатно *[отсюда](https://code.visualstudio.com/)*) или Блокнот.  

Этот короткий видеоролик демонстрирует использование XML-разметки для определения доменов сбоев.

[![Щелкните это изображение, чтобы ознакомьтесь с коротким видео о том, как использовать XML для указания доменов сбоя](media/Fault-Domains-in-Windows-Server-2016/Part-3-Using-XML-Markup.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-3-Using-XML)

В PowerShell выполните следующий командлет: `Get-ClusterFaultDomainXML`. Будет выведена текущая спецификация домена сбоя для кластера в виде XML-кода. Это отражает каждые обнаруженных `<Node>`заключен в открывающие и закрывающие `<Topology>` теги.  

Чтобы сохранить эти выходные данные в файл, выполните следующую команду.  

```PowerShell
Get-ClusterFaultDomainXML | Out-File <Path>  
```

Откройте файл и добавьте `<Site>`, `<Rack>`, и `<Chassis>` теги, чтобы указать способ распределения этих узлов между сайтами, стойками и корпусами. Каждый тег должен быть идентифицирован уникальным **именем**. Для узлов необходимо сохранить имена, заданные по умолчанию.  

> [!IMPORTANT]  
> Хотя все дополнительные теги являются необязательными, они должны соответствовать транзитивной иерархии Site &gt; Rack &gt; Chassis &gt; Node и должны быть правильно закрыты.  
В дополнение к имени, произвольные `Location="..."` и `Description="..."` дескрипторы могут добавляться к любому тегу.  

#### <a name="example-two-sites-one-rack-each"></a>Пример. Два сайта, в одной стойке  

```XML
<Topology>  
  <Site Name="SEA" Location="Contoso HQ, 123 Example St, Room 4010, Seattle">  
    <Rack Name="A01" Location="Aisle A, Rack 01">  
      <Node Name="Server01" Location="Rack Unit 33" />  
      <Node Name="Server02" Location="Rack Unit 35" />  
      <Node Name="Server03" Location="Rack Unit 37" />  
    </Rack>  
  </Site>  
  <Site Name="NYC" Location="Regional Datacenter, 456 Example Ave, New York City">  
    <Rack Name="B07" Location="Aisle B, Rack 07">  
      <Node Name="Server04" Location="Rack Unit 20" />  
      <Node Name="Server05" Location="Rack Unit 22" />  
      <Node Name="Server06" Location="Rack Unit 24" />  
    </Rack>  
  </Site>  
</Topology> 
``` 

#### <a name="example-two-chassis-blade-servers"></a>Пример: два корпуса, стоечные серверы  
```XML
<Topology>  
  <Rack Name="A01" Location="Contoso HQ, Room 4010, Aisle A, Rack 01">  
    <Chassis Name="Chassis01" Location="Rack Unit 2 (Upper)" >  
      <Node Name="Server01" Location="Left" />  
      <Node Name="Server02" Location="Right" />  
    </Chassis>  
    <Chassis Name="Chassis02" Location="Rack Unit 6 (Lower)" >  
      <Node Name="Server03" Location="Left" />  
      <Node Name="Server04" Location="Right" />  
    </Chassis>  
  </Rack>  
</Topology>  
```

Чтобы задать новую спецификацию домена сбоя, сохраните XML и выполните следующую команду в PowerShell.  

```PowerShell
$xml = Get-Content <Path> | Out-String  
Set-ClusterFaultDomainXML -XML $xml
```

В этом руководстве представлены только два примера, но `<Site>`, `<Rack>`, `<Chassis>`, и `<Node>` теги, которые можно комбинировать и сопоставлять разному в соответствии с физической топологией развертывания, все, что возможно. Мы надеемся, что приведенные примеры иллюстрируют гибкость этих тегов и значение произвольных дескрипторов расположения для их однозначного определения.  

### <a name="optional-location-and-description-metadata"></a>Дополнительно Расположение и описание метаданных

Вы можете указать необязательные **расположение** или **описание** метаданные для любого домена сбоя. Эти сведения будут включены в оповещения службы работоспособности, касающиеся оборудования. Этот короткий видеоролик демонстрирует значение добавления таких дескрипторов.

[![Щелкните, чтобы просмотреть краткое видео, в котором значение добавления дескрипторов расположения к доменам сбоя](media/Fault-Domains-in-Windows-Server-2016/part-4-location-description.jpg)](https://channel9.msdn.com/Blogs/windowsserver/Fault-Domain-Awareness-in-WS2016-Part-4-Location-Description)

## <a name="see-also"></a>См. также  
-   [Windows Server 2016](../get-started/windows-server-2016.md)  
-   [Дисковые пространства в Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md) 