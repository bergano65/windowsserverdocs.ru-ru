---
title: "Перенос Windows SBS 2011 Standard параметров и данных на целевой сервер для миграции Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16b24026-2fe3-4bd0-b82f-900e1564be99
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: b0ee150be2452fdf4c31c6a2a372958640fa5e4a
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="move-windows-sbs-2011-standard-settings-and-data-to-the-destination-server-for-windows-server-essentials-migration"></a>Перенос Windows SBS 2011 Standard параметров и данных на целевой сервер для миграции Windows Server Essentials

>Область применения: Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Перенос параметров и данных на целевой сервер следующим образом:  
  

1.  [Копирование данных на конечный сервер](Move-Windows-SBS-2011-Standard-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_CopyData)  
  
2.  [Импорт пользовательских учетных записей Active Directory для мониторинга Windows Server Essentials (необязательно)](Move-Windows-SBS-2003-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_ImportADaccounts)  
  
3.  [Перемещение роли DHCP-сервера с исходного сервера на маршрутизатор](Move-Windows-SBS-2011-Standard-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_MoveDHCP)  
  
4.  [Настройка сети](Move-Windows-SBS-2011-Standard-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_Network)  
  
5.  [Удаление устаревших объектов Active Directory групповой политики (необязательно)](Move-Windows-SBS-2011-Standard-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_RemoveLegacyADGPO)  
  
