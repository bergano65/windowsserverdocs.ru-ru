---
title: Выпуски и продукты Windows Server 2016
description: Описание различий между выпусками Windows Server Standard и Windows Server Datacenter.
ms.prod: windows-server
ms.date: 10/04/2019
ms.technology: server-general
ms.topic: article
ms.assetid: c5ca3bfe-7ced-49f6-a932-80cab33f419e
author: jasongerend
ms.author: jgerend
manager: dongill
ms.localizationpriority: medium
ms.openlocfilehash: f2940e5ad75fab90f717284eabafd555573cab35
ms.sourcegitcommit: e92a78f8d307200e64617431a701b9112a9b4e48
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/05/2019
ms.locfileid: "71973849"
---
# <a name="comparison-of-standard-and-datacenter-editions-of-windows-server-2016"></a>Сравнение выпусков Windows Server 2016 Standard и Datacenter

> Область применения. Windows Server 2016
  
## <a name="locks-and-limits"></a>Блокировки и ограничения

| Блокировки и ограничения | Windows Server 2016 Standard | Windows Server 2016 Datacenter |
| ------------------- |---------- | --------------------------- |  
| Максимальное число пользователей | По числу клиентских лицензий   | По числу клиентских лицензий     |
| Максимальное число подключений SMB | 16 777 216      | 16 777 216          |
| Максимальное число подключений RRAS| Без ограничений       | Без ограничений         |
| Максимальное число подключений IAS | 2 147 483 647   | 2 147 483 647        |
| Максимальное число подключений RDS | 65 535           | 65 535             |
| Максимальное число сокетов в 64-разрядной версии | 64     | 64                |
| Максимальное число ядер | Без ограничений       | Без ограничений      |
| Максимальный объем ОЗУ             | 24 ТБ           | 24 ТБ             |
| Можно использовать как гостевую службу виртуализации | Да; 2 виртуальные машины и один узел Hyper-V на лицензию | Да; <strong>неограниченное количество виртуальных машин</strong> и один узел Hyper-V на лицензию. |
| Сервер может присоединиться к домену | Да            | Да                |
| Защита периметра сети или брандмауэр | Нет     | Нет                 |
| DirectAccess            | Да             | Да                |
| DLNA-кодеки и потоковая передача мультимедиа в Интернете | Да, если продукт установлен как сервер с возможностями рабочего стола | Да, если продукт установлен как сервер с возможностями рабочего стола |

## <a name="server-roles"></a>Роли сервера

| Доступны роли Windows Server     | Службы ролей | Windows Server 2016 Standard | Windows Server 2016 Datacenter |  
| -------------------                | ----------    | ----------                   | ---------------------------    |  
| Службы сертификатов Active Directory|              | Да                          | Да                            |
| Доменные службы Active Directory    |               | Да                          | Да                            |
| Службы федерации Active Directory (AD FS)|               | Да                          | Да                            |
| Службы Active Directory облегченного доступа к каталогам [AD LDS]| |Да|Да|
| Службы управления правами Active Directory (AD RMS)| |Да|Да|
| Аттестация работоспособности устройства| |Да|Да|
| DHCP-сервер| |Да|Да|
| DNS-сервер| |Да|Да|
| Факс-сервер| |Да|Да|
| Файловые службы и службы хранилища|Файловый сервер|Да|Да|
| Файловые службы и службы хранилища|Служба BranchCache для сетевых файлов|Да|Да|
| Файловые службы и службы хранилища|Дедупликация данных|Да|Да|
| Файловые службы и службы хранилища|Пространства имен DFS|Да|Да|
| Файловые службы и службы хранилища|Репликация DFS|Да|Да|
| Файловые службы и службы хранилища|Диспетчер ресурсов файлового сервера|Да|Да|
| Файловые службы и службы хранилища|Служба агента VSS файлового сервера|Да|Да|
| Файловые службы и службы хранилища|Целевой сервер iSCSI|Да|Да|
| Файловые службы и службы хранилища|Поставщик хранилища цели iSCSI|Да|Да|
| Файловые службы и службы хранилища|Сервер для NFS|Да|Да|
| Файловые службы и службы хранилища|рабочие папки|Да|Да|
| Файловые службы и службы хранилища|Службы хранения|Да|Да|
| Служба защиты узла| |Да|Да|
| Hyper-V| |Да|Да; <strong>в том числе экранированные виртуальные машины</strong>.|
| Службы MultiPoint| |Да|Да|
| Сетевой контроллер| |Нет| <strong>Да</strong> |
| Службы политики сети и доступа| |Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
| Службы печати и документов| |Да|Да|
| Удаленный доступ| |Да|Да|
| Службы удаленных рабочих столов| |Да|Да|
| Службы активации корпоративных лицензий| |Да|Да|
| Веб-службы (IIS)| |Да|Да|
| Службы развертывания Windows| |Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
| Режим Windows Server Essentials| |Да|Да|
| Службы Windows Server Update Services| |Да|Да|

## <a name="features"></a>Возможности

