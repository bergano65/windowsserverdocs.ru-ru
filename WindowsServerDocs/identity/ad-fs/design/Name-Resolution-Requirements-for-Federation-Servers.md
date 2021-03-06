---
ms.assetid: 74ef34c8-e13f-499b-b2bb-952ad7036622
title: Требования к разрешению имен для серверов федерации
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 88ec418bd72a6389856deb1abd85641d8782bc30
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408047"
---
# <a name="name-resolution-requirements-for-federation-servers"></a>Требования к разрешению имен для серверов федерации

Когда клиентские компьютеры в корпоративной сети пытаются получить доступ к приложению или веб-службе, защищенной службы федерации Active Directory (AD FS) \(AD FS\), они должны сначала пройти проверку подлинности на сервере федерации. Одним из способов проверки подлинности является наличие у клиентов корпоративной сети доступа к локальному серверу федерации через встроенную проверку подлинности Windows.  
  
## <a name="configure-corporate-dns"></a>Настройка корпоративной DNS  
Чтобы успешно разрешить полное разрешение имен через встроенную проверку подлинности Windows на локальных серверах федерации, система доменных имен \(DNS-\) в корпоративной сети партнера по учетным записям должна быть настроена для нового узла \(\)ной записи ресурса, которая будет разрешать полные доменные имена \(имя узла сервера федерации с IP-адресом кластера Федерации.\)  
  
На следующем рисунке показано, как эта задача выполняется для данного сценария. В этом сценарии балансировка сетевой нагрузки (Майкрософт) \(NLB\) предоставляет одно полное доменное имя кластера и один IP-адрес кластера для существующей фермы серверов федерации.  
  
![требования к имени](media/adfs2_deploy_single_fs.gif)  
  
Сведения о том, как настроить IP-адрес кластера или полное доменное имя кластера с помощью балансировки сетевой нагрузки, см. [в разделе Указание параметров кластера](https://go.microsoft.com/fwlink/?LinkId=75282).  
  
Сведения о настройке корпоративного DNS для сервера федерации см. в разделе [Добавление записи ресурса узла &#40;a&#41; в корпоративную службу DNS для сервера федерации](../../ad-fs/deployment/Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md).  
  
Сведения о настройке прокси-серверов федерации в сети периметра см. в разделе [требования к разрешению имен для прокси-серверов федерации](Name-Resolution-Requirements-for-Federation-Server-Proxies.md).  
  

## <a name="see-also"></a>См. также
[Руководство по разработке служб федерации Active Directory в Windows Server 2012](AD-FS-Design-Guide-in-Windows-Server-2012.md)
