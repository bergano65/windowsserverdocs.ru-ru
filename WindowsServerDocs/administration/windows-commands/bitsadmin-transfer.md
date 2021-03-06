---
title: bitsadmin Transfer
description: Раздел команд Windows для **передачи битсадмин** — передача одного или нескольких файлов.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fe302141-b33a-4a05-835e-dc4fc4db7d5a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a12e6e2023c979d5b0c095c1eddd77eb5155d1e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380351"
---
# <a name="bitsadmin-transfer"></a>bitsadmin Transfer

Передает один или несколько файлов. Чтобы переместить более одного файла, укажите несколько \<Ремотефиленаме\>-\<Локалфиленаме\> пар. Эти пары разделяются пробелами.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Transfer <Name> [<Type>] [/Priority <Job_Priority>] [/ACLFlags <Flags>] [/DYNAMIC] <RemoteFileName> <LocalFileName>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Имя|Имя задания. В отличие от большинства команд, **имя** может быть только именем, а не идентификатором GUID.|
|Тип|Необязательно — укажите тип задания. Используйте **/download** (значение по умолчанию) для задания загрузки или **/upload** для задания отправки.|
|Priority|(Необязательно) задайте для job_priority одно из следующих значений:</br>— ПЕРЕДНИй план</br>-ВЫСОКИЙ</br>— Обычная</br>-Низкий уровень|
|аклфлагс|(Необязательно) указывает, что вы хотите сохранить сведения о владельце и списке управления доступом с загружаемым файлом. Например, чтобы сохранить владельца и группу с файлом, установите флаги в значение `OG`. Укажите один или несколько следующих флагов:</br>-O: копирование сведений о владельце с помощью файла.</br>-G: копирование сведений о группе с помощью файла.</br>-D: копирование сведений DACL в файл.</br>-S: копирование сведений SACL с помощью файла.|
|\/DYNAMIC|Настраивает задание с [**BITS_JOB_PROPERTY_DYNAMIC_CONTENT**](/windows/desktop/api/bits5_0/ne-bits5_0-bits_job_property_id), что ослабляет требования на стороне сервера.|
|ремотефиленаме|Имя файла при передаче на сервер.|
|локалфиленаме|Имя файла, расположенного локально.|

## <a name="remarks"></a>Замечания

По умолчанию служба Битсадмин создает задание загрузки, которое выполняется с **нормальным** приоритетом, и обновляет окно командной строки с информацией о ходе выполнения до тех пор, пока не завершится процесс перемещения или не будет вызвана критическая ошибка. Служба завершает задание, если успешно передает все файлы и отменяет задание в случае возникновения критической ошибки. Служба не создает задание, если не удается добавить файлы в задание или если указано недопустимое значение для *типа* или *Job_Priority*. Чтобы переместить более одного файла, укажите несколько пар *ремотефиленаме*-*локалфиленаме* . Эти пары разделяются пробелами.

> [!NOTE]
> Команда Битсадмин продолжит работу при возникновении временной ошибки. Чтобы завершить команду, нажмите клавиши CTRL + C.

## <a name="BKMK_examples"></a>Примеров

В следующем примере запускается задание перемещения с именем *мидовнлоаджоб*.
```
C:\>bitsadmin /Transfer myDownloadJob http://prodserver/audio.wma c:\downloads\audio.wma
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)