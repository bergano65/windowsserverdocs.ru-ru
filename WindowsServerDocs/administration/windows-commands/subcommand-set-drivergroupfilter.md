---
title: Набор подкоманд-Дриверграупфилтер
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 829ab1f0-4514-421e-9cc0-767b238da69c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: efdfd3aa1725749d177f06ff23deb777529a95a6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71383848"
---
# <a name="subcommand-set-drivergroupfilter"></a>Подкоманда: Set-Дриверграупфилтер



Добавляет или удаляет существующий фильтр группы драйверов из группы драйверов.

## <a name="syntax"></a>Синтаксис

```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> [/Policy:{Include | Exclude}] [/AddValue:<Value> [/AddValue:<Value> ...]] [/RemoveValue:<Value> [/RemoveValue:<Value> ...]]
```

## <a name="parameters"></a>Параметры

|         Параметр          |                                                                                                                                                                                                                                                                                                                                                                                                                                                                               Описание                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| /Дриверграуп: имя группы\<> |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Указывает имя группы драйверов.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|  [/Server:\<имя сервера >]  |                                                                                                                                                                                                                                                                                                                                                                                                                Указывает имя сервера. Это может быть NetBIOS-имя или FQDN. Если имя сервера не указано, используется локальный сервер.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| /Филтертипе:\<FilterType >  |                                                                                                                                                                                                                                                                       Указывает тип фильтра группы драйверов для добавления или удаления. В одной команде можно указать несколько фильтров. Для каждого **/филтертипе**можно добавить или удалить несколько значений с помощью **/ремовевалуе** и **/аддвалуе**. \<FilterType > может быть одним из следующих:</br>**биосвендор**</br>**биосверсион**</br>**чассистипе**</br>**Производителя**</br>**UUID**</br>**OsVersion**</br>**оседитион**</br>**ослангуаже**                                                                                                                                                                                                                                                                        |
|     [/Полици: {include      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                Exclude}]                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|    [/Аддвалуе:\<значение >]    | Указывает новое значение клиента, добавляемое в фильтр. Для одного типа фильтра можно указать несколько значений. Допустимые значения атрибутов для **чассистипе**см. в следующем списке. Сведения о получении значений для всех других типов фильтров см. в разделе [фильтры группы драйверов](https://go.microsoft.com/fwlink/?LinkID=155158) (<https://go.microsoft.com/fwlink/?LinkID=155158>).</br>**Иной**</br>**ункновнчассис**</br>**Настольный компьютер**</br>**ловпрофиледесктоп**</br>**пиззабокс**</br>**минитовер**</br>**Вертикаль**</br>**Устройств**</br>**Ноутбук**</br>**Занятий**</br>**Перенос**</br>**доккингстатион**</br>**аллиноне**</br>**Подзаписная книжка**</br>**спацесавинг**</br>**лунчбокс**</br>**маинсистемчассис**</br>**експансиончассис**</br>**Подшасси**</br>**бусекспансиончассис**</br>**перифералчассис**</br>**сторажечассис**</br>**раккмаунтчассис**</br>**сеаледкасекомпутер**</br>**мултисистемчассис**</br>**компактпЦи**</br>**адванцедтка** |
|  [/Ремовевалуе:\<значение >]   |                                                                                                                                                                                                                                                                                                                                                                                                                                     Указывает существующее значение клиента, которое необходимо удалить из фильтра, как указано в **/аддвалуе**.                                                                                                                                                                                                                                                                                                                                                                                                                                      |

## <a name="BKMK_examples"></a>Примеров

Чтобы удалить фильтр, введите один из следующих элементов:
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /AddValue:Name1 /RemoveValue:Name2
```
```
WDSUTIL /Set-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /RemoveValue:Name1 /FilterType:ChassisType /Policy:Exclude /AddValue:Tower /AddValue:MiniTower
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)