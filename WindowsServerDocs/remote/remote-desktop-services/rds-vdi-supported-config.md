---
title: Поддерживаемые конфигурации безопасности Windows Server 10 для среды VDI на основе служб удаленных рабочих столов
description: Предоставляет сведения о поддерживаемых конфигурациях для среды VDI на основе Windows 10 с использованием RDS в Windows Server 2016.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 10/27/2016
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8f164f5d-a498-4f91-a12f-3e01d554f810
author: lizap
manager: dongill
ms.openlocfilehash: 08941c49469dcf9b9e3e42c7ab799186380bab35
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71387027"
---
# <a name="supported-windows-10-security-configurations-for-remote-desktop-services-vdi"></a>Поддерживаемые конфигурации безопасности Windows Server 10 для среды VDI на основе служб удаленных рабочих столов

> Область применения. Windows Server 2016

В Windows 10 и Windows Server 2016 встроены новые уровни защиты для предотвращения брешей в системе безопасности, блокировки вредоносных атак и повышения безопасности виртуальных машин, приложений и данных.

> [!NOTE]
> Не забудьте ознакомиться с [информацией о поддерживаемой конфигурации служб удаленных рабочих столов](rds-supported-config.md).

В следующей таблице показано, какие новые функции поддерживаются в развертывании VDI с использованием RDS.

|  Тип коллекции VDI               |  Управляемая среда в составе пула |  Управляемая личная среда |  Неуправляемая среда в составе пула                                     |  Неуправляемая личная среда                                    |
|-------------------------------------|------------------|--------------------|--------------------------------------------------------|--------------------------------------------------------|
| [Credential Guard](https://technet.microsoft.com/itpro/windows/keep-secure/credential-guard)                    | Да              | Да                | Да                                                    | Да                                                    |
| [Device Guard](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)                        | Да              | Да                | Да                                                    | Да                                                    |
| [Удаленный Credential Guard](https://technet.microsoft.com/itpro/windows/keep-secure/remote-credential-guard)             | Нет               | Нет                 | Нет                                                     | Нет                                                     |
| [Виртуальные машины с поддержкой экранирования и шифрования](../../security/guarded-fabric-shielded-vm/guarded-fabric-and-shielded-vms.md) | Нет               | Нет                 | Виртуальные машины, поддерживающие шифрование при дополнительной настройке | Виртуальные машины, поддерживающие шифрование при дополнительной настройке |

## <a name="remote-credential-guard"></a>Удаленный Credential Guard

Удаленный Credential Guard поддерживается только для прямых подключений к целевым компьютерам, а не для подключений через посредник подключений к удаленному рабочему столу и шлюз удаленных рабочих столов.
> [!NOTE]
> Если вы используете посредник подключений в среде с одним экземпляром и DNS-имя соответствует имени компьютера, то вы можете использовать удаленный Credential Guard, хотя это не поддерживается.

## <a name="shielded-vms-and-encryption-supported-vms"></a>Экранированные виртуальные машины и виртуальные машины с поддержкой шифрования 

- Экранированные виртуальные машины не поддерживаются в службах удаленных рабочих столов VDI. 

Чтобы использовать виртуальные машины с поддержкой шифрования, необходимо выполнить следующее.
- Используйте неуправляемую коллекцию и технологию подготовки вне процесса создания коллекции служб удаленных рабочих столов для подготовки виртуальных машин. 
- Диски профилей пользователей не поддерживаются, так как они используют разностные диски. 

