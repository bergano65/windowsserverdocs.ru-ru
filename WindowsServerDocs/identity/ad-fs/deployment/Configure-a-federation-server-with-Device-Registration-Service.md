---
ms.assetid: fdd1c1fd-55aa-4eb8-ae84-53f811de042c
title: настройка сервера федерации с помощью службы регистрации устройств
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 511a039afd47cf7570fffdcaf17842e0eccc5683
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843065"
---
# <a name="configure-a-federation-server-with-device-registration-service"></a>настройка сервера федерации с помощью службы регистрации устройств

>Область применения. Windows Server 2012 R2

Вы можете включить службу регистрации устройств \(DRS\) на сервере федерации после завершения процедуры, описанные в [Step 4: Настройка сервера федерации](https://technet.microsoft.com/library/dn303424.aspx). Служба регистрации устройств предоставляет механизм адаптации эффективная идентификации, постоянные единого входа\-на \(SSO\)и условный доступ для пользователей, которым требуется доступ к компании ресурсы. Дополнительные сведения о DRS см. в разделе [присоединение к рабочему месту с любого устройства для единого входа и эффективная двухфакторная проверка подлинности между компании приложениях](../../ad-fs/operations/Join-to-Workplace-from-Any-Device-for-SSO-and-Seamless-Second-Factor-Authentication-Across-Company-Applications.md)  
  
## <a name="prepare-your-active-directory-forest-to-support-devices"></a>Подготовка леса Active Directory для поддержки устройств  
  
> [!NOTE]  
> Это та\-время операции, которая должна быть запущена для подготовки леса Active Directory для поддержки устройств. Необходимо войти в систему с правами администратора предприятия и ваш лес Active Directory должен иметь схему Windows Server 2012 R2 для выполнения этой процедуры.  
>   
> Кроме того DRS требуется наличие по крайней мере один сервер глобального каталога в корневом домене леса. Сервер глобального каталога нужно запустить Initialize\-ADDeviceRegistration и во время проверки подлинности AD FS. Инициализирует AD FS в\-памяти представление конфигурации DRS объекта при каждом запросе проверки подлинности, и если не удается найти объект конфигурации DRS на Контроллере домена в текущем домене, запрос производится попытка от глобального Каталога, на котором были объекты DRS настраивается во время инициализации\-ADDeviceRegistration.  
  
#### <a name="to-prepare-the-active-directory-forest"></a>Подготовка леса Active Directory  
  
1.  На своем сервере федерации откройте командное окно Windows PowerShell и введите:  
  
    ```  
    Initialize-ADDeviceRegistration  
    ```  
  
2.  При запросе ServiceAccountName, введите имя учетной записи службы, которые вы выбрали в качестве учетной записи службы для AD FS.  Если это Групповая управляемая учетная запись, укажите учетную запись в **домена\\название_учетной_записи $** формат. Для учетной записи домена, используйте формат **домена\\accountname**.  
  
## <a name="enable-device-registration-service-on-a-federation-server-farm-node"></a>Включение службы регистрации устройств в узле фермы серверов федерации  
  
> [!NOTE]  
> Необходимо войти в систему с правами администратора домена для выполнения этой процедуры.  
  
#### <a name="to-enable-device-registration-service"></a>Чтобы включить службу регистрации устройств  
  
1.  На своем сервере федерации откройте командное окно Windows PowerShell и введите:  
  
    ```  
    Enable-AdfsDeviceRegistration  
    ```  
  
2.  Повторите этот шаг, на каждом узле фермы федерации в ферме AD FS...  
  
## <a name="enable-seamless-second-factor-authentication"></a>Включить простой двухфакторной проверки подлинности  
Простой двухфакторной проверки подлинности — это расширение в AD FS, которая обеспечивает дополнительный уровень защиты доступа к корпоративным ресурсам и приложениям с внешними устройствами, которые пытаются получить к ним доступ. Если личные устройства, присоединенные к рабочей области она станет «известные» устройства, а администраторы могут использовать эту информацию для обеспечения условного доступа и доступа к ресурсам.  
  
#### <a name="to-enable-seamless-second-factor-authentication-persistent-single-sign-on-sso-and-conditional-access-for-workplace-joined-devices"></a>Чтобы включить простой, во-вторых с помощью многофакторной идентификации, постоянные единого входа\-на \(SSO\) и условного доступа для устройства, подключенные к рабочему месту  
  
1.  В консоли управления AD FS перейдите к политики проверки подлинности. Выберите Редактировать глобальную первичную аутентификацию. Установите флажок рядом с включить аутентификацию устройств и нажмите кнопку ОК.  
  
## <a name="update-the-web-application-proxy-configuration"></a>Обновить конфигурацию прокси веб-приложения  
  
> [!IMPORTANT]  
> Необходимо опубликовать службу регистрации устройств для прокси веб-приложения.  Служба регистрации устройств будет доступно прокси веб-приложения после его включения для сервера федерации.  Может потребоваться выполнить эту процедуру, чтобы обновить конфигурацию прокси веб-приложения, если оно было развернуто до включения службы регистрации устройств.  
  
#### <a name="to-update-the-web-application-proxy-configuration"></a>Чтобы обновить конфигурацию прокси-сервера веб-приложения  
  
1.  На сервере прокси веб-приложения откройте командную строку Windows PowerShell и введите  
  
    ```  
    Update-WebApplicationProxyDeviceRegistration  
    ```  
  
2.  При запросе учетных данных, введите учетные данные учетной записи, которая имеет права администратора на серверах федерации.  
  
## <a name="see-also"></a>См. также 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
