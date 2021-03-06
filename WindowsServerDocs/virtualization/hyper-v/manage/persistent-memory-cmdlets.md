---
title: Командлеты для настройки устройств постоянной памяти для виртуальных машин Hyper-V
description: Настройка устройств энергонезависимой памяти для виртуальных машин Hyper-V
ms.prod: windows-server
ms.service: na
manager: jasgroce
ms.technology: compute-hyper-v
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b5715c02-a90f-4de9-a71e-0fc08039ba1d
author: coreyp-at-msft
ms.author: coreyp
ms.openlocfilehash: ecae1fe96bc5088fa840c6e2e24a75bb72a9e8f3
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71392542"
---
# <a name="cmdlets-for-configuring-persistent-memory-devices-for-hyper-v-vms"></a>Командлеты для настройки устройств постоянной памяти для виртуальных машин Hyper-V

>Область применения. Windows Server 2019

Эта статья предоставляет системным администраторам и ИТ-специалистам сведения о настройке виртуальных машин Hyper-V с энергонезависимой памятью (память класса хранения или устройство NVDIMM). Устройства энергонезависимой памяти NVDIMM-N, совместимые с ЖДЕК, поддерживаются в Windows Server 2016 и Windows 10 и предоставляют доступ на уровне байт к очень низким временным устройствам без временных задержек. Устройства с постоянной памятью виртуальной машины поддерживаются в Windows Server 2019. 

## <a name="create-a-persistent-memory-device-for-a-vm"></a>Создание постоянного устройства памяти для виртуальной машины

Используйте командлет **[New-VHD](https://docs.microsoft.com/powershell/module/hyper-v/new-vhd?view=win10-ps)** , чтобы создать постоянное устройство памяти для виртуальной машины. Устройство должно быть создано на существующем томе DAX NTFS.  Новое расширение имени файла (. вхдпмем) используется для указания того, что устройство является устройством постоянного обмена памятью. Поддерживается только фиксированный формат VHD-файла.

**Пример:** `New-VHD d:\VMPMEMDevice1.vhdpmem -Fixed -SizeBytes 4GB`

## <a name="create-a-vm-with-a-persistent-memory-controller"></a>Создание виртуальной машины с постоянным контроллером памяти



Используйте **командлет New-VM** , чтобы создать виртуальную машину поколения 2 с указанными размером памяти и путем к образу VHDX. Затем используйте **Add-вмпмемконтроллер** , чтобы добавить контроллер энергонезависимой памяти к виртуальной машине.

**Например** 
    
    New-VM -Name "ProductionVM1" -MemoryStartupBytes 1GB -VHDPath c:\vhd\BaseImage.vhdx

    Add-VMPmemController ProductionVM1x

## <a name="attach-a-persistent-memory-device-to-a-vm"></a>Подключение устройства энергонезависимой памяти к виртуальной машине

Использование **[Add-вмхарддискдриве](https://docs.microsoft.com/powershell/module/hyper-v/add-vmharddiskdrive?view=win10-ps)** для подключения устройства энергонезависимой памяти к виртуальной машине

**Пример:** `Add-VMHardDiskDrive ProductionVM1 PMEM -ControllerLocation 1 -Path D:\VPMEMDevice1.vhdpmem`

Устройства с энергопотреблением памяти в виртуальной машине Hyper-V отображаются в виде постоянного устройства памяти для использования и управления гостевой операционной системой. Гостевые операционные системы могут использовать устройство в качестве блока или тома DAX. Если устройства энергонезависимой памяти в виртуальной машине используются в качестве тома DAX, они получают преимущества от небольшого количества байт на уровне байтов (без виртуализации ввода-вывода в пути кода). 

>[!NOTE] 
>Постоянная память поддерживается только для виртуальных машин Hyper-V Gen2. Динамическая миграция и миграция хранилища не поддерживаются для виртуальных машин с энергонезависимой памятью. Рабочие контрольные точки виртуальных машин не включают постоянное состояние памяти. 