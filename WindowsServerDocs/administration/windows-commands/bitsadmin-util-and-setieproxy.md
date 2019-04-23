---
title: bitsadmin util и setieproxy
description: Раздел Windows команды для **bitsadmin util и setieproxy** -задайте параметры прокси-сервера для использования при передаче файлов с помощью учетной записи службы.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e9f31ba-3070-4ffd-a94c-388c8d78f688
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d4f6ab2e52284895d2e7918364c24bbb69f2b1c9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59853515"
---
# <a name="bitsadmin-util-and-setieproxy"></a>bitsadmin util и setieproxy

Задайте параметры прокси-сервера для использования при передаче файлов с помощью учетной записи службы.

**BITSAdmin 1.5 и более ранних**: Не поддерживается.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /SetIEProxy <Account> <Usage>[/Conn <ConnectionName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|Учетная запись|Указывает тип учетной записи службы прокси-сервера, параметры которого требуется определить. Возможные значения:</br>-LOCALSYSTEM</br>-СЕТЕВОЙ СЛУЖБЫ</br>-LOCALSERVICE|
|Использование|Указывает форму обнаружение прокси-сервера для использования. Возможные значения:</br>-NO_PROXY — не использовать прокси-сервер.</br>-АВТООБНАРУЖЕНИЕ — автоматическое определение параметров прокси-сервера.</br>-MANUAL_PROXY — использовать список явных прокси-сервера, а также в список исключений. Укажите список прокси-сервера и сразу после использования тега список обхода. Например, MANUAL_PROXY proxy1 proxy2 NULL.</br>    -Список прокси-сервера является разделенный запятыми список прокси-серверов для использования.</br>    -В списке пропускаемых адресов является список с разделителями пробелами имена узлов или IP-адреса или оба параметра, для которого передачи которых не должны направляться через прокси-сервер. Это может быть \<локальный > для ссылки на все серверы в той же локальной сети. Значение NULL или «» может использоваться для обхода списка пустой прокси-сервера.</br>-AUTOSCRIPT — Совпадает со значением АВТООБНАРУЖЕНИЕ, за исключением того, он также выполняет сценарий. Укажите URL-адрес сценария сразу после использования тега. Например, AUTOSCRIPT http://server/proxy.js.</br>-Сброс — Так же, как NO_PROXY, но удаляет URL-адресов вручную прокси-сервера (Если указано) и URL-адреса обнаружить с помощью автоматического обнаружения.|
|ConnectionName|Необязательно — используется с **/Conn** параметр, чтобы указать соединение для использования. Если вы не укажете **/Conn** параметр, BITS использует подключение по локальной сети. Укажите имя подключения модем сразу после **/Conn** параметра.|

## <a name="remarks"></a>Примечания

Каждого последующего вызова с помощью этого переключателя заменяет ранее указанного потребления, но параметры не ранее определенных использования. Например при указании NO_PROXY, АВТООБНАРУЖЕНИЕ и MANUAL_PROXY на отдельные вызовы BITS использует последнего использования предоставленного, но предотвращает использование ранее определенные параметры.

> [!IMPORTANT]
> Эту команду необходимо запустить из командной строки с повышенными правами для его успешного завершения.

## <a name="BKMK_examples"></a>Примеры

Следующий пример задает использование прокси-сервера для учетной записи СЕТЕВОЙ службы.

```
C:\>bitsadmin /Util /SetIEProxy localsystem AUTODETECT
```

Ниже приведены некоторые примеры.

```
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1,proxy2,proxy3 NULL
bitsadmin /util /setieproxy localsystem MANUAL_PROXY proxy1:80 ""
```

#### <a name="additional-references"></a>Дополнительная справка

[Ключ синтаксиса командной строки](command-line-syntax-key.md)