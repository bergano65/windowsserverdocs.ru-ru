---
title: Использование команды Add-Имажедриверпаккаже
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6c2a4833-6427-47f8-9ffb-20b3786cb406
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1069b7c63e8b3bbc28fd900e8c869afc8abc03bc
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71363734"
---
# <a name="using-the-add-imagedriverpackage-command"></a>Использование команды Add-Имажедриверпаккаже

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Добавляет пакет драйверов, который находится в хранилище драйверов, в существующий образ загрузки на сервере. Версия образа должна быть Windows 7 или Windows Server 2008 R2 или более поздней версии.
## <a name="syntax"></a>Синтаксис
```
wdsutil /add-ImageDriverPackage [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64} 
```
```
[/Filename:<File name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
## <a name="parameters"></a>Параметры

|                 Параметр                  |                                                                                                                                                                                                            Описание                                                                                                                                                                                                             |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           [/Server:<Server name>           |                                                                                                                                               Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.                                                                                                                                                |
|             носитель:<Image name>             |                                                                                                                                                                                       Указывает имя образа, в который добавляется драйвер.                                                                                                                                                                                        |
|               mediaType: Загрузка               |                                                                                                                                                                Указывает тип образа, в который добавляется драйвер. Пакеты драйверов можно добавлять только в загрузочные образы.                                                                                                                                                                 |
| /Арчитектуре: {x86 &#124; ia64 &#124; x64} |                                                                                                       Указывает архитектуру загрузочного образа. Так как для образов загрузки в разных архитектурах можно использовать одно и то же имя образа, необходимо указать архитектуру для обеспечения правильного использования образа.                                                                                                        |
|           /Филенаме:<File name>]           |                                                                                                                                                        Указывает имя файла. Если образ не может быть однозначно определен по имени, необходимо указать имя файла.                                                                                                                                                        |
|           [/Дриверпаккаже:<Name>           |                                                                                                                                                                                   Указывает имя пакета драйверов, добавляемого к образу.                                                                                                                                                                                    |
|             [/Паккажеид:<ID>]              | Указывает идентификатор служб развертывания Windows для пакета драйверов. Этот параметр необходимо указать, если пакет драйверов не может быть однозначно идентифицирован по имени. Чтобы найти идентификатор пакета, щелкните группу драйверов, в которой находится пакет (или узел **все пакеты** ), щелкните правой кнопкой мыши пакет и выберите пункт **свойства**. Идентификатор пакета указан на вкладке **Общие** . Например: {DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}. |

## <a name="BKMK_examples"></a>Примеров
Чтобы добавить пакет драйверов в загрузочный образ, введите один из следующих элементов:
```
wdsutil /add-ImageDriverPackagmedia:"WinPE Boot Imagemediatype:Boot /Architecture:x86 /DriverPackage:XYZ
```
```
wdsutil /verbose /add-ImageDriverPackagmedia:"WinPE Boot Image" /Server:MyWDSServemediatype:Boot /Architecture:x64 /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса командной строки](command-line-syntax-key.md)
[с помощью команды Add-имажедриверпаккажес](using-the-add-imagedriverpackages-command.md)
