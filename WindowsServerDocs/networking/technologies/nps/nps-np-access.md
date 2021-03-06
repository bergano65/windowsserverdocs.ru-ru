---
title: Разрешение на доступ
description: В этом разделе приводятся общие сведения о разрешении на доступ политики сети для сервера политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: d6d1ca5e-bde0-4509-9e14-dc3fa9ff447e
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 8a63bf7d277108a528a3ab1c20263e31b59c1547
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405380"
---
# <a name="access-permission"></a>Разрешение на доступ

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Разрешение на доступ настраивается на вкладке **Обзор** каждой сетевой политики на сервере политики сети (NPS). 

Этот параметр позволяет настроить политику, чтобы предоставить или запретить доступ пользователям, если условия и ограничения политики сети соответствуют запросу на подключение. 

Параметры разрешений на доступ имеют следующий результат:

- **Предоставление доступа**. Доступ предоставляется, если запрос на подключение соответствует условиям и ограничениям, настроенным в политике.
- **Запрет доступа**. Отказано в доступе, если запрос на подключение соответствует условиям и ограничениям, настроенным в политике.

Разрешение на доступ также предоставляется или запрещается в зависимости от конфигурации свойств входящих звонков каждой учетной записи пользователя.

>[!NOTE]
>Учетные записи пользователей и их свойства, такие как свойства входящих звонков, настраиваются в консоли управления (Active Directory пользователи и компьютеры) или оснастке MMC "Локальные пользователи и группы" \(ММС\) в зависимости от того, установлены ли Active Directory&reg; доменных служб (AD DS).

Параметр учетной записи пользователя **разрешение на доступ к сети**, настроенный в свойствах входящих звонков учетных записей пользователей, переопределяет параметр разрешения на доступ к политике сети. Если разрешение на доступ к сети для учетной записи пользователя настроено на **Управление доступом через политику сети NPS** , параметр разрешения доступа политики сети определяет, предоставлен ли пользователю или запрещен доступ.

>[!NOTE]
>В Windows Server 2016 значение по умолчанию для **разрешения сетевого доступа** в AD DS свойствах удаленного доступа учетной записи пользователя управляет **доступом через политику сети NPS**.

Когда сервер политики сети оценивает запросы на подключение к настроенным сетевым политикам, он выполняет следующие действия:

- Если условия первой политики не совпадают, NPS оценивает следующую политику и продолжит выполнение этого процесса, пока не будет найдено соответствие или не будут проверены все политики для соответствия.
- Если условия и ограничения политики совпадают, сервер политики сети предоставляет или запрещает доступ в зависимости от значения параметра разрешения доступа в политике.
- Если условия соответствия политике, но ограничения в политике не совпадают, сервер политики сети отклоняет запрос на подключение.
- Если условия всех политик не совпадают, сервер политики сети отклоняет запрос на подключение.

## <a name="ignore-user-account-dial-in-properties"></a>Игнорировать свойства входящих звонков учетной записи пользователя

Можно настроить политику сети NPS, чтобы игнорировать свойства входящих звонков учетных записей пользователей, установив или сняв флажок **игнорировать свойства удаленного доступа учетной записи пользователя** на вкладке **Обзор** политики сети. 

Обычно, когда NPS выполняет авторизацию запроса на подключение, он проверяет свойства удаленного доступа учетной записи пользователя, где значение параметра разрешения на доступ к сети может влиять на то, разрешено ли пользователю подключаться к сети. При настройке NPS для игнорирования свойств входящих звонков учетных записей пользователей во время авторизации параметры сетевой политики определяют, предоставлен ли пользователю доступ к сети.

В свойствах входящих звонков учетных записей пользователей содержатся следующие параметры.

- Разрешение на доступ к сети
- Идентификатор звонящего
- Параметры обратного вызова
- Статический IP-адрес
- Статические маршруты

Для поддержки нескольких типов подключений, для которых NPS обеспечивает проверку подлинности и авторизацию, может потребоваться отключить обработку свойств входящих звонков учетной записи пользователя. Это можно сделать для поддержки сценариев, в которых определенные свойства входящих звонков не требуются.

Например, свойства "Caller-ID", "Callback", "статический IP-адрес" и "статические маршруты" предназначены для клиента, который подключается к серверу доступа к сети \(\)NAS, а не для клиентов, подключающихся к точкам беспроводного доступа. Беспроводная точка доступа, получающая эти параметры в сообщении RADIUS из NPS, может не суметь обработать их, что может привести к отключению беспроводного клиента.

Если сервер политики сети обеспечивает проверку подлинности и авторизацию для пользователей, которые одновременно подключаются к сети организации и обращаются к ней через точки беспроводного доступа, необходимо настроить свойства удаленного доступа для поддержки обоих подключений удаленного доступа \(путем установки свойств входящих звонков\) или беспроводных подключений \(, не устанавливая\)свойства входящих звонков.

Сервер политики сети можно использовать для включения обработки свойств удаленного доступа для учетной записи пользователя в некоторых сценариях \(например,\) удаленного доступа, а также для отключения обработки свойств удаленного доступа в других сценариях \(например, 802.1 X Wireless и Authenticator Switch\).

Для управления доступом к сети с помощью групп и параметров разрешения на доступ в сетевой политике можно также использовать параметр **игнорировать учетные записи пользователей** . При установке флажка **игнорировать свойства удаленного доступа к учетной записи пользователя** разрешение на доступ к сети для учетной записи пользователя игнорируется.

Единственным недостатком этой конфигурации является то, что нельзя использовать дополнительные свойства удаленного доступа учетной записи пользователя для идентификатора звонящего, обратного вызова, статического IP-адреса и статических маршрутов.

Дополнительные сведения о NPS см. в разделе [сервер политики сети (NPS)](nps-top.md).
