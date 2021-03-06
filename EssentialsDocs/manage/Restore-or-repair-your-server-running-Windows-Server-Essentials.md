---
title: Восстановление сервера под управлением Windows Server Essentials
description: Описание использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 27bf6f24-30c4-4935-9b24-069eb43e22f4
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: bb3cc834e0ab6641c14f5e9fbb6afe5c9f187c7c
ms.sourcegitcommit: e40fce7b8b4bc0bef278e676435306f14078cf00
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787174"
---
# <a name="restore-or-repair-your-server-running-windows-server-essentials"></a>Восстановление сервера под управлением Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials
 
 В этом разделе приводятся общие сведения и вспомогательные процедуры по восстановлению или исправлению сервера, на котором выполняется Windows Server Essentials, и приведены следующие разделы.  
  
-   [Общие сведения о восстановлении серверных систем](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Overview)  
  
-   [Восстановить или восстановить системный диск](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore)  
  
-   [Восстановление файлов и папок на сервере](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders)  
  
##  <a name="BKMK_Overview"></a>Общие сведения о восстановлении серверных систем  
 От состояния сервера зависят доступные способы восстановления и результаты процесса.  
  
 К наиболее частым причинам восстановления сервера относятся:  
  
- Наличие на сервере зараженных файлов, которые невозможно вылечить или удалить.  
  
- Сервер неверно настроен и не запускается.  
  
- Вы заменили системный диск.  
  
- Вы больше не планируете использовать устройство и желаете перенести данные на новый сервер.  
  
  Вы можете восстановить сервер из резервной копии или сбросить параметры к значениям по умолчанию.  
  
- [Восстановление сервера из резервной копии](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFromBackup)  
  
- [Сброс параметров сервера до заводских настроек по умолчанию](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_FactoryReset)  
  
###  <a name="BKMK_RestoreFromBackup"></a>Восстановление сервера из резервной копии  
 В этом разделе представлены инструкции по выбору типа архивации.  
  
 Если резервная копия доступна, лучшим выбором для восстановления сервера является использование установочного носителя изготовителя для восстановления из внешней резервной копии. Восстановление поможет извлечь параметры и папки сервера из выбранного вами архива. Вам потребуется лишь настроить параметры и восстановить данные, созданные после архивации.  
  
 Если вы планируете восстановить ваш сервер из ранее созданной резервной копии, следует выбрать необходимый архив для восстановления, хранящийся на внешнем жестком диске, напрямую подключенном к серверу.  
  
- **Если у вас есть недавняя успешно созданная резервная копия сервера**, и вы уверены, что она содержит все важные данные, ваш выбор вполне очевиден. Вам потребуется лишь восстановить данные, созданные после последней успешной архивации, и заново настроить параметры сервера, измененные после резервирования  
  
- **Если вы восстанавливаете сервер из-за вируса**, выберите резервную копию, созданную до заражения. При восстановления из последней подходящей резервной копии может быть выполнен откат на несколько дней.  
  
- **Если вы восстанавливаете сервер из-за неверных параметров**, выберите резервную копию, созданную до изменения вызвавших проблемы настроек.  
  
  Если вы восстанавливаетесь из резервной копии, точные действия и необходимые доработки зависят от числа жестких дисков на сервере и факта замены системного диска:  
  
- **Если на сервере установлен один жесткий диск, замена которого не производилась**, информация о разделах останется неизменной после восстановления. Системный том будет восстановлен и данные остальных разделов сохранятся.  
  
- **Если на сервере используется один жесткий диск и выполнена его замена**, будет восстановлен системный том, после чего вам потребуется вручную скопировать папки и данные из остальных разделов. Любые созданные вами общие папки потребуется восстановить вручную.  
  
- **Если на сервере установлено несколько жестких дисков, и диск 0 (содержащий системный том) не заменялся**, информация о разделах диска сохранится после восстановления. Системный том будет восстановлен и данные всех остальных разделов останутся неизменны.  
  
- **Если на сервере установлено несколько жестких дисков, и выполнена замена диска 0 (содержащего системный том)** , системный том будет восстановлен, после чего вам потребуется вручную восстановить все общие папки, хранившиеся на диске 0 ранее.  
  
###  <a name="BKMK_FactoryReset"></a>Сброс параметров сервера до заводских настроек по умолчанию  
 Если у вас нет резервной копии, которую можно использовать для восстановления, или по какой-то другой причине вы желаете или вам требуется выполнить полное восстановление системы без возвращения предыдущей конфигурации сервера, вы можете сбросить параметры сервера к значениям по умолчанию, используя носитель для установки или восстановления от производителя серверного оборудования.  
  
 Все текущие параметры и установленные приложения сервера теряются при сбросе, и требуется повторная настройка устройства. После сброса параметров происходит перезагрузка сервера.  
  
 При сбросе настроек к значениям по умолчанию вы можете сохранить ваши данные или удалить их:  
  
