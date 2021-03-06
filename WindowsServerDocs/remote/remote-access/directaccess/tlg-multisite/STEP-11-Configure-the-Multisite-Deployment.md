---
title: Шаг 11. Настройка многосайтового развертывания
description: 'Этот раздел является частью руководства по лаборатории тестирования: демонстрация многосайтового развертывания DirectAccess для Windows Server 2016'
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cbdeb1d-5f7c-4360-bcc1-ab40d3cd8040
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3a80697665eeb67c2dda0d4d25201c7d02ed0c7e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404807"
---
# <a name="step-11-configure-the-multisite-deployment"></a>Шаг 11. Настройка многосайтового развертывания

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

Чтобы настроить развертывание с несколькими сайтами, внесите изменения в текущий мастер настройки удаленного доступа на EDGE1, включите многосайтовую функцию, а затем добавьте 2-EDGE1 в качестве второй точки входа.  
  
- Настройка удаленного доступа на EDGE1  
  
- Включение многосайтовой конфигурации в EDGE1  
  
- Добавление 2-EDGE1 в качестве второй точки входа  
  
## <a name="configDA"></a>Настройка удаленного доступа на EDGE1  
  
1.  На **начальном** экране введите**рамгмтуи. exe**и нажмите клавишу ВВОД. Если появится диалоговое окно **контроля учетных записей**, подтвердите, что отображаемое в нем действие именно то, которое требуется, и нажмите кнопку **Да**.  
  
2.  В консоли управления удаленным доступом щелкните **Конфигурация**.  
  
3.  В средней области консоли в области **сервер удаленного доступа шаг 2** нажмите кнопку **изменить**.  
  
4.  Щелкните **Конфигурация префикса**. На странице **Конфигурация префикса** в **префиксах IPv6 внутренней сети**введите **2001: db8:1::/64; 2001: db8:2::/64**. В качестве **префикса IPv6, назначенного клиентским компьютерам DirectAccess**, введите **2001: db8:1: 1000::/64**, нажмите кнопку **Далее**, а затем нажмите кнопку **Готово**.  
  
5.  На средней панели консоли в области **Шаг 3. серверы инфраструктуры** нажмите кнопку **изменить**.  
  
6.  Щелкните **список поиска DNS-суффиксов**. На странице **список поиска DNS-суффиксов** убедитесь, что установлен флажок **настроить клиенты DirectAccess с суффиксом DNS-клиента** , и что суффиксы домена **Corp.contoso.com** и **corp2.Corp.contoso.com** в списке **использовать суффиксы домена** нажмите кнопку **Далее**, а затем кнопку Готово.  
  
7.  В средней области консоли нажмите кнопку **Готово**.  
  
8.  В диалоговом окне **Проверка удаленного доступа** просмотрите параметры конфигурации и нажмите кнопку **Применить**. В диалоговом окне **Применение параметров мастера настройки удаленного доступа** нажмите кнопку **Закрыть**.  
  
9. В области **задачи** щелкните **обновить серверы управления**и нажмите кнопку **Закрыть** после завершения.  
  
## <a name="EnabledMultisite"></a>Включение многосайтовой конфигурации в EDGE1  
  
1.  В консоли управления удаленным доступом в области **задачи** щелкните **включить многосайтовое**подключение.  
  
2.  В мастере включения многосайтового развертывания на странице **перед началом** работы нажмите кнопку **Далее**.  
  
3.  На странице **имя развертывания** в поле **имя многосайтового развертывания**введите **contoso**, в **первом поле Имя точки входа**введите **EDGE1-site**, а затем нажмите кнопку **Далее**.  
  
4.  На странице **Выбор точки входа** щелкните **автоматически назначить точки входа и разрешить клиентам выбирать вручную**, а затем нажмите кнопку **Далее**.  
  
5.  На странице **Глобальная балансировка нагрузки** выберите **нет, не использовать глобальную балансировку нагрузки**, а затем нажмите кнопку **Далее**.  
  
6.  На странице **Поддержка клиентов** щелкните **разрешить клиентским компьютерам под управлением Windows 7 доступ к этой точке входа**и нажмите кнопку **добавить**.  
  
7.  В диалоговом окне **Выбор групп** в поле **Введите имена объектов для выбора**введите **Win7_Clients_Site1**, нажмите кнопку **ОК**, а затем нажмите кнопку **Далее**.  
  
8.  На странице **Параметры объекта групповой политики клиента** нажмите кнопку **Далее**.  
  
9. На странице **Сводка** нажмите кнопку **зафиксировать**.  
  
10. В диалоговом окне **Включение многосайтового развертывания** нажмите кнопку **Закрыть** , а затем в мастере включения многосайтового развертывания нажмите кнопку **Закрыть**.  
  
## <a name="AddEP"></a>Добавление 2-EDGE1 в качестве второй точки входа  
  
1.  В консоли управления удаленным доступом в области **задачи** щелкните **Добавить точку входа**.  
  
2.  В мастере добавления точки входа на странице **сведения о точке входа** в поле **сервер удаленного доступа**введите **2-EDGE1.corp2.Corp.contoso.com**, в поле **имя точки входа**введите **2-EDGE1-site**, а затем нажмите кнопку **Далее**.  
  
3.  На странице **топология сети** щелкните элемент **граница**и нажмите кнопку **Далее**.  
  
4.  На странице **Сетевое имя или IP-адрес** в поле **введите общедоступное имя или IP-адрес, используемые клиентами для подключения к серверу удаленного доступа**, введите **2-EDGE1.contoso.com**, а затем нажмите кнопку **Далее**.  
  
5.  На странице **Сетевые адаптеры** убедитесь, что **внешний адаптер** имеет значение **Интернет**, **Внутренний адаптер** — **2**, а сертификат — **CN = 2-EDGE1.contoso.com**, а затем нажмите кнопку **Далее**.  
  
6.  На странице **Конфигурация префикса** в поле **IPv6-префикс, назначенное клиентским компьютерам DirectAccess**введите **2001: db8:2: 2000::/64**, а затем нажмите кнопку **Далее**.  
  
7.  На странице **Поддержка клиентов** щелкните **разрешить клиентским компьютерам под управлением Windows 7 доступ к этой точке входа**и нажмите кнопку **добавить**.  
  
8.  В диалоговом окне **Выбор групп** в поле **Введите имена объектов для выбора**введите **Win7_Clients_Site2**, нажмите кнопку **ОК**, а затем нажмите кнопку **Далее**.  
  
9. На странице **Параметры объекта групповой политики клиента** нажмите кнопку **Далее**.  
  
10. На странице **Параметры объекта групповой политики сервера** нажмите кнопку **Далее**.  
  
11. На странице **Сводка** нажмите кнопку **зафиксировать**.  
  
12. В диалоговом окне **Добавление точки входа** нажмите кнопку **Закрыть** , а затем в мастере добавления точки входа нажмите кнопку **Закрыть**.  
  


