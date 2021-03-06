---
ms.assetid: 6b49cde3-d2cb-4ece-b9b7-dc600e037495
title: Контрольный список — реализация федеративного единого входа в Интернете
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 165471fd06031a68343a54d019357afee782d082
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71359947"
---
# <a name="checklist-implementing-a-federated-web-sso-design"></a>Контрольный список: реализация проекта единого входа федерации для интернет-решений

Этот родительский контрольный список включает ссылки на\-ссылки на важные понятия федеративного веб-\-Sign\-on \(SSO\) проектировании службы федерации Active Directory (AD FS) \(AD FS.\) Кроме того, в списке присутствуют ссылки на вложенные контрольные списки, которые помогут выполнить действия, необходимые для внедрения разработки.  
  
> [!NOTE]  
> Выполните по порядку задачи в контрольном списке. В случае перехода по ссылке в раздел общих понятий или вложенный контрольный список вернитесь после просмотра раздела общих понятий или выполнения действий из вложенного контрольного списка, чтобы можно было перейти к остальным задачам этого контрольного списка.  
  
Контрольный список федеративного единого входа для веб-сайта ![](media/2b05dce3-938f-4168-9b8f-1f4398cbdb9b.gif)**. Реализация федеративной веб-разработки**  
  
||Задача|Справочные материалы|  
|-|--------|-------------|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Ознакомьтесь с важными понятиями о проекте федеративного единого входа в Интернете и определите, какие AD FS цели развертывания можно использовать для настройки этого проекта в соответствии с потребностями Организации.|](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Разработка федеративного единого входа](https://technet.microsoft.com/library/dd807050.aspx) в веб-службу единого входа ![федеративного веб-сайта<br /><br />![Федеративная веб-служба SSO,](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[определяющая цели развертывания AD FS](https://technet.microsoft.com/library/dd807053.aspx)<br /><br />![Федеративная веб-служба SSO](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Планирование развертывания](https://technet.microsoft.com/library/dd807083.aspx)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Ознакомьтесь с оборудованием, программным обеспечением, сертификатом, системой доменных имен \(\)DNS, хранилищем атрибутов и требованиями клиента для развертывания AD FS в вашей организации.|![Федеративная веб-](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[приложение SSO: Проверка требований AD FS](https://technet.microsoft.com/library/ff678034.aspx)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Прежде чем развертывать AD FS в обеих партнерских организациях, ознакомьтесь с важными понятиями о заявках, правилах утверждений, хранилищах атрибутов и базе данных конфигурации AD FS.|![Федеративная веб-служба SSO](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[понимание ключевых AD FS концепций](../../ad-fs/technical-reference/Understanding-Key-AD-FS-Concepts.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|В соответствии с планом проектирования установите один или несколько серверов федерации в каждой партнерской организации. **Примечание.** Для проектирования федеративного единого входа в Интернете требуется по крайней мере один сервер федерации в организации партнера по учетным записям и хотя бы один сервер федерации в организации партнера по ресурсам.|Контрольный список федеративного веб-единого входа ![](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[. Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|\(необязательно\) определить, требуется ли вашей организации прокси-сервер федерации. Если ваш план разработки вызывает прокси, можно установить один или несколько прокси-серверов федерации в каждой партнерской организации.|](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[Контрольный список федеративного единого входа в ![. Настройка прокси-сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Осуществите обмен сертификатами, настройте клиенты и отношения доверия в обеих партнерских организациях согласно плану разработки, чтобы организации могли обмениваться данными через доверие федерации.|Контрольный список федеративного веб-единого входа ![](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[. Настройка организации партнера по учетным записям](Checklist--Configuring-the-Account-Partner-Organization.md)<br /><br />Контрольный список федеративного веб-единого входа ![](media/bc6cea1a-1c6c-4124-8c8f-1df5adfe8c88.gif)[. Настройка организации партнера по ресурсам](Checklist--Configuring-the-Resource-Partner-Organization.md)|  
|![Федеративная веб-служба SSO](media/icon_checkboxo.gif)|Если вы являетесь администратором в организации партнера по ресурсам, утверждения\-включить приложение веб-браузера, приложение веб-службы или Microsoft® Office SharePoint® Server, используя WIF и пакет SDK для WIF.|![федеративный веб-единый вход](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation](https://go.microsoft.com/fwlink/?LinkId=122266)<br /><br />![федеративный веб-единый вход](media/faa393df-4856-4431-9eda-4f4e5be72a90.gif)[Windows Identity Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266)|  
