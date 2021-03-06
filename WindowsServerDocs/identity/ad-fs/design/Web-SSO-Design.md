---
ms.assetid: eb778f63-f7be-438e-8c5e-1fd9b194b967
title: Проект единого входа через Интернет
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: d7f52cd36588a1e5de4536a760c38c147dd1e003
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71407835"
---
# <a name="web-sso-design"></a>Проект единого входа через Интернет

В\-\(единого\) входа на веб-сайте в режиме службы федерации Active Directory (AD FS) \(AD FS\)необходимо выполнить проверку подлинности только один раз, чтобы получить доступ к нескольким AD FS защищенным приложениям или службам\-.\- В этом проекте все пользователи являются внешними, и федеративное доверие отсутствует, так как нет партнерских организаций. Как правило, этот проект развертывается, если требуется предоставить индивидуальный потребитель или клиентский доступ к одной или нескольким AD FS защищенным службам или приложениям через Интернет, как показано на следующем рисунке.  
  
![Разработка единого входа в Интернете](media/adfs2_WebSSODesign.gif)  
  
При проектировании единого входа в Интернете организация, которая обычно размещает AD FS\-защищенное приложение или службу в сети периметра, может поддерживать отдельное хранилище учетных записей клиентов в сети периметра, что упрощает изоляцию учетных записей клиентов от учетных записей сотрудников.  
  
Управлять локальными учетными записями для клиентов в сети периметра можно с помощью служб домен Active Directory Services \(AD DS\), SQL Server или пользовательского хранилища атрибутов.  
  
Такая структура совпадает с целью развертывания в [Provide Your Active Directory Users Access to Your Claims-Aware Applications and Services](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md).  
  
Список подробных задач, которые можно использовать для планирования и развертывания проекта единого входа через Интернет, см. в разделе [Checklist: Implementing a Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Web-SSO-Design.md).  
  
## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
