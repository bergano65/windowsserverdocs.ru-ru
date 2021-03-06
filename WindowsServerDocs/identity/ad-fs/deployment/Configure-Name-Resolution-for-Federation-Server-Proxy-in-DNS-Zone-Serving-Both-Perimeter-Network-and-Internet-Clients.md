---
ms.assetid: 1a6740e6-5b6d-41f8-9ec4-32cdbee3e1bb
title: Настройка разрешения имен для прокси-сервера федерации в зоне DNS, которая обслуживает как сеть периметра, так и интернет-клиенты
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 118c03ada32d3cd5b198ecd238078984a38df0db
ms.sourcegitcommit: 8fbd2d877612a9feb02d7d91ed0372d7cd441d5c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2019
ms.locfileid: "71359829"
---
# <a name="configure-name-resolution-for-a-federation-server-proxy-in-a-dns-zone-that-serves-both-the-perimeter-network-and-internet-clients"></a>Настройка разрешения имен для прокси-сервера федерации в зоне DNS, которая обслуживает как сеть периметра, так и интернет-клиенты


Таким образом, разрешение имен может успешно работать для прокси-сервера федерации в службы федерации Active Directory (AD FS) \(AD FS\), в котором одна или несколько систем доменных имен \(зон DNS\) служат как для сети периметра, так и для интернет-клиентов, необходимо выполнить следующие задачи.  
  
-   Служба DNS в зоне Интернета, которую вы контролируете, должна быть настроена для разрешения всех запросов клиентов в Интернете по имени узла AD FS на прокси-сервер федерации. Для этого необходимо добавить узел \(\) записи ресурса в зону DNS Интернета для прокси-сервера федерации.  
  
-   DNS в сети периметра должна быть настроена на разрешение всех входящих клиентских запросов для имени узла AD FS на сервере федерации. Для этого необходимо добавить узел \(запись ресурса\) в зону DNS периметра для прокси-сервера федерации.  
  
> [!NOTE]  
> Предполагается, что узел \(запись ресурса\) для сервера федерации уже создана в DNS-службе корпоративной сети. Если эта запись еще не существует, создайте эту запись и выполните эти процедуры. Дополнительные сведения о создании узла \(записи ресурса\) для сервера федерации см. в разделе [Добавление записи ресурса узла &#40;a&#41; в корпоративную службу DNS для сервера федерации](Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md).  
  
## <a name="add-a-host-a-resource-record-to-the-internet-dns-zone-for-a-federation-server-proxy"></a>Добавление узла \(записи ресурса\) в зону DNS Интернета для прокси-сервера федерации  
Чтобы клиентские компьютеры в Интернете могли успешно получить доступ к серверу федерации через вновь развернутый прокси-сервер федерации, необходимо сначала создать узел \(\) записью ресурса в зоне DNS Интернета, которую вы контролируете. Эта запись ресурса разрешает имя узла сервера федерации учетной записи \(например, fs.fabrikam.com\) IP-адрес прокси-сервера федерации учетной записи \(например 131.107.27.68\) в сети периметра.  
  
> [!NOTE]  
> Предполагается, что вы используете DNS-сервер под управлением Windows 2000 Server, Windows Server 2003 или Windows Server 2008 со службой DNS-сервера для управления зоной DNS в Интернете.  
  
Членство в группах « **Администраторы**» или «эквивалентное» является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
#### <a name="to-add-a-host-a-resource-record-to-the-internet-dns-zone-for-a-federation-server-proxy"></a>Добавление узла \(записи ресурса\) в зону DNS Интернета для прокси-сервера федерации  
  
1.  На DNS-сервере для зоны DNS Интернета откройте\-оснастки DNS в.  
  
2.  В дереве консоли\-щелкните правой кнопкой мыши подходящую зону прямого просмотра и выберите **создать узел \(A или AAAA\)** .  
  
3.  В поле **имя**введите только имя компьютера сервера федерации. Например, чтобы указать полное доменное имя \(FQDN\) fs.fabrikam.com, введите **FS**.  
  
4.  В поле **IP-адрес**введите IP-адрес для нового прокси-сервера федерации, например 131.107.27.68.  
  
5.  Нажмите кнопку **Добавить узел**.  
  
## <a name="add-a-host-a-resource-record-to-the-perimeter-dns-zone-for-a-federation-server-proxy"></a>Добавление узла \(записи ресурса\) в зону DNS периметра для прокси-сервера федерации  
Чтобы клиент Интернет мог успешно обрабатываться прокси-сервером федерации и достигать сервера федерации после того, как они разрешаются зоной DNS в Интернете, необходимо создать узел \(\) записи ресурса в зоне периметра зоны DNS. Эта запись ресурса разрешает имя узла сервера федерации учетной записи \(например, FS. fabrikam.com\) IP-адрес сервера федерации учетной записи \(например 192.168.1.4\) в корпоративной сети.  
  
> [!NOTE]  
> Предполагается, что вы используете DNS-сервер под управлением Windows 2000 Server, Windows Server 2003, Windows Server 2008 или Windows Server® 2012 со службой DNS-сервера для управления зоной DNS периметра.  
  
Членство в группах « **Администраторы**» или «эквивалентное» является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
#### <a name="to-add-a-host-a-resource-record-to-the-perimeter-dns-zone-for-a-federation-server-proxy"></a>Добавление узла \(записи\) ресурса в зону DNS периметра для прокси-сервера федерации  
  
1.  На DNS-сервере сети периметра откройте **\-оснастки DNS в**.  
  
2.  В дереве консоли\-щелкните правой кнопкой мыши подходящую зону прямого просмотра и выберите **создать узел \(A или AAAA\)** .  
  
3.  В поле **имя**введите только имя компьютера сервера федерации. Например, для полного доменного имени fs.fabrikam.com следует ввести **fs**.  
  
4.  В текстовом поле **IP-адрес** введите IP-адрес сервера федерации в корпоративной сети, например 192.168.1.4.  
  
5.  Нажмите кнопку **Добавить узел**.  
  
## <a name="additional-references"></a>Дополнительная справка  
[Контрольный список: Настройка прокси-сервера федерации](Checklist--Setting-Up-a-Federation-Server-Proxy.md)  
  
[Требования к разрешению имен для прокси-серверов федерации](https://technet.microsoft.com/library/dd807055.aspx)  
  

