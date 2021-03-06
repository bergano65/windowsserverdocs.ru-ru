---
ms.assetid: 503733f8-be0c-429c-81f0-cd4205e8b118
title: Контрольный список — создание правил утверждений для отношения доверия поставщика утверждений
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: fb1e0dba5921a2f49452cab5cb622aed3e7eb57d
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359961"
---
# <a name="checklist-creating-claim-rules-for-a-claims-provider-trust"></a>Контрольный список: создание правил утверждений для отношений доверия с поставщиком утверждений


Этот контрольный список содержит задачи по планированию, проектированию и развертыванию правил утверждений, связанных с отношением доверия поставщика утверждений в службы федерации Active Directory (AD FS) \(AD FS\).  
  
> [!NOTE]  
> Выполните по порядку задачи в контрольном списке. После выполнения всех шагов процедуры, на которую указывает ссылка, следует вернуться к этому разделу и продолжить выполнение оставшихся задач контрольного списка.  
  
![создание](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**контрольного списка правил утверждений: создание набора правил утверждений для отношения доверия поставщика утверждений**  
  
||Задача|Справочные материалы|  
|-|--------|-------------|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|Ознакомьтесь с основными понятиями о заявках, правилах утверждений, наборах правил заявок и шаблонах правил утверждений, а также о том, как они связаны с федеративным доверием.|![создание правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль утверждений](../../ad-fs/technical-reference/The-Role-of-Claims.md)<br /><br />![создании правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль правил утверждений](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|Ознакомьтесь с основными понятиями о том, как утверждение проходит через все этапы конвейера выдачи утверждений и как правила обрабатываются подсистемой выдачи утверждений.|![создании правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль конвейера утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claims-Pipeline.md)<br /><br />![создании правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль обработчика утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claims-Engine.md)|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|Чтобы эффективно спланировать и реализовать выходные утверждения, которые будут выдаваться через это отношение доверия поставщика утверждений, определите, требуются ли одно или несколько правил утверждений и какие правила утверждений следует использовать с этим отношением доверия поставщиков утверждений.|![создании правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определяет тип используемого шаблона правила утверждений](../../ad-fs/technical-reference/Determine-the-Type-of-Claim-Rule-Template-to-Use.md)|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|Ознакомьтесь с основными понятиями о том, когда следует создать одно правило утверждения на основе другого и как можно использовать язык правил утверждений, чтобы предоставить более сложную логику, чем стандартные правила, чтобы предоставить желаемый результат в идеальном наборе исходящих заявок.|![создании правил утверждений,](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует использовать правило прохождения или фильтрации утверждений](../../ad-fs/technical-reference/When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)<br /><br />![создания правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[при использовании правила утверждения преобразования](../../ad-fs/technical-reference/When-to-Use-a-Transform-Claim-Rule.md)<br /><br />![создании правил утверждений,](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда необходимо использовать атрибуты отправки АТРИБУТОВ LDAP в качестве утверждений](../../ad-fs/technical-reference/When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)<br /><br />![создании правил утверждений,](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[когда следует использовать членство в группе отправки в качестве правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)<br /><br />![создания правил утверждений](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[при использовании настраиваемого правила утверждения](../../ad-fs/technical-reference/When-to-Use-a-Custom-Claim-Rule.md)<br /><br />![создании правил утверждений.](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[роль языка правил утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md)|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|Описание утверждения должно быть создано, если оно еще не существует, которое будет удовлетворять потребности вашей организации. AD FS поставляется с набором описаний утверждений по умолчанию, которые доступны в\-оснастки управления AD FS в.|![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Добавление описания утверждения](../../ad-fs/operations/Add-a-Claim-Description.md)|  
|![Создание правил утверждений](media/icon_checkboxo.gif)|В зависимости от потребностей организации создайте одно или несколько правил утверждений для набора правил преобразования принятия, связанного с этим отношением доверия поставщика утверждений, чтобы утверждения были выданы соответствующим образом.|![создании правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для передачи или фильтрации входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки АТРИБУТОВ LDAP в качестве утверждений](../../ad-fs/operations/Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки членства в группе в качестве утверждения](../../ad-fs/operations/Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для преобразования входящего утверждения](../../ad-fs/operations/Create-a-Rule-to-Transform-an-Incoming-Claim.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки утверждения метода проверки подлинности](../../ad-fs/operations/Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки утверждений AD FS 1. x](../../ad-fs/operations/Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)<br /><br />![создание правил утверждений](media/15dd35b6-6cc6-421f-93f8-7109920e7144.gif)[Создание правила для отправки утверждений с помощью настраиваемого правила](../../ad-fs/operations/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)|  
  