-   Если вы решите сохранить все ваши данные, то вся информация, хранящаяся в системном томе, будет удалена; данные других томов сохранятся.  
  
    > [!CAUTION]
    >  Если параметры диска не соответствуют настройкам по умолчанию, все данные будут потеряны. При замене системного диска новый диск должен быть больше, чем системный том исходного диска.  
    >   
    >  Если информация о разделах системного диска недоступна, или вы заменили системный диск, все данные на нем будут удалены, даже если вы выберете их сохранение.  
  
-   Если вы планируете списать сервер или использовать его для других целей, рекомендуется удалить на нем все данные. Помимо параметров сервера, прочих настроек и данных системного тома, удаляется вся остальная информация и производится форматирование всех жестких дисков сервера.  
  
> [!NOTE]
>  Если на сервере настроены дисковые пространства, перед сбросом к значениям по умолчанию откройте консоль **Управление дисковыми пространствами**, перейдите к секции **Дополнительно** и вручную удалите все дисковые пространства.  
  
 После сброса параметров вам потребуется выполнить следующие действия:  
  
-   **Повторная настройка сервера.** Используйте мастер настройки сервера, чтобы повторно установить параметры. Чтобы настроить удаленно управляемый сервер Windows Server Essentials с клиентского компьютера, откройте веб-браузер и введите в адресной строке **http://** _<\> йоурсервернаме_ .  
  
