---
title: Настройка политик запросов на подключение
description: В этом разделе содержатся сведения о настройке политик запросов на подключение на сервере политики сети в Windows Server 2016.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: f62c6a67-4dda-47f8-8bdf-9b76c37953e6
ms.author: pashort
author: shortpatti
ms.openlocfilehash: d62beb3106141d4683c957020bc96e4a7dfb306f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405474"
---
# <a name="configure-connection-request-policies"></a>Настройка политик запросов на подключение

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

С помощью этого раздела можно создавать и настраивать политики запросов на подключение, определяющие, будет ли локальный сервер политики сети обрабатывать запросы на подключение или пересылать их на удаленный сервер RADIUS для обработки.

Политики запросов на подключение — это наборы условий и параметров, которые позволяют сетевым администраторам определять, какие серверы протокол RADIUS (RADIUS) выполняют проверку подлинности и авторизацию запросов на подключение, которые сервер, на котором работает сервер политики сети \(\) NPS, получают от клиентов RADIUS.

Политика запросов на подключение по умолчанию использует NPS в качестве сервера RADIUS и обрабатывает все запросы проверки подлинности локально.

Чтобы настроить сервер политики сети на работу в качестве прокси-сервера RADIUS и пересылать запросы на подключение другим серверам политики сети или RADIUS, необходимо настроить группу удаленных серверов RADIUS в дополнение к добавлению новой политики запросов на подключение, в которой указаны условия и параметры, которые запросы на подключение должны совпадать.

Вы можете создать новую группу удаленных серверов RADIUS во время создания новой политики запросов на подключение с помощью мастера создания политики запросов на подключение.

Если сервер политики сети не должен работать в качестве сервера RADIUS и обрабатывать запросы на подключение локально, можно удалить политику запросов на подключение по умолчанию.

Если вы хотите, чтобы сервер политики сети действовал в качестве сервера RADIUS, обрабатывая запросы на подключение локально и в качестве прокси-сервера RADIUS, пересылая некоторые запросы на подключение в группу удаленных серверов RADIUS, добавьте новую политику, выполнив приведенную ниже процедуру, и убедитесь, что по умолчанию используется. Политика запросов на подключение — это последняя обработанная политика, которая помещается в последнюю очередь в списке политик.

## <a name="add-a-connection-request-policy"></a>Добавление политики запроса на подключение

Чтобы выполнить эту процедуру, вы должны быть членом группы **Администраторы домена** или аналогичной.

### <a name="to-add-a-new-connection-request-policy"></a>Добавление новой политики запросов на подключение 

1. В диспетчер сервера выберите **Сервис**, а затем — **сервер политики сети** , чтобы открыть консоль NPS. 
2. В дереве консоли дважды щелкните **политики**.
3. Щелкните правой кнопкой мыши **политики запросов на подключение**и выберите **создать политику запросов на подключение**.
4. Используйте мастер создания политики запросов на подключение, чтобы настроить политику запросов на подключение и, если она не была настроена, группу удаленных серверов RADIUS.


Дополнительные сведения об управлении NPS см. в разделе [Управление сервером политики сети](nps-manage-top.md).

Дополнительные сведения о NPS см. в разделе [сервер политики сети (NPS)](nps-top.md).

