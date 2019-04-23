---
ms.assetid: 44271f44-b50a-4bce-9375-4fcab9618048
title: Контрольный список — Создание правил для утверждений для проверяющей стороны доверия
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 9c75cd4ccbafefdda83cba4551fd6b9af63c4822
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817405"
---
# <a name="checklist-creating-claim-rules-for-a-relying-party-trust"></a>Контрольный список: Создание правил для утверждений для доверия проверяющей стороны

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот контрольный список содержит задачи, которые необходимы для планирования, разработки, и развертывание утверждений правила, которые связаны с доверия с проверяющей стороной в службах федерации Active Directory \(AD FS\).  
  
> [!NOTE]  
> Выполните по порядку задачи в контрольном списке. После выполнения всех шагов процедуры, на которую указывает ссылка, следует вернуться к этому разделу и продолжить выполнение оставшихся задач контрольного списка.  
  
![Создание правил утверждений](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольный список: Создание набора правил утверждений для отношения доверия с проверяющей стороной**  
  
||Задача|Ссылка|  
|-|--------|-------------|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Просмотрите основные понятия об утверждениях, правила утверждений, утверждения наборов правил и утверждений шаблонов правил и как они связаны с федеративного отношения доверия.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claims](../../ad-fs/technical-reference/The-Role-of-Claims.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of Claim Rules](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Основные понятия о том, как утверждение проходит через все этапы конвейера выдачи утверждений и как правила обрабатываются подсистемой выдачи утверждений.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Pipeline](../../ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[The Role of the Claims Engine](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Для эффективного планирования и реализации исходящие утверждения, которые будут выдаваться через это отношение доверия, определяют ли необходимы одно или несколько правил утверждений и также утверждение, правила, которые следует использовать с этим доверия с проверяющей стороной.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определить тип из утверждения шаблон правила для использования](../../ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Просмотрите основные понятия о создать одно утверждение правило на другое и об использовании языка правил утверждений для предоставления более сложная логика, чем стандартные правила для обеспечения желаемого результата в выходных данных идеально утверждение набора.|![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[использование Pass Through or Filter правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует использовать правила преобразования утверждения](../../ad-fs/technical-reference/When-to-Use-a-Transform-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования Send LDAP Attributes as Claims Rule](../../ad-fs/technical-reference/When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования Send Group Membership, как правило утверждения](../../ad-fs/technical-reference/When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует использовать правило авторизации утверждений](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[необходимости использования настраиваемого правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Custom-Claim-Rule.md)<br /><br />![Создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль языка правил утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|Описания утверждения должны создаваться, если еще не существует, будет соответствовать потребностям вашей организации. AD FS поставляется со стандартным набором описаний утверждений, которые отображаются в консоли управления AD FS\-в.|![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Добавление описания утверждения](../../ad-fs/operations/Add-a-Claim-Description.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|В зависимости от потребностей вашей организации создайте один или несколько правил для утверждений для наборов правил, которые связаны с этой доверия с проверяющей стороной, чтобы соответствующим образом будут выдаваться утверждений.|![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы пропуск или Фильтрация входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять атрибуты LDAP как утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять членство в группе как утверждение](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создайте правило для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки утверждений метода проверки подлинности](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки с AD FS 1.x, совместимый утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы отправлять утверждения с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)|  
|![Создание правил для утверждений](media/icon_checkboxo.gif)|В зависимости от потребностей вашей организации создайте один или несколько правил для утверждений для набора правил авторизации делегирования, связанный с этой доверия с проверяющей стороной, таким образом, пользователи могут доступ к проверяющей стороны или набор правил авторизации выдачи субъект.|![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы разрешить всем пользователям](../../ad-fs/operations/Create-a-Rule-to-Permit-All-Users.md)<br /><br />![Создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[создать правило, чтобы разрешать или запрещать пользователям основании входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)|  