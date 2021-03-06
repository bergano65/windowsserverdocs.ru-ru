---
ms.assetid: 97999892-29c6-4076-be19-5e5259d8ada6
title: Развертывание серверов федерации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: f2aaca5ffc846c41af82c276750c564db38b5020
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359510"
---
# <a name="interoperating-with-ad-fs-1x"></a>Взаимодействие с AD FS 1.x

Для взаимодействия между службы федерации Active Directory (AD FS) \(AD FS\) в Windows Server® 2012 и AD FS 1. *x*, выполните одну или несколько из следующих задач в зависимости от потребностей Организации:  
  
-   Планируйте взаимодействие между AD FS в Windows Server 2012 и предыдущих версиях AD FS и Узнайте больше о типе утверждения идентификатора имени. Дополнительные сведения см. в разделе [Планирование взаимодействия с AD FS 1. x](https://technet.microsoft.com/library/ff678040.aspx).  
  
-   Если вы отправите утверждения от AD FS служба федерации в Windows Server 2012, которые могут использоваться AD FS 1. служба федерации *x* см. [в разделе Контрольный список: настройка AD FS для отправки утверждений в AD FS 1. x служба федерации](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Federation-Service.md).  
  
-   Если вы отправите утверждения от AD FS служба федерации в Windows Server 2012, которые могут использоваться приложением, размещенным на веб-сервере, на котором выполняется AD FS 1. *x* claims\-с поддержкой веб-агента. см. [Контрольный список: настройка AD FS для отправки утверждений в веб-агент, поддерживающий утверждения AD FS 1. x](Checklist--Configuring-AD-FS-to-Send-Claims-to-an-AD-FS-1.x-Claims-Aware-Web-Agent.md).  
  
-   Если вы будете отправлять утверждения из AD FS 1. *x* служба Федерации, которые будут использоваться AD FS Служба федерации в Windows Server 2012, см. в разделе [Контрольный список: настройка AD FS для использования утверждений от AD FS 1. x](Checklist--Configuring-AD-FS--to-Consume-Claims-from-AD-FS-1.x.md).  
  
## <a name="differences-between-federation-service-settings"></a>Различия между параметрами служба федерации  
Хотя большая часть AD FS 1. параметры *x* служба федерации работают аналогичным образом AD FS Служба федерации в параметрах Windows Server 2012 некоторые имена параметров изменились. В следующей таблице перечислены имена параметров для AD FS 1. *x* служба Федерации и их эквивалентные имена для AD FS Служба федерации в Windows Server 2012.  
  
|AD FS 1. x служба федерации параметр|Эквивалентный служба федерации AD FS в параметре Windows Server 2012  
|----------------------------------------|---------------------------------------------------------------------------------------------------------- 
|Партнер по учетным записям|Отношения доверия с поставщиком утверждений  
|Партнер по ресурсам|Отношения доверия с проверяющей стороной 
|Развертывание|Отношения доверия с проверяющей стороной  
|Свойства приложения|Свойства отношения доверия с проверяющей стороной  
|URL-адрес приложения|Идентификатор проверяющей стороны и URL-адрес пассивной конечной точки WS\-Federation  
|служба федерации URI|Идентификатор службы федерации  
|URL-адрес конечной точки служба федерации|URL-адрес пассивной конечной точки WS\-Federation  
  
## <a name="see-also"></a>См. также  
[Взаимодействие AD FS и AD FS 1. x](https://go.microsoft.com/fwlink/?LinkId=200776)  
  

