---
title: Восстановление леса AD — присвоение роли хозяина операций
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 7e6bb370-f840-4416-b5e2-86b0ba715f4f
ms.technology: identity-adds
ms.openlocfilehash: 672dc119845acbe9cf38f82c793bd377d31db3b2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71390284"
---
# <a name="ad-forest-recovery---seizing-an-operations-master-role"></a>Восстановление леса AD — присвоение роли хозяина операций  

>Область применения. Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Используйте следующую процедуру для присвоения роли хозяина операций (также известной как роль FSMO). Можно использовать Ntdsutil. exe — программу командной строки, которая автоматически устанавливается на всех контроллерах домена.  
  
## <a name="to-seize-an-operations-master-role"></a>Присвоение роли хозяина операций  
  
1. В командной строке введите следующую команду и нажмите клавишу ВВОД:  

   ```  
   ntdsutil  
   ```  

2. В командной строке **ntdsutil:** введите следующую команду и нажмите клавишу ВВОД:  

   ```  
   roles  
   ```  

3. В командной строке **FSMO Maintenance:** введите следующую команду и нажмите клавишу ВВОД:  

   ```  
   connections  
   ```  

4. На странице **подключения к серверу:** введите следующую команду и нажмите клавишу ВВОД:  

   ```  
   Connect to server ServerFQDN  
   ```  

   Где *ServerFQDN* — полное доменное имя (FQDN) этого контроллера домена, например: **подключение к серверу nycdc01.example.com**.  

   Если *ServerFQDN* не удается, используйте NetBIOS-имя контроллера домена.  

5. На странице **подключения к серверу:** введите следующую команду и нажмите клавишу ВВОД:  

   ```  
   quit  
   ```  

6. В зависимости от роли, которую требуется захватить, в командной строке " **FSMO Maintenance:** " введите соответствующую команду, как описано в следующей таблице, и нажмите клавишу ВВОД.  
  
|Role|Учетные данные|Command|  
|----------|-----------------|-------------|  
|Хозяин именования доменов|Администраторы предприятия|**Присвоение имени хозяину именования**|  
|Хозяин схемы|Администраторы схемы|**Присвоение роли хозяина схемы**|  
|Главное Примечание к инфраструктуре **:**  После присвоения роли хозяина инфраструктуры вы можете получить сообщение об ошибке позже, если необходимо запустить Adprep/Родкпреп. Дополнительные сведения см. в статье базы знаний [949257](https://support.microsoft.com/kb/949257).|Администраторы домена|**Присвоение роли хозяина инфраструктуры**|  
|Хозяин эмулятора PDC|Администраторы домена|**Захватить основной контроллер домена**|  
|.|Администраторы домена|**Захватить хозяина RID**|  

После подтверждения запроса Active Directory или AD DS пытается переместить роль. В случае сбоя при переносе появляется часть сведений об ошибке, а Active Directory или AD DS переходит к захвату. После завершения переименования отображается список ролей и имя сервера, на котором в настоящее время содержится каждая роль. Можно также выполнить команду **netdom query fsmo** в командной строке с повышенными привилегиями для проверки текущих владельцев ролей.  
  
> [!NOTE]
> Если этот компьютер не был хозяином RID до сбоя и вы пытаетесь присвоить роль хозяина RID, то перед принятием этой роли компьютер пытается выполнить синхронизацию с партнером репликации. Однако поскольку этот шаг выполняется, когда компьютер изолирован, синхронизация с партнером не будет выполнена. Поэтому появится диалоговое окно с запросом на продолжение операции, несмотря на то, что этот компьютер не может синхронизироваться с партнером. нажмите кнопку **Да**.  
  
## <a name="next-steps"></a>Следующие шаги

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
