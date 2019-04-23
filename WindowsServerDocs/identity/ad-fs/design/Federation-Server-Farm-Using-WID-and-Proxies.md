---
ms.assetid: f0464182-56a2-4bfa-a8c8-7e39c1bd62d3
title: Ферма серверов федерации с использованием WID и прокси-серверов
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: e372f066fc82b9857d438234b491732a177e24fa
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59860395"
---
# <a name="federation-server-farm-using-wid-and-proxies"></a>Ферма серверов федерации с использованием WID и прокси-серверов

>Область применения. Windows Server 2016, Windows Server 2012 R2

Данная топология развертывания для служб федерации Active Directory \(AD FS\) идентичен фермы серверов федерации с внутренней базой данных Windows \(WID\) топологии, однако он добавляет компьютеры прокси-сервера для сети периметра для поддержки внешних пользователей. Эти прокси-серверы перенаправления запросов проверки подлинности клиента, поступающие от за пределами корпоративной сети к ферме серверов федерации. В предыдущих версиях служб AD FS они должны были вызваны прокси-серверов федерации.  
  
> [!IMPORTANT]  
> В службах федерации Active Directory \(AD FS\) в Windows Server 2012 R2 роль прокси-сервера федерации выполняет, новая служба роли удаленного доступа, которая называется прокси веб-приложения. Чтобы разрешить доступ к AD FS доступ из-за пределами корпоративной сети, что является целью развертывания прокси-сервера федерации в прежних версиях AD FS, например AD FS 2.0 и AD FS в Windows Server 2012, можно развернуть один или несколько прокси веб-приложений для A D FS в Windows Server 2012 R2.  
>   
> В контексте AD FS прокси веб-приложения выступает в качестве прокси-сервера федерации AD FS. Кроме того, прокси-сервер веб-приложения предоставляет функции обратного прокси-сервера для веб-приложений в корпоративной сети, что делает их доступными для пользователей с любых устройств из-за пределов корпоративной сети. Дополнительные сведения о службе роли прокси веб-приложения см. в разделе "Обзор прокси-сервера веб-приложения".  
>   
> При планировании развертывания прокси-сервера веб-приложения можно использовать сведения из следующих разделов.  
>   
> -   [Планирование инфраструктуры прокси-сервера веб-приложений (WAP)](https://technet.microsoft.com/library/dn383648.aspx)  
> -   [Планирование сервера прокси-сервера веб-приложений](https://technet.microsoft.com/library/dn383647.aspx)  
  
## <a name="deployment-considerations"></a>Вопросы развертывания  
В этом разделе описываются различные вопросы о целевая аудитория, преимущества и ограничения, связанные с этой топологии развертывания.  
  
### <a name="who-should-use-this-topology"></a>Для кого предназначена эта топология?  
  
-   Организации с 100 или меньше настроенного доверительных отношений, которым требуется предоставить как внутренних пользователей, так и внешним пользователям \(, вошедшим в систему компьютерах, которые физически находятся за пределами корпоративной сети\) с одним знак\-на \(SSO\) доступ к федеративным приложениям или службам  
  
-   Организаций, которым требуется предоставить как внутренних пользователей, так и внешним пользователям доступ с единым ВХОДОМ в Microsoft Office 365  
  
-   Небольших организаций с внешними пользователями и доставляет избыточное и масштабируемых служб  
  
### <a name="what-are-the-benefits-of-using-this-topology"></a>Каковы преимущества использования этой топологии?  
  
-   Же преимущества, как указано для [федерации сервера фермы с использованием WID](Federation-Server-Farm-Using-WID.md) топологии, а также обеспечивает доступ к дополнительным возможностям для внешних пользователей  
  
### <a name="what-are-the-limitations-of-using-this-topology"></a>Что такое ограничение на использование этой топологии  
  
-   Те же ограничения, что для перечисленных [федерации сервера фермы с использованием WID](Federation-Server-Farm-Using-WID.md) топологии  

||1 \- 100 отношениями доверия RP|Более чем 100 отношениями доверия RP 
| ----- |-----| ------ |
|1 \- узлов 30 AD FS|Поддерживается внутренней базы данных Windows|Не поддерживается с использованием WID \- SQL требуется 
|Узлы более чем 30 AD FS|Не поддерживается с использованием WID \- SQL требуется|Не поддерживается с использованием WID \- SQL требуется  
  
## <a name="server-placement-and-network-layout-recommendations"></a>Рекомендации макета для размещения и сети сервера  
Для развертывания этой топологии, помимо добавления двух прокси веб-приложения, необходимо убедиться, что сети периметра, может предоставить доступ для доменных имен \(DNS\) сервера и для второй балансировкой сетевой нагрузки \( NLB\) узла. Второй узел балансировки сетевой Нагрузки должны быть настроены как кластер балансировки сетевой Нагрузки, использующий Интернета\-IP-адрес кластера доступны и его необходимо использовать тот же параметр именем DNS кластера предыдущего кластера балансировки сетевой Нагрузки, настроенного в корпоративной сети \( FS.Fabrikam.com\). Прокси веб-приложения также должны быть настроены с Интернетом\-доступный IP-адресов.  
  
На следующем рисунке показан существующую ферму серверов федерации с топологией WID, как было описано ранее, и как вымышленной компании Fabrikam, Inc., обеспечивает доступ к серверу DNS периметра, добавляет второй узел балансировки сетевой Нагрузки с тем же именем DNS кластера \(fs.fabrikam.com\)и добавляет два веб-прокси приложений \(wap1 и wap2\) к сети периметра.  
  
![Фермы WID и прокси-серверы](media/WIDFarmADFSBlue.gif)  
  
Дополнительные сведения о том, как настроить сетевую среду для использования с серверами федерации и прокси веб-приложений см. в разделе «Требования к разрешению имен» статьи [требований AD FS](AD-FS-Requirements.md) и [плана веб-узла Инфраструктуры прокси-сервера приложения (WAP)](https://technet.microsoft.com/library/dn383648.aspx).  
  
## <a name="see-also"></a>См. также  
[Планирование топологии развертывания AD FS](Plan-Your-AD-FS-Deployment-Topology.md)  
[Руководство по разработке AD FS в Windows Server 2012 R2](AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)  
  
