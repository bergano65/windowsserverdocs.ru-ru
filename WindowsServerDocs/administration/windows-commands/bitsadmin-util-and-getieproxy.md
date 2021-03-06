---
title: битсадмин util и жетиепрокси
description: Раздел команд Windows для **битсадмин util и жетиепрокси** — получение сведений об использовании прокси-сервера для данной учетной записи службы.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6d50c7e3-f4eb-4ca5-9f0c-4ed396087db6
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6936e088ddcf467b5a8f931bc8217ba9da4662c2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71380269"
---
# <a name="bitsadmin-util-and-getieproxy"></a>битсадмин util и жетиепрокси

> Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Возвращает сведения об использовании прокси-сервера для данной учетной записи службы.

## <a name="syntax"></a>Синтаксис

```
bitsadmin /Util /GetIEProxy <Account> [/Conn <ConnectionName>]
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|-------|--------|
|Учетная запись|Указывает учетную запись службы, параметры прокси которой необходимо получить. Возможные значения:<br /><br />-LOCALSYSTEM<br />-NETWORKSERVICE<br />-LOCALSERVICE|
|ConnectionName|Необязательно используется с параметром **/conn** для указания используемого подключения к модему. Если параметр **/conn** не указан, служба BITS использует подключение по локальной сети. Укажите имя подключения к модему сразу после параметра **/conn** .|

## <a name="remarks"></a>Примечания

Этот параметр показывает значение для каждого использования прокси-сервера, а не только использование прокси-сервера, указанного для учетной записи службы. Дополнительные сведения о настройке использования прокси-сервера для учетных записей служб см. в разделе [битсадмин util and сетиепрокси](bitsadmin-util-and-setieproxy.md) Switch.

## <a name="BKMK_examples"></a>Примеров

В следующем примере показано использование прокси-сервера для учетной записи сетевой службы.

```
C:\>bitsadmin /Util /GetIEProxy NETWORKSERVICE
```

## <a name="additional-references"></a>Дополнительные ссылки

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
