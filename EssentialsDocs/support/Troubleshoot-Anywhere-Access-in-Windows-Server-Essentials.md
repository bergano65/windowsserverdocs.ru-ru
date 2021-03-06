---
title: Устранение неполадок повсеместного доступа в Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68f2b05c-09eb-4cba-8db4-a91353b513c6
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a14dbaed8c36f52814ba8080262ef60c399931dc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59874015"
---
# <a name="troubleshoot-anywhere-access-in-windows-server-essentials"></a>Устранение неполадок повсеместного доступа в Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

В этом разделе приведены общие инструкции по использованию мастера исправления повсеместного доступа в Windows Server Essentials для устранения неполадок, предотвращая сетевой доступ к ресурсам сервера. Повсеместный доступ функции удаленного веб-доступа, виртуальной частной сети (VPN), и DirectAccess позволяют пользователям сети получать доступ к ресурсам сервера из любого места с подключением к Интернету, в любое время, с любого устройства.  
  
 Мастер исправления повсеместного доступа пытается определить и устранить неполадки с маршрутизатором, именем домена или брандмауэром, которые не позволяют пользователям сети получить удаленный доступ к ресурсам сервера.  
  
> [!NOTE]
>  Самые последние сведения об устранении неполадок от сообщества Windows Server Essentials, мы рекомендуем посетить [форум по Windows Server Essentials](https://social.technet.microsoft.com/Forums/winserveressentials/threads). Форум Windows Server Essentials — это отличный ресурс, на котором можно получить помощь или задать вопрос.  
  
### <a name="to-repair-anywhere-access"></a>Исправление повсеместного доступа  
  
1.  Войдите в сервер и откройте панель мониторинга.  
  
2.  Нажмите кнопку **Параметры**, а затем откройте вкладку **Повсеместный доступ**.  
  
3.  Щелкните **Восстановить**. Запускается мастер исправления повсеместного доступа.  
  
4.  Нажмите кнопку **Далее**. Мастер анализирует работу повсеместного доступа, определяет проблему и пытается устранить неполадку.  
  
5.  Если вы получите предупреждение по окончании работы мастера, можно щелкнуть **Повторить** , чтобы попытаться устранить проблему еще раз. Если вы продолжите получать предупреждение, ознакомьтесь с дополнительными сведениями о проблеме и рекомендациями по ее устранению в составе предупреждения.  
  
### <a name="to-get-more-information-about-an-alert"></a>Получение дополнительных сведений об оповещении  
  
1.  В правом верхнем углу панели мониторинга щелкните любой значок ошибки или предупреждения, чтобы открыть средство просмотра оповещений.  
  
2.  В средстве просмотра оповещений выберите ошибку или оповещение для просмотра дополнительной информации.  
  
## <a name="additional-troubleshooting-for-anywhere-access"></a>Дополнительные возможности устранения неполадок повсеместного доступа  
 Если мастеру исправления повсеместного доступа не удается восстановить повсеместный доступ, ознакомьтесь со следующими разделами, посвященными устранению неполадок удаленного веб-доступа, VPN и DirectAccess:  
  

-   [Устранение проблем с подключением удаленного веб-доступа](Troubleshoot-Remote-Web-Access-connectivity-in-Windows-Server-Essentials.md)  
  
-   [Устранение неполадок брандмауэра](Troubleshoot-your-firewall-in-Windows-Server-Essentials.md)  

-   [Устранение проблем с подключением удаленного веб-доступа](../support/Troubleshoot-Remote-Web-Access-connectivity-in-Windows-Server-Essentials.md)  
  
-   [Устранение неполадок брандмауэра](../support/Troubleshoot-your-firewall-in-Windows-Server-Essentials.md)  

  
-   Проверьте [форум по Windows Server Essentials](https://social.technet.microsoft.com/Forums/winserveressentials/threads) последних проблем, выявленных в сообществе Windows Server Essentials.
