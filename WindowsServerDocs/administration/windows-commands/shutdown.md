---
title: shutdown
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c432f5cf-c5aa-4665-83af-0ec52c87112e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5d03a8d35f3e56ec7829bc51c1499fddd13b86e8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59837255"
---
# <a name="shutdown"></a>shutdown



Можно выключить или перезагрузить локальных или удаленных компьютерах одной за раз.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
shutdown [/i | /l | /s | /r | /a | /p | /h | /e] [/f] [/m \\<ComputerName>] [/t <XXX>] [/d [p|u:]<XX>:<YY> [/c "comment"]] 
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|/i|Отображает **удаленного диалоговое окно Завершение работы** поле. **/I** должен указываться после команды первого параметра. Если **/i** указан, все остальные параметры игнорируются.|
|/l|Осуществляет выход текущего пользователя немедленно, без периода времени ожидания. Нельзя использовать **/l** с **/m** или **/t**.|
|/s|Завершает работу компьютера.|
|/r|Перезапускает компьютер после завершения работы.|
|/a|Прерывает выполнение завершением. Вступают в силу только в течение периода времени ожидания. Чтобы использовать **/a**, необходимо также использовать **/m** параметр.|
|/p|Выключает только на локальном компьютере (удаленный компьютер) — без времени ожидания или предупреждение. Можно использовать **/p** только с **/d** или **/f**. Если компьютер не поддерживает выключение функциональные возможности, он завершит работу, при использовании **/p**, но питание компьютера не будут удалены.|
|/h|Переводит локальный компьютер в спящий режим, если включен режим гибернации. Можно использовать **/h** только с **/f**.|
|/e|Используется для документирования причины неожиданного завершения работы на конечном компьютере.|
|/f|Принудительное выполнение приложения будут закрываться без предупреждения пользователя.</br>Осторожно. С помощью **/f** параметр может привести к потере несохраненных данных.|
|/m \\ \\ \<имя_компьютера >|Указание целевого компьютера. Нельзя использовать с **/l** параметр.|
|/t \<XXX >|Задает интервал времени ожидания или задержка *XXX* секунд до перезагрузки или завершения работы. В результате на локальной консоли отображается предупреждение. Можно указать 0 до 600 секунд. Если вы не используете **/t**, период ожидания составляет 30 секунд по умолчанию.|
|/d [p\|u:]\<XX>:\<YY>|Списки причин перезагрузки или завершения работы. Ниже приведены значения параметров.</br>**p** указывает, что планируется перезагрузки или завершения работы.</br>**u** указывает, что причина в том, определяемые пользователем.</br>Примечание. Если **p** или **u** не указаны, перезагрузки или завершения работы не запланировано.</br>*XX* номер основной причины (положительное целое число меньше 256).</br>*ГГ* номер дополнительной причины (целое положительное число, меньшее 65536).|
|/c "\<комментарий >»|Позволяет ввести подробный комментарий о причине завершения работы. Во-первых, необходимо указать причину, используя **/d** параметр. Комментарии необходимо заключить в кавычки. Можно использовать до 511 символов.|
|/?|Отображает справку командной строки, включая список основных и дополнительных версий причины, которые определены на локальном компьютере.|

## <a name="remarks"></a>Примечания

-   Пользователям должны быть назначены **завершение работы системы** право завершить работу локального или удаленного администрирования компьютера, использующего **завершение работы** команды.
-   Пользователи должны быть членами группы "Администраторы" для добавления заметок к непредвиденного завершения работы локальных или удаленно администрируемого компьютера. Если целевой компьютер будет присоединен к домену, члены группы "Администраторы домена" может иметь возможность выполнения этой процедуры. Дополнительные сведения см. в следующих разделах:  
    -   [Локальные группы по умолчанию](https://technet.microsoft.com/library/cc785098(v=ws.10).aspx)
    -   [Группы по умолчанию](https://technet.microsoft.com/library/cc756898(v=ws.10).aspx)
-   Если вы хотите завершить работу более чем на одном компьютере одновременно, можно вызвать **завершение работы** для каждого компьютера с помощью скрипта, или могут использовать **завершение работы** **/i** для отображения удаленного Диалоговое окно завершения работы.
-   Если указать основной и дополнительный причины, необходимо сначала определить эти коды причин на каждом компьютере, где планируется использовать причины. Если коды причины не определены на целевом компьютере, регистрации событий завершения работы не удается зарегистрировать правильный текст причины.
-   Не забудьте указать, что завершение работы было запланировано с помощью **p:** параметра. Пропуск **p:** указывает, что завершение работы незапланированной. При вводе **p:** следуют код причины для незапланированного завершения работы, команда не выполнит завершение работы. И наоборот Если опустить **p:** и типа в код причины для запланированного завершения работы, команда не выполнит завершение работы.

## <a name="BKMK_examples"></a>Примеры

Чтобы заставить приложение, чтобы закрыть и перезагрузить локальный компьютер с задержкой до минуты с указанием причины «приложение: Обслуживание (запланированное)» и комментарий «Перенастройка myapp.exe» тип:
```
shutdown /r /t 60 /c "Reconfiguring myapp.exe" /f /d p:4:1
```
Чтобы перезагрузить удаленный компьютер \\ \\ServerName с теми же параметрами, введите:
```
shutdown /r /m \\servername /t 60 /c "Reconfiguring myapp.exe" /f /d p:4:1
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)