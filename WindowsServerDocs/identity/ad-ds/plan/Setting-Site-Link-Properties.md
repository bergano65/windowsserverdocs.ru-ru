---
ms.assetid: de054ac2-a386-43ec-a537-c0de21549741
title: Задание свойств связи сайтов
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: c9a9b25aa56948e3116ebfef67a6af73917b76c2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402477"
---
# <a name="setting-site-link-properties"></a>Задание свойств связи сайтов

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Межсайтовая репликация выполняется в соответствии со свойствами объектов подключения. Когда средство проверки согласованности знаний создает объекты подключения, оно получает расписание репликации из свойств объектов связи сайтов. Каждый объект связи сайтов представляет собой подключение к глобальной сети (WAN) между двумя или более сайтами.  
  
Настройка свойств объекта связи сайтов включает следующие шаги.  
  
-   Определение затрат, связанных с этим путем репликации. В KCC используются затраты для определения наименее дорогостоящего маршрута для репликации между двумя сайтами, которые реплицируют один и тот же раздел каталога.  
  
-   Определение расписания, определяющего время, в течение которого может выполняться межсайтовая репликация.  
  
-   Определение интервала репликации, который определяет, как часто должна происходить репликация в период, когда разрешена репликация, как определено в расписании.  
  
## <a name="in-this-guide"></a>В данном руководстве  
  
-   [Определение стоимости](../../ad-ds/plan/Determining-the-Cost.md)  
  
-   [Определение расписания](../../ad-ds/plan/Determining-the-Schedule.md)  
  
-   [Определение интервала](../../ad-ds/plan/Determining-the-Interval.md)  
  


