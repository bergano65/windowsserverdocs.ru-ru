---
ms.assetid: 8890ccc9-068d-4da2-bd51-8a2964173ff1
title: Ферма серверов федерации с использованием WID и прокси-серверов
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 4bd815daccdd72a8c612b9b728ce12378c1926e7
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59817625"
---
# <a name="federation-server-farm-using-wid-and-proxies"></a>Ферма серверов федерации с использованием WID и прокси-серверов

>Область применения. Windows Server 2012

Данная топология развертывания для служб федерации Active Directory \(AD FS\) идентичен фермы серверов федерации с внутренней базой данных Windows \(WID\) топологии, однако он добавляет прокси-серверов федерации к сети периметра для поддержки внешних пользователей. Прокси-серверов федерации перенаправления запросов проверки подлинности клиента, поступающие от за пределами корпоративной сети к ферме серверов федерации.  
  
## <a name="deployment-considerations"></a>Вопросы развертывания  
В этом разделе описываются различные вопросы о целевая аудитория, преимущества и ограничения, связанные с этой топологии развертывания.  
  
### <a name="who-should-use-this-topology"></a>Для кого предназначена эта топология?  
  
-   Организации с 100 или меньше настроенного доверительных отношений, которым требуется предоставить как внутренних пользователей, так и внешним пользователям \(, вошедшим в систему компьютерах, которые физически находятся за пределами корпоративной сети\) с одним знак\-на \(SSO\) доступ к федеративным приложениям или службам  
  
-   Организаций, которым требуется предоставить как внутренних пользователей, так и внешним пользователям доступ с единым ВХОДОМ в Microsoft Office 365  
  
-   Небольших организаций с внешними пользователями и доставляет избыточное и масштабируемых служб  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>Каковы преимущества использования этой топологии?  
  
-   Же преимущества, как указано для [федерации сервера фермы с использованием WID](Federation-Server-Farm-Using-WID-2012.md) топологии, а также обеспечивает доступ к дополнительным возможностям для внешних пользователей  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>Что такое ограничение на использование этой топологии  
  
-   Те же ограничения, что для перечисленных [федерации сервера фермы с использованием WID](Federation-Server-Farm-Using-WID-2012.md) топологии  
  
## <a name="server-placement-and-network-layout-recommendations"></a>Рекомендации макета для размещения и сети сервера  
Для развертывания этой топологии, помимо добавления двух прокси серверов федерации, необходимо убедиться, что сети периметра, может предоставить доступ для доменных имен \(DNS\) сервера и для второй балансировкой сетевой нагрузки \(Балансировки сетевой Нагрузки\) узла. Второй узел балансировки сетевой Нагрузки должны быть настроены как кластер балансировки сетевой Нагрузки, использующий Интернета\-IP-адрес кластера доступны и его необходимо использовать тот же параметр именем DNS кластера предыдущего кластера балансировки сетевой Нагрузки, настроенного в корпоративной сети \( FS.Fabrikam.com\). Прокси-серверов федерации также должны быть настроены с Интернетом\-доступный IP-адресов.  
  
На следующем рисунке показан существующую ферму серверов федерации с топологией WID, как было описано ранее, и как вымышленной компании Fabrikam, Inc., обеспечивает доступ к серверу DNS периметра, добавляет второй узел балансировки сетевой Нагрузки с тем же именем DNS кластера \(fs.fabrikam.com\), и добавляет два прокси-сервера федерации \(fsp1 и fsp2\) к сети периметра.  
  
![Ферма серверов с использованием WID](media/FarmWIDProxies.gif)  
  
Дополнительные сведения о том, как настроить сетевую среду для использования с серверами федерации и прокси-сервера федерации см. в статье [требования к разрешению имен для серверов федерации](Name-Resolution-Requirements-for-Federation-Servers.md) или [имя Требования к разрешению для прокси-серверов федерации](Name-Resolution-Requirements-for-Federation-Server-Proxies.md).  
  
## <a name="see-also"></a>См. также
[Руководство по разработке AD FS в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)