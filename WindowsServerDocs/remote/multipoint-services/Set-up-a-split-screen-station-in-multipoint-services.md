---
title: Установка станции с разделенными экранами
description: Описывается, как настроить MultiPoint Services, чтобы два пользователя могут совместно использовать одну систему
ms.custom: na
ms.date: 07/22/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35d1d434-79b2-4e0a-835f-d94ed8ee6b21
author: evaseydl
manager: scottman
ms.author: evas
ms.openlocfilehash: b2d01df6175eee99fd1374cd5af270cbcc764ca8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849945"
---
# <a name="set-up-a-split-screen-station"></a>Установка станции с разделенными экранами
Можно настроить станцию разделенного окна, два пользователя одновременно можно использовать систему.

Любой монитор с разрешением минимальное 1200 x 720, при подключении к станции, которая поддерживает эту функцию с разделенным экраном, можно разделить на две станции. После разделения станции, рабочего стола, который монитор, отображающий перемещается на левую половину экрана и новую станцию отображается на правой половине экрана. Чтобы завершить создание новой станции, необходимо сопоставить клавиатурой, мышью и USB-концентратору станции. После того, как станция будет разделена, один пользователь сможет войти на станцию слева, а другой — на станцию справа.  
  
Станции с разделенным экраном имеет несколько преимуществ.  
  
-   Можно уменьшить расходов и занимаемого места, приспособление дополнительных пользователей в системе MultiPoint Services.  
  
-   Два пользователя могут совместно работать вместе, бок о бок, над проектом.  
  
-   Пользователь MultiPoint Dashboard могут демонстрировать процедуру на одной рабочей станции, то время как учащийся на другие станции.  
  
Ниже показана система MultiPoint Services с экрана объединение разделенной станции (справа).  
  
![Станции с разделенными экранами](./media/WMS_diagram3.gif)  
   
## <a name="requirements-for-a-split-screen-station"></a>Требования для экрана объединение разделенной станции  
Для создания разделенного окна станции, на станции и монитор должен соответствовать следующим требованиям:  
  
-   Монитор должен иметь разрешение 1200 x720 или более поздней версии.  
  
-   Если вы используете клиент USB через Ethernet нулю, проверьте у поставщика оборудования, чтобы узнать, поддерживаются ли станции с разделенным экраном. Многие клиентские устройства USB через Ethernet ноль имеют ограничения, которые препятствуют их конфигурации в качестве станции с разделенным экраном.  
  
## <a name="setting-up-a-split-screen-station"></a>Настройка станции с разделенным экраном  
Используйте следующие процедуры для добавления во второй концентратор для станции с разделенным экраном и затем разделить станцию в MultiPoint Services. Последняя процедура объясняет, как для возврата одной станции станции с разделенным экраном.  
  
> [!NOTE]  
> В случае разделения активный сеанс на станции приостанавливается. Пользователю необходимо войти в систему еще раз, чтобы продолжить работу после разделения станции.  
  
**Чтобы добавить второй концентратор с клавиатуры и мыши:**  
  
1.  Подключение USB-концентратор к доступному порту USB на компьютере, как показано на следующем рисунке.  
  
    ![Снимок экрана: MultiPoint server подключение USB-концентратора](./media/WMSUSBHubConnection.gif)  
  
2.  Подключите клавиатуру и мышь к USB-концентратору.  
  
    ![Изображение входящих подключений устройств к USB-концентратору](./media/WMSUSBDeviceConnection.gif)  
  
3.  Подключите все Дополнительные периферийные устройства, например наушники к USB-концентратору.  
  
4.  Если вы используете концентратор с внешним питанием, подключите кабель питания концентратора к розетке питания.  
  
**Разделение станции:**  
  
1.  В диспетчере MultiPoint щелкните **станции** вкладки.  
  
2.  В разделе **станции**, выберите имя станции, которую необходимо разделить.  
  
3.  В разделе **задачи для выбранного элемента**, нажмите кнопку **разделение станции**.  
  
    Исходное окно перемещается на левую половину экрана монитора, а на правой половине том же мониторе создается новая станция экрана.  
  
4.  Создание новой станции, нажав на вновь добавленный клавиатуры указанного письма, как указано при **создания станции MultiPoint Server** экран отображается на правой половине монитор.  
  
После разделения станции, один пользователь может войти станцию слева, а другой — на станцию справа.  
  
**Для возврата одной станции объединение разделенной станции:**  
  
1.  В диспетчере MultiPoint щелкните **станции** вкладки.  
  
2.  В разделе **станции**, щелкните имя нужной станции неразбитый.  
  
3.  В разделе **задачи для выбранного элемента**, нажмите кнопку **Отменить разделение станции**.