|Компоненты Windows Server, доступные для установки с помощью диспетчера серверов (или PowerShell)|Windows Server 2016 Standard|Windows Server 2016 Datacenter|  
|-------------------|----------|---------------------------|  
|.NET Framework 3.5|Да|Да|
|.NET Framework 4.6|Да|Да|
|Фоновая интеллектуальная служба передачи (BITS)|Да|Да|
|Шифрование диска BitLocker|Да|Да|
|Сетевая разблокировка BitLocker|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|BranchCache|Да|Да|
|Клиент для NFS|Да|Да|
|Контейнеры|Да (контейнеры Windows — без ограничений; контейнеры Hyper-V — до двух)|Да (все типы контейнеров — без ограничений)|
|Мост для центра обработки данных|Да|Да|
|Direct Play|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Enhanced Storage|Да|Да|
|Отказоустойчивая кластеризация|Да|Да|
|Управление групповой политикой|Да|Да|
|Поддержка защиты узла Hyper-V|Нет|<strong>Да</strong> |
|Качество обслуживания ввода-вывода|Да|Да|
|Внедряемое веб-ядро служб IIS|Да|Да|
|Клиент печати через Интернет|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|IPAM-сервер|Да|Да|
|Службы iSNS-сервера|Да|Да|
|Монитор порта LPR|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Расширение IIS OData для управления|Да|Да|
|Media Foundation|Да|Да|
|Очередь сообщений|Да|Да|
|Multipath I/O;|Да|Да|
|Соединитель MultiPoint|Да|Да|
|Балансировка сетевой нагрузки|Да|Да|
|Протокол однорангового разрешения имен (PNRP)|Да|Да|
|Quality Windows Audio Video Experience (qWave)|Да|Да|
|Пакет администрирования диспетчера подключений RAS|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Удаленная помощь|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|удаленное разностное сжатие;|Да|Да|
|RSAT|Да|Да|
|RPC-через-HTTP-прокси|Да|Да|
|Коллекция событий установки и загрузки|Да|Да|
|простые службы TCP/IP;|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Поддержка протоколов общего доступа к файлам SMB 1.0 и CIFS|Установлено|Установлено|
|Ограничение пропускной способности SMB|Да|Да|
|SMTP-сервер|Да|Да|
|Служба SNMP|Да|Да|
|Подсистема балансировки нагрузки программного обеспечения|Нет| <strong>Да</strong> |
|Реплика хранилища|Нет|Да|
|Клиент Telnet|Да|Да|
|TFTP-клиент|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Средства экранирования виртуальных машин для управления структурой|Да|Да|
|Перенаправитель WebDAV|Да|Да|
|Биометрическая платформа Windows|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Компоненты Защитника Windows|Установлено|Установлено|
|Windows Identity Foundation 3.5|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Внутренняя база данных Windows|Да|Да|
|Windows PowerShell|Установлено|Установлено|
|Служба активации процессов Windows|Да|Да|
|Служба Windows Search|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Система архивации данных Windows Server|Да|Да|
|Средства миграции Windows Server|Да|Да|
|Стандартизированное управление хранилищами Windows|Да|Да|
|Фильтры Windows TIFF IFilter|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|
|Расширение IIS WinRM|Да|Да|
|WINS-сервер|Да|Да|
|Служба беспроводной локальной сети|Да|Да|
|поддержка WoW64.|Установлено|Установлено|
|Средство просмотра XPS|Да, если продукт установлен как сервер с возможностями рабочего стола|Да, если продукт установлен как сервер с возможностями рабочего стола|

|Общедоступные компоненты|Windows Server 2016 Standard|Windows Server 2016 Datacenter|  
|-------------------|----------|---------------------------|  
|Анализатор соответствия рекомендациям|Да|Да|
|Прямой доступ|Да|Да|
|Динамическая память (в виртуализации)|Да|Да|
|Горячее добавление и удаление оперативной памяти|Да|Да|
|Microsoft Management Console (MMC)|Да|Да|
|Минимальный интерфейс сервера|Да|Да|
|Балансировка сетевой нагрузки|Да|Да|
|Windows PowerShell|Да|Да|
|Установка основных серверных компонентов|Да|Да|
|Вариант установки Nano Server|Да|Да|
|Диспетчер серверов|Да|Да|
|SMB Direct и SMB через RDMA|Да|Да|
| Программно-определяемая сеть | Нет | <strong>Да</strong> |
|Реплика хранилища | Нет | <strong>Да</strong> |
|Дисковые пространства|Да|Да|
|Локальные дисковые пространства|Нет| <strong>Да</strong> |
|Службы активации корпоративных лицензий|Да|Да|
|Интеграция со службами теневого копирования (VSS)|Да|Да|
|Службы Windows Server Update Services|Да|Да|
|Диспетчер системных ресурсов Windows|Да|Да|
|Учет серверных лицензий|Да|Да|
|Наследование активаций|Как гость, если служба размещена на выпуске Datacenter| <strong>Узел или гость</strong> |
|рабочие папки|Да|Да|

