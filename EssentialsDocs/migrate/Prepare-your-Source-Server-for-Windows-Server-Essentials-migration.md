---
title: Подготовка исходного сервера для Windows Server Essentials migration1
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5861ae9-77cb-4d37-b4c5-8f0757213385
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 929c7506c78667646e429c4f28df7e5642c575ab
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59841155"
---
# <a name="prepare-your-source-server-for-windows-server-essentials-migration1"></a>Подготовка исходного сервера для Windows Server Essentials migration1

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Чтобы обеспечить успешную миграцию параметров и данных с исходного сервера на конечный сервер, выполните следующие подготовительные действия.  
  
#### <a name="to-prepare-for-migration"></a>Подготовка к миграции  
  

1.  [Резервное копирование исходного сервера](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_BackUpYourSourceServerToPrepareForMigration)  
  
2.  [Установите последние пакеты обновления](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_InstallTheMostRecentServicePacksToPrepareForMigration)  
  
3.  [Оценка работоспособности исходного сервера](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_UseWindowsBestPracticeAnalyzer)  
  
4.  [Запустите средство подготовки миграции на исходном сервере](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_MPT)  
  
5.  [Создание плана для миграции бизнес приложений](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_PlanToMigrateLineOfBusinessApplications)  

1.  [Резервное копирование исходного сервера](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_BackUpYourSourceServerToPrepareForMigration)  
  
2.  [Установите последние пакеты обновления](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_InstallTheMostRecentServicePacksToPrepareForMigration)  
  
3.  [Оценка работоспособности исходного сервера](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_UseWindowsBestPracticeAnalyzer)  
  
4.  [Запустите средство подготовки миграции на исходном сервере](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_MPT)  
  
