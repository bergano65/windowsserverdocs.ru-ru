---
title: Обновление до AD FS в Windows Server 2016 с SQL Server
description: ''
author: billmath
manager: mtillman
ms.date: 04/11/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.assetid: 70f279bf-aea1-4f4f-9ab3-e9157233e267
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: 59b761e69da5b1c1e27fea71b32447b19d2b83c6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59812085"
---
# <a name="upgrading-to-ad-fs-in-windows-server-2016-with-sql-server"></a>Обновление до AD FS в Windows Server 2016 с SQL Server

>Область применения. Windows Server 2016


## <a name="moving-from-a-windows-server-2012-r2-ad-fs-farm-to-a-windows-server-2016-ad-fs-farm"></a>Перемещение из фермы Windows Server 2012 R2 AD FS в ферме Windows Server 2016 AD FS  
Следующий документ показывает, как для обновления фермы AD FS Windows Server 2012 R2 для AD FS в Windows Server 2016, при использовании SQL Server для базы данных AD FS.  

### <a name="upgrading-ad-fs-to-windows-server-2016-fbl"></a>Обновление до Windows Server 2016 FBL AD FS  
Новые возможности AD FS в Windows Server 2016 поведение уровня фермы (FBL).   В этой функции всю ферму и определяет функции, которые можно использовать в ферме AD FS.   По умолчанию FBL в ферме Windows Server 2012 R2 AD FS находится в Windows Server 2012 R2 FBL.  

Сервер Windows Server 2016 AD FS можно добавить в ферму Windows Server 2012 R2, и он будет работать на том же FBL как на Windows Server 2012 R2.  Если у вас есть сервер Windows Server 2016 AD FS, работающий в такой манере, считается, что ферме быть «mixed».  Тем не менее вы не сможете воспользоваться преимуществами новых функций Windows Server 2016, пока не возникает FBL до Windows Server 2016.  С помощью смешанных фермы:  

-   Администраторы могут добавлять новые серверы федерации Windows Server 2016 в существующую ферму Windows Server 2012 R2.  В результате ферма находится в «смешанный режим» и работает на уровне поведения фермы Windows Server 2012 R2.  Для обеспечения согласованного поведения в ферме, новые возможности Windows Server 2016 нельзя настроить или использовать в этом режиме.  

-   После того как все серверы федерации Windows Server 2012 R2 будут удалены из фермы смешанный режим, и в случае ферме внутренней базы данных Windows, один из новых серверов федерации Windows Server 2016 выдвинут на роль основного узла, администратор может затем изменить FBL от Win семинары, посвященные Server 2012 R2 до Windows Server 2016.  Таким образом все новые возможности AD FS Windows Server 2016 можно затем настроить и использовать.  

-   В результате компонента смешанной фермы AD FS Windows Server 2012 R2, организаций, которые собираются для обновления до Windows Server 2016 не придется развернуть новую ферму, экспорт и импорт данных конфигурации.  Вместо этого можно добавить узлы Windows Server 2016 в существующую ферму, когда он находится в сети и взималась только за относительно небольшой простой, участвующих в FBL raise.  

Имейте в виду, что в режиме смешанной фермы фермы AD FS не может быть любой новые компоненты или функциональные возможности, появившиеся в AD FS в Windows Server 2016.  Это означает, что организаций, которые хотят опробовать новые компоненты невозможно, пока не возникает FBL.  Поэтому если организации требуется для тестирования новых функций до rasing FBL, необходимо будет развернуть отдельный ферму для этого.  

В оставшейся части является документе описываются действия по добавлению сервера федерации Windows Server 2016 в среде Windows Server 2012 R2 и затем увеличивать их FBL до Windows Server 2016.  Эти действия были выполнены в тестовой среде, описанные на следующей схеме архитектуры.  

> [!NOTE]  
> Прежде чем можно переместить в AD FS в Windows Server 2016 FBL, необходимо удалить все узлы Windows 2012 R2.  Невозможно просто обновить ОС Windows Server 2012 R2 до Windows Server 2016 и его становятся узлами 2016.  Необходимо будет удалить его и замените его на новый узел 2016.  

На следующей схеме архитектуры показано установки, который был использован для проверки и запишите указанные ниже действия.

