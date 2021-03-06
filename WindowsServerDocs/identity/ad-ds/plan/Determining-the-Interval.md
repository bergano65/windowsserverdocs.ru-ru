---
ms.assetid: 96a6749c-6c9f-4f2f-ad0a-51272d282ace
title: Определение интервала
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 065b4ff707bdd8b82e33e06ad2b52c57a746045f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71402630"
---
# <a name="determining-the-interval"></a>Определение интервала

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Необходимо задать свойство интервал репликации связи сайтов, чтобы указать, как часто должна происходить репликация в период, когда расписание разрешает репликацию. Например, если расписание допускает репликацию от 02:00 часов до 04:00 часов, а интервал репликации устанавливается в течение 30 минут, репликация может выполняться до четырех раз в запланированное время. Интервал репликации по умолчанию составляет 180 минут или 3 часа. Минимальный интервал составляет 15 минут.  
  
Примите во внимание следующие критерии, чтобы определить частоту выполнения репликации в окне расписания.  
  
-   Небольшой интервал сокращает задержку, но увеличивает объем трафика глобальной сети (WAN).  
  
-   Для обновления разделов каталога домена рекомендуется использовать низкую задержку.  
  
При использовании стратегии репликации с сохранением и переадресацией трудно определить, как долго может выполняться обновление каталога на каждом контроллере домена. Чтобы обеспечить консервативную оценку максимальной задержки, выполните следующие задачи.  
  
-   Создайте таблицу со всеми сайтами в сети, как показано в следующем примере:  
  
    |Сайты|Сиэтл|Бостон|Лос-Анджелес|Нью-Йорк|Вашингтон, округ Колумбия|  
    |---------|-----------|----------|---------------|------------|--------------------|  
    |Сиэтл|0,25|||||  
    |Бостон||0,25||||  
    |Лос-Анджелес|||0,25|||  
    |Нью-Йорк||||0,25||  
    |Вашингтон, округ Колумбия|||||0,25|  
  
    В худшем случае задержка в пределах сайта будет равна 15 минутам.  
  
-   В расписании репликации Определите максимальную задержку репликации, возможную для любой связи сайтов, соединяющей два концентратора.  
  
    Например, если репликация выполняется между Сиэтл и Нью-Йорк каждые три часа, максимальная задержка репликации между этими сайтами составляет три часа. Если задержка репликации между Нью-Йорком и Сиэтл является максимальной запланированной задержкой между всеми узлами концентраторов, максимальная задержка между всеми центрами составляет три часа.  
  
-   Для каждого узла концентратора создайте таблицу с максимальными задержками между сайтом концентратора и любыми его вспомогательными сайтами.  
  
    Например, если репликация выполняется между Нью-Йорком и Вашингтонм, округ Колумбия, каждые четыре часа и это самая длинная задержка репликации между Нью-Йорком и любыми вспомогательными сайтами, максимальная задержка между Нью-Йорком и ее спутниками составляет четыре часа.  
  
-   Объедините эти максимальные задержки, чтобы определить максимальную задержку для всей сети.  
  
    Например, если максимальная задержка между Сиэтлом и ее вспомогательным сайтом в Лос-Анджелес составляет один день, максимальная задержка репликации для этого набора ссылок (Вашингтон, округ Колумбия-Нью-Сиэтл – Лос-Анджелес) составляет 31 час, то есть 4 (штат Вашингтон, округ Колумбия-новый Москва) + 3 (новый York-Сиэтл) + 24 (Сиэтл — Лос-Анджелес), как показано в следующей таблице.  
  
    |Сайты|Сиэтл|Бостон|Лос-Анджелес|Нью-Йорк|Вашингтон, округ Колумбия|  
    |---------|-----------|----------|---------------|------------|--------------------|  
    |Сиэтл|0,25|4 + 3|24,00|3,00|4 + 3|  
    |Бостон||0,25|4 + 3 + 24|4,00|4,00|  
    |Лос-Анджелес|||0,25|24 + 3|24 + 3 + 4|  
    |Нью-Йорк||||0,25|4,00|  
    |Вашингтон, округ Колумбия|||||0,25|  
  


