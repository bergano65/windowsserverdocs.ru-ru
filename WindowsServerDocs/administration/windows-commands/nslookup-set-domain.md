---
title: nslookup set domain
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9d4d28e8-6e88-42cc-801f-94e9d8e051f4
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f140a371a6374baa7921ca823df469156593423c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71372934"
---
# <a name="nslookup-set-domain"></a>nslookup set domain

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

изменяет доменное имя DNS по умолчанию на указанное имя.
## <a name="syntax"></a>Синтаксис
```
set domain=<DomainName>
```
## <a name="parameters"></a>Параметры

|    Параметр    |                                           Описание                                           |
|-----------------|-------------------------------------------------------------------------------------------------|
|  <DomainName>   | Указывает новое имя для доменного имени DNS по умолчанию. Доменное имя по умолчанию — имя узла. |
| {Help &#124; ?} |                      Отображает краткую сводку подкоманд **nslookup** .                      |

## <a name="remarks"></a>Примечания
- Доменное имя DNS по умолчанию добавляется к поисковому запросу в зависимости от состояния параметров **дефнаме** и **поиска** . Список поиска доменов DNS содержит родительские домены DNS по умолчанию, если в имени содержится по крайней мере два компонента. Например, если домен DNS по умолчанию — mfg.widgets.com, список поиска будет называться как mfg.widgets.com, так и widgets.com. Используйте команду **Set срчлист** , чтобы указать другой список, и команда **Set All** для вывода списка.
  ## <a name="additional-references"></a>Дополнительные ссылки
  [Синтаксис командной строки](command-line-syntax-key.md)
  [nslookup set срчлист](nslookup-set-srchlist.md)
  [nslookup set ALL](nslookup-set-all.md)
