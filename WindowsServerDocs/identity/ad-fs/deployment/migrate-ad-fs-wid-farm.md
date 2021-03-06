---
title: Миграция фермы WID сервера AD FS 2,0
description: Содержит сведения о миграции фермы AD FS 2,0 Server WID на Windows Server 2012
author: billmath
ms.author: billmath
manager: femila
ms.date: 06/28/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 89da3de4bc626e12a1fc34752841f2de1afb5322
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71408242"
---
# <a name="migrate-an-ad-fs-20-wid-farm"></a>Перенос фермы AD FS 2,0 WID  
В этом документе содержатся подробные сведения о переносе фермы AD FS 2,0 на базе внутренней базы данных Windows (WID) в Windows Server 2012.

## <a name="migrate-an-ad-fs-wid-farm"></a>Перенос фермы AD FS WID
Чтобы перенести ферму WID на Windows Server 2012, выполните следующую процедуру.  
  
1.  Для каждого узла (сервера) в ферме WID проверьте и выполните процедуры, описанные в подокне [Подготовка к миграции фермы WID](prepare-to-migrate-a-wid-farm.md).  
  
2.  Удалите из балансировщика нагрузки все неосновные узлы.  
  
3.  Обновление операционной системы на этом сервере с Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).  
  
> [!IMPORTANT]
>  В результате обновления операционной системы AD FS конфигурация на этом сервере теряется, а роль сервера AD FS 2,0 удаляется. Вместо этого устанавливается роль сервера AD FS Windows Server 2012, но она не настроена. Необходимо создать исходную конфигурацию AD FS и восстановить остальные параметры AD FS, чтобы завершить миграцию сервера федерации.  
  
4. Создайте исходную конфигурацию AD FS на этом сервере.  
  
Исходную конфигурацию AD FS можно создать с помощью **мастера настройки сервера федерации AD FS** , чтобы добавить сервер федерации в ферму WID. Дополнительные сведения см. в разделе [Добавление сервера федерации на ферму серверов федерации](add-a-federation-server-to-a-federation-server-farm.md).  
  
> [!NOTE]
> Когда вы найдете на страницу **Указание основного сервера федерации и учетной записи службы** в **AD FS мастера настройки сервера федерации**, введите имя основного сервера федерации для фермы WID и обязательно введите сведения об учетной записи службы, записанные при подготовке к миграции AD FS. Дополнительные сведения см. в разделе [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-a-wid-farm.md). 
>  
> При переходе на страницу **Указание имени служба федерации** выберите тот же SSL-сертификат, который вы записали в подокне "Подготовка к миграции на ферму WID" в статье [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-a-wid-farm.md).  
  
5. Обновите веб-страницы AD FS на этом сервере. Если при подготовке к миграции была создана резервная копия настроенных AD FS веб-страниц, необходимо использовать данные резервного копирования, чтобы перезаписать AD FS веб-страницы по умолчанию, созданные по умолчанию в каталоге **%системдриве%\инетпуб\адфс\лс** в результате настройки AD FS в Windows Server 2012.  
  
6. Добавьте только что обновленный сервер до Windows Server 2012 в подсистему балансировки нагрузки.  
  
7. Повторите шаги с 1 по 6 для оставшихся серверов-получателей в ферме WID.  
  
8. Повысьте один из обновленных дополнительных серверов до уровня основного на ферме внутренней базы данных Windows. Для этого откройте Windows PowerShell и выполните следующую команду: `PSH:> Set-AdfsSyncProperties –Role PrimaryComputer`.  
  
9. Удалите первоначальный основной сервер фермы внутренней базы Windows из балансировщика нагрузки.  
  
10. С помощью Windows PowerShell понизьте основной сервер фермы внутренней базы данных Windows до уровня дополнительного. Откройте Windows PowerShell и выполните следующую команду, чтобы добавить командлеты AD FS в сеанс Windows PowerShell: `PSH:>add-pssnapin “Microsoft.adfs.powershell”`. Затем выполните следующую команду, чтобы понизить первоначальный сервер-источник до вторичного сервера: `PSH:> Set-AdfsSyncProperties – Role SecondaryComputer –PrimaryComputerName <FQDN of the Primary Federation Server>`.  
  
11. Обновление операционной системы на этом последнем узле (сервере) в ферме WID с Windows Server 2008 R2 или Windows Server 2008 до Windows Server 2012. Дополнительные сведения см. в разделе [Установка Windows Server 2012](https://technet.microsoft.com/library/jj134246.aspx).  
  
> [!IMPORTANT]
>  В результате обновления операционной системы AD FS конфигурация на этом сервере теряется, а роль сервера AD FS 2,0 удаляется. Вместо этого устанавливается роль сервера AD FS Windows Server 2012, но она не настроена. Необходимо вручную создать исходную конфигурацию AD FS и восстановить остальные параметры AD FS, чтобы завершить миграцию сервера федерации.  
  
12. Создайте исходную конфигурацию AD FS на этом последнем узле (сервере) в ферме WID.  
  
Исходную конфигурацию AD FS можно создать с помощью **мастера настройки сервера федерации AD FS** , чтобы добавить сервер федерации в ферму WID. Дополнительные сведения см. в разделе [Добавление сервера федерации на ферму серверов федерации](add-a-federation-server-to-a-federation-server-farm.md).  
  
> [!NOTE]
> При переходе на страницу **Указание основного сервера федерации и учетной записи службы** в **AD FS мастера настройки сервера федерации**введите сведения об учетной записи службы, записанные при подготовке к миграции AD FS. Дополнительные сведения см. в разделе [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-a-wid-farm.md). 
>  
> При переходе на страницу **Указание имени служба федерации** убедитесь, что выбран тот же SSL-сертификат, который вы записали при [подготовке к переносу сервера федерации AD FS 2,0](prepare-to-migrate-a-wid-farm.md).  
  
13. Обновите веб-страницы AD FS на этом последнем сервере в ферме WID. Если при подготовке к миграции была создана резервная копия настроенных AD FS веб-страниц, используйте данные резервного копирования, чтобы перезаписать AD FS веб-страницы по умолчанию, которые были созданы по умолчанию в каталоге **%системдриве%\инетпуб\адфс\лс** в результате настройки AD FS в Windows Server 2012.  
  
14. Добавьте последний сервер фермы WID, который был обновлен до Windows Server 2012, в подсистему балансировки нагрузки.  
  
15. Восстановите остальные пользовательские настройки AD FS, например хранилища настраиваемых атрибутов.  
  
## <a name="next-steps"></a>Дальнейшие действия
 [Подготовка к переносу сервера федерации AD FS 2,0](prepare-to-migrate-ad-fs-fed-server.md)   
 [Подготовка к миграции прокси-сервера AD FS 2,0 федерации](prepare-to-migrate-ad-fs-fed-proxy.md)   
 [Перенесите сервер федерации AD FS 2,0](migrate-the-ad-fs-fed-server.md)   
 [Перенесите прокси-сервер AD FS 2,0 федерации](migrate-the-ad-fs-2-fed-server-proxy.md)   
 [Перенос веб-агентов AD FS 1.1](migrate-the-ad-fs-web-agent.md)