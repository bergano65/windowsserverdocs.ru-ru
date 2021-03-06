---
ms.assetid: e2651dc8-4b31-4cd8-a400-3b8123890210
title: Рекомендации по защите Active Directory
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 0d6f4abbf5dd071a2e229acbda2057c1f81851e6
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408628"
---
# <a name="best-practices-for-securing-active-directory"></a>Рекомендации по защите Active Directory

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Этот документ содержит ряд практических методик, помогающих ИТ-специалистам защитить корпоративную Active Directoryную среду. Active Directory играет важную роль в ИТ-инфраструктуре и позволяет обеспечить согласованную и безопасную работу с сетевыми ресурсами в глобализированной и взаимосвязанной среде. Обсуждаемые методы основываются на опытах Организации в сфере информационной безопасности и управления рисками (ИСРМ), которые могут быть защищены для защиты активов ИТ-отделов корпорации Майкрософт и других подразделений корпорации Майкрософт, а также для получения выбранное число клиентов Microsoft Global 500.  
  
-   [Краткий обзор](../../../ad-ds/manage/component-updates/Executive-Summary.md)  
  
-   [Введение](../../../ad-ds/manage/component-updates/Introduction.md)  
  
-   [Способы решения проблем](../../../ad-ds/plan/security-best-practices/Avenues-to-Compromise.md)  
  
-   [Учетные записи, подверженные риску кражи учетных данных](../../../ad-ds/plan/security-best-practices/Attractive-Accounts-for-Credential-Theft.md)  
  
-   [Сокращение Active Directory уязвимой зоны](../../../ad-ds/plan/security-best-practices/Reducing-the-Active-Directory-Attack-Surface.md)  
  
-   [Реализация административных моделей с минимальными правами доступа](../../../ad-ds/plan/security-best-practices/Implementing-Least-Privilege-Administrative-Models.md)  
  
-   [Внедрение узлов безопасного администрирования узлов](../../../ad-ds/plan/security-best-practices/Implementing-Secure-Administrative-Hosts.md)  
  
-   [Защита контроллеров домена от атак](../../../ad-ds/plan/security-best-practices/Securing-Domain-Controllers-Against-Attack.md)  
  
-   [Мониторинг Active Directory для подписывания компромисса](../../../ad-ds/plan/security-best-practices/Monitoring-Active-Directory-for-Signs-of-Compromise.md)  
  
-   [Рекомендации по политике аудита](../../../ad-ds/plan/security-best-practices/Audit-Policy-Recommendations.md)  
  
-   [Планирование компрометации](../../../ad-ds/plan/security-best-practices/Planning-for-Compromise.md)  
  
-   [Поддержка более безопасной среды](../../../ad-ds/plan/security-best-practices/Maintaining-a-More-Secure-Environment.md)  
  
-   [Приложения](../../../ad-ds/plan/security-best-practices/Appendices.md)  
   
-   [Приложение Б. Привилегированные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-B--Privileged-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение В. Защищенные учетные записи и группы в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-C--Protected-Accounts-and-Groups-in-Active-Directory.md)  
  
-   [Приложение Г. Защита встроенных учетных записей администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-D--Securing-Built-In-Administrator-Accounts-in-Active-Directory.md)  
  
-   [Приложение Д. Защита групп корпоративных администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-E--Securing-Enterprise-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение Е. Защита групп администраторов домена в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-F--Securing-Domain-Admins-Groups-in-Active-Directory.md)  
  
-   [Приложение Ж. Защита групп администраторов в Active Directory](../../../ad-ds/plan/security-best-practices/Appendix-G--Securing-Administrators-Groups-in-Active-Directory.md)  
  
-   [Приложение З. Защита учетных записей и групп локальных администраторов](../../../ad-ds/plan/security-best-practices/Appendix-H--Securing-Local-Administrator-Accounts-and-Groups.md)  
  
-   [Приложение И. Создание учетных записей управления для защищенных учетных записей и групп в Active Directory](../../../ad-ds/manage/component-updates/Appendix-I--Creating-Management-Accounts-for-Protected-Accounts-and-Groups-in-Active-Directory.md)   
  
-   [Приложение М. События для мониторинга](../../../ad-ds/plan/Appendix-L--Events-to-Monitor.md)  
  
-   [Приложение Н. Ссылки на документы и рекомендуемая литература](../../../ad-ds/manage/Appendix-M--Document-Links-and-Recommended-Reading.md)  
  


