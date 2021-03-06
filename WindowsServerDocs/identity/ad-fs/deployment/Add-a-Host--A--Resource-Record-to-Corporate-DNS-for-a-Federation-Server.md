---
ms.assetid: 026747c7-4c34-41c7-b7ea-27f9a7f64a35
title: Добавление записи ресурса (A) узла в корпоративную систему DNS для сервера федерации
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 132e71cec134d17dd73be998683c09f752fdc414
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71360328"
---
# <a name="add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>Добавление записи ресурса (A) узла в корпоративную систему DNS для сервера федерации



Чтобы клиенты в корпоративной сети успешно подключались к серверу федерации с помощью встроенной проверки подлинности Windows, узел \(запись ресурса\) необходимо сначала создать в корпоративной системе доменных имен \(DNS-\), которая разрешает имя узла сервера федерации учетной записи \(например, fs.fabrikam.com\) IP-адресу сервера федерации или кластера Федерации. Следующую процедуру можно использовать для добавления узла \(записи ресурса\) в корпоративную службу DNS для сервера федерации.  
  
Членство в группах « **Администраторы**» или «эквивалентное» является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членстве в группах в [локальной среде и группах домена по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="to-add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>Добавление узла \(записи\) ресурса в корпоративную службу DNS для сервера федерации  
  
1.  На DNS-сервере для корпоративной сети откройте\-оснастки DNS в.  
  
2.  В дереве консоли\-щелкните правой кнопкой мыши подходящую зону прямого просмотра и выберите **создать узел \(A или AAAA\)** .  
  
3.  В поле **имя**введите только имя компьютера сервера федерации или кластера серверов федерации. Например, чтобы указать полное доменное имя \(FQDN\) fs.fabrikam.com, введите **FS**.  
  
4.  В поле **IP-адрес**введите IP-адрес сервера федерации или кластера серверов федерации, например 192.168.1.4.  
  
5.  Нажмите кнопку **Добавить узел**.  
  
## <a name="additional-references"></a>Дополнительная справка  
[Контрольный список: Настройка сервера федерации](Checklist--Setting-Up-a-Federation-Server.md)  
  
[Требования к разрешению имен для серверов федерации](https://technet.microsoft.com/library/dd807055.aspx)  
  

