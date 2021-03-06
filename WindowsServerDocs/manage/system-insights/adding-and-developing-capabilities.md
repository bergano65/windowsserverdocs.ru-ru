---
title: Добавление и разработка возможностей
description: System Insights позволяет добавлять новые возможности прогнозирования в Insights системы без использования все обновления операционной системы. Это позволяет разработчикам, включая Майкрософт и сторонних производителей, чтобы создать и передать новый выпуск среднего возможности для сценариев, которые вас интересуют. Новые возможности можно указать пользовательские данные для сбора и анализа, и они также интегрируются с существующей плоскости управления Insights системы.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: system-insights
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ''
author: gawatu
ms.author: gawatu
manager: mallikarjun.chadalapaka
ms.date: 7/31/2018
ms.openlocfilehash: 8caddead774ac69a38906f3c0a0d2eaf005c1d28
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817485"
---
# <a name="adding-and-developing-new-capabilities"></a>Добавления и разработки новых возможностей

>Область применения. Windows Server 2019

System Insights позволяет добавлять новые возможности прогнозирования в Insights системы без использования все обновления операционной системы. Это позволяет разработчикам, включая Майкрософт и сторонних производителей, чтобы создать и передать новый выпуск среднего возможности для сценариев, которые вас интересуют. 

Либо новая возможность могут интегрироваться и дополнять существующую инфраструктуру системы аналитики:

- Новые возможности можно **укажите любое событие счетчика или система производительности**, который собираемых, сохраненными на локальном компьютере и возвращается возможности для анализа в том случае, если функция вызывается.  
- Новые возможности можно **использовать существующие Windows Admin Center и плоскости управления PowerShell**. Не только будет в системе Insights обнаруживаемый новые возможности, они также задействуют пользовательские расписания и действия по исправлению. 

## <a name="manage-new-capabilities"></a>Управление новыми возможностями
- [Узнайте,](add-remove-update-capabilities.md) как добавление, удаление и обновление возможностей с помощью PowerShell. 

## <a name="develop-a-capability"></a>Разработка возможности
Используйте следующие ресурсы помогут вам приступить к написанию собственных пользовательских возможностей:
- [Узнайте,](data-sources.md) об источниках данных, можно собирать.
- [Скачайте](https://www.nuget.org/packages/Microsoft.WindowsServer.SystemInsights/) пакет NuGet Insights системы, который содержит классы и интерфейсы, вам нужно написать функцию.
- [Посетите](https://aka.ms/systeminsights-api) документацию по API, чтобы узнать о системе Insights классы и интерфейсы. 
- [Используйте](https://aka.ms/systeminsights-samplecapability) возможность образец системы аналитики помогут вам приступить к работе. Это показано, как зарегистрировать функцию, указать источники данных для сбора и анализа данных системы.

>[!NOTE]
>Это предварительная функциональные возможности. Это может быть изменена, так как мы добавлять новые функциональные возможности и встраивать обратной связи.

## <a name="see-also"></a>См. также
Дополнительные сведения о системе аналитики, используйте следующие ресурсы:

- [Обзор системы аналитики](overview.md)
- [Основные сведения о возможностях](understanding-capabilities.md)
- [Управление возможностями](managing-capabilities.md)
- [Добавление, удаление и обновление возможностей](add-remove-update-capabilities.md)
- [Система аналитики часто задаваемые вопросы](faq.md)