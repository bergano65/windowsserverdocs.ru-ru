---
title: Использование приложения My Server для подключения к Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e40b57f-6917-43ef-92e0-030baa9d2b99
9author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 836f65551c05d50e861ca9b7d22b73bdbf4baf84
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856845"
---
# <a name="use-the-my-server-app-to-connect-to-windows-server-essentials"></a>Использование приложения My Server для подключения к Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Приложения My Server для Windows Server Essentials позволяют подключаться к ресурсам и выполнять несложные административные задачи на сервере Windows Server Essentials с ноутбука, ПК или устройства Surface. С помощью приложения My Server можно управлять пользователями, устройствами и оповещениями, а также работать с общими файлами на сервере. В автономном режиме можно продолжать работать с файлами, которые недавно открывались в приложении My Server. Автономные изменения автоматически синхронизируются с сервером при следующем подключении.  
  
 Если сервер работает под управлением операционной системы Windows Server Essentials, используйте исходное приложение My Server. Если сервер работает под управлением операционной системы Windows Server Essentials, необходимо использовать обновленное приложение My Server 2012 R2. Оба приложения можно скачать из раздела [Приложения для Windows](https://windows.microsoft.com/windows-8/apps).  
  
> [!TIP]

>  Получить доступ к ресурсам в Windows Server Essentials на Windows Phone, используйте приложение My Server для телефона (для Windows Server Essentials) или приложение для телефона My Server 2012 R2 (для Windows Server Essentials). Сведения о приложении My Server для телефона см. в разделе [используйте приложение My Server для Windows Phone](Work-Remotely-in-Windows-Server-Essentials.md#BKMK_2). Сведения о приложении My Server 2012 R2 для телефона см. в публикации в блоге [Приложения My Server 2012 R2 для Windows и Windows Phone](http://blogs.technet.com/b/sbs/archive/2013/11/19/my-server-2012-r2-windows-and-windows-phone-apps.aspx).  
  
## <a name="in-this-topic"></a>В этом разделе  
  
-   [Новых возможностях My Server 2012 R2](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_WhatsNew)  
  
-   [Требования к операционной системе](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_OS)  
  
-   [Установка приложения My Server](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_Install)  
  
-   [Использование My Server](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_UseServer)  
  
-   [Возможности My Server](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_Features)  
  
-   [Как подключиться к серверу из локальной сети](Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_ConnectServer)  

>  Получить доступ к ресурсам в Windows Server Essentials на Windows Phone, используйте приложение My Server для телефона (для Windows Server Essentials) или приложение для телефона My Server 2012 R2 (для Windows Server Essentials). Сведения о приложении My Server для телефона см. в разделе [используйте приложение My Server для Windows Phone](../use/Work-Remotely-in-Windows-Server-Essentials.md#BKMK_2). Сведения о приложении My Server 2012 R2 для телефона см. в публикации в блоге [Приложения My Server 2012 R2 для Windows и Windows Phone](http://blogs.technet.com/b/sbs/archive/2013/11/19/my-server-2012-r2-windows-and-windows-phone-apps.aspx).  
  
## <a name="in-this-topic"></a>В этом разделе  
  
-   [Новых возможностях My Server 2012 R2](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_WhatsNew)  
  
-   [Требования к операционной системе](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_OS)  
  
-   [Установка приложения My Server](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_Install)  
  
-   [Использование My Server](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_UseServer)  
  
-   [Возможности My Server](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_Features)  
  
-   [Как подключиться к серверу из локальной сети](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md#BKMK_ConnectServer)  

  
##  <a name="BKMK_WhatsNew"></a> Новых возможностях My Server 2012 R2  
 Кроме функций, доступных в My Server My Server 2012 R2 предлагает следующие новые возможности для клиентов с Windows Server Essentials:  
  
-   **Доступ к сайтам SharePoint Online группы и библиотекам** — используйте Microsoft интеграцию Office 365 с Windows Server Essentials для сайтов групп SharePoint Online и открывайте документы из библиотек SharePoint Online в My Server 2012 R2.  
  
-   **Удаленное подключение к серверу и компьютерам** -использование **удаленное подключение** в My Server 2012 R2 для подключения к серверу Windows Server Essentials и клиентских компьютеров с помощью удаленного рабочего стола.  
  
##  <a name="BKMK_OS"></a> Требования к операционной системе  
 Чтобы использовать My Server или My Server 2012 R2 на ноутбуке, ПК или устройства Surface, на компьютере должен быть один из следующих операционных систем:  Windows 8.1, Windows RT 8.1, Windows 8 или Windows RT.  
  
##  <a name="BKMK_Install"></a> Установка приложения My Server  
 Можно скачать любое нужное приложение My Server из Магазина [приложений для Windows](https://windows.microsoft.com/windows-8/apps) . Если на компьютере установлена ОС, Windows 8 или Windows RT, и вы хотите подключиться к серверу в интрасети, используя имя сервера, необходимо также установить сертификат с сервера.  
  
#### <a name="to-install-my-server-or-my-server-2012-r2-on-your-windows-based-laptop-pc-or-surface-device"></a>Установка My Server или My Server 2012 R2 на ноутбук или ПК с Windows либо на устройство Surface  
  
1.  Установите соответствующее приложение My Server из раздела [Приложения для Windows](https://windows.microsoft.com/windows-8/apps) на ноутбук или ПК с Windows либо на устройство Surface.  
  
    |Операционная система сервера|Загрузить|  
    |-----------------------------|--------------|  
    | Windows Server Essentials|[Моего сервера](https://apps.microsoft.com/webpdp/app/19d94f81-db21-4234-8b49-806694dbbaea)|  
    | Windows Server Essentials|[My Server 2012 R2](https://apps.microsoft.com/webpdp/app/67e86695-bda3-4f32-96c4-2e20e56f1cf3)|  
  
2.  Если вы хотите иметь возможность использовать имя сервера для подключения к серверу Windows Server Essentials через интрасеть и устройство имеет операционную систему Windows 8 или Windows RT, установите сертификат CAROOT.cer по умолчанию на компьютере, выполнив следующие p rocedure. Установка сертификата вручную не требуется в Windows 8.1 и Windows RT 8.1.  
  
###  <a name="BKMK_InstallCert"></a> Установка сертификата для My Server на устройстве Windows 8, Windows 8.1 или Windows RT  
  
1.  Откройте браузер на компьютере и скачайте сертификат CAROOT.cer по умолчанию с сервера. Для этого введите следующее, указав имя своего сервера (например, **marketing.contoso.com**) для <*имя_сервера*>:  
  
     **http://<ServerName\>/connect/default.aspx?get=caroot.cer**  
  
2.  Установка сертификата  
  
    1.  На **начальной** странице откройте **проводник**.  
  
    2.  Убедитесь, что скрытые элементы и расширения имен файлов отображаются. На вкладке **Представление**, в группе **Показать/скрыть** установите флажки **Скрытые элементы** и **Расширения имен файлов**.  
  
    3.  Перейдите в папку, которая содержит файл CAROOT.cer, который вы скачали.  
  
    4.  Щелкните правой кнопкой мыши файл CAROOT.cer и выберите в меню пункт **Открыть**.  
  
    5.  В диалоговом окне **Сертификат** щелкните **Установить сертификат**.  
  
    6.  Выберите **Локальный компьютер** в качестве расположения установки, а затем нажмите кнопку **Далее**.  
  
    7.  На странице мастера **хранения сертификатов** выберите **Поместить все сертификаты в следующее хранилище**и нажмите кнопку **Обзор** , чтобы выбрать хранилище **Доверенные корневые центры сертификации** . Затем нажмите кнопку **Готово**.  
  
##  <a name="BKMK_UseServer"></a> Использование My Server  
 Чтобы начать использовать приложение My Server или My Server 2012 R2, откройте приложение и кратко ознакомьтесь с его функциями.  
  
#### <a name="to-open-my-server-or-my-server-2012-r2"></a>Открытие My Server или My Server 2012 R2  
  
1.  Открытие My Server (для Windows Server Essentials) или My Server 2012 R2 (для Windows Server Essentials) из **запустить** страницы устройства Windows.  
  
2.  Войдите на сервер Windows Server Essentials с помощью учетной записи на сервере. Нахождение сервера  
  
    -   В среде за пределами организации, использовать имя домена сервера s, например, **marketing.contoso.com**.  
  
    -   Если вы подключаетесь к локальной через интрасеть, используйте имя сервера в предыдущем примере, имя сервера — **маркетинга**. (Если вы используете для подключения на локальном компьютере с Windows 8 или Windows RT, и вы хотите использовать этот метод, необходимо установить сертификат CAROOT.cer с сервера. Дополнительные сведения см. в разделе [для установки сертификата для My Server на устройстве Windows 8, Windows 8.1 или Windows RT](#BKMK_InstallCert).)  
  
###  <a name="BKMK_Features"></a> Возможности My Server  
 В следующей таблице описаны возможности приложений My Server и My Server 2012 R2. Тип учетной записи на сервере определяет, что вы можете просматривать и делать. Все пользователи могут работать с общими ресурсами, настраивать отображение **последних элементов** , определять длительность кэширования последних использованных файлов для автономного доступа и включать или отключать скачивание данных по платным подключениям. Администраторы на сервере Windows Server Essentials также могут управлять оповещениями, устройствами и пользователями. Учетные записи обычных пользователей имеют более ограниченные возможности для просмотра оповещений и подключения к устройствам, заданным свойствами в учетной записи пользователя. Требования для использования отдельных возможностей перечислены в следующей таблице.  
  
### <a name="features-of-the-my-server-and-my-server-2012-r2-apps-for-windows-server-essentials"></a>Возможности приложений My Server и My Server 2012 R2 для Windows Server Essentials  
  
|Возможности|Описание|  
|-----------------|-----------------|  
|Управление оповещениями|-(Только администраторы) разрешение оповещений на сервере или пропуск оповещений, что Дон t требуют действий. Включение и отключение уведомлений (параметры**Разрешения** , параметр **Уведомления** ).<br />— Оповещения о работоспособности сети представления (учетные записи обычного пользователя).<br />     **Примечание.** Пользователь может просматривать оповещения в My Server **пользователь может просматривать оповещения о работоспособности сети** необходимо выбрать параметр в **Общие** параметры учетной записи пользователя. Дополнительные сведения см. в разделе [Manage user accounts using the Dashboard](../manage/Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage8).|  
|Управление устройствами|(Только администраторы.)<br /><br /> -При подключении к серверу Windows Server Essentials, просмотреть сведения о каждом подключенном компьютере в **устройств** представления. Автономные устройства затенены.<br />— Запуск и остановка создания резервных копий для подключенных компьютеров.<br />-Включение и отключение уведомлений в My Server. (Параметры**Разрешения** , параметр **Уведомления** .)<br /><br /> Все пользователи.<br /><br /> — Просмотр клиентских компьютеров, к которым имеет доступ к учетной записи пользователя. (Окно**Устройства** .)<br />-Мониторинг оповещений для этих компьютеров. (Окно **Оповещения**.)<br />-(В My Server 2012 R2 только) подключение к этим компьютерам с помощью удаленного веб-доступа. (Окно**Устройство** , кнопка **Удаленное подключение** .)|  
|Подключение к компьютерам с помощью удаленного рабочего стола|(Только my Server 2012 R2) Откройте сеанс удаленного рабочего стола с сервера Windows Server Essentials или клиентском компьютере. (Окно**Устройство** , кнопка **Удаленное подключение** .)<br /><br /> **Примечание.** Чтобы включить эту функцию, загрузите и установите [приложение удаленного рабочего стола](https://apps.microsoft.com/webpdp/app/051f560e-5e9b-4dad-8b2e-fa5e0b05a480) из приложений для Windows на компьютере. Учетные записи обычных пользователей могут подключаться к устройствам, на которых им разрешено выполнять вход в систему. Чтобы разрешить пользователю вход на компьютер, добавьте компьютер на вкладку **Доступ к компьютеру** учетной записи пользователя. Дополнительные сведения см. в разделе [Assign user accounts permission to log on to specific network computers](../manage/Manage-Devices-in-Windows-Server-Essentials.md#BKMK_2).|  
|Управление пользователями|(Только администраторы.) Изменение пароля для учетной записи пользователя. Завершение сеанса пользователя s на сервере. (Параметры**Пользователи** .)|  
|Работа с общими файлами|<ul><li>Отправка и загрузка файлов из общих файлов (из общих папок на сервере имеется доступ к), из частной папки или из Windows 8.1 устройства, из SkyDrive либо сетевого хранилища. Создание папок. Добавление (отправка), изменение и удаление файлов с сервера.</li><li>Просмотр состояния передачи при отправке или скачивании файла. Отмена передачи. Разрешение конфликтов файлов.</li><li>Беспрепятственная работа с файлами и папками на локальном компьютере, сервере, в SkyDrive или сетевом хранилище. В файле перечислены папки, которые вы недавно использовали на компьютере, в SkyDrive или сетевом хранилище, а также общие папки на сервере. Здесь можно просматривать папки из любого из этих расположений.</li><li>Выполните поиск папок и файлов на сервере; щелкните файл, чтобы скачать его, и откройте его в приложении по умолчанию. В автономном режиме можно искать только автономные файлы.</li><li>Общий доступ к изображениям, музыке и видео. Щелкните файл, чтобы открыть его в изображение Windows 8, музыки или видеопроигрывателя. Либо используйте команды **Открыть** или **Открыть с помощью**, чтобы открыть файл в другом приложении. Как обычно, можно сделать выбранное приложение приложением по умолчанию для этого типа данных.<br /><br />     **Примечание.** По умолчанию функции потоковой передачи мультимедиа недоступна в Windows Server Essentials и Windows Server 2012 R2 с установленной ролью Windows Server Essentials Experience. Дополнительные сведения см. в разделе [Manage Digital Media](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md).<br /><br /> <ul><li>**Изображения** — в представлении **Изображения** коснитесь изображения, чтобы открыть его. Повторно коснитесь изображения, чтобы вернуться к представлению эскизов в My Server.</li><li>**Музыка** в **музыки** Просмотр, альбомы или композиции, переданные на сервер. Коснитесь элемента, чтобы открыть его в музыкальном проигрывателе.</li><li>**Видео** щелкните эскиз в **видео** представление, чтобы открыть видеопроигрыватель.</li></ul></li></ul>|  
|Использование библиотек SharePoint Online|(Только my Server 2012 R2) Работа с файлами в библиотеках SharePoint Online team s. Открытие сайтов групп. (Раздел SharePoint Online: откройте сайт группы и ознакомьтесь с библиотекой документов или файлом, который вы хотите открыть. При открытии файла, необходимо войти Office 365 с помощью учетной записи Майкрософт, связанных с сетевой учетной записью.)<br /><br /> **Примечание.** Чтобы использовать эту функцию, сервер должен быть интегрирован с Office 365, подписка Office 365 должна включать SharePoint Online и учетной записи пользователя на сервере необходимо иметь учетную запись Microsoft Online Services, связанные с ней. Сведения об интеграции Office 365 и SharePoint Online с Windows Server Essentials, см. в разделе [служб интеграции Обзор для Windows Server Essentials — часть 1](http://blogs.technet.com/b/sbs/archive/2013/11/06/services-integration-overview-for-windows-server-2012-r2-essentials-part-1.aspx) и [служб интеграции Windows Server Essentials — часть 2](http://blogs.technet.com/b/sbs/archive/2013/11/06/services-integration-overview-for-windows-server-2012-r2-essentials-part-2.aspx).|  
|Настройка списка **Последние элементы**|В списке **Последние** предоставляется быстрый доступ к файлам, над которыми вы сейчас работаете. Вы можете внести следующие изменения:<br /><br /> -Задайте число дней журнал последних файлов для отображения. (Параметры списка **Последние**: **Дней хранения последних файлов**; по умолчанию = 7 дней.)<br />-Clear **последние** отобразить, если вам больше не нужно работать над файлами, работа с. Это не затронет кэш: файлы будут по-прежнему доступны автономно. (Параметры списка **Последние**: кнопка **Очистить**.)<br />     **Совет.** Если t необходимости автономного доступа к файлам, использовать **очистить все** в **Offline** параметры, чтобы удалить файлы из кэша.|  
|Работа в автономном режиме|По умолчанию файлы, к которым вы получили доступ в течение последних семи дней, доступны автономно. Автономные изменения синхронизируются с сервером при каждом подключении к нему.<br /><br /> Вы можете внести следующие изменения в автономную конфигурацию:<br /><br /> -Измените количество дней работы кэш. (**Offline** параметры в My Server **файлы** параметры в My Server 2012 R2: **Период кэширования**; по умолчанию = 7 дней.)<br />-Разрешить передачу файлов по платным сетям или отключить эту функцию. Эта функция отключена по умолчанию для предотвращения передачи больших (и следовательно, дорогих) файлов по платным сетям. (Параметры **автономного доступа** или параметры **Файлы**: **Включить или выключить автоматическую передачу файлов по платным сетям**; по умолчанию = **Выкл.**.)<br />— Можно иногда может потребоваться очистить кэш. Проверьте размер кэша в параметрах списка **Последние** или параметрах **Файлы** ; затем выберите **Очистить** или **Очистить все** , чтобы очистить кэш.<br /><br /> **Совет.** Чтобы узнать, какие файлы будут доступны автономно, в любой общей папке выберите фильтр Автономные кэшированные вместо фильтра **Все**.<br /><br /> **Примечание.** По умолчанию в кэше хранятся те же файлы, которые отображаются в списке **Последние**. Обратите внимание, что если при очистке кэша или изменении параметров кэша список **Последние** не соответствует внесенным вами изменениям, некоторые файлы в списке **Последние** могут быть недоступны автономно.|  
|Фоновая синхронизация|Ваши файлы синхронизируются с сервером при каждом входе на My Server и при внесении изменений, когда вы подключены к серверу. Чтобы поддерживать высокий уровень производительности, ресурсоемкие фоновые синхронизации не выполняются автоматически в большинстве папок. Чтобы избежать затратных передач, фоновая синхронизация не выполняется в сетях размером 3 ГБ.<br /><br /> — Разрешение конфликтов файлов, отображенных в **конфликтующих** область **состояние передачи** страницы. При выполнении передач файлов в основном окне отображаются чудо-кнопки **Состояние передачи** и **Оповещения** .|  
  
##  <a name="BKMK_ConnectServer"></a> Как подключиться к серверу из локальной сети  
 Для успешного использования приложения My Server в Windows Server Essentials для Windows Phone, Windows 8 и Windows 8.1 необходимо сначала установить сертификат сервера на устройство. Это подключит устройство к серверу под управлением Windows Server Essentials в локальной сети. Используйте следующие процедуры, чтобы подключиться к серверу в локальной сети и установить сертификат сервера на Windows Phone или на компьютере под управлением Windows 8 или Windows 8.1.  
  
#### <a name="to-connect-to-your-server-from-your-windows-phone"></a>Подключение к серверу с Windows Phone  
  
1.  В Windows Phone под управлением Windows 8 или Windows 8.1 откройте Internet Explorer.  
  
2.  В адресной строке введите **http://<yourservername\>/connect/default.aspx?get=caroot.cer**, и нажмите клавишу ВВОД.  
  
3.  При запросе на установку сертификата caroot.cer щелкните **Установить**.  
  
4.  Дождитесь установки сертификата.  
  
    > [!NOTE]
    >  После завершения установки вы сможете войти в приложение My Server для Windows Phone, используя имя сервера и сетевые учетные данные.  
  
#### <a name="to-connect-to-your-server-in-your-local-network-from-a-computer-running-windows-8-or-windows-81"></a>Подключение к серверу в локальной сети с компьютера под управлением Windows 8 или Windows 8.1  
  
1.  На компьютере под управлением Windows 8 или Windows 8.1 откройте Internet Explorer.  
  
2.  В адресной строке введите **http://<yourservername\>/connect/default.aspx?get=caroot.cer**, и нажмите клавишу ВВОД.  
  
3.  При запросе на установку сертификата caroot.cer щелкните **Открыть**.  
  
4.  В диалоговом окне **Сертификат** щелкните **Установить сертификат**.  
  
5.  В мастере импорта сертификатов выберите **Локальный компьютер** в качестве расположения хранилища.  
  
6.  Выберите **Поместить все сертификаты в следующее хранилище**и откройте раздел **Доверенные корневые центры сертификации** .  
  
7.  Для завершения работы мастера следуйте инструкциям на экране.  
  
    > [!NOTE]
    >  После установки сертификата вы сможете войти в приложение My Server для Windows 8 или Windows 8.1, используя имя сервера и сетевые учетные данные.  
  
## <a name="see-also"></a>См. также  
  
-   [Обзор служб интеграции для Windows Server Essentials — часть 1](http://blogs.technet.com/b/sbs/archive/2013/11/06/services-integration-overview-for-windows-server-2012-r2-essentials-part-1.aspx)  
  
-   [Обзор служб интеграции для Windows Server Essentials — часть 2](http://blogs.technet.com/b/sbs/archive/2013/11/06/services-integration-overview-for-windows-server-2012-r2-essentials-part-2.aspx)  
  
-   [Управление повсеместным доступом](../manage/Manage-Anywhere-Access-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](../manage/Manage-Windows-Server-Essentials.md)  
  

-   [Удаленная работа](Work-Remotely-in-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](Use-Windows-Server-Essentials.md)

-   [Удаленная работа](../use/Work-Remotely-in-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
