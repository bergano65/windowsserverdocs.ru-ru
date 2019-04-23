---
ms.assetid: d590c90e-9adf-4305-b226-eb2a5743337b
title: Общее представление о схеме доменных служб Active Directory
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/07/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: c94f6ddd19e3178243545b0cc71f6f4c7bb4dbec
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828795"
---
# <a name="understanding-ad-ds-design"></a>Общее представление о схеме доменных служб Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Организации могут использовать доменных служб Active Directory (AD DS) в Windows Server, чтобы упростить управление пользователями и ресурсами при создании масштабируемой, безопасной и управляемой инфраструктуры. AD DS можно использовать для управления сетевой инфраструктурой, включая филиала, Microsoft Exchange Server и нескольких сред лесов.  
  
Это проект развертывания AD DS включает три этапа: этап проектирования, этап развертывания и этап эксплуатации. На этапе проектирования проектная группа создает схему логической структуры AD DS, который лучше всего соответствует потребностям каждого структурного подразделения организации, которая будет использовать служба каталогов. После утверждения проекта Группа развертывания тестирование этого проекта в лабораторных условиях и затем внедряет проект в производственной среде. Так как тестирование выполняется группой развертывания и влиять на этапе проектирования, оно является промежуточной действием, постарайтесь проектирования и развертывания. После завершения развертывания группа эксплуатации отвечает за обслуживание этой службы каталогов.  
  
Несмотря на то, что стратегии проектирования и развертывания Windows Server AD DS, которые представлены в этом руководстве основаны на лабораторных и тестирования экспериментальных и успешной реализации в средах клиентов, может потребоваться настроить дизайна AD DS и развертывание для лучшего соответствия средах.
  
- Дополнительные сведения о развертывании AD DS в среде филиалов компании см. в разделе [контроллера домена только для чтения (RODC) Branch Office Planning Guide](https://go.microsoft.com/fwlink/?LinkId=100207).  
- Дополнительные сведения о развертывании AD DS в среде Exchange см. в статье [Exchange 2007 — Планирование Active Directory](https://go.microsoft.com/fwlink/?LinkId=88904).  
- Дополнительные сведения о развертывании AD DS в среде с несколькими лесами см. в статье [Multiple Forest Considerations в Windows 2000 и Windows Server 2003](https://go.microsoft.com/fwlink/?LinkId=88905).  