5.  [Создание плана для миграции бизнес приложений](../migrate/Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md#BKMK_PlanToMigrateLineOfBusinessApplications)  

  
###  <a name="BKMK_BackUpYourSourceServerToPrepareForMigration"></a> Резервное копирование исходного сервера  
 Перед началом миграции создайте резервную копию исходного сервера. Это поможет защитить данные от случайной утраты, если во время миграции произойдут неустранимые ошибки.  
  
##### <a name="to-back-up-the-source-server"></a>Чтобы создать резервную копию исходного сервера  
  
1.  Выполните полное резервное копирование исходного сервера. Дополнительные сведения о резервном копировании Windows Small Business Server 2011 Essentials, см. в разделе [Дополнительные сведения о настройке архивации сервера](https://technet.microsoft.com/library/server-backup-support-1.aspx).  
  
2.  Убедитесь, что резервное копирование выполнено успешно. Чтобы проверить целостность резервной копии, произвольно выберите несколько файлов из резервной копии, восстановите их в другом месте и убедитесь, что они совпадают с исходными.  
  
###  <a name="BKMK_InstallTheMostRecentServicePacksToPrepareForMigration"></a> Установите последние пакеты обновления  
 Необходимо установить последние обновления и пакеты обновлений на исходный сервер перед миграцией.  
  
###  <a name="BKMK_UseWindowsBestPracticeAnalyzer"></a> Оценка работоспособности исходного сервера  
 Важно оценить работоспособность исходного сервера перед началом миграции. Для проверки текущих обновлений, вывода отчета о работоспособности системы, а также запуска анализатора соответствия рекомендациям Windows Server используйте следующие процедуры.  
  
#### <a name="download-and-install-critical-and-security-updates"></a>Загрузка и установка критически важных обновлений и обновлений для системы безопасности  
 Установка критически важных обновлений и обновлений для системы безопасности на исходном сервере помогает обеспечить успешное выполнение миграции и защитить сеть в процессе миграции.  
  
###### <a name="to-check-for-the-latest-updates"></a>Проверка наличия новых обновлений  
  
1.  На исходном сервере щелкните **Пуск**, затем **Все программы**и **Центр обновления Windows**.  
  
2.  Щелкните ссылку **Проверка обновлений**.  
  
3.  При обнаружении обновлений щелкните элемент **Установить обновления**.  
  
#### <a name="check-the-alert-viewer-for-critical-errors"></a>Проверка сведений о критических ошибках в средстве просмотра оповещений  
 Сведения о критических ошибках можно проверить с помощью средства просмотра оповещений на панели мониторинга.  
  
#### <a name="run-the-windows-server-solutions-best-practices-analyzer"></a>Запуск анализатора соответствия рекомендациям Windows Server  
 Чтобы убедиться в отсутствии проблем с сервером, сетью и доменом перед началом миграции, можно запустить анализатор соответствия рекомендациям Windows Server. Анализатор соответствия рекомендациям собирает сведения о конфигурации из следующих источников:  
  
-   инструментарий управления Windows (WMI) Active Directory®;  
  
-   реестр;  
  
-   метабаза служб IIS.  
  
###### <a name="to-use-the-windows-server-solutions-bpa-to-analyze-your-source-server"></a>Анализ исходного сервера с помощью анализатора соответствия рекомендациям Windows Server  
  
1.  Скачайте и установите [Windows Server Solutions Best Practices Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=15556) в центре загрузки Майкрософт.  
  
2.  По окончании процесса загрузки нажмите **Пуск**, выберите пункт **Все программы**, а затем щелкните **Анализатор соответствия рекомендациям SBS**.  
  
    > [!NOTE]
    >  Перед сканированием сервера проверьте наличие обновлений.  
  
3.  В области навигации щелкните ссылку **Начать сканирование**.  
  
4.  На панели сведений введите метку сканирования и нажмите кнопку **Начать сканирование**. Эта метка содержит имя отчета о сканировании, например **SBS BPA Scan 1Jul2012**.  
  
5.  После завершения сканирования щелкните ссылку **Просмотреть отчет о сканировании соответствия рекомендациям**.  
  
 После сбора сведений о конфигурации сервера анализатор соответствия рекомендациям Windows Server проверяет правильность сведений, а также предоставляет администраторам список сведений и проблем, отсортированный по степени серьезности. Список содержит описание каждой проблемы, а также рекомендации или возможные решения. Доступно три типа отчетов.  
  
|Тип отчета|Описание|  
|-----------------|-----------------|  
|Отчеты-списки|Отчеты, представляемые в виде обычного списка.|  
|Древовидные отчеты|Отчеты, представляемые в виде иерархического списка.|  
|Прочие отчеты|Журнал времени выполнения и другие отчеты.|  
  
 Щелкните проблему в отчете, чтобы просмотреть ее описание и рекомендуемое решение. Не все проблемы, которые передаются в анализатор соответствия Рекомендациям Windows SBS 2011 Essentials влияют на миграцию, но вам следует устранить многие проблемы, возможно, чтобы обеспечить успешную миграцию.  
  
####  <a name="BKMK_SynchronizeTheSourceServerTimeWithAnExternalTimeSource"></a> Синхронизировать время исходного сервера с внешнего источника времени  
 Показатели времени исходного сервера и конечного сервера должны различаться максимум на пять минут, дата и часовой пояс должны быть одинаковы на обоих серверах. Если исходный сервер запущен на виртуальном компьютере, дата, время и часовой пояс сервера узла должны совпадать с данными исходного и конечного серверов. Для обеспечения успешной установки Windows Server Essentials, необходимо синхронизировать время исходного сервера с сервером протокола сетевого времени (NTP) в Интернете.  
  
###### <a name="to-synchronize-the-source-server-time-with-the-ntp-server"></a>Синхронизация времени исходного сервера с NTP-сервером  
  
1.  Войдите на исходный сервер с учетной записью и паролем администратора домена.  
  
2.  Щелкните **Пуск**, нажмите кнопку **Выполнить**, в текстовом поле введите **cmd** и нажмите клавишу ВВОД.  
  
3.  В командной строке введите syncfromflags: DOMHIER w32tm/config / reliable: не/Update, а затем нажмите клавишу ВВОД.  
  
4.  В командной строке введите net stop w32time и нажмите клавишу ВВОД.  
  
5.  В командной строке введите net start w32time и нажмите клавишу ВВОД.  
  
> [!IMPORTANT]
>  Во время установки Windows Server Essentials у вас есть возможность проверить время на целевом сервере и изменить его при необходимости. Убедитесь, что это время отличается от времени на исходном сервере не более чем на пять минут. После завершения установки конечный сервер синхронизируется с NTP-сервером. Все компьютеры, присоединенные к домену, в том числе исходный сервер, синхронизируются с конечным сервером, который принимает роль хозяина эмулятора основного контроллера домена (PDC).  
  
###  <a name="BKMK_MPT"></a> Запустите средство подготовки миграции на исходном сервере  
 Вы не можете выполнить установку в режиме миграции без предварительного запуска средства подготовки миграции на исходном сервере. Это средство позволяет подготовить исходный сервер и домен для миграции на Windows Server Essentials.  
  
> [!IMPORTANT]
>  Создайте архив исходного сервера перед запуском средства подготовки миграции. Изменения, внесенные в схему средством подготовки к миграции, являются необратимыми. При возникновении проблем в ходе миграции единственный путь возврата исходного сервера к состоянию, в котором он находился перед запуском средства — это восстановление архива в исходное расположение.  
  
 Для запуска средства подготовки к миграции необходимо входить в группу администраторов предприятия, группу администраторов схемы и группу администраторов домена.  
  
##### <a name="to-verify-that-you-have-the-appropriate-permissions-to-run-the-tool-on-the-source-server"></a>Чтобы убедиться в наличии соответствующих разрешений, следует запустить данное средство на исходном сервере  
  
1.  На исходном сервере нажмите кнопку **Пуск**, выберите пункт **Администрирование**, а затем щелкните значок **Active Directory — пользователи и компьютеры**.  
  
2.  В дереве консоли разверните свой домен и щелкните **Пользователи**.  
  
3.  Нажмите правой кнопкой мыши учетную запись администратора, которая используется для проведения миграции, а затем нажмите **Свойства**.  
  
4.  Перейдите на вкладку **Входит в состав** и проверьте, перечислены ли администраторы предприятия, схемы и домена в текстовом поле **Входит в состав**.  
  
5.  Если группы отсутствуют в списке, нажмите **Добавить**, а затем добавьте каждую группу.  
  
    > [!NOTE]
    >  -   Если служба Netlogon не запущена, может возникнуть ошибка разрешений.  
    > -   Для того чтобы изменения вступили в силу, необходимо выйти из учетной записи на сервере и войти в нее повторно.  
  
     Вы можете использовать последнюю версию агента обновления Windows, чтобы обеспечить правильную работу процесса обновления сервера.  
  
 Вы можете использовать последнюю версию агента обновления Windows, чтобы обеспечить правильную работу процесса обновления сервера.  
  
 Перед установкой агента обновления Windows на исходном сервере, необходимо сначала установить Windows PowerShell 2.0 и Microsoft Baseline Configuration Analyzer 2.0.  
  
-   Чтобы скачать и установить Windows PowerShell 2.0, см. в разделе [статье 968929](https://go.microsoft.com/fwlink/p/?LinkId=241483) в базе знаний Майкрософт.  
  
-   Чтобы скачать и установить Microsoft Baseline Configuration Analyzer 2.0, см. в разделе [Microsoft Baseline Configuration Analyzer 2.0](https://go.microsoft.com/fwlink/p/?LinkId=241484) в центре загрузки Майкрософт.  
  
-   Чтобы загрузить и установить последнюю версию агента обновления Windows, см. в разделе [статье 949104](https://go.microsoft.com/fwlink/p/?LinkId=237493) в базе знаний Майкрософт.  
  
##### <a name="to-install-and-run-the-migration-preparation-tool-on-the-source-server"></a>Установка и запуск средства подготовки миграции на исходном сервере  
  
1.  Вставьте диск Windows Server Essentials DVD1 в DVD-дисковод на исходном сервере.  
  
2.  Откройте Windows Explorer, перейдите в папку **\support\tools** на DVD и дважды щелкните файл **sourcetool.msi**.  
  
    > [!NOTE]
    >  -   Если средство подготовки миграции уже установлена на сервере, запустите его из меню **Пуск**.  
    > -   Для обеспечения максимально правильного выполнения миграции компания рекомендуется всегда выбирать самое последнее обновление.  
  
     Мастер выполнит установку средства подготовки к миграции на исходный сервер. По завершении установки средство подготовки к миграции автоматически запустится и установит последние обновления.  
  
3.  В средстве подготовки миграции установите флажок **Архив сохранен. Можно продолжать выполнение миграции**, а затем щелкните **Далее**.  
  
    > [!WARNING]
    >  Если появится сообщение об ошибке, связанное с установкой исправления, см. метод 2: Переименование папки Catroot2 в [статье 822798](https://go.microsoft.com/FWLink/p/?LinkID=118672) в базе знаний Майкрософт.  
  
     Средство подготовки миграции готовит исходный домен к миграции, расширяя схему Active Directory. После завершения задачи нажмите кнопку **Далее** для продолжения.  
  
4.  После подготовки исходного домена средство подготовки миграции проверяет исходный сервер для определения двух типов потенциальных проблем.  
  
    -   **Ошибки** проблемы, обнаруженные на исходном сервере, которые могут блокировать миграцию или вызывать ошибку миграции. Следуйте инструкциям в сообщении об ошибке, чтобы устранить проблему, а затем нажмите кнопку **Повторить сканирование**.  
  
    -   **Предупреждения** проблемы, обнаруженные на исходном сервере, которые могут вызвать функциональные неполадки во время миграции. Настоятельно рекомендуется следовать инструкциям в сообщении об ошибке, чтобы устранить проблемы перед продолжением миграции.  
  
     После устранения или подтверждения всех проблем нажмите кнопку **Далее**.  
  
5.  В средстве подготовки миграции нажмите кнопку **Готово**.  
  
6.  По завершении работы средства подготовки миграции вам может быть предложено перезагрузить исходный сервер, прежде чем начать переход на Windows Server Essentials.  
  
> [!NOTE]
>  Необходимо выполнить при успешном выполнении средства подготовки миграции на исходном сервере в течение двух недель после установки Windows Server Essentials на конечном сервере. В противном случае установка Windows Server Essentials на конечном сервере будет заблокирована. В этом случае запустите средство подготовки миграции на исходном сервере еще раз.  
  
###  <a name="BKMK_PlanToMigrateLineOfBusinessApplications"></a> Создание плана для миграции бизнес приложений  
 Бизнес-приложения (LOB, line-of-business application) — это компьютерные приложения, жизненно необходимые для функционирования бизнеса. К ним относятся приложения в области бухгалтерского учета, управления логистическими цепочками и планирования ресурсов.  
  
 При планировании миграции бизнес-приложений необходимо проконсультироваться с поставщиком бизнес-приложения для определения подходящего метода миграции каждого из них. Также необходимо подготовить носители, используемые для установки бизнес-приложений на целевом сервере.  
  
> [!NOTE]
>  Если вы использовали Windows Small Business Server 2011 Essentials SDK для разработки настраиваемых работоспособности системы или оповещения надстройки и вы хотите продолжить использование надстройки с Windows Server Essentials, необходимо также обновить надстройку и развернуть ее на целевом сервере.  
  