![Architecture (Архитектура)](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/arch.png) 


#### <a name="join-the-windows-2016-ad-fs-server-to-the-ad-fs-farm"></a>Присоединение к ферме AD FS сервера AD FS Windows 2016

1.  С помощью установки диспетчера серверов роль служб федерации Active Directory в Windows Server 2016  

2.  С помощью мастера настройки AD FS, присоедините новый сервер Windows Server 2016 в существующую ферму AD FS.  На **приветствия** откройте **Далее**.
 ![Присоединение к ферме](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/configure1.png)  
3.  На **подключение к доменных служб Active Directory** экрана, s**укажите учетную запись администратора** с разрешениями для выполнения настройки служб федерации и нажмите кнопку **Далее**.
4.  На **укажите ферму** экрана, введите имя SQL server и экземпляр и нажмите кнопку **Далее**.
![Присоединение к ферме](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/configure3.png)
5.  На **укажите SSL-сертификат** экрана, укажите сертификат и нажмите кнопку **Далее**.
![Присоединение к ферме](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/configure4.png)
6.  На **укажите учетную запись службы** экрана, укажите учетную запись службы и нажмите кнопку **Далее**. 
7.  На **просмотреть параметры** экране Проверьте параметры и нажмите кнопку **Далее**. 
8.  На **проверяет предварительные требования** экрана, убедитесь, что все предварительные проверки пройдены и нажмите кнопку **Настройка**.
9.  На **результатов** экрана, убедитесь, что сервер успешно настроен и нажмите кнопку **закрыть**.
 
   
#### <a name="remove-the-windows-server-2012-r2-ad-fs-server"></a>Удаление сервера Windows Server 2012 R2 AD FS

>[!NOTE]
>Необходимо установить основной сервер AD FS, с помощью набора AdfsSyncProperties-роли при использовании в качестве базы данных SQL.  Это потому, что все узлы считаются основного сервера в этой конфигурации.

1.  На сервере Windows Server 2012 R2 AD FS используется диспетчер серверов **удалить роли и компоненты** под **управление**. 
![Удаление сервера](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/remove1.png)
2.  На странице **Приступая к работе** нажмите кнопку **Далее**.
3.  На **Выбор сервера** экрана, нажмите кнопку **Далее**.
4.  На **ролей сервера** экрана, снимите флажок рядом с полем **служб федерации Active Directory** и нажмите кнопку **Далее**.
![Удаление сервера](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/remove2.png)
5.  На **функции** экрана, нажмите кнопку **Далее**.
6.  На **Подтверждение** экрана, нажмите кнопку **удалить**.
7.  По завершении перезапустите сервер.
     
#### <a name="raise-the-farm-behavior-level-fbl"></a>Повысить уровень поведение фермы (FBL)
До этого шага необходимо убедиться, что forestprep и domainprep были запущены в среде Active Directory, и что Active Directory имеет схему Windows Server 2016.  В этом документе к работе с контроллером домена Windows 2016 и не требовал бы выполнения этих, так как они выполнялись при установке AD.

>[!NOTE]
>Прежде чем начать процесс, описанный ниже, убедитесь, что Windows Server 2016 является текущей, запустив из параметров обновления Windows.  Продолжайте этот процесс, пока не перестанут требоваться обновления. 

1. Теперь на сервере Windows Server 2016 откройте PowerShell и выполните следующую команду: **$cred = Get-Credential** и нажмите клавишу ВВОД.
2. Введите учетные данные, имеющие права администратора на сервере SQL Server.
3. Теперь в PowerShell, введите следующее: **Вызвать AdfsFarmBehaviorLevelRaise-Credential $cred**
2. При появлении запроса введите **Y**.  После этого начнется повышение уровня.  После завершения проверки вы сообщили успешно FBL.  
![Обновление готово](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/finish1.png)
3. Теперь если перейти на управление AD FS, вы увидите новые узлы, которые были добавлены для AD FS в Windows Server 2016  
4. Аналогичным образом можно использовать командлет PowerShell:  Get-AdfsFarmInformation показать текущее FBL.  
![Обновление готово](media/Upgrading-to-AD-FS-in-Windows-Server-2016-SQL/finish2.png)