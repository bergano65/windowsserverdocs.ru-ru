---
ms.assetid: ce3be131-06ad-41dc-a26b-1168fa68c8ed
title: "Сопоставление требований и стратегии развертывания AD DS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: b4f625f06fede5b9dc751282cda19b68d7f9e535
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="mapping-your-requirements-to-an-ad-ds-deployment-strategy"></a>Сопоставление требований и стратегии развертывания AD DS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

После завершения проверки и определение проектирования доменных служб Active Directory (AD DS) и требования для развертывания и определив, какие из них относятся к конкретное развертывание, вы можете сопоставить эти требования определенных стратегии развертывания Доменных служб Active.  
  
Используйте следующую таблицу, чтобы определить, какая из стратегий развертывания AD DS сопоставляется с соответствующей комбинацией AD DS проектирования и развертывания потребностей вашей организации. («Да» означает, что конкретные требования для стратегии развертывания; «Нет» означает, что конкретные требования, не является обязательным для стратегии развертывания.)  
  
Эта таблица ссылается только три основные стратегии развертывания AD DS как описано в этом руководстве:  
  
-   [Развертывание AD DS в новой организации](../../ad-ds/plan/Deploying-AD-DS-in-a-New-Organization.md)  
  
-   [Развертывание AD DS в организации Windows Server 2003](../../ad-ds/plan/Deploying-AD-DS-in-a-Windows-Server-2003-Organization.md)  
  
-   [Развертывание AD DS в организации Windows 2000](../../ad-ds/plan/Deploying-AD-DS-in-a-Windows-2000-Organization.md)  
  
Тем не менее можно создать гибридный или пользовательские стратегии развертывания Доменных службах Active Directory, используя любую комбинацию требования к разработке и развертыванию AD DS в соответствии с потребностями вашей организации.  
  
|Требования к разработке и развертыванию доменных служб Active Directory AD|Развертывание AD DS в новой организации|Развертывание AD DS в организации Windows Server 2003|Развертывание AD DS в организации Windows 2000|  
|--------------------------------------------|-----------------------------------------|---------------------------------------------------------|--------------------------------------------------|  
|[Проектирование логической структуры для Windows Server 2008, AD DS](https://technet.microsoft.com/library/cc770806.aspx)|Да|Да|Да|  
|[Проектирование топологии сайта для Windows Server 2008, AD DS](Designing-the-Site-Topology.md)|Да|Да|Да|  
|Планирование мощности контроллеров доменов|Да|Да|Да|  
|[Развертывание корневого домена леса Windows Server 2008](https://technet.microsoft.com/library/cc731174.aspx)|Да|Нет|Нет|  
|[Развертывание региональных доменов Windows Server 2008](https://technet.microsoft.com/library/cc755118.aspx)|Да|Да|Да|  
|[Включение дополнительных возможностей для службы AD DS](../../ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md)|Да|Да, но все контроллеры домена в среде необходимо выполнить Windows Server 2008 установите режим работы домена или леса до Windows Server 2008.|Да, но все контроллеры домена в среде необходимо выполнить Windows Server 2008 установите режим работы домена или леса до Windows Server 2008.|  
|[Обновление доменов Active Directory для Windows Server 2008 и Windows Server 2008 R2 AD DS доменов](https://technet.microsoft.com/library/cc731188.aspx)|Нет|Да|Да|  
|[Реструктуризация доменов AD DS между лесами](https://go.microsoft.com/fwlink/?LinkId=93678)|Да, если вы хотите перенести пилотных домена в вашу производственную среду, объединить с другой организацией и объединить две ИТ-инфраструктуры сведения или объединить домены ресурсов и учетной записи, вы выполнили обновление на месте с Windows 2000 или Windows Server 2003 средах.|Да, если требуется объединить с другой организацией и объединить две ИТ-инфраструктуры или объединить домены ресурсов и учетной записи, вы выполнили обновление на месте с Windows 2000 или Windows Server 2003 средах.|Да, если требуется объединить с другой организацией и объединить две ИТ-инфраструктуры или объединить домены ресурсов и учетной записи, вы выполнили обновление на месте с Windows 2000 или Windows Server 2003 средах.|  
|[Реструктуризация доменов AD DS в лесах](https://go.microsoft.com/fwlink/?LinkId=82740))|Нет|Да, если требуется уменьшить количество доменов, снизить трафик репликации и объем необходимого пользователя и группы администрирования или упрощения администрирования групповой политики.|Да, если требуется уменьшить количество доменов, снизить трафик репликации и объем необходимого пользователя и группы администрирования или упрощения администрирования групповой политики.|  
  