6.  [Сопоставление разрешенных компьютеров с учетными записями пользователей](Move-Windows-SBS-2011-Standard-settings-and-data-to-the-Destination-Server-for-Windows-Server-Essentials-migration.md#BKMK_MapPermittedComputers)  
  
##  <a name="BKMK_CopyData"></a>Копирование данных на конечный сервер  
 Перед копированием данных с исходного сервера на конечный сервер, выполните следующие задачи.  
  
-   Просмотрите список общих папок на исходном сервере, включая разрешения для каждой папки. Создайте или настройте папки на конечном сервере в соответствии со структурой папок, которую вы перемещаете с исходного сервера.  
  
-   Проверьте размер каждой папки и убедитесь, что целевой сервер имеет достаточно свободного дискового пространства.  
  
-   Сделайте общие папки на исходном сервере только для чтения для всех пользователей, не записи может занять место на диске, при копировании файлов на конечный сервер.  
  
#### <a name="to-copy-data-from-the-source-server-to-the-destination-server"></a>Копирование данных с исходного сервера на конечный сервер  
  
1.  Войдите на конечный сервер с правами администратора домена и откройте окно командной строки.  
  
2.  В командной строке введите следующую команду и нажмите клавишу ВВОД:  
  
    `robocopy \\<SourceServerName> \<SharedSourceFolderName> \\<DestinationServerName> \<SharedDestinationFolderName> /E /B /COPY:DATSOU /LOG:C:\Copyresults.txt`  
  
     Где:
     - \ < SourceServerName\ > — имя исходного сервера
     - \ < SharedSourceFolderName\ > — имя общей папки на исходном сервере
     - \ < DestinationServerName\ > — имя конечного сервера
     - \ < SharedDestinationFolderName\ > — Общая папка на конечном сервере, на который будут копироваться данные.  
  
3.  Повторите предыдущий шаг для каждой общей папки, которую вы перемещаете с исходного сервера.  
  
##  <a name="BKMK_ImportADaccounts"></a>Импорт пользовательских учетных записей Active Directory для мониторинга Windows Server Essentials (необязательно)  
 По умолчанию все учетные записи пользователей, созданные на исходном сервере, автоматически переносятся на панель мониторинга в Windows Server Essentials. Тем не менее автоматического переноса учетной записи пользователя в Active Directory завершится сбоем, если некоторые свойства не будут соответствовать требованиям миграции. Следующий командлет Windows PowerShell можно использовать для импорта пользователей Active Directory.  
  
#### <a name="to-import-an-active-directory-user-account-to-the-windows-server-essentials-dashboard"></a>Чтобы импортировать учетную запись пользователя Active Directory на панели мониторинга Windows Server Essentials  
  
1.  Войдите на целевой сервер как администратор домена.  
  
2.  Откройте Windows PowerShell от имени администратора.  
  
3.  Выполните следующий командлет, где `[AD username]` — это имя учетной записи пользователя Active Directory, который требуется импортировать:  
  
     `Import-WssUser  SamAccountName [AD username]`  
  
##  <a name="BKMK_MoveDHCP"></a>Перемещение роли DHCP-сервера с исходного сервера на маршрутизатор  
 Если исходный сервер выполняется роль сервера DHCP, выполните следующие действия, чтобы перемещение роли DHCP на маршрутизатор.  
  
#### <a name="to-move-the-dhcp-role-from-the-source-server-to-the-router"></a>Перемещение роли DHCP с исходного сервера на маршрутизатор  
  
1.  Отключите службу DHCP на исходном сервере следующим образом:  
  
    1.  На исходном сервере нажмите кнопку **запустить**, нажмите кнопку **Администрирование**, а затем нажмите кнопку **службы**.  
  
    2.  В списке текущих выполняемых служб щелкните правой кнопкой мыши **DHCP-сервера**, а затем нажмите кнопку **свойства**.  
  
    3.  Для **типа запуска**выберите **отключено**.  
  
    4.  Остановите службу.  
  
2.  Включение роли DHCP на маршрутизаторе.  
  
    1.  Следуйте инструкциям в документации на маршрутизатор, чтобы включить роль DHCP на маршрутизаторе.  
  
    2.  Чтобы убедиться, что IP-адреса, выданные сервером источника не изменяются, следуйте инструкциям в документации на маршрутизатор, чтобы настроить диапазон DHCP на маршрутизаторе должен быть идентичен диапазону DHCP на исходном сервере.  
  
        > [!IMPORTANT]
        >  Если вы не настроили статический IP или резервирования DHCP на маршрутизаторе для целевого сервера, и диапазон DHCP не совпадает с исходным сервером, что маршрутизатор может выдать новый IP-адрес для конечного сервера. В этом случае сбросьте правила маршрутизатор для пересылки на новый IP-адрес конечного сервера перенаправления портов.  
  
##  <a name="BKMK_Network"></a>Настройка сети  
 После переноса роли DHCP на маршрутизатор настройте параметры сети на конечном сервере.  
  
#### <a name="to-configure-the-network"></a>Для настройки сети  
  
1.  На конечном сервере откройте панель мониторинга.  
  
2.  На **Главная** щелкните **установки**, нажмите кнопку **Настройка повсеместного доступа**и выберите **щелкните, чтобы настроить Повсеместный доступ** параметр.  
  
3.  Выполните инструкции в мастере для настройки маршрутизатора и доменных имен.  
  
 Если маршрутизатор не поддерживает инфраструктуру UPnP, или если UPnP-инфраструктура отключена, рядом с именем маршрутизатора может появиться желтый значок предупреждения. Убедитесь, что открыты следующие порты, и что они будут направляться на IP-адрес конечного сервера:  
  
-   Порт 80: Веб-трафик HTTP  
  
-   Порт 443: Веб-трафик HTTPS  
  
> [!NOTE]
>  При настройке локального сервера Exchange на второй сервер, необходимо убедиться, порт 25 (SMTP) также открыт и перенаправляется на IP-адрес локального сервера Exchange Server.  
  
##  <a name="BKMK_RemoveLegacyADGPO"></a>Удаление устаревших объектов Active Directory групповой политики (необязательно)  
 Объекты групповой политики (GPO) обновляются для Windows Server Essentials. Они являются подмножеством объектов Small Business Server 2011 г. групповой политики Windows. Для Windows Server Essentials ряд фильтров малого бизнеса 2011 групповой политики Windows Server и инструментария управления Windows (WMI) необходимо вручную удалить для предотвращения конфликтов с групповой политики Windows Server Essentials и фильтров WMI.  
  
> [!NOTE]
>  Если вы изменили исходного Windows малого бизнеса сервера 2011 объекты групповой политики, следует сохранить их копии в другом месте и затем удалить их из Windows Small Business Server 2011.  
  
#### <a name="to-remove-old-group-policy-objects-from-windows-small-business-server-2011"></a>Для удаления старых объектов групповой политики из Windows Small Business Server 2011  
  
1.  Войдите на исходный сервер с учетной записью администратора.  
  
2.  Нажмите кнопку **запустить**, а затем нажмите кнопку **управление сервером**.  
  
3.  В области навигации щелкните **расширенного управления**, нажмите кнопку **Управление групповой политикой**, а затем нажмите кнопку **леса:***< YourDomainName\ >*.  
  
4.  Нажмите кнопку **домены**, нажмите кнопку *< YourDomainName\ >*, а затем нажмите кнопку **объектов групповой политики**.  
  
5.  Щелкните правой кнопкой мыши **Small Business Server-политика аудита**, нажмите кнопку **удалить**, а затем нажмите кнопку **ОК**.  
  
6.  Повторите шаг 5, чтобы удалить следующие объекты групповой политики, которые применяются к сети:  
  
    -   Windows SBS клиента Windows 7 и Windows Vista политики  
  
    -   Политика клиента Windows XP для Windows SBS  
  
    -   Политика CSE Windows SBS  
  
    -   Политика пользователей Windows SBS  
  
    -   Обновление политики компьютера клиента служб  
  
    -   Обновление политики общих параметров службы  
  
    -   Обновление политики компьютера сервера служб  
  
7.  Убедитесь, что все объекты групповой политики удалены.  
  
#### <a name="to-remove-wmi-filters-from-the-source-server"></a>Удаление фильтров WMI с исходного сервера  
  
1.  Войдите на исходный сервер с учетной записью администратора.  
  
2.  Нажмите кнопку **запустить**, а затем нажмите кнопку **управление сервером**.  
  
3.  В области навигации щелкните **функции**, нажмите кнопку **Управление групповой политикой**, а затем нажмите кнопку **леса:***< YourNetworkDomainName\ >*  
  
4.  Нажмите кнопку **домены**, нажмите кнопку *< YourNetworkDomainName\ >*, а затем нажмите кнопку **фильтры WMI**.  
  
5.  Щелкните правой кнопкой мыши **клиента Windows SBS**, нажмите кнопку **удалить**, а затем нажмите кнопку **Да**.  
  
6.  Щелкните правой кнопкой мыши **Windows SBS клиента Windows 7 и Windows Vista**, нажмите кнопку **удалить**, а затем нажмите кнопку **Да**.  
  
7.  Щелкните правой кнопкой мыши **Windows SBS клиента Windows XP**, нажмите кнопку **удалить**, а затем нажмите кнопку **Да**.  
  
8.  Убедитесь, что эти фильтры WMI удалены.  
  
##  <a name="BKMK_MapPermittedComputers"></a>Сопоставление разрешенных компьютеров с учетными записями пользователей  
 При подключении пользователя к удаленного веб-доступа в Windows Small Business Server 2011, отображаются все компьютеры в сети. Это могут быть компьютеры, которые пользователь не имеет разрешения на доступ к. В Windows Server Essentials пользователь должен быть явно назначен компьютеру, чтобы он отображался в удаленном веб-доступа. Каждая учетная запись пользователя, которая переносится из Windows Small Business Server 2011 должна быть сопоставлена с одним или несколькими компьютерами.  
  
#### <a name="to-map-user-accounts-to-computers"></a>Сопоставление учетных записей и компьютеров  
  
1.  Откройте панель мониторинга Windows Server Essentials.  
  
2.  На панели навигации щелкните **пользователей**.  
  
3.  В списке учетных записей пользователей, щелкните правой кнопкой мыши учетную запись пользователя и нажмите кнопку **просмотреть свойства учетной записи**.  
  
4.  Нажмите кнопку **повсеместного доступа** , а затем щелкните **разрешить удаленный веб-доступ и доступ к веб-приложениям служб**.  
  
5.  Выберите **общих папок**, выберите **компьютеры**выберите **ссылки главной страницы**, а затем нажмите кнопку **применить**.  
  
6.  Нажмите кнопку **доступ к компьютеру** , а затем щелкните имя компьютера, к которому вы хотите разрешить доступ.  
  
7.  Повторите шаги 3, 4, 5 и 6 для каждой учетной записи пользователя.  
  
> [!NOTE]
>  Необходимо изменить конфигурацию клиентского компьютера. Она настраивается автоматически.  
  
> [!NOTE]
>  По окончании процесса миграции, если вы столкнулись с проблемой при создании первой новой учетной записи пользователя на конечном сервере, удалить учетную запись пользователя, который вы добавили и создайте его заново.