-   **Переподключение клиентского компьютера к серверу.** Если компьютер ранее был подключен к серверу, необходимо удалить программное обеспечение соединителя Windows Server Essentials с компьютера перед повторным подключением компьютера к серверу. Дополнительные сведения см. в статьях [Uninstall the Connector software](../use/Get-Connected-in-Windows-Server-Essentials.md#BKMK_13) и [Connect computers to the server](../use/Get-Connected-in-Windows-Server-Essentials.md#BKMK_9).  
  
##  <a name="BKMK_Restore"></a>Восстановить или восстановить системный диск  
 Чтобы сервер вернулся к работе, в первую очередь необходимо восстановить его системный диск. После этого вы можете выполнить любые необходимые действия для восстановления дисков с данными и любых потерянных при восстановлении сервера общих папок.  
  
 Доступно три способа восстановления:  
  
-   [Восстановление сервера с помощью установочного носителя](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_1). Используйте установочный носитель от производителя сервера, чтобы восстановиться из резервной копии.  
  
-   **Сброс параметров сервера к значениям по умолчанию с помощью установочного носителя**. См. документацию от производителя сервера.  
  
-   [Восстановление сервера с клиентского компьютера с помощью специального DVD-диска](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_2). Если необходимо восстановить удаленно администрируемый сервер под управлением Windows Server Essentials, необходимо выполнить восстановление с клиентского компьютера с помощью DVD-диска восстановления от изготовителя сервера.  
  
###  <a name="BKMK_Restore_1"></a>Восстановите или восстановите сервер с помощью установочного носителя.  
 Следующая процедура описывает восстановление системного диска сервера из резервной копии с помощью установочного носителя Windows Server Essentials. (информацию о сбросе параметров к значениям по умолчанию с помощью установочного носителя см. в документации от производителя сервера).  
  
> [!NOTE]
>  Если сервер использует дисковые пространства и вы восстанавливаете данные на новый сервер, необходимо сначала восстановить системный диск, а затем войти на панель мониторинга Windows Server Essentials, настроить дисковые пространства так же, как на старом сервере, а затем восстановить dat. тома.  
  
##### <a name="to-restore-the-server-system-drive-from-a-backup-using-installation-media"></a>Восстановление системного диска сервера из резервной копии с помощью установочного носителя  
  
1.  Вставьте установочный DVD-диск Windows Server Essentials на DVD-диск сервера, перезапустите сервер и нажмите любую клавишу для запуска с DVD-диска.  
  
    > [!NOTE]
    >  Если процесс восстановления не начинается автоматически, проверьте параметры BIOS на вашем сервере и убедитесь, что в списке приоритетов загрузки DVD-дисковод находится на первом месте.  
  
     -Или-  
  
     Если производитель предварительно загрузил содержимое установочного носителя на сервер, нажмите клавишу F8 при запуске, чтобы начать восстановление.  
  
2.  После загрузки файлов Windows Server выберите язык и другие необходимые настройки, после чего щелкните **Далее**.  
  
3.  На следующей странице мастера щелкните **Восстановить компьютер**.  
  
    > [!CAUTION]
    >  Не выбирайте вариант **Установить сейчас** . В противном случае начнется полная установка системы и все параметры конфигурации системного диска и данные на нем будут удалены.  
  
4.  На странице **Выбор варианта** щелкните **Устранение неполадок**.  
  
5.  На странице **Восстановление образа системы** выберите текущую систему, либо **Windows Server Essentials** , либо **Windows Server Essentials**.  
  
     Откроется мастер восстановления из образа.  
  
6.  На странице **Выбор архивного образа системы** вы можете выбрать последнюю или более раннюю резервную копию. Система будет восстановлена к состоянию на момент создания выбранной вами резервной копии. Потребуется вручную восстановить добавленные после архивации данные или измененные параметры.  
  
     Выберите один из следующих вариантов и щелкните **Далее**:  
  
    -   **Использовать последний доступный образ системы (рекомендуется)**  
  
    -   **Выбор архивного образа системы**  
  
    > [!NOTE]
    >  Если у вас есть недавняя успешно созданная резервная копия сервера, и вы уверены, что она содержит все важные данные, то ваш выбор вполне очевиден. Вам потребуется лишь восстановить данные, созданные после последней успешной архивации, и заново настроить параметры сервера, измененные после резервирования  
    >   
    >  Если вы восстанавливаете сервер из-за вируса, выберите резервную копию, созданную до заражения. При восстановления из последней подходящей резервной копии может быть выполнен откат на несколько дней.  
    >   
    >  Если вы восстанавливаете сервер из-за неверных параметров, выберите резервную копию, созданную до изменения вызвавших проблемы настроек.  
  
7.  Для завершения восстановления системы следуйте инструкциям мастера.  
  
8.  После успешного восстановления сервера извлеките установочный DVD-диск, если вы его использовали, и выполните перезагрузку.  
  
> [!NOTE]
>  Для восстановления папок на сервере и открытия к ним общего доступа могут потребоваться дополнительные действия. Дополнительные сведения см. в разделе [Restore files and folders on the server](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders).  
  
###  <a name="BKMK_Restore_2"></a>Восстановление или сброс сервера с клиентского компьютера с помощью DVD-диска восстановления  
 В Windows Server Essentials можно запустить сервер с загрузочного диска USB, который вы создали, а затем восстановить сервер с клиентского компьютера с помощью DVD-диска восстановления, полученного от изготовителя сервера. Клиентский компьютер должен находиться в одной сети с сервером Этот метод недоступен в Windows Server Essentials.  
  
 Далее описаны основные действия, необходимые для восстановления сервера. Приведенные шаги подходят как для восстановления из резервной копии, так и для сброса параметров к значениям по умолчанию. Более точные инструкции см. в документации от производителя вашего сервера.  
  
##### <a name="to-restore-or-reset-the-server-from-a-client-computer-using-the-recovery-dvd"></a>Восстановление сервера с клиентского компьютера с помощью специального DVD-диска  
  
1.  Вставьте носитель для восстановления сервера Windows Server Essentials, полученный от изготовителя сервера, на клиентском компьютере.  
  
     Откроется мастер восстановления сервера.  
  
2.  Следуйте инструкциям мастера, чтобы создать загрузочное USB-устройство флэш-памяти, которое будет использоваться для запуска сервера в режиме восстановления.  
  
3.  Когда загрузочное USB-устройство флэш-памяти будет подготовлено с помощью мастера восстановления сервера, вставьте его в сервер, чтобы загрузить режим восстановления. Информацию о запуске вашего сервера в режиме восстановления см. в документации от производителя вашего серверного оборудования.  
  
     После запуска в режиме восстановления мастер обнаружит сервер и установит соединение.  
  
4.  Для завершения восстановления сервера следуйте инструкциям мастера.  
  
> [!NOTE]
>  При этом способе восстановления игнорируются внешние устройства хранения, подключенные к серверу. Если вы желаете очистить данные с внешнего устройства хранения, потребуется сделать это вручную.  
  
> [!NOTE]
>  Если вы создали на сервере дополнительные общие папки, после восстановления данных из резервной копии эти папки могут не распознаться на сервере. В этом случае потребуется заново открыть к этим папкам общий доступ. Дополнительные сведения см. в разделе [Restore files and folders on the server](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesAndFolders).  
  
##  <a name="BKMK_RestoreFilesAndFolders"></a>Восстановление файлов и папок на сервере  
 В зависимости от способа восстановления сервера и типа используемых устройств хранения, после восстановления системного диска вам может потребоваться вернуть тома с данными. В некоторых случаях вам придется повторно открыть доступ к существующим папкам, чтобы они распознались на сервере.  
  
 Далее описаны случаи, в которых вам может потребоваться восстановить файлы и папки:  
  
-   [Восстановление файлов и папок из резервной копии сервера](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_RestoreFilesFromBackup). Если вы заменили системный диск, или информация о разделах системного диска недоступна, вы можете восстановить систему, однако данные из других томов диска будут потеряны. Чтобы восстановить файлы и папки из других томов с данными, используйте мастер восстановления файлов и папок.  
  
-   [Восстановление общих папок на сервере](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_ConfigreSharedFolders). Если вы создали на сервере дополнительные общие папки, после восстановления системного диска из резервной копии они будут расположены в разделе с данными, однако могут не распознаваться на сервере. В этом случае потребуется заново открыть к этим папкам общий доступ.  
  
###  <a name="BKMK_RestoreFilesFromBackup"></a>Восстановление файлов и папок из резервной копии сервера  
 Мастер восстановления файлов и папок поможет вам защитить данные на случай поломки жесткого диска или непреднамеренного удаления информации. С помощью резервного копирования Windows Server Essentials можно создать копию всех данных на жестком диске и сохранить их на внешнем устройстве хранения. Если исходные данные будут непреднамеренно удалены, перезаписаны или станут недоступны в результате поломки, вы сможете восстановить их из резервной копии. С помощью мастера восстановления файлов и папок вы можете извлечь из резервной копии отдельный файл или папку, несколько файлов или папок, или же целый жесткий диск.  
  
 Чтобы вернуть файлы и папки, оказавшиеся недоступными после восстановления, вам может потребоваться мастер восстановления файлов и папок. Например, если вы заменили системный диск, или информация о его разделах недоступна, у вас не получится восстановить данные других томов жесткого диска.  
  
> [!NOTE]
>  С помощью мастера восстановления файлов и папок вы не сможете восстановить целый системный диск. Сведения о восстановлении всей системы, см. в разделе [восстановление сервера с помощью установочного носителя](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_1) или [восстановление сервера с клиентского компьютера с помощью DVD-диска восстановления](Restore-or-repair-your-server-running-Windows-Server-Essentials.md#BKMK_Restore_2).  
  
##### <a name="to-restore-files-and-folders-from-a-server-backup"></a>Восстановление файлов и папок из резервной копии сервера  
  
1.  Откройте панель мониторинга Windows Server Essentials и перейдите на вкладку **устройства** .  
  
2.  Щелкните имя сервера и нажмите в области **Задачи** кнопку **Восстановить файлы и папки сервера**.  
  
     Откроется мастер восстановления файлов и папок.  
  
3.  Чтобы восстановить необходимые файлы и папки, следуйте инструкциям мастера.  
  
> [!WARNING]
>  Дополнительные сведения о резервном копировании и восстановлении файлов и папок см. в разделе [Управление резервным копированием](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)и восстановлением.  
  
###  <a name="BKMK_ConfigreSharedFolders"></a>Восстановление общих папок на сервере  
 После восстановления системного диска сервера, если общие папки по-прежнему находятся в разделе данных или восстановлены в разделе данных, может потребоваться еще раз настроить общие папки, чтобы сервер мог распознать папки. Далее описано, как открыть доступ к папкам, уже использованным ранее в качестве общих.  
  
##### <a name="to-add-an-existing-folder-to-the-server-shared-folders"></a>Добавление существующего каталога в список общих папок сервера.  
  
1.  Найдите необходимую папку на жестком диске с помощью проводника.  
  
2.  Щелкните правой кнопкой мыши по общей папке, выберите **Свойства**, перейдите во вкладку **Доступ** и запишите разрешения для этой папки.  
  
3.  Войдите на панель мониторинга Windows Server Essentials, перейдите на вкладку **хранилище** и нажмите кнопку **Добавить папку** в области **задачи папки сервера** .  
  
     Откроется мастер добавления папок.  
  
4.  Укажите имя общей папки в поле **Имя**.  
  
5.  Нажмите кнопку **Обзор**, перейдите к *<\>диск\\<\>ServerName*\серверфолдерс (например, *д:\контосо\серверфолдерс*), выберите папку, к которой требуется предоставить общий доступ, и нажмите кнопку **ОК**.  
  
6.  Нажмите кнопку **Далее**.  
  
7.  Укажите записанные на шаге 2 разрешения и щелкните **Добавить папку**.  
  
    > [!IMPORTANT]
    >  Эти разрешения будут заменять любые существующие разрешения, которые не были добавлены в папку с помощью панели мониторинга Windows Server Essentials.  
  
> [!IMPORTANT]
>  После добавления папок в список общего доступа, убедитесь, что в дальнейшем будет выполняться их архивация. Информацию о добавлении папок в резервную копию сервера см. в статье [Настройка или изменение параметров архивации сервера](Set-up-or-customize-server-backup.md).  
  
## <a name="see-also"></a>См. также  
  
-   [Управление резервным копированием и восстановлением](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)  
  
-   [Управление Windows Server Essentials](Manage-Windows-Server-Essentials.md)  
  
-   [Использование Windows Server Essentials](../use/Use-Windows-Server-Essentials.md)
