---
ms.assetid: c28a1b8b-5bec-4eed-8c95-a1a29cfc957c
title: Установка службы роли AD FS
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: 9851134d1ad73092ee44c34c99bc2d873d20ca07
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831175"
---
# <a name="install-the-ad-fs-role-service"></a>Установка службы роли AD FS

>Область применения. Windows Server 2016, Windows Server 2012 R2

Чтобы установить службу роли AD FS на компьютере под управлением Windows Server 2012 R2 в качестве первого сервера федерации в ферме серверов федерации или сервера федерации в существующую ферму серверов федерации, можно использовать следующую процедуру.  
  
Членство в группе **Администраторы**, или наличие эквивалентных прав на локальном компьютере, является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).   
  
### <a name="to-install-the-ad-fs-server-role-via-the-add-roles-and-features-wizard"></a>Для установки роли сервера AD FS с помощью мастера добавления ролей и компонентов  
  
1.  Откройте диспетчер сервера. Чтобы открыть диспетчер сервера, щелкните **диспетчера серверов** на **запустить** экрана, или **диспетчера серверов** на панели задач на рабочем столе. На вкладке **Быстрый запуск****плитки приветствия** на странице **Панель мониторинга** выберите элемент **Добавить роли и компоненты**. Либо выберите пункт **Добавить роли и компоненты** в меню **Управление**.  
  
2.  На странице **Перед работой** нажмите кнопку **Далее**.  
  
3.  На **Выбор типа установки** щелкните **роли\-или компонентов\-Установка на основе**, а затем нажмите кнопку **Далее**.  
  
4.  На странице **Выбор целевого сервера** щелкните **Выбрать сервер из пула серверов**, убедитесь, что выбран целевой компьютер, а затем нажмите кнопку **Далее**.  
  
5.  На странице **Выбор ролей сервера** щелкните **Службы федерации Active Directory**, а затем нажмите кнопку **Далее**.  
  
6.  На странице **Выбор компонентов** нажмите кнопку **Далее**. Обязательные компоненты будут выбраны заранее для вас. Необходимо выбирать другие компоненты.  
  
7.  На **служб федерации Active Directory \(AD FS\)**  щелкните **Далее**.  
  
8.  После проверки информации на **подтверждение выбранных параметров установки** щелкните **установить**.  
  
9. На странице **Ход установки** убедитесь, что все установлено верно, а затем нажмите кнопку **Закрыть**.  
  
### <a name="to-install-the-ad-fs-server-role-via-windows-powershell"></a>Чтобы установить роль сервера AD FS с помощью Windows PowerShell  
  
1.  На компьютере, где вы хотите настроить в качестве сервера федерации, откройте командное окно Windows PowerShell и выполните следующую команду: `Install-windowsfeature adfs-federation –IncludeManagementTools`.  
  
## <a name="see-also"></a>См. также 

[Развертывание AD FS](../../ad-fs/AD-FS-Deployment.md)  

[Руководство по развертыванию Windows Server 2012 R2 AD FS](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)  
 
[Развертывание фермы серверов федерации](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)  
  
