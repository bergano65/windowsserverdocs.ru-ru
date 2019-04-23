---
title: Защита учетных данных и управление ими
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-credential-protection
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e457229c-0126-40fe-948c-101c943e1b57
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 16cc1f2260bf0552da6902dc3e97de65d29c7931
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59812205"
---
# <a name="credentials-protection-and-management"></a>Защита учетных данных и управление ими

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе для ИТ-специалистов рассматриваются функции и методы, появившиеся в Windows Server 2012 R2 и Windows 8.1 для защиты учетных данных и элементов управления проверки подлинности домена для уменьшения риска кражи.

## <a name="BKMK_CredentialsProtectionManagement"></a>
### <a name="restricted-admin-mode-for-remote-desktop-connection"></a>Ограниченный административный режим для подключения к удаленному рабочему столу
Ограниченный административный режим позволяет устанавливать интерактивное подключение к удаленному серверу без передачи на него своих учетных данных. В случае взлома сервера это предотвращает раскрытие учетных данных при изначальном подключении.

Используя этот режим для защиты учетных данных администратора, клиент удаленного рабочего стола предпринимает попытку интерактивного подключения к главному компьютеру, также поддерживающему этот режим. После успешной проверки прав администратора и поддержки ограниченного административного режима для учетной записи подключающегося пользователя происходит установка соединения. В противном случае попытка подключения терпит неудачу. При использовании ограниченного административного режима ни при каких условиях не происходит отправка на удаленные компьютеры учетных данных в виде обычного текста или в других доступных для использования формах.

### <a name="lsa-protection"></a>Защита LSA
Локальная система безопасности (LSA), входящая в службу LSASS, проверяет пользователей во время локального и удаленного входа и применяет локальные политики безопасности. Операционная система Windows 8.1 предоставляет дополнительную защиту для LSA, предотвращая внедрение кода незащищенными процессами. Это усиливает безопасность учетных данных, которые хранит LSA и которыми управляет LSA. Этот параметр защищенного процесса для LSA можно настроить в Windows 8.1, но по умолчанию в Windows RT 8.1 и не может быть изменено.

Сведения о настройке брандмауэра см. в разделе [Configuring Additional LSA Protection](configuring-additional-lsa-protection.md).

### <a name="protected-users-security-group"></a>Группа безопасности "Защищенные пользователи"
Эта новая глобальная группа домена активирует новый ненастраиваемую защиту для устройств и главных компьютеров под управлением Windows Server 2012 R2 и Windows 8.1. В группу защищенных пользователей можно расширить защиту доменных контроллеров и доменов в доменах Windows Server 2012 R2. Это позволяет существенно уменьшить количество типов учетных данных, доступных при подключении пользователей к компьютерам сети с помощью устройства, которое не было взломано.

Члены группы защищенных пользователей ограничены в следующие методы проверки подлинности:

-   Члены группы "Защищенные пользователи" могут устанавливать подключение только при помощи протокола Kerberos. Учетная запись не может пройти проверку подлинности с помощью NTLM, дайджест-проверки или CredSSP. На устройстве под управлением Windows 8.1 пароли не кэшируются, поэтому устройство, которое используется один из этих поставщиков поддержки безопасности (SSP) сможет пройти проверку подлинности в домен, если учетная запись входит в группу защищенных пользователей.

-   В процессе предварительной проверки подлинности протоколом Kerberos не будут использоваться менее надежные способы шифрования DES и RC4. Это означает, что домен должен как минимум быть настроен на поддержку наборов шифров AES.

-   Учетная запись пользователя не может быть делегирована с Kerberos ограниченное или неограниченное делегирование. Это означает, что если компьютер входит в группу "Защищенные пользователи", старые подключения к другим системам могут выйти из строя.

-   Время действия билетов предоставления билетов Kerberos по умолчанию, составляющее 4 часа, можно изменить в настройках политик проверки подлинности и приемников команд в центре администрирования Active Directory. Настройки по умолчанию означают, что по прошествии четырех часов пользователь должен снова пройти проверку подлинности.

> [!WARNING]
> Учетные записи служб и компьютеров не должны входить в группу защищенных пользователей. Это группа не предоставляет локальной защиты, поскольку пароль или сертификат всегда доступен на узле. Проверка подлинности завершится сбоем с ошибкой «имя пользователя или пароль неправильный» для службы или компьютера, который добавляется в группу защищенных пользователей.

Подробную информацию об этой группе см. в разделе [Группа безопасности "Защищенные пользователи"](protected-users-security-group.md).

### <a name="authentication-policy-and-authentication-policy-silos"></a>Политика проверки подлинности и приемники команд политик проверки подлинности
Вводятся политики на основе леса Active Directory, и они могут применяться к учетным записям в домене с режимом работы домена Windows Server 2012 R2. Эти политики проверки подлинности могут управлять тем, какие узлы используют пользователи для входа. Политики функционируют совместно с группой безопасности "Защищенные пользователи", и для проверки подлинности этих учетных записей администраторы могут применить условия контроля доступа. Эти политики проверки подлинности изолируют соответствующие учетные записи и ограничивают для них доступную область сети.

Новый класс объектов Active Directory, политика проверки подлинности, дает возможность применения конфигурации проверки подлинности к классам учетных записей в доменах с режимом работы домена Windows Server 2012 R2. Политики проверки подлинности применяются при обмене Kerberos типа AS и TGS. Классы учетных записей Active Directory.

-   Пользовательская

-   Computer

-   Управляемая учетная запись службы

-   Групповая управляемая учетная запись службы

Подробную информацию см. в разделе [Политики проверки подлинности и приемники команд политик проверки подлинности](authentication-policies-and-authentication-policy-silos.md).

Подробную информацию о настройке защищенных учетных записей см. в разделе [Настройка защищенных учетных записей](how-to-configure-protected-accounts.md).

## <a name="see-also"></a>См. также
Дополнительные сведения о соглашениях LSA и LSASS см. в разделе [Обзор входа в Windows и проверки подлинности](https://technet.microsoft.com/library/dn169029(v=ws.10).aspx).


