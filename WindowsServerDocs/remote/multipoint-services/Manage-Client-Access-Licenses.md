---
title: Управление клиентскими лицензиями
description: Узнайте, как работать с клиентских лицензий в службах MultiPoint
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 675e089e-d841-401e-bba7-69f3929ef609
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 744c2d7ff2965474b90686f88c21f7e6d87deced
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59813665"
---
# <a name="manage-client-access-licenses"></a>Управление клиентскими лицензиями
Каждая станция, подключаемая к системе MultiPoint Services, включая компьютер, на котором работает MultiPoint Services, используемый в качестве станции, должен иметь допустимый пользователя удаленного рабочего стола *клиентской лицензии (CAL)*.

Если вы используете виртуальные рабочие столы станций вместо физических станции, необходимо установить CAL для каждой станции виртуальных рабочих столов.  
  
1.  Приобрести клиентскую лицензию для каждой станции, подключенной к вашему компьютеру MultiPoint Services или сервера. Дополнительные сведения о приобретении клиентских лицензий обратитесь к документации для лицензирования удаленного рабочего стола. <!--@Liza: add link to RDS licensing here-->

2.  Из **запустить** экране откройте **MultiPoint Manager**.  
  
3.  Нажмите кнопку **Главная** , а затем щелкните **Добавление клиентских лицензий**.  Откроется средство управления для лицензирования CAL.

# <a name="set-the-licensing-mode-manually"></a>Установка режима лицензирования вручную
Если не правильно настроить MultiPoint Services настройки отобразится запрос с уведомлением о истек срок действия льготного периода. Выполните следующие действия, чтобы задать режим лицензирования.

1. Запустите **редактор локальных групповых политик** (gpedit.msc).

2. В области слева, перейдите к **политика локального компьютера "->" Конфигурация компьютера - > Административные шаблоны -> Windows -> компоненты удаленного рабочего стола служб - > узла сеансов удаленных рабочих столов "->" Лицензирование**.

3. В области справа щелкните правой кнопкой мыши **использовать указанный серверы лицензирования удаленных рабочих столов** и выберите **изменить**:
  - В диалоговом окне редактора групповой политики, выберите **включено**
  - Введите имя локального компьютера в **серверы для использования лицензий** поля.
  - Выберите **ОК**
  
4. В области справа щелкните правой кнопкой мыши **Установка режима лицензирования удаленного рабочего стола** и выберите **изменение**
 - В диалоговом окне редактора групповой политики, выберите **включено**
 - Задайте **режим лицензирования** для каждого устройства / для отдельного пользователя
 - Выберите **ОК** 

  
## <a name="see-also"></a>См. также  
[Управление системными задачами с помощью MultiPoint Manager](Manage-System-Tasks-Using-MultiPoint-Manager.md)