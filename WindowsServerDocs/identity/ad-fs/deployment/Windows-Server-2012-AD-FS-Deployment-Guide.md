---
ms.assetid: e2ad9e80-a036-4bac-a4fb-afa83756aa1f
title: "Руководство по развертыванию Windows Server 2012 AD FS"
description: 
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 3e555d1003878e12320cb8557bd205ac24e1bbb3
ms.sourcegitcommit: 70c1b6cedad55b9c7d2068c9aa4891c6c533ee4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2017
---
# <a name="windows-server-2012-ad-fs-deployment-guide"></a>Руководство по развертыванию Windows Server 2012 AD FS

>Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Чтобы создать решение для управления федеративными удостоверениями, которое расширяет службы распределенной идентификации, проверки подлинности и авторизации службы веб-приложениям за границы организации и платформы, можно использовать \(AD FS\) служб федерации Active Directory® с операционной системой Windows Server® 2012. При развертывании Служб федерации Active Directory, можно расширить существующие возможности управления удостоверениями вашей организации к Интернету.  
  
Можно развернуть службы федерации Active Directory:  
  
-   Предоставлять сотрудникам или клиентам возможности \(SSO\) веб-, выполняющей одну входа на для получения удаленного доступа к внутренним веб-сайты и службы.  
  
-   Предоставлять сотрудникам или клиентам с веб-службы Единого входа при доступе к организации cross\ веб-сайты или службам через брандмауэры сети.  
  
-   Предоставлять сотрудникам или клиентам легкий доступ к веб-ресурсам в любой партнерской организации федерации через Интернет не требуя сотрудникам или клиентам более повторного входа в систему.  
  
-   Сохранять полный контроль над удостоверениями сотрудников или клиентов без использования других поставщиков входа на \ (идентификатора Windows Live ID, Liberty Alliance и others\).  
  
## <a name="about-this-guide"></a>Об этом руководстве  
Это руководство предназначено для использования системными администраторами и системных инженеров. Он предоставляет подробные инструкции по развертыванию дизайна AD FS, который был предварительно выбран вами либо инфраструктуре специалиста или системным архитектором в вашей организации.  
  
Если проект еще не выбран, мы рекомендуем отложить выполнение инструкций в этом руководстве до ознакомившись с вариантами проектов в [AD FS Design Guide in Windows Server 2012](https://technet.microsoft.com/library/dd807036.aspx) и выбран наиболее подходящий для вашей организации. Дополнительные сведения об использовании этого руководства с уже выбранным проектом см. в разделе [реализация AD FS плана разработки](Implementing-Your-AD-FS-Design-Plan.md).  
  
После проекта с помощью руководства по проектированию и Собрав необходимую информацию об утверждениях, типах токенов, хранилищах атрибутов и других элементов, можно использовать это руководство по развертыванию AD FS топологии в рабочей среде. В этом руководстве приводятся инструкции по развертыванию одно из основных способов AD FS:  
  
-   Веб-служба SSO  
  
-   Федеративные веб-служба SSO  
  
Используйте контрольные списки в [реализация AD FS плана разработки](Implementing-Your-AD-FS-Design-Plan.md), чтобы определить, как эффективнее использовать инструкции в этом руководстве по развертыванию конкретной топологии. Сведения о требованиях к оборудованию и программному обеспечению для развертывания служб AD FS см. в разделе [приложение а. Общие сведения об AD FS требования](https://technet.microsoft.com/library/ff678034.aspx) в руководстве по проектированию AD FS.  
  
### <a name="what-this-guide-does-not-provide"></a>Что это руководство не содержит  
В этом руководстве не содержатся.  
  
-   Указаний касательно время и место для размещения серверов федерации, прокси-серверов федерации или веб-серверы в существующей сетевой инфраструктуре. Подробнее см. в разделе [планирование размещения сервера федерации](https://technet.microsoft.com/library/dd807069.aspx) и [планирование размещения прокси-сервера федерации](https://technet.microsoft.com/library/dd807130.aspx) в руководстве по проектированию AD FS.  
  
-   Руководство по использованию \(CAs\) центров сертификации для настройки Служб федерации Active Directory  
  
-   Инструкции по установке или настройке конкретных веб-приложений  
  
-   Настройка инструкций по настройке тестовой лабораторной среде.  
  
-   Сведения о настройке экранов федеративного входа, файлов web.config и базы данных конфигурации.  
  
## <a name="in-this-guide"></a>В этом руководстве  
  
-   [Планирование развертывания AD FS](Planning-to-Deploy-AD-FS.md)  
  
-   [Реализация плана проектирования вашего AD FS](Implementing-Your-AD-FS-Design-Plan.md)  
  
-   [Контрольный список: Реализация Web SSO Design](Checklist--Implementing-a-Web-SSO-Design.md)  
  
-   [Контрольный список: Реализация проекта единого входа Интернет-решений](Checklist--Implementing-a-Federated-Web-SSO-Design.md)  
  
-   [Настройка партнерских организаций](Configuring-Partner-Organizations.md)  
  
-   [Настройка правил утверждений](Configuring-Claim-Rules.md)  
  
-   [Развертывание серверов федерации](Deploying-Federation-Servers.md)  
  
-   [Развертывание прокси-сервера федерации](Deploying-Federation-Server-Proxies.md)  
  
-   [Взаимодействие с AD FS 1.x](Interoperating-with-AD-FS-1.x.md)  