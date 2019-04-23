---
title: Создание файла Cfg.ini
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 93a73556-22ef-402d-b8d4-582b74c22bcf
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 967db5f36ea27fb04eab9a6682a106ba0072d45d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820125"
---
# <a name="create-the-cfgini-file"></a>Создание файла Cfg.ini

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Файл cfg.ini используется для автоматизации установки операционной системы в следующем сценарии:  
  
-   При тестировании работы конечного пользователя с помощью образа, предварительно установленного на целевом компьютере, раздел начальной настройки используется для пошагового выполнения установки в автоматическом или ручном режиме. Сведения об этом см. в подразделе [Создание раздела начальной настройки](Create-the-Cfg.ini-File.md#BKMK_CreateInit2).  
  
##  <a name="BKMK_CreateInit2"></a> Создание раздела начальной настройки  
 Раздел начальной настройки файла cfg.ini используется для пошагового выполнения установки в автоматическом или ручном режиме.  
  
#### <a name="to-define-the-initial-configuration-section"></a>Определение раздела начальной настройки  
  
1.  Если файл cfg.ini уже существует, откройте его в Блокноте. В противном случае создайте новый файл.  
  
2.  Добавьте следующий текст, чтобы создать раздел InitialConfiguration.  
  
    ```  
  
    [InitialConfiguration]  
    ;Optional, display language can only be one of the installed language  
    Language=en-us  
    ;Optional, The name of a script that runs after setupComplete.cmd but before the initial configuration begins.  
    ;Optional  
    Locale=en-us  
    ;Optional  
    Country=US  
    ;Optional  
    Keyboard=0409:00000409  
    AcceptEula=true  
    ;This is only required on a server where an OEM EULA has been specified   
    ;by using the OOBE.xml file  
    AcceptOEMEula=true  
    ;Optional. Example: My Company Name  
    CompanyName=EnterCompanyName  
    ServerName=EnterServerName  
    ; Example: CONTOSO  
    NetbiosName=EnterNetbiosDomainName  
    ; Example: contoso.local  
    DNSName=EnterDNSDomain   
    ; Used to set the user name for the domain admin  
    UserName=EnterDomainAdminUserName  
    ;The password has to be strong and at least 8 characters  
    PlainTextPassword=EnterAdminPassword  
    ;. Used to set the user name for the domain standard user account. Ignored in migration mode.  
    StdUserName=EnterDomainStandardUserName  
    ;. The password for the domain standard user account has to be strong and at least 8 characters  
    StdUserPlainTextPassword=EnterStandardUserPassword  
    ;Controls the Watson and automatic update settings  
    Settings=All or Updates or None  
    WebDomainName=www.abc.com  
    TrustedCertFileName=c:\cert\a.pfx  
    TrustedCertPassword=Enteryourpassword  
    EnableVPN=true  
    EnableRWA=true  
    IPv4DNSForwarder=<IPV4Address,IPV4Address,¦>  
    IPv6DNSForwarder=<IPV6Address,IPV6Address,¦>  
    VpnIPv4StartAddress=<IPV4Address>  
    VpnIPv4EndAddress=<IPV4Address>  
    VpnBaseIPv6Address=<IPV6Address>  
    VpnIPv6PrefixLength=<number>  
    ;All these section are optional.  
     [PostOSInstall]  
    ;Optional, The name of a script that runs after setupComplete.cmd but before the initial configuration begins.  
  
    IsHosted=true  
    StaticIPv4Address=<IPV4Address>  
    StaticIPv4Gateway=<IPV4Address>  
    StaticIPv4SubnetMask=<IPV4SubnetMask>   
    StaticIPv6Address=<IPV6Address>  
    StaticIPv6SubnetPrefixLength=<number>  
    StaticIPv6Gateway=<IPV6Address>  
    ClientBackupOn=true  
    FileHistoryOn=true  
    LaunchPadHiddenTasks=<Microsoft.LaunchPad.AdminDashboard,Microsoft.LaunchPad.Backup>  
  
    ```  
  
    > [!NOTE]
    >  Параметр для выбора другого языка во время начальной установки не предусмотрен. При сбросе параметров операционной системы в ней используется первоначально установленный язык.  
  
    |Имя параметра|Описание параметра|  
    |--------------------|---------------------------|  
    |*AcceptEula*|Указывает, что пользователь принял условия лицензионного соглашения на использование программного обеспечения корпорации Майкрософт. Допустимые значения: True и False. Однако установка продолжается, только если задано значение True.|  
    |*AcceptOEMEula*|(Необязательно) Указывает, что пользователь принял условия лицензии Microsoft для партнера. Допустимые значения: True и False. Это поле требуется только в случае, если сервер был приобретен у партнера, который предоставил отдельное лицензионное соглашение.|  
    |*Название организации*|(необязательно) Название компании. Название компании используется для связи сервера с конкретной компанией и настройки отчетов этой компании. Должно содержать не более 254 символов.|  
    |*Страны*|(Необязательно) Строка, в которой указана требуемая страна или регион. Пример. US, обозначая Соединенные Штаты Америки.|  
    |*Имя_сервера*|Имя сервера однозначно определяет сервер в сети. Имя сервера должно удовлетворять следующим условиям:<br /><br /> — Может содержать до 15 символов.<br /><br /> — Может содержать буквы, цифры и дефисы (-).<br /><br /> -Не должно начинаться с дефиса.<br /><br /> -Не может содержать пробелы.<br /><br /> -Не может содержать только цифры.<br /><br /> Пример. ContosoServer.|  
    |*DNSName*|Внутренний домен группирует сервер и клиентские компьютеры для совместного использования общей базы данных имен пользователей, паролей и другой общей информации. Это имя отображается для пользователей, когда они входят в системы компьютеров, однако оно используется только во внутренней сети и не совпадает с именем домена в Интернете. Имя внутреннего домена должно удовлетворять тем же условиям, что предъявляются к *ServerName*.<br /><br /> Пример: contoso.local.|  
    |*NetbiosName*|Имя NetBIOS используется для идентификации ресурсов, которые выполняются на сервере. Должно содержать не более 15 символов. Пример. Contoso.|  
    |*Язык*|(Необязательно) Задает язык интерфейса. Это может быть только один из установленных языков. Пример: en-us для английского языка (США).|  
    |*Языковой стандарт*|(Необязательно) Задает формат времени и денежных единиц с помощью формата *LocaleID* . Пример: en-us для отображения времени и денежных единиц на английском языке в соответствии с правилами форматирования, принятыми в США.|  
    |*Клавиатура*|Возможны два формата клавиатуры:<br /><br /> - **входной язык: раскладка клавиатуры.** Пример: 0409:00000409, где 0409 перед **:** обозначает язык ввода, а **00000409** – раскладка клавиатуры. Список раскладок клавиатуры можно найти в разделе реестра **HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\Keyboard Layouts**.<br /><br /> - **язык ввода: идентификатор IME.** Ниже приведен полный список идентификаторов IME.<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{8F96574E-C86C-4bd6-9666-3F7327D4CBE8} Амхарский метод ввода<br /><br /> -{81d4e9c9-1d3b-41bc-9e6c-4b40bf79e35e}{FA550B04-5AD7-411F-A5AC-CA038EC515D7} Майкрософт ПИН - инь – простая Быстрая (Китайская упрощенная)<br /><br /> — {531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{B2F9C502-1742-11D4-9790-0080C882687E} китайский (традиционный) - New Phonetic<br /><br /> — {531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{4BDF9F03-C7D3-11D4-B2AB-0080C882687E} китайский (традиционный) - ChangJie<br /><br /> Экспресс - {531FDEBF-9B4C-4A43-A2AA-960E8FCDC732}{6024B45F-5C54-11D4-B921-0080C882687E} китайский (традиционный)-<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{D38EFF65-AA46-4FD5-91A7-67845FB02F5B} китайский традиционный массива<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{037B2C25-480C-4D7F-B027-D6CA6B69788A} китайский традиционный DaYi<br /><br /> -{03B5835F-F03C-411B-9CE2-AA23E1171E36}{A76C93D9-5523-4E90-AAFA-4DB112F9AC76} Microsoft IME (японский)<br /><br /> -{A028AE76-01B1-46C2-99C4-ACD9858AE02F}{B5FE1F02-D5F2-4445-9C03-C568F23C99A1} Microsoft IME (корейский)<br /><br /> -{A1E2B86B-924A-4D43-80F6-8A820DF7190F}{B60AF051-257A-46BC-B9D3-84DAD819BAFB} старый IME хангыль (корейский)<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{409C8376-007B-4357-AE8E-26316EE3FB0D} входных данных Yi-метод<br /><br /> -{E429B25A-E5D3-4D1F-9BE3-0C608477E3A1}{3CAB88B7-CC3E-46A6-9765-B772AD7761FF} тигринья метод ввода|  
    |*Параметры*|Задает возможности выбора, доступные пользователю при обновлении. Используйте одно из следующих значений:<br /><br /> **— Все** равно использовать рекомендуемые параметры.<br /><br /> **— Обновляет** означает устанавливать только важные обновления. Только<br /><br /> **-None** equals не проверять наличие обновлений.|  
    |*имя пользователя*|— Имя новой учетной записи администратора, которая создается во время установки. Имена учетных записей администратора и обычного пользователя должны отвечать следующим критериям:<br /><br /> — Может иметь до 19 символов.<br /><br /> — Не может содержать / \ [] &#124; < > + =; , ? *<br /><br /> -Не должно начинаться или заканчиваться точкой.<br /><br /> -Не может содержать две точки подряд.<br /><br /> — Должен быть не так же, как имя сервера или внутренним именем домена.<br /><br /> — Должен не совпадать с предопределенным именем пользователя как администратора или гостя.|  
    |*PlainTextPassword*|Это пароль для новой учетной записи администратора, созданной при установке.<br /><br /> — Должен быть по крайней мере 8 символов.<br /><br /> — Должен содержать по крайней мере три из следующих четырех категорий:<br /><br /> — Прописные буквы.<br /><br /> -Строчные буквы.<br /><br /> -Номера.<br /><br /> -Символы.|  
    |*StdUserName*|Имя новой стандартной учетной записи пользователя, которая создается при установке. Требования аналогичны требованиям для параметра *UserName* .|  
    |*StdUserPlainTextPassword*|Пароль новой стандартной учетной записи пользователя, которая создается при установке.|  
    |WebDomainName|(Необязательно) Настройка имени домена Интернета для сервера. Этот файл позволяет настраивать доменное имя аналогично тому методу, который использовался для ручной настройки в мастере настройки доменного имени.|  
    |TrustedCertFileName|(Необязательно) Настройка доверенного сертификата для доменного имени. Это позволяет использовать PFX-сертификат, содержащий закрытый ключ.|  
    |TrustedCertPassword|(Необязательно) Пароль для импорта PFX-файла.|  
    |EnableVPN|(Необязательно) Включение VPN по умолчанию.|  
    |VpnIPv4StartAddress|(Необязательно) Задание начального адреса VPN.|  
    |VpnIPv4EndAddress|(Необязательно) Задание конечного адреса VPN.|  
    |VpnBaseIPv6Address|(Необязательно) Задание базового IPV6-адреса для VPN.|  
    |VpnIPv6PrefixLength|(Необязательно) Задание длины префикса IPv6-адреса VPN.|  
    |IsHosted|(Необязательно) Если не указано, значение по умолчанию – "ложь". Задайте это значение, если установка выполняется в среде поставщика услуг размещения. При этом конфигурация маршрутизатора отключается.|  
    |StaticIPv4Address|(Необязательно) Укажите статический IP-адрес, если необходимо настроить статический IP-адрес вместо динамического.|  
    |StaticIPv4Gateway|(Необязательно) Укажите адрес основного шлюза, если необходимо настроить статический IP-адрес вместо динамического.|  
    |StaticIPv4SubnetMask|(Необязательно) Укажите маску подсети, если необходимо настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6Address|(Необязательно) Укажите IP-адрес по умолчанию, если необходимо настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6SubnetPrefixLength|(Необязательно) Укажите длину префикса IPv6 подсети, если хотите настроить статический IP-адрес вместо динамического.|  
    |StaticIPv6Gateway|(Необязательно) Укажите адрес шлюза по умолчанию, если хотите настроить статический IP-адрес вместо динамического.|  
    |ClientBackupOn|(Необязательно) Выключите архивацию клиента по умолчанию при подключении к серверу новых клиентов.|  
    |FileHistoryOn|(Необязательно) Выключите архивацию журнала файлов по умолчанию при подключении к серверу новых клиентов, работающих в среде Windows 8 Consumer Preview.|  
    |EnableRWA|Активируется удаленный веб-доступ при установке Windows Server Essentials, но настройка маршрутизатора. Поддерживается только при чистой установке продукта. Значение по умолчанию — "ложь".|  
    |IPv4DNSForwarder|Установите сервер пересылки IPv4 DNS.|  
    |IPv6DNSForwarder|Установите сервер пересылки Set IPv6 DNS.|  
    |LaunchPadHiddenTasks|— (Необязательно) можно скрыть записи резервной копии или / и панель мониторинга администратора запись на панели запуска.<br /><br /> — Чтобы отключение панели администрирования: LaunchPadHiddenTasks=Microsoft.LaunchPad.AdminDashboard<br /><br /> -Чтобы отключить резервное копирование: LaunchPadHiddenTasks=Microsoft.LaunchPad.Backup<br /><br /> — Чтобы отключение архивации и панели мониторинга: LaunchPadHiddenTasks=Microsoft.LaunchPad.Backup,Microsoft.LaunchPad.AdminDashboard|  
  
3.  Сохраните файл. Убедитесь, что файл был сохранен как cfg.ini, а не cfg.ini.txt.  
  
    > [!NOTE]
    >  Созданный файл можно сохранить на USB-устройстве флэш-памяти, которое можно использовать на определенных этапах установки. Можно также поместить файл cfg.ini в корневую папку любого жесткого диска на целевом сервере. Необходимо убедиться, что для файла выбрана кодировка ANSI или Юникод, кодировка UTF-8 не поддерживается.  
  
> [!IMPORTANT]
>  Раздел начальной настройки файла cfg.ini должен использоваться только конечным пользователем для персонализации сервера или партнером для тестирования работы пользователей сервера с помощью файла ответов автоматической установки. Этот раздел файла не предназначен для использования при создании образа.  
  
## <a name="see-also"></a>См. также  

 [Начало работы с ADK Windows Server Essentials](Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Начало работы с ADK Windows Server Essentials](../install/Getting-Started-with-the-Windows-Server-Essentials-ADK.md)   
 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)
