---
title: Расширение томов в локальных дисковых пространствах
ms.assetid: fa48f8f7-44e7-4a0b-b32d-d127eff470f0
ms.prod: windows-server-threshold
ms.author: cosmosdarwin
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: cosmosdarwin
ms.date: 01/23/2017
ms.localizationpriority: medium
ms.openlocfilehash: 51f58ec23c55a6cb1664d800d6f4a75dae545899
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824975"
---
# <a name="extending-volumes-in-storage-spaces-direct"></a>Расширение томов в локальных дисковых пространствах
> Относится к: Windows Server 2019, Windows Server 2016

Эта статья содержит инструкции по изменению размеров томов в [локальных дисковых пространствах](storage-spaces-direct-overview.md).

## <a name="prerequisites"></a>предварительные требования

### <a name="capacity-in-the-storage-pool"></a>Емкость в пуле носителей

Прежде чем изменять размер тома, убедитесь, что у вас достаточно емкости в пуле носителей. Например, если размер тома с трехсторонним зеркальным отображением, который составляет 1 ТБ, меняется на 2 ТБ, занимаемое этим томом место увеличится с 3 до 6 ТБ. Для изменения размера необходимо по крайней мере 3 ТБ доступного места в пуле носителей (6 – 3 = 3).

### <a name="familiarity-with-volumes-in-storage-spaces"></a>Знакомство с томами в дисковых пространствах

В локальных дисковых пространствах каждый том состоит из нескольких объектов в стеке: общего тома кластера (CSV), т. е. тома; раздела; диска, т. е. виртуального диска; одного или нескольких уровней хранилища (если применимо). Чтобы изменить размер тома, необходимо изменить размер нескольких из этих объектов.

![volumes-in-smapi](media/resize-volumes/volumes-in-smapi.png)

Чтобы ознакомиться с ними, выполните командлет **Get-** с соответствующим существительным в PowerShell.

Пример:

```PowerShell
Get-VirtualDisk
```

Чтобы проследить связи между объектами в стеке, передайте один командлет **Get-** в следующий.

Например, вот как перейти от виртуального диска к его тому:

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-Disk | Get-Partition | Get-Volume 
```

## <a name="step-1--resize-the-virtual-disk"></a>Шаг 1. Изменение размера виртуального диска

В зависимости от способа создания, у виртуального диска могут быть уровни хранилища.

Чтобы проверить, выполните следующий командлет:

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-StorageTier 
```

Если командлет ничего не возвращает, у виртуального диска нет уровней хранилища.

### <a name="no-storage-tiers"></a>Нет уровней хранилища

Если у виртуального диска нет уровней хранилища, вы можете изменить его размер непосредственно с помощью командлета **Resize-VirtualDisk**.

Укажите новый размер в параметре **-Size**.

```PowerShell
Get-VirtualDisk <FriendlyName> | Resize-VirtualDisk -Size <Size>
```

При изменении размера **VirtualDisk** также автоматически изменяется размер **Disk**.

![Resize-VirtualDisk](media/resize-volumes/Resize-VirtualDisk.gif)

### <a name="with-storage-tiers"></a>С уровнями хранилища

Если у виртуального диска есть уровни хранилища, вы можете изменить размер каждого уровня по отдельности с помощью командлета **Resize-StorageTier**.

Получите имена уровней хранилища, проследив связи с виртуального диска.

```PowerShell
Get-VirtualDisk <FriendlyName> | Get-StorageTier | Select FriendlyName
```

Затем укажите новый размер для каждого уровня в параметре **-Size**.

```PowerShell
Get-StorageTier <FriendlyName> | Resize-StorageTier -Size <Size>
```

> [!TIP]
> Если уровни отличаются по типу физического носителя (например, **MediaType = SSD** и **MediaType = HDD**), убедитесь, что в пуле носителей достаточно емкости каждого типа носителя.

При изменении размера **StorageTier** также автоматически изменяются размеры **VirtualDisk** и **Disk**.

![Resize-StorageTier](media/resize-volumes/Resize-StorageTier.gif)

## <a name="step-2--resize-the-partition"></a>Шаг 2. Изменение размера раздела

Измените размер раздела с помощью командлета **Resize-Partition**. Ожидается, что виртуальный диск содержит два раздела. Один из них зарезервирован и не должен меняться. Вам нужно изменить размер раздела **PartitionNumber = 2** и **Type = Basic**.

Укажите новый размер в параметре **-Size**. Рекомендуем использовать максимальный поддерживаемый размер, указанный ниже.

```PowerShell
# Choose virtual disk
$VirtualDisk = Get-VirtualDisk <FriendlyName>

# Get its partition
$Partition = $VirtualDisk | Get-Disk | Get-Partition | Where PartitionNumber -Eq 2

# Resize to its maximum supported size 
$Partition | Resize-Partition -Size ($Partition | Get-PartitionSupportedSize).SizeMax
```

При изменении размера **Partition** также автоматически изменяются размеры **Volume** и **ClusterSharedVolume**.

![Resize-Partition](media/resize-volumes/Resize-Partition.gif)

Вот и все!

> [!TIP]
> Чтобы убедиться, что размер тома изменился, выполните командлет **Get-Volume**.

## <a name="see-also"></a>См. также

- [Дисковые пространства в Windows Server 2016](storage-spaces-direct-overview.md)
- [Планирование томов в дисковых пространств](plan-volumes.md)
- [Создание томов в дисковых пространств](create-volumes.md)