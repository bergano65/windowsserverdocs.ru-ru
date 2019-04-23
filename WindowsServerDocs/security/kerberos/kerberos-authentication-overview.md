---
title: Kerberos Authentication Overview
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-kerberos
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 646c6309-e865-4be2-b415-44dd125af5c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 9f8878fb959c34663b1e1f3858fa7e0b6e7b6105
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824115"
---
# <a name="kerberos-authentication-overview"></a>Kerberos Authentication Overview

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

Kerberos — это протокол проверки подлинности, используемый для проверки удостоверения пользователя или узла. Этот раздел содержит сведения о проверке подлинности Kerberos в Windows Server 2012 и Windows 8.

## <a name="BKMK_OVER"></a>Описание компонента
Операционные системы Windows Server реализуют протокол проверки подлинности Kerberos версии 5 и расширения для проверки подлинности с помощью открытого ключа, переноса данных авторизации и делегирования. Клиент проверки подлинности Kerberos реализован как поставщик поддержки безопасности \(SSP\), и он может осуществляться через интерфейс поставщика поддержки безопасности \(SSPI\). Начальная проверка подлинности пользователя интегрирована с помощью единого входа Winlogon\-на архитектуре.

Центр распространения ключей Kerberos \(KDC\) интегрирован с другими службами безопасности Windows Server, работающие на контроллере домена. Служба KDC использует базу данных доменных служб Active Directory домена как базы данных учетной записи безопасности. Доменные службы Active Directory необходимы для реализации Kerberos по умолчанию в рамках домена или леса.

## <a name="kerb_tr_Kerb_Benefits"></a>Практическое применение
Преимущества, полученные с помощью Kerberos для домена\-, проверку подлинности на основе:

-   **Делегирование проверки подлинности.**

    Службы, работающие в операционных системах Windows может олицетворять клиентский компьютер, при доступе к ресурсам от имени клиента. Во многих случаях служба может выполнить свою работу для клиента путем доступа к ресурсам на локальном компьютере. Когда клиентский компьютер проходит проверку подлинности в службе, протоколы NTLM и Kerberos предоставляют сведения авторизации, которые требуются службе для локального олицетворения клиентского компьютера. Однако некоторые распределенные приложения разработаны таким образом, чтобы внешнего\-интерфейса веб-службы необходимо использовать удостоверение клиентского компьютера, когда он подключается к резервного\-службам на других компьютерах. Проверка подлинности Kerberos поддерживает механизм делегирования, позволяющий службе действовать от имени клиента при подключении к другим службам.

-   **Единый вход.**

    Использование проверки подлинности Kerberos в домене или в лесу позволяет пользователю или службе получать доступ к ресурсам, разрешенным администраторами, без многократного ввода учетных данных. После первоначального входа в систему домена через функцию Winlogon протокол Kerberos управляет учетными данными по всему лесу при каждой попытке доступа к ресурсам.

-   **Взаимодействие.**

    Реализация протокола Kerberos V5 Майкрософт основана на стандартах\-отслеживания спецификации, которые рекомендуются для Internet Engineering Task Force \(IETF\). Поэтому в операционных системах Windows протокол Kerberos лежит в основе взаимодействия с другими сетями, в которых для проверки подлинности также используется протокол Kerberos. Кроме того, корпорация Майкрософт публикует документацию "Протоколы Windows", содержащую сведения о реализации протокола Kerberos. Документация содержит технические требования, ограничения, зависимости и Windows\-поведение конкретного протокола для корпорации Майкрософт реализация протокола Kerberos.

-   **Более эффективная проверка подлинности на серверах.**

    Перед применением Kerberos можно использовать проверку подлинности NTLM, которая требует подключения сервера приложений к контроллеру домена для проверки подлинности каждого клиентского компьютера или службы. С помощью протокола Kerberos возобновляемые билеты сеанса заменяют pass\-через проверку подлинности. Сервер не требуется переходить к контроллеру домена \(, если только требуется проверка сертификата атрибута привилегий \(PAC\)\). Вместо этого сервер может проверить подлинность клиентского компьютера путем проверки учетных данных, предоставленных клиентом. Клиентские компьютеры могут получить учетные данные для определенного сервера однократно и затем использовать их в течение всего сеанса после входа в сеть.

-   **Взаимная проверка подлинности.**

    С помощью протокола Kerberos сторона на любом конце сетевого подключения может проверить, что сторона на противоположном конце является субъектом, за которого себя выдает. NTLM не позволяет клиентам проверить удостоверение сервера с или включить одному серверу проверять удостоверение другого. Проверка подлинности NTLM предназначена для сетевой среды, в которой серверы считаются подлинными. В протоколе Kerberos такого допущения нет.

## <a name="see-also"></a>См. также
[Обзор проверки подлинности Windows](../windows-authentication/windows-authentication-overview.md)

