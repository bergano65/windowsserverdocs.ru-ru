---
title: Перенос в MultiPoint Services в Windows Server 2016
description: Сведения о миграции с предыдущей версии служб MultiPoint
ms.custom: na
ms.date: 07/29/2016
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16c217ad-700a-48a3-8398-4a7f7e9edb52
author: lizap
manager: dongill
ms.author: elizapo
ms.openlocfilehash: 24c35c31bf920c41bafa16901ee30a023565dad8
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59861205"
---
# <a name="multipoint-services-migration-in-windows-server-2016"></a>Миграция служб multiPoint в Windows Server 2016
>Область применения. Windows Server 2016

Можно перенести из предыдущего выпуска Windows Server 2016 MultiPoint Services до версии RTM MultiPoint Services. Ниже приведены сведения подготовки сведения и переноса и проверки.

Документация и средства переноса облегчают процесс переноса параметров ролей сервера и данных с существующего сервера на конечный сервер под управлением Windows Server 2016. Описанная в этом руководстве процедура позволяет упростить процесс миграции, сократить его продолжительность, повысить точность и избежать потенциальных конфликтов. 

## <a name="what-to-know-before-you-begin"></a>Что следует знать перед началом работы
Перед началом процесса миграции, имейте в виду следующее:

- Процесс миграции автоматически собирать и запишите параметры для приложений на роль MultiPoint Services. Необходимо создать план миграции, настроенный для приложений, которые требуется перенести. Это также верно при использовании функции виртуальных рабочих столов в MultiPoint Services.
- В этом руководстве не предоставляет руководство по перемещению данных, сохраненные в пользователя или общих папок на сервере MultiPoint. Это относится к регулярных станции и виртуального рабочего стола станции.
- Это руководство содержит инструкции по миграции при исходном сервере выполняется несколько ролей. Если на сервере выполняется несколько ролей, необходимо разработать специальную процедуру миграции для данной серверной среды на основе информации из руководств по миграции ролей.
- Это руководство содержит сведения для переноса удаленных рабочих столов клиентских лицензий. Дополнительные сведения см. в разделе [перенос удаленного рабочего стола клиентских лицензий служб (RDS CAL)](https://technet.microsoft.com/library/dd851844.aspx).

## <a name="supported-migration-scenarios-for-multipoint-services-in-windows-server-2016"></a>Поддерживаемые сценарии миграции для служб MultiPoint в Windows Server 2016
Службы роли службы MultiPoint доступна в Windows Server 2016 Standard и Datacenter. Это руководство по миграции описан процесс переноса служб ролей служб Multipoint с исходного сервера под управлением Windows Server 2016 на конечный сервер под управлением той же версии.

## <a name="scenarios-that-are-not-supported"></a>Сценарии, которые не поддерживаются

Не поддерживаются следующие сценарии миграции:

- Миграция или обновление с Windows MultiPoint Server 2012 и 2011 г.
- Миграция с исходного сервера на конечный сервер, на котором выполняется в операционной системе с другой системы установленного языка пользовательского интерфейса.
- Миграции службы роли служб MultiPoint из физических серверов на виртуальные машины.
- Перенос любых приложений или параметров приложения с сервера MultiPoint.

## <a name="the-impact-of-migration-on-multipoint-services"></a>Влияние миграции в системе MultiPoint Services
Имейте в виду, что роль MultiPoint Services не будут доступны во время миграции. Чтобы минимизировать время простоя и сократить воздействие на пользователей, планируйте выполнение переноса данных на часы внепиковой нагрузки. Уведомите пользователей, что в это время ресурсы будут недоступны.

## <a name="migration-information-and-steps"></a>Сведения о миграции и действия
Используйте следующие сведения для планирования и выполнения миграции MultiPoint Services:

- [Соберите сведения, необходимые для миграции.](multipoint-services-migration-preparation.md)
- [Миграция службы роли служб MultiPoint.](multipoint-services-migration-steps.md)
- [Проверка миграции и выполните все задачи очистки после миграции](multipoint-services-post-migration-steps.md)