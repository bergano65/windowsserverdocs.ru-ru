---
title: wscript
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fbaf193-cdbd-414c-84c9-bb5720f84c29
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 08/21/2018
ms.openlocfilehash: 771c1231ee5379ec797f535505839de8671e32a8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821305"
---
# <a name="wscript"></a>wscript



Сервер сценариев Windows предоставляет среду, в котором пользователи могут выполнять скрипты в различных языков, использующих разнообразные объектные модели для выполнения задач.

## <a name="syntax"></a>Синтаксис

```
wscript [<scriptname>] [/b] [/d] [/e:<engine>] [{/h:cscript|/h:wscript}] [/i] [/job:<identifier>] [{/logo|/nologo}] [/s] [/t:<number>] [/x] [/?] [<ScriptArguments>]
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|имя_сценария|Указывает путь и имя файла скрипта.|
|/b|Указывает режим пакетной службы, в котором не отображаются предупреждения, сообщения об ошибках и запросов на входные данные. Это противоположность **/i**.|
|/d|Запускает отладчик.|
|/e|Задает обработчик, который используется для запуска скрипта. Это позволяет выполнять сценарии, использующие расширение имени файла. Без параметра /e можно выполнять только скрипты, использующие зарегистрированных расширений. Например, если вы попытаетесь выполнить эту команду:<br>```cscript test.admin```<br>Вы получите следующее сообщение об ошибке: Ошибка ввода: Имеется обработчик сценария для расширения файла «. администратором.»<br>Одно из преимуществ использования расширений имен файлов в нестандартных — что он защищает от случайного дважды щелкните сценарий и запуска чего-либо был не действительно необходимо запустить. <br>Это не создает постоянного связь между расширением .admin и VBScript. Каждый раз при запуске сценарий, который использует расширение имени файла .admin необходимо будет использовать параметр /e.|
|/ h|Регистрирует **cscript.exe** как сервера сценариев по умолчанию для выполнения скриптов.|
|/h:wscript|Регистрирует **wscript.exe** как сервера сценариев по умолчанию для выполнения скриптов. Это значение по умолчанию при **/h** опущен параметр.|
|/i|Указывает интерактивный режим, в котором отображаются предупреждения, сообщения об ошибках и запросов на входные данные.</br>Это значение по умолчанию и противоположностью **/b**.|
|/job:\<identifier>|Запускает задание, определяемое *идентификатор* в **.wsf** файл скрипта.|
|/Logo|Указывает, что Windows Script Host баннер отображается в консоли, перед выполнением сценария.</br>Это значение по умолчанию и противоположностью **/nologo**.|
|/ nologo|Указывает, что Windows Script Host баннер не отображается, перед выполнением сценария. Это противоположность **/logo**.|
|/s|Сохраняет текущие параметры командной строки для текущего пользователя.|
|/ t:\<номер >|Указывает максимальное время выполнения сценария (в секундах). Можно указать до 32 767 секунд.</br>По умолчанию используется без временных ограничений.|
|/x|Запускает сценарий в отладчике.|
|Аргументы_сценария|Задает аргументы, переданные в сценарий. Каждый аргумент скрипт должен предшествовать косая черта (/).|
|/?|Отображает справку в командной строке.|

## <a name="remarks"></a>Примечания

-   Для выполнения этой задачи не требуются права, соответствующие учетным данным администратора. Таким образом, по соображениям безопасности ее рекомендуется выполнять от имени пользователя, не обладающего правами на администрирование системы.
-   Чтобы открыть командную строку, на **начальном экране** введите **cmd** и щелкните **командная строка**.
-   Все параметры являются необязательными; Тем не менее нельзя указать аргументы скрипта, не указывая сценарий. Если вы не укажете сценарий или любые аргументы скрипта **wscript.exe** отображает **параметры сервера сценариев Windows** диалоговое окно, который можно использовать, чтобы задать глобальные свойства для всех сценариев этого **wscript.exe** выполняется на локальном компьютере.
-   **/T** параметр предотвращает чрезмерное выполнение сценариев с помощью таймера. Если время превышает указанное значение **wscript** прерывает работу обработчика сценариев и завершает процесс.
-   Файлы скриптов Windows обычно имеют один из следующих расширений имени файла: **.wsf**, **.vbs**, **.js**.
-   Если дважды щелкнуть файл сценария с расширением, не связан ни, **открыть с помощью** откроется диалоговое окно. Выберите **wscript** или **cscript**, а затем выберите **всегда используйте программу для открытия данного типа файлов**. При этом регистрируется **wscript.exe** или **cscript.exe** как сервера сценариев по умолчанию для файлов этого типа.
-   Можно задать свойства для отдельных сценариев. См. в разделе [Обзор Windows Script Host](https://technet.microsoft.com/library/cc738350(v=ws.10).aspx) Дополнительные сведения.
-   Можно использовать Windows Script Host **.wsf** файлы скриптов. Каждый **.wsf** файл может иметь несколько обработчиков и выполнять несколько заданий.

#### <a name="additional-references"></a>Дополнительная справка

-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)