---
title: "Обзор панели мониторинга в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f70a79de-9c56-4496-89b5-20a1bff2293e
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c2cc603f5e0303ada245956a524151393c538b27
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="overview-of-the-dashboard-in-windows-server-essentials"></a>Обзор панели мониторинга в Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience включают панель администрирования, которая упрощает задачи по управлению сети Windows Server Essentials и сервера. С помощью панели мониторинга Windows Server Essentials, вы можете:  
  
-   Завершение настройки сервера  
  
-   Доступ и выполнение стандартных задач администрирования  
  
-   Просмотр предупреждений сервера и принятие соответствующих мер  
  
-   Настройка и изменение параметров сервера  
  
-   Поиск разделов справки в Интернете доступ к ним  
  
-   Доступ к ресурсам сообщества в Интернете  
  
-   Управление учетными записями пользователей  
  
-   Управление устройствами и резервными копиями  
  
-   Управление доступом и параметрами для серверных папок и жестких дисков  
  
-   Просмотр и управление ими в приложениях-надстройках  
  
-   Интеграция с Microsoft online services  
  
 Этот раздел включает:  
  
-   [Базовые функции панели мониторинга](#BKMK_Design)  
  
-   [Функции страницы "Домашняя страница панели мониторинга"](#BKMK_Home)  
  
-   [Административные разделы панели мониторинга](#BKMK_Features)  
  
-   [Доступ к панели мониторинга Windows Server Essentials](#BKMK_AccessDb)  
  
-   [Использование в безопасном режиме](#BKMK_UseSafeMode)  
  
##  <a name="BKMK_Design"></a>Базовые функции панели мониторинга  
 Панели мониторинга Windows Server Essentials позволяет быстро получить доступ к ключевым информации и функциям управления сервера. Панель мониторинга состоит из нескольких разделов. В таблице ниже описаны эти разделы.  
  
 
  
|Элемент|Функция на панели мониторинга|Описание|  
|----------|-----------------------|-----------------|  
|1|Панель навигации|Щелкните раздел на панели навигации для доступа к сведениям и задачам, которые связаны с этим разделом. Каждый раз при открытии панели мониторинга **Главная** по умолчанию отображается страница.|  
|2|Вкладки подразделов|Вкладки подразделов предоставляют доступ к административным задачам Windows Server Essentials второго уровня.|  
|3|Область списков|В списке отображаются объекты, можно управлять и содержит основные сведения о каждом объекте.|  
|4|Область сведений|В области сведений отображается дополнительная информация об объекте, выбранном в представлении списка.|  
|5|Область задач|Область задач содержит ссылки на инструменты и сведения, облегчающие управление свойствами конкретного объекта (например, учетной записи пользователя или компьютера) или глобальными параметрами категории объекта. На панели задач можно разделить на следующие два раздела:<br /><br /> **Объект задачи** œ содержит ссылки на инструменты и сведения, облегчающие управление свойствами объекта, выбранного в представлении списка (например, учетной записи пользователя или компьютера).<br /><br /> **К глобальным задачам** œ содержит ссылки на инструменты и сведения, облегчающие управление глобальными задачами для данной области функций. К глобальным задачам относятся следующие: Добавление новых объектов, Настройка политики и т. д.|  
|6|Сведения и параметры|В этом разделе предоставляет прямой доступ к параметрам сервера, Справка ссылки на сведения о просматриваемой странице панели мониторинга.|  
|7|Статус предупреждений|Статус предупреждений позволяет быстро получить визуальное представление о работоспособности сервера. Щелкните изображение предупреждения для просмотра критических и важных предупреждений.<br /><br /> **Примечание:** в Windows Server Essentials и Windows Server 2012 R2 Standard с установленной ролью Windows Server Essentials Experience можно найти в состояние предупреждения **сведения и параметры** вкладку.|  
|8|Строка состояния|В строке состояния отображается число объектов, которые отображаются в представлении списка. Add-in приложений также может отображаться другой статус.|  
  
##  <a name="BKMK_Home"></a>Функции страницы "Домашняя страница панели мониторинга"  
 При открытии панели мониторинга **Главная** по умолчанию отображается страница **установки** категорией. **Главная** страницы панели мониторинга Windows Server Essentials обеспечивает быстрый доступ к задачам и сведениям, упрощающим пользовательскую настройку сервера и конфигурацию основных функций. Домашняя страница состоит из четырех функциональных областей, которые предоставляют сведения и задачи конфигурации для выбранных параметров. В таблице ниже описаны компоненты.  
  
|Элемент|Функция|Описание|  
|----------|-------------|-----------------|  
|1|Панель навигации|Щелкните раздел на панели навигации для доступа к сведениям и задачам, которые связаны с этим разделом. Каждый раз при открытии панели мониторинга **Главная** по умолчанию отображается страница.|  
|2|Область "Категория"|В этой области отображаются основные функциональные области, обеспечивающие быстрый доступ к информации и конфигурации средства, которые помогут настроить и настройки сервера. Щелкните категорию, чтобы отобразить задачи и ресурсы, которые связаны с этой категорией.|  
|3|Область задач|В этой области отображаются ссылки на задачи и сведения, применяемые к выбранной категории. Щелкните задачу или ресурс, чтобы просмотреть дополнительные сведения.|  
|4|Область действий|В этой области предоставляет краткое описание функции или задачи и ссылки для открытия мастеров конфигурации и страниц со сведениями. Щелкните ссылку, чтобы предпринять дальнейшие действия.|  
  
##  <a name="BKMK_Features"></a>Административные разделы панели мониторинга  
 Панели мониторинга Windows Server Essentials сетевая информация и административные задачи упорядочены функциональным областям. Страница управления каждой функциональной области содержит сведения об объектах, связанных с этой областью, например **пользователей**, или **устройств**. На странице управления также отображаются задачи, которые можно использовать для просмотра или изменения параметров или запускать программы, автоматизирующие выполнение многошаговых задач.  
  
 В следующей таблице описаны административные разделы панели мониторинга, доступных по умолчанию после установки. В таблице также перечислены задачи, которые доступны в каждом разделе.  
  
|Раздел|Описание|  
|-------------|-----------------|  
|Домашняя|**Главная** по умолчанию отображается страница каждый раз при открытии панели мониторинга. Здесь отображаются задачи и сведения в следующих категориях:<br /><br /> **Настройка** œ задачи в этой категории для настройки сервера в первый раз. Сведения об этих задачах см. в разделе [Установка и настройка Windows Server Essentials](../install/Install-and-Configure-Windows-Server-Essentials.md).<br /><br /> **По электронной ПОЧТЕ** œ вариант в этой категории позволяют интегрировать службу эл. почты с сервером.<br /><br /> **Примечание:** эта категория доступна только в Windows Server Essentials.<br /><br /> **СЛУЖБЫ** œ выберите задачу в этой категории позволяют интегрировать служб Microsoft online services на сервере.<br /><br /> **Примечание:** эта категория доступна только в Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience.<br /><br /> **Надстройки** œ щелкните эту категорию, чтобы установить полезные надстройки для вашего бизнеса.<br /><br /> **КРАТКАЯ информация о состоянии** œ отображает состояние высокого уровня сервера. Щелкните статус, чтобы просмотреть сведения и параметры конфигурации для этого компонента. Если выполнены все задачи в категории настройки, эта категория отображается вверху области категории.<br /><br /> **СПРАВКА** œ используйте поле поиска для поиска справки в Интернете. Щелкните ссылку, чтобы посетить веб-сайт выбранного варианта поддержки.|  
|Пользователи|Для доступа к предоставляемым Windows Server Essentials ресурсам необходимо создать учетные записи пользователей с помощью панели мониторинга Windows Server Essentials. После создания учетных записей пользователей, можно управлять учетными записями с помощью задач, которые обычно доступны в **пользователей** страницы панели мониторинга. Следующие задачи можно выполнять на этой странице.<br /><br /> -Просмотр списка учетных записей пользователей.<br /><br /> — Просмотр и управление свойства учетной записи пользователя.<br /><br /> -Активировать или отключение учетных записей пользователей.<br /><br /> — Добавление или удаление учетных записей пользователей.<br /><br /> -Назначение для учетных записей Microsoft online services учетным записям локальной сети, если ваш сервер интегрирован с Office 365.<br /><br /> -Изменение паролей учетных записей пользователей и управление политиками паролей.<br /><br /> Сведения об управлении учетными записями пользователей см. в разделе [управление учетными записями пользователей](Manage-User-Accounts-in-Windows-Server-Essentials.md).|  
|Группы пользователей|**Примечание:** эта функция доступна только в Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience.<br /><br /> Следующие задачи можно выполнять на этой странице.<br /><br /> -Просмотр списка групп пользователей.<br /><br /> — Просмотр и управление группами пользователей.<br /><br /> — Добавление или удаление групп пользователей.|  
|Группы рассылки|**Примечание:** эта функция доступна только в Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience. Эта вкладка отображается только при условии интеграции Windows Server Essentials с Office 365.<br /><br /> Следующие задачи можно выполнять на этой странице.<br /><br /> -Просмотр списка групп рассылки.<br /><br /> — Добавление или удаление групп рассылки.|  
|Устройства|После подключения компьютеров к сети Windows Server Essentials, можно управлять компьютерами из **устройств** страницы панели мониторинга. Следующие задачи можно выполнять на этой странице.<br /><br /> -Просмотрите список компьютеров, подключенных к сети.<br /><br /> -Управление мобильными устройствами с использованием функции управления мобильными устройствами для Office 365.<br /><br /> **Примечание:** эта функция доступна только в Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience.<br /><br /> -Просмотр свойств компьютера и оповещений о работоспособности для каждого компьютера.<br /><br /> — Настройка и Управление архивацией данных компьютера.<br /><br /> -Восстановление файлов и папок на компьютеры.<br /><br /> -Установить подключение удаленного рабочего стола на компьютере<br /><br /> -Настроить параметры архивации компьютеров и журнала файлов<br /><br /> Сведения об управлении компьютерами и резервным копированием см. в разделе [управление устройствами](Manage-Devices-in-Windows-Server-Essentials.md).|  
|Хранилища|В зависимости от версии Windows Server Essentials выполняется **хранилища** на панели мониторинга по умолчанию содержит следующие разделы.<br /><br /> - **Папок сервера** содержит задачи, облегчающие просмотр и управление свойствами для папок сервера. На этой странице также доступны задачи по открытию и добавлению серверных папок.<br /><br /> - **Жестких дисков** страница содержит задачи, облегчающие просмотр и проверку состояния дисков, подключенных к серверу.<br /><br /> -В Windows Server Essentials и Windows Server 2012 R2 Standard с включенной ролью Windows Server Essentials Experience **библиотеки SharePoint** страница содержит задачи, облегчающие управление библиотеками SharePoint в службе Office 365.<br /><br /> Сведения об управлении серверными папками см. в разделе [Управление серверными папками](Manage-Server-Folders-in-Windows-Server-Essentials.md).<br /><br /> Сведения об управлении жесткими дисками см. в разделе [Управление хранилищем сервера](Manage-Server-Storage-in-Windows-Server-Essentials.md).|  
|Приложения|- **Приложений** разделе панели мониторинга Windows Server Essentials по умолчанию состоит из двух частей.<br /><br /> Сведения об управлении приложениями надстроек см. в разделе [управление приложениями](Manage-Applications-in-Windows-Server-Essentials.md).<br /><br /> - **Надстройки** подразделе отображаются список установленных надстроек и задачи, которые позволяют для удаления надстройки и получения дополнительной информации о выбранной надстройке.<br /><br /> - **Microsoft Pinpoint** содержится список приложений, доступных из Microsoft Pinpoint.|  
|Office 365|**Office 365** вкладка отображается только при интеграции Windows Server Essentials с Microsoft Office 365. В этом разделе содержится информация учетной записи подписки и администратора Office 365.|  
  
> [!NOTE]
>  Если устанавливается надстройка для панели мониторинга Windows Server Essentials, надстройки могут быть созданы дополнительные административные разделы. Эти разделы могут отображаться в главной строке навигации или на вкладке подразделов.  
  
##  <a name="BKMK_AccessDb"></a>Доступ к панели мониторинга Windows Server Essentials  
 Доступ к панели мониторинга можно с помощью одного из следующих методов. Выбор способа зависит от того, ли вы обращаетесь к панели мониторинга с сервера, на компьютере, подключенном к сети Windows Server Essentials или удаленном компьютере.  
  
 В целях обеспечения безопасности сети, только пользователи с разрешениями администратора могут получить доступ к панели мониторинга Windows Server Essentials. Кроме того невозможно использовать встроенную учетную запись администратора для входа в панель мониторинга Windows Server Essentials из панели запуска.  
  
###  <a name="BKMK_Server"></a>Доступ к панели мониторинга с сервера  
 При установке Windows Server Essentials, процесс установки создает ярлык на панель мониторинга на **запустить** экрана, а также на рабочем столе. Если в указанных расположениях отсутствует ярлык, можно использовать **поиска** панели, чтобы найти и запустить программу панели мониторинга.  
  
##### <a name="to-access-the-dashboard-from-the-server"></a>Доступ к панели мониторинга с сервера  
  
-   Войдите сервер с правами администратора, а затем выполните одно из следующих:  
  
    -   На **запустить** нажмите кнопку **мониторинга**.  
  
    -   На рабочем столе дважды щелкните **мониторинга**.  
  
    -   В **поиска** введите **мониторинга**, а затем нажмите кнопку **панели мониторинга** в результатах поиска.  
  
###  <a name="BKMK_Network"></a>Доступ к панели мониторинга с компьютера, подключенного к сети  
 В Windows Server Essentials после присоединения компьютера к сети, администраторы могут использовать панель запуска для доступа к панели мониторинга сервера с компьютера.  
  
> [!WARNING]
>  В Windows Server Essentials для подключения к панели мониторинга с клиентского компьютера, щелкните правой кнопкой мыши значок на панели задач и затем открыть панель мониторинга из контекстного меню.  
  
##### <a name="to-access-the-dashboard-by-using-the-launchpad"></a>Доступ к панели мониторинга с помощью панели запуска  
  
1.  На компьютере, подключенном к сети, откройте **запуска**.  
  
2.  В меню панели запуска щелкните **мониторинга**.  
  
3.  На панели мониторинга **вход** страницы, введите учетные данные администратора сети и нажмите клавишу ВВОД.  
  
     Откроется удаленное подключение к панели мониторинга Windows Server Essentials.  
  
###  <a name="BKMK_Remote"></a>Доступ к панели мониторинга с удаленного компьютера  
 При работе с удаленного компьютера можно получить доступ к панели мониторинга Windows Server Essentials с помощью сайта удаленного веб-доступа.  
  
##### <a name="to-access-the-dashboard-by-using-remote-web-access"></a>Доступ к панели мониторинга с помощью удаленного веб-доступа  
  
1.  С удаленного компьютера откройте веб-браузер, например Internet Explorer.  
  
2.  Введите следующую команду в адресной строке браузера Internet:**https://<DomainName\>/remote**, где *DomainName* — внешнее доменное имя вашей организации (например, contoso.com).  
  
3.  Введите имя пользователя и пароль для входа на сайт удаленного веб-доступа.  
  
4.  В **компьютеры** раздел удаленного веб-доступа**Главная** страницы; Найдите нужный сервер и нажмите кнопку **Connect**.  
  
     Откроется удаленное подключение к панели мониторинга.  
  
    > [!NOTE]
    >  Если сервер не отображается в **компьютеры** раздел на домашней странице, нажмите кнопку **подключиться к другим компьютерам**, найдите сервер в списке и затем щелкните сервер, чтобы подключиться к ней.  
    >   
    >  Чтобы предоставить пользователю разрешение осуществлять доступ к панели мониторинга с удаленного веб-доступа, откройте страницу свойств для учетной записи пользователя и выберите **панели мониторинга сервера** вариант на **повсеместного доступа** вкладку.  
  
##  <a name="BKMK_UseSafeMode"></a>Использование в безопасном режиме  
 Функция безопасного режима в Windows Server Essentials осуществляет мониторинг надстроек, установленных на сервере. Если панель мониторинга становится нестабильной или не отвечает, безопасный режим обнаруживает и изолирует надстройки, которые могут быть причиной проблемы и отображает их на **параметры безопасного режима** страницу в следующий раз при открытии панели мониторинга. Из **параметры безопасного режима** страницы, можно отключать и включать надстройки одной для определения, какая из них является причиной проблемы. Затем вы можете оставить надстройка отключена для последующих запусках или удалить надстройку.  
  
 Можно просмотреть список всех надстроек, установленных на сервере в любое время. Можно также открыть панель мониторинга в безопасном режиме, автоматически отключив все надстройки сторонних разработчиков. Windows Server Essentials также позволяет получить доступ к панели мониторинга в безопасном режиме с другого компьютера в сети.  
  
#### <a name="to-view-a-list-of-installed-add-ins"></a>Чтобы просмотреть список установленных надстроек  
  
-   С помощью панели мониторинга щелкните **помочь**, а затем нажмите кнопку **параметры безопасного режима**.  
  
#### <a name="to-open-the-dashboard-in-safe-mode"></a>Чтобы открыть панель мониторинга в безопасном режиме  
  
-   В **поиска** введите **безопасном**, а затем нажмите кнопку **панель мониторинга (безопасный режим)** в результатах поиска.  
  
#### <a name="to-open-the-dashboard-in-safe-mode-from-another-computer-on-the-network"></a>Чтобы открыть панель мониторинга в безопасном режиме с другого компьютера в сети  
  
1.  Откройте панель запуска Windows Server Essentials с компьютера, подключенного к сети и нажмите кнопку **мониторинга**.  
  
2.  На панели мониторинга-страницу входа, введите имя пользователя и пароль для учетной записи, имеющей разрешение на вход на сервер, select **Разрешить мне выбрать надстройки для загрузки** флажок и нажмите кнопку со стрелкой для входа в систему.  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление приложениями](Manage-Applications-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)