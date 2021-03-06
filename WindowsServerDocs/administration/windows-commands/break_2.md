---
title: break
description: Раздел команд Windows для **break_2** — отменяет связь тома теневых копий из VSS и делает его доступным как обычный том.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: de2b6c95-1c2e-4a43-bec5-341a9014371b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a5789e3442152c705b3197bf1ce5e63dc782a15c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71379784"
---
# <a name="break"></a>break



Отменяет связь тома теневой копии с VSS и делает его доступным как обычный том. Доступ к тому можно получить с помощью буквы диска (если она назначена) или имени тома. Если используется без параметров, команда **break** отображает справку в командной строке.

> [!NOTE]
> Эта команда относится только к аппаратным теневым копиям после импорта.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
break [writable] <SetID>
```

## <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------|-----------|
|записывать|Включает доступ на чтение и запись для тома.|
|\<Сетид >|Указывает идентификатор набора теневых копий.|

## <a name="remarks"></a>Замечания

-   Предоставляемые тома, например теневые копии, из которых они берутся, доступны только для чтения по умолчанию.
-   Псевдоним идентификатора теневой копии, который хранится в виде переменной среды с помощью команды **загрузить метаданные** , можно использовать в параметре *сетид* .

## <a name="BKMK_examples"></a>Примеров

Чтобы сделать теневую копию с именем псевдонима Alias1 доступной в качестве тома с возможностью записи в операционной системе, введите:
```
break writable %Alias1%
```

> [!NOTE]
> Доступ к тому предоставляется непосредственно поставщику оборудования без записи тома, имеющего теневую копию.

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)