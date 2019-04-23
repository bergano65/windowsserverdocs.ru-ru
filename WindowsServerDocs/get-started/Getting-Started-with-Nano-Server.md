---
title: Установка сервера Nano Server
description: Чистая установка, обновление, перенос и оценка сервера Nano Server
ms.prod: windows-server-threshold
ms.service: na
manager: dougkim
ms.technology: server-nano
ms.date: 09/06/2017
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2c2fa45b-6f3b-4663-b421-2da6ecc463bf
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 295402a3bcdcec07025ad1f803cddd47127baa8d
ms.sourcegitcommit: e84e328c13a701e8039b16a4824a6e58a6e59b0b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/22/2018
ms.locfileid: "4133740"
---
# Установка сервера Nano Server

>Область применения: Windows Server2016

> [!IMPORTANT]
> Начиная с Windows Server версии 1709, сервер Nano Server будет доступен только в качестве [базового образа ОС контейнера](/virtualization/windowscontainers/quick-start/using-insider-container-images#install-base-container-image). Ознакомьтесь с разделом [Изменения сервера Nano Server](nano-in-semi-annual-channel.md), чтобы узнать, что это означает. 

В Windows Server2016 доступен новый вариант установки: Nano Server. Nano Server: это удаленно управляемая серверная ОС, оптимизированная для частных облаков и центров обработки данных. Этот вариант аналогичен Windows Server в режиме основных серверных компонентов, однако значительно меньше по размеру, не имеет функций локального входа и поддерживает только 64-разрядные приложения, средства и агенты. В сравнении с Windows Server она занимает гораздо меньше места на диске, намного быстрее запускается и требует на порядок меньше обновлений и перезапусков. При этом сам перезапуск выполняется гораздо быстрее. Вариант установки Nano Server доступен для выпусков Standard и Datacenter продукта Windows Server2016.  

Nano Server оптимально подходит для различных сценариев:  
  
-   В качестве "вычислительного" узла для виртуальных машин Hyper-V, включенных или не включенных в кластеры.  
  
-   В качестве узла хранения для масштабируемого файлового сервера.  
  
-   В качестве DNS-сервера.  
  
-   В качестве веб-сервера, на котором выполняются службы IIS.  
  
-   В качестве узла для приложений, разработанных с использованием шаблонов облачных приложений и выполняемых в контейнере или гостевой операционной системе виртуальной машины.  
  
## Важные отличия сервера Nano Server

Сервер Nano Server оптимизирован для работы в качестве облегченной операционной системы для запуска созданных для облака приложений на основе контейнеров и микрослужб или в качестве гибкого и экономичного узла центра обработки данных существенно меньшего размера. Поэтому существуют важные различия между установкой сервера Nano Server и установкой основных серверных компонентов или сервера с возможностями рабочего стола.

- Сервер Nano Server работает без монитора, в нем нет возможности локального входа в систему или запуска графического пользовательского интерфейса.
- Поддерживаются только 64-разрядные приложения, средства и агенты.
- Сервер Nano Server невозможно использовать в качестве контроллера домена Active Directory.
- Групповая политика не поддерживается. Тем не менее можно использовать [настройку требуемого состояния](https://msdn.microsoft.com/powershell/dsc/nanoDsc) для масштабного применения параметров.
- Сервер Nano Server не может использовать прокси-сервер для доступа к Интернету.
- Объединение сетевых карт (в частности, балансировка нагрузки и отработка отказа или LBFO) не поддерживается. Вместо этого поддерживается объединение внедренных коммутаторов (SET).
- System Center Configuration Manager и System Center Data Protection Manager не поддерживаются.
- Командлеты анализатора соответствия рекомендациям (BPA) и интеграция BPA с диспетчером серверов не поддерживаются.
- Сервер Nano Server не поддерживает виртуальные адаптеры шины (HBA).
- Сервер Nano Server не нужно активировать с помощью ключа продукта. Функционируя как узел Hyper-V, Nano Server не поддерживает [автоматическую активацию виртуальной машины](https://technet.microsoft.com/library/dn303421%28v=ws.11%29.aspx) (AVMA). Виртуальные машины, которые работают на узле Nano Server, можно активировать при помощи [службы управления ключами](https://technet.microsoft.com/library/jj612867(v=ws.11).aspx) (KMS) с лицензионным ключом универсального тома или воспользовавшись [активацией с помощью Active Directory](https://technet.microsoft.com/library/dn502534(v=ws.11).aspx).
- Версия Windows PowerShell в составе сервера Nano Server имеет важные отличия. Сведения о них см в разделе [PowerShell для Nano Server](PowerShell-on-Nano-Server.md).
- Сервер Nano Server поддерживается только в модели Current Branch for Business (CBB), выпуск Long-Term Servicing Branch (LTSB) для сервера Nano Server сейчас отсутствует. Дополнительные сведения см. в следующих подразделах.

### Current Branch for Business
Сервер Nano обслуживается по более активной модели, Current Branch for Business (CBB), чтобы предоставлять поддержку пользователям, которые работают в "облачном темпе" — используют циклы быстрой разработки. В этой модели обновления компонентов сервера Nano Server выходят два-три раза в год. В этой модели необходимо, чтобы программа [Software Assurance](https://www.microsoft.com/en-us/licensing/licensing-programs/software-assurance-default.aspx) для серверов Nano Server была развернута и использовалась в рабочей среде. Чтобы сохранить поддержку, администраторы должны использовать один из двух последних выпусков CBB. Но эти выпуски не обновляют существующие развертывания автоматически; администраторы должны при первой возможности вручную установить новый выпуск CBB. Некоторые дополнительные сведения см. в разделе [Новый вариант обслуживания Current Branch for Business для Windows Server2016](https://blogs.technet.microsoft.com/windowsserver/2016/07/12/windows-server-2016-new-current-branch-for-business-servicing-option/).

Варианты установки основных серверных компонентов или сервера с возможностями рабочего стола обслуживаются по [модели Long-Term Servicing Branch (LTSB)](https://support.microsoft.com/lifecycle#gp%2Fgp_msl_policy), которая подразумевает пять лет основной и пять лет продленной фазы поддержки.

## Сценарии установки

### Оценка
Вы можете получить пробную версию Windows Server, лицензированную на 180 дней, на странице [оценки Windows Server](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). Чтобы оценить Nano Server, выберите параметр **Nano Server | 64-разрядный исполняемый файл**, а затем вернитесь к разделу [Краткое руководство по серверу Nano Server](Nano-Server-Quick-Start.md) или [Развертывание сервера Nano Server](Deploy-Nano-Server.md) для начала работы.

### Чистая установка
Поскольку сервер Nano устанавливается путем настройки виртуального жесткого диска, чистая установка является самым быстрым и простым способом развертывания.

- Чтобы быстро приступить к работе с базовым развертыванием Nano Server, используя DHCP для получения IP-адреса, см. статью [Краткое руководство по серверу Nano Server](Nano-Server-Quick-Start.md) 
- Если вы уже знакомы с основами использования Nano Server, обратитесь к более подробным разделам, начиная с [Развертывание сервера Nano Server](Deploy-Nano-Server.md), где приведен полный набор инструкций по настройке образов, работе с доменами, установке пакетов для ролей сервера и другим компонентам, работающим как в сети, так и в автономном режиме, и многие другие сведения.

> [!IMPORTANT]  
> Завершив работу программы установки, сразу после установки всех нужных ролей сервера и функций нужно проверить наличие обновлений для Windows Server2016 и установить их. Для Nano Server ознакомьтесь с разделом "Управление обновлениями на сервере Nano Server" статьи [Управление сервером Nano Server](Manage-Nano-Server.md).

### Обновление с более ранней версии:
Поскольку Nano Server является новой функцией в Windows Server2016, не существует способа для обновления предыдущих версий операционной системы до Nano Server.

### Миграция
Поскольку Nano Server является новой функцией в Windows Server2016, не существует способа для миграции из предыдущих версий операционной системы на Nano Server.
  
-------------------------------------
Если требуется другой вариант установки, можно [вернуться на главную страницу Windows Server2016](windows-server-2016.md). 

  


 