---
title: Обработка запросов на подключение
description: В этом разделе приводится обзор обработки запросов на подключение к серверу политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 849d661a-42c1-4f93-b669-6009d52aad39
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 268a307336d9a4fae1be5621eec7c32a06a6204e
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405395"
---
# <a name="connection-request-processing"></a>Обработка запросов на подключение

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела вы узнаете об обработке запросов на подключение на сервере политики сети в Windows Server 2016.

>[!NOTE]
>Помимо этого раздела, доступна следующая документация по обработке запросов на подключение.
> - [Политики запросов на подключение](nps-crp-crpolicies.md)
> - [Имена областей](nps-crp-realm-names.md)
> - [Группы удаленных серверов RADIUS](nps-crp-rrsg.md)

Можно использовать обработку запросов на подключение, чтобы указать, где выполняется проверка подлинности запросов на локальном компьютере или на удаленном RADIUS-сервере, входящем в группу удаленных серверов RADIUS. 

Если требуется, чтобы локальный сервер, на котором работает сервер политики сети (NPS), выполнял проверку подлинности для запросов на подключение, можно использовать политику запросов на подключение по умолчанию без дополнительной настройки. В зависимости от политики по умолчанию NPS проверяет подлинность пользователей и компьютеров, имеющих учетную запись в локальном домене и в доверенных доменах.

Если вы хотите перенаправить запросы на подключение к удаленному серверу политики сети или к другим серверам RADIUS, создайте группу удаленных серверов RADIUS, а затем настройте политику запросов на подключение, которая перенаправляет запросы в эту группу удаленных серверов RADIUS. В этой конфигурации сервер политики сети может перенаправлять запросы на проверку подлинности на любой сервер RADIUS, и пользователи с учетными записями в недоверенных доменах могут пройти проверку подлинности.

На следующем рисунке показан путь сообщения запроса доступа с сервера доступа к сети к прокси-серверу RADIUS, а затем на сервере RADIUS в группе удаленных серверов RADIUS. На прокси-сервере RADIUS сервер сетевого доступа настроен в качестве RADIUS-клиента. и на каждом сервере RADIUS прокси-сервер RADIUS настраивается как клиент RADIUS.


![Обработка запроса на подключение к NPS](../../media/Nps-Connection-Request-Processing/Nps-Connection-Request-Processing.jpg)


>[!NOTE]
>Серверы сетевого доступа, используемые с NPS, могут быть устройствами шлюза, совместимыми с протоколом RADIUS, такими как точки беспроводного доступа 802.1 X и коммутаторами проверки подлинности, серверами с удаленным доступом, настроенными как VPN или серверы удаленного доступа. другие совместимые с RADIUS устройства.

Если требуется, чтобы сервер политики сети обрабатывал некоторые запросы проверки подлинности локально при пересылке других запросов в группу удаленных серверов RADIUS, настройте несколько политик запросов на подключение.

Сведения о настройке политики запросов на подключение, указывающей, какая группа серверов политики сети или сервера RADIUS обрабатывает запросы проверки подлинности, см. в разделе политики запросов на подключение.

Чтобы указать сервер политики сети или другие серверы RADIUS, на которые перенаправляются запросы на проверку подлинности, см. Раздел удаленные группы серверов RADIUS.

## <a name="nps-as-a-radius-server-connection-request-processing"></a>Сервер политики сети как обработка запроса на соединение с сервером RADIUS

При использовании NPS в качестве сервера RADIUS сообщения RADIUS обеспечивают проверку подлинности, авторизацию и учет подключений доступа к сети следующим образом.

1. Серверы доступа, такие как серверы удаленного доступа к сети, VPN-серверы и точки беспроводного доступа, получают запросы на подключение от клиентов доступа. 

2. Сервер доступа, настроенный на использование RADIUS в качестве протокола проверки подлинности, авторизации и учета, создает сообщение запроса доступа и отправляет его на сервер политики сети. 

3. Сервер политики сети оценивает сообщение запроса доступа. 

4. При необходимости сервер политики сети отправляет сообщение с запросом доступа к серверу доступа. Сервер доступа обрабатывает запрос и отправляет обновленный запрос на доступ к NPS. 

5. Проверяются учетные данные пользователя, а свойства входящих звонков учетной записи пользователя получаются с помощью безопасного подключения к контроллеру домена. 

6. Авторизация выполняется с помощью свойств входящих звонков учетной записи пользователя и политики сети. 

7. Если попытка подключения проходит проверку подлинности и авторизацию, NPS отправляет на сервер доступа сообщение о доступе. Если попытка подключения не прошла проверку подлинности или не авторизована, NPS отправляет на сервер доступа сообщение об отклонении доступа. 

8. Сервер доступа завершает процесс подключения с клиентом доступа и отправляет сообщение запроса учетной записи на сервер политики сети, где сообщение заносится в журнал. 

9. Сервер политики сети отправляет запрос на учетные данные для сервера доступа. 

>[!NOTE]
>Сервер доступа также отправляет сообщения запроса на учет во время установки соединения, при закрытии подключения клиента доступа и при запуске и остановке сервера доступа.

## <a name="nps-as-a-radius-proxy-connection-request-processing"></a>Обработка запросов NPS в качестве прокси-сервера RADIUS

Если сервер политики сети используется в качестве прокси-сервера RADIUS между клиентом RADIUS и сервером RADIUS, сообщения RADIUS для подключений доступа к сети перенаправляются следующим образом:

1. Серверы доступа, такие как серверы удаленного доступа к сети, серверы виртуальной частной сети (VPN) и точки беспроводного доступа, получают запросы на подключение от клиентов доступа.

2. Сервер доступа, настроенный на использование RADIUS в качестве протокола проверки подлинности, авторизации и учета, создает сообщение запроса доступа и отправляет его в NPS, который используется в качестве прокси-сервера RADIUS сервера политики сети.

3. Прокси-сервер политики сети RADIUS получает сообщение запроса доступа и, в зависимости от настроенных локально политик запросов на подключение, определяет, куда перенаправлять сообщение запроса доступа.

4. Прокси-сервер NPS RADIUS перенаправляет сообщение запроса доступа на соответствующий сервер RADIUS.

5. Сервер RADIUS оценивает сообщение запроса доступа.

6. При необходимости сервер RADIUS отправляет сообщение с запросом доступа к прокси-серверу NPS, где он перенаправляется на сервер доступа. Сервер доступа обрабатывает проблему с клиентом доступа и отправляет обновленный запрос на доступ к прокси-серверу NPS, где он перенаправляется на сервер RADIUS.

7. Сервер RADIUS выполняет проверку подлинности и авторизует попытки подключения.

8. Если попытка подключения проходит проверку подлинности и авторизацию, сервер RADIUS отправляет сообщение о доступе с правами доступа на прокси-сервер NPS, где он перенаправляется на сервер доступа. Если попытка подключения не прошла проверку подлинности или не авторизована, сервер RADIUS отправляет сообщение об отказе в доступе на прокси-сервер NPS, где он перенаправляется на сервер доступа.

9. Сервер доступа завершает процесс подключения с клиентом доступа и отправляет сообщение запроса учетных данных в прокси-сервер NPS RADIUS. Прокси-сервер NPS RADIUS регистрирует данные учета и перенаправляет их на сервер RADIUS.

10. Сервер RADIUS отправляет учетные данные для прокси-сервера NPS, который перенаправляется на сервер доступа.

Дополнительные сведения о NPS см. в разделе [сервер политики сети (NPS)](nps-top.md).
