---
title: Управление серверами с помощью центра администрирования Windows
description: Управление серверами с помощью центра администрирования Windows (проект Хонолулу)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 11/21/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: ddc8eea67cde9d6677836af1201e169c911e77e0
ms.sourcegitcommit: 083ff9bed4867604dfe1cb42914550da05093d25
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2020
ms.locfileid: "75950480"
---
# <a name="manage-servers-with-windows-admin-center"></a>Управление серверами с помощью центра администрирования Windows

>Относится к Windows Admin Center, ознакомительной версии Windows Admin Center

> [!Tip]
> Только начинаете знакомство с Windows Admin Center?
> [Скачайте или Узнайте больше о центре администрирования Windows](../overview.md).

## <a name="managing-windows-server-machines"></a>Управление компьютерами с Windows Server

Вы можете добавить отдельные серверы под управлением Windows Server 2012 или более поздней версии в центр администрирования Windows для управления сервером с помощью исчерпывающего набора средств, включая сертификаты, устройства, события, процессы, роли и компоненты, обновления, виртуальные машины и многое другое.

![Экран "Обзор подключения к серверу"](../media/manage-servers/server-overview.png)

## <a name="adding-a-server-to-windows-admin-center"></a>Добавление сервера в центр администрирования Windows

Чтобы добавить сервер в центр администрирования Windows, выполните следующие действия.

1. Щелкните **+ Добавить** в разделе все подключения.
2. Выберите Добавление соединения с **сервером**.
3. Введите имя сервера и при появлении запроса укажите учетные данные для использования.
4. Нажмите кнопку **Отправить** , чтобы завершить работу.

Сервер будет добавлен в список подключений на странице обзора. Щелкните его, чтобы подключиться к серверу.

> [!NOTE]
> В центре администрирования Windows также можно добавить [отказоустойчивые кластеры](manage-failover-clusters.md) или кластеры с [поддержкой Hyper-](manage-hyper-converged.md) в качестве отдельного подключения.

## <a name="tools"></a>Средства

Для подключений к серверу доступны следующие средства.

| Средство | Описание |
| ---- | ----------- |
| [Обзор](#overview) | Просмотр сведений о сервере и контроль состояния сервера |
| [Active Directory](#active-directory-preview) | Управление Active Directory |
| [Azure Backup](#backup) | Просмотр и настройка Azure Backup |  
| [Сертификаты](#certificates) | Просмотр и изменение сертификатов |
| [Контейнеры](#containers) | Просмотр контейнеров |
| [Устройства](#devices) | Просмотр и изменение устройств |
| [DHCP](#dhcp) | Просмотр конфигурации DHCP-сервера и управление ею |
| [DNS](#dns) | Просмотр и управление конфигурацией DNS-сервера |
| [События](#events) | Просмотреть события |
| [Файлы](#files) | Обзор файлов и папок |
| [Брандмауэр](#firewall). | Просмотр и изменение правил брандмауэра |
| [Установленные приложения](#installed-apps) | Просмотр и удаление установленных приложений |
| [Локальные пользователи и группы](#local-users-and-groups) | Просмотр и изменение локальных пользователей и групп |
| [Сеть](#network) | Просмотр и изменение сетевых устройств |
| [Мониторинг пакетов](https://aka.ms/wac1908) | Мониторинг сетевых пакетов |
| [Системный монитор](https://aka.ms/perfmon-blog) | Просмотр счетчиков производительности и отчетов |
| [PowerShell](#powershell) | Взаимодействие с сервером с помощью PowerShell |
| [Процессы](#processes) | Просмотр и изменение запущенных процессов |
| [Registry](#registry) | Просмотр и изменение записей реестра |
| [Удаленный рабочий стол](#remote-desktop) | Взаимодействие с сервером с помощью удаленный рабочий стол |
| [Роли и компоненты](#roles-and-features) | Просмотр и изменение ролей и компонентов |
| [Запланированные задачи](#scheduled-tasks) | Просмотр и изменение запланированных задач |
| [Службы](#services) | Просмотр и изменение служб |
| [Параметры](#settings) | Просмотр и изменение служб |
| [Хранилище](#storage) | Просмотр и изменение запоминающих устройств |
| [Служба миграции хранилища](#storage-migration-service) | Перенос серверов и файловых ресурсов в Azure или Windows Server 2019 |
| [Реплика хранилища](#storage-replica) | Использование реплики хранилища для управления репликацией хранилища "сервер-сервер" |
| [Системная аналитика](#system-insights) | System Insights позволяет получить представление о работе сервера. |
| [Обновления](#updates) | Просмотреть установленные и проверить новые обновления |
| [Виртуальные машины](manage-virtual-machines.md) | Просмотр виртуальных машин и управление ими |
| [Виртуальные коммутаторы](#virtual-switches) | Просмотр виртуальных коммутаторов и управление ими |

## <a name="overview"></a>Обзор

**Обзор** позволяет просматривать текущее состояние ЦП, памяти и производительности сети, а также выполнять операции и изменять параметры на целевом компьютере или сервере.

### <a name="features"></a>Возможности

В обзоре диспетчер сервера поддерживаются следующие функции:

- Просмотр сведений о сервере
- Просмотр активности ЦП
- Просмотр активности памяти
- Просмотр сетевых операций
- Перезапуск сервера
- Завершение работы сервера
- Включить метрики диска на сервере
- Изменение идентификатора компьютера на сервере
- Просмотрите IP-адрес контроллера BMC с помощью гиперссылки (требуется BMC-совместимая с IPMI).

[**Просмотр отзывов и предлагаемых функций для обзора сервера**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BOverview%5D).

## <a name="active-directory-preview"></a>Active Directory (Предварительная версия)

**Active Directory** является ранней предварительной версией, доступной в [веб-канале расширений](../configure/using-extensions.md).

### <a name="features"></a>Возможности

Доступны следующие возможности управления Active Directory:

- создание пользователя;
- Создание группы
- Поиск пользователей, компьютеров и групп
- Область сведений для пользователей, компьютеров и групп при выборе в сетке
- Глобальные действия с сеткой пользователи, компьютеры и группы (включение и отключение, удаление)
- Сброс пароля пользователя
- Пользовательские объекты: Настройка основных свойств & членства в группах
- Объекты компьютеров: Настройка делегирования для одного компьютера
- Объекты групп: Управление членством (Добавление или удаление пользователя за раз)  

[**Просмотрите Отзывы и предлагаемые функции для Active Directory**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BActive%20Directory%5D).

## <a name="backup"></a>"Резервная копия"

**Резервное копирование** позволяет защитить сервер Windows Server от повреждений, атак или аварий путем резервного копирования сервера непосредственно на Microsoft Azure.
[Дополнительные сведения о Azure Backup.](https://aka.ms/windows-admin-center-backup)

[Оставить отзыв о резервном копировании в центре администрирования Windows](https://aka.ms/backup-wac-feedback)

### <a name="features"></a>Возможности

В резервном копировании поддерживаются следующие возможности.

- Просмотр сведений о состоянии службы архивации Azure
- Настройка элементов и расписания архивации
- Запуск или завершение задания резервного копирования
- Просмотр журнала заданий резервного копирования и состояния
- Просмотр точек восстановления и восстановление данных
- Удаление данных резервных копий

## <a name="certificates"></a>Сертификаты

**Сертификаты** позволяют управлять хранилищами сертификатов на компьютере или сервере.

### <a name="features"></a>Возможности

В сертификатах поддерживаются следующие возможности.

- Обзор и поиск существующих сертификатов
- Просмотр сведений о сертификате
- Экспорт сертификатов
- Обновление сертификатов
- Запросить новые сертификаты
- Удаление сертификатов

[**Просмотр отзывов и предлагаемых функций для сертификатов**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BCertificates%5D).

## <a name="containers"></a>Контейнеры

**Контейнеры** позволяют просматривать контейнеры на узле контейнера Windows Server. В случае с контейнером Windows Server Core можно просматривать журналы событий и получать доступ к интерфейсу командной строки контейнера.

[**Просмотр отзывов и предлагаемых функций для контейнеров**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BContainers%5D).

## <a name="devices"></a>"Устройства"

**Устройства** позволяют управлять подключенными устройствами на компьютере или сервере.

### <a name="features"></a>Возможности

В устройствах поддерживаются следующие функции:

- Просмотр и поиск устройств
- просмотр сведений об устройстве;
- Отключение устройства
- Обновление драйвера на устройстве

[**Просмотр отзывов и предлагаемых функций для устройств**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BDevices%5D).

## <a name="dhcp"></a>DHCP

**DHCP** позволяет управлять подключенными устройствами на компьютере или сервере.

### <a name="features"></a>Возможности

- Создание, Настройка и Просмотр областей IPV4 и IPV6
- Создание исключений адресов и настройка начального и конечного IP-адресов
- Создание резервирования адресов и настройка MAC-адреса клиента (IPV4), DUID и IAID (IPV6)

[**Просмотрите Отзывы и предлагаемые функции для DHCP**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BDHCP%5D).

## <a name="dns"></a>Служба доменных имен (DNS)

**Служба DNS** позволяет управлять подключенными устройствами на компьютере или сервере.

### <a name="features"></a>Возможности

- Просмотр сведений о зонах прямого просмотра DNS, зонах обратного просмотра и записях DNS
- Создание зон прямого просмотра (первичной, вторичной или заглушки) и Настройка свойств зоны прямого просмотра
- Создание записей DNS типа "узел (A, AAAA)", CNAME или MX
- Настройка свойств записей DNS
- Создание зон обратного просмотра IPV4 и IPV6 (первичная, вторичная и заглушка), Настройка свойств зоны обратного просмотра
- Создание записей DNS типа PTR, CNAME в зоне обратного просмотра.

[**Просмотрите Отзывы и предлагаемые функции для DHCP**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BDNS%5D).

## <a name="events"></a>Мероприятия

**События** позволяют управлять журналами событий на компьютере или сервере.

### <a name="features"></a>Возможности

В событиях поддерживаются следующие функции.

- Просмотр и поиск событий
- Просмотр сведений о событии
- Удалить события из журнала
- Экспорт событий из журнала

[**Просмотр отзывов и предлагаемых функций для событий**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BEvents%5D).

## <a name="files"></a>Файлы

**Файлы** позволяют управлять файлами и папками на компьютере или сервере.

### <a name="features"></a>Возможности

В файлах поддерживаются следующие возможности.

- Обзор файлов и папок
- Поиск файла или папки
- Создание папки
- Удаление файла или папки
- Скачивание файла или папки
- Отправка файла или папки
- Переименование файла или папки
- Извлечение ZIP-файла
- Просмотр свойств файла или папки
- Добавление, изменение и удаление файловых ресурсов
- Изменение разрешений пользователя и группы на файловые ресурсы

[**Просмотр отзывов и предлагаемых функций для файлов**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BFiles%5D).

## <a name="firewall"></a>Брандмауэр

**Брандмауэр** позволяет управлять параметрами брандмауэра и правилами на компьютере или сервере.

### <a name="features"></a>Возможности

В брандмауэре поддерживаются следующие возможности.

- Просмотр обзора параметров брандмауэра
- Просмотр входящих правил брандмауэра
- Просмотр исходящих правил брандмауэра
- Поиск правил брандмауэра
- Просмотр сведений о правиле брандмауэра
- Создание нового правила брандмауэра
- Включение или отключение правила брандмауэра
- Удаление правила брандмауэра
- Изменение свойств правила брандмауэра

[**Просмотр отзывов и предлагаемых функций для брандмауэра**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BFirewall%5D).

## <a name="installed-apps"></a>Установленные приложения

**Установленные** приложения позволяют перечислять и удалять установленные приложения.

[**Просмотр отзывов и предлагаемых функций для установленных приложений**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BInstalled%20Apps%5D).

## <a name="local-users-and-groups"></a>Локальные пользователи и группы

**Локальные пользователи и группы** позволяют управлять группами безопасности и пользователями, которые существуют локально на компьютере или сервере.

### <a name="features"></a>Возможности

В оснастке "Локальные пользователи и группы" поддерживаются следующие функции:

- Просмотр и поиск пользователей и групп
- Создание нового пользователя или группы
- Управление членством пользователя в группах
- Удаление пользователя или группы
- Изменяет пароль пользователя
- Изменение свойств пользователя или группы

[**Просмотр отзывов и предлагаемых функций для локальных пользователей и групп**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BLocal%20users%20and%20Groups%5D)

## <a name="network"></a>Network

**Сеть** позволяет управлять сетевыми устройствами и параметрами на компьютере или сервере.

### <a name="features"></a>Возможности

В сети поддерживаются следующие функции:

- Обзор и поиск существующих сетевых адаптеров
- Просмотр сведений о сетевом адаптере
- Изменение свойств сетевого адаптера
- Создание [сетевого адаптера Azure (функция предварительной версии)](https://blogs.technet.microsoft.com/networking/2018/09/05/azurenetworkadapter/)

[**Просмотр отзывов и предлагаемых функций для сети**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BNetwork%5D)

## <a name="powershell"></a>PowerShell

**PowerShell** позволяет взаимодействовать с компьютером или сервером через сеанс PowerShell.

### <a name="features"></a>Возможности

В PowerShell поддерживаются следующие функции:

- Создание интерактивного сеанса PowerShell на сервере
- Отключение от сеанса PowerShell на сервере

[**Просмотр отзывов и предлагаемых функций для PowerShell**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BPowerShell%5D)

## <a name="processes"></a>Процессы

**Процессы** позволяют управлять выполняющимися процессами на компьютере или сервере.

### <a name="features"></a>Возможности

В процессах поддерживаются следующие функции:

- Обзор и поиск выполняющихся процессов
- Просмотр сведений о процессе
- Запуск процесса
- Завершение процесса
- Создание дампа процесса
- Поиск дескрипторов процессов

[**Просмотр отзывов и предлагаемых функций для процессов**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BProcesses%5D).

## <a name="registry"></a>Реестр

**Реестр** позволяет управлять разделами и значениями реестра на компьютере или сервере.

### <a name="features"></a>Возможности

В реестре поддерживаются следующие возможности.

- Обзор разделов и значений реестра
- Добавление или изменение значений реестра
- Удаление значений реестра

[**Просмотрите Отзывы и предлагаемые функции для реестра**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BRegistry%5D).

## <a name="remote-desktop"></a>Удаленный рабочий стол

**Удаленный рабочий стол** позволяет взаимодействовать с компьютером или сервером через интерактивный сеанс рабочего стола.

### <a name="features"></a>Возможности

В удаленный рабочий стол поддерживаются следующие функции:

- Запуск интерактивного сеанса удаленного рабочего стола
- Отключение от сеанса удаленного рабочего стола
- Отправка нажатий клавиш Ctrl + Alt + Del в сеанс удаленного рабочего стола

[**Просмотрите Отзывы и предлагаемые функции для удаленный рабочий стол**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BRemote%20Desktop%5D).

## <a name="roles-and-features"></a>Роли и компоненты

**Роли и компоненты** позволяют управлять ролями и компонентами на сервере.

### <a name="features"></a>Возможности

В ролях и компонентах поддерживаются следующие возможности.

- Просмотр списка ролей и компонентов на сервере
- Просмотр сведений о роли или функции
- Установка роли или компонента
- Удаление роли или компонента

[**Просмотр отзывов и предлагаемых функций для ролей и компонентов**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BRoles%20and%20Features%5D).

## <a name="scheduled-tasks"></a>Назначенные задачи

**Запланированные задачи** позволяют управлять запланированными задачами на компьютере или сервере.

### <a name="features"></a>Возможности

В запланированных задачах поддерживаются следующие возможности.

- Просмотр библиотеки планировщика заданий
- Изменение запланированных задач
- Включение & отключение запланированных задач
- Запуск & завершение запланированных задач
- Создание запланированных задач

[**Просмотр отзывов и предлагаемых функций для запланированных задач**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BScheduled%20Tasks%5D).

## <a name="services"></a>"Службы"

**Службы** позволяют управлять службами на компьютере или сервере.

### <a name="features"></a>Возможности

В службах поддерживаются следующие функции:

- Поиск и поиск служб на сервере
- Просмотр сведений о службе
- Запуск службы
- Приостановка службы
- Изменение свойств службы

[**Просмотр отзывов и предлагаемых функций для служб**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BServices%5D).

## <a name="settings"></a>"Параметры"

**Параметры** — это центральное расположение для управления параметрами на компьютере или сервере.

### <a name="features"></a>Возможности

- Просмотр и изменение переменных среды пользователя и системы
- Просмотр конфигурации оповещений мониторинга от [Azure Monitor](azure-monitor.md)
- Просмотр и изменение конфигурации питания
- Просмотр и изменение параметров удаленный рабочий стол
- Просмотр и изменение параметров управления доступом на основе ролей
- Просмотр и изменение параметров узла Hyper-V (если применимо)

## <a name="storage"></a>Хранение

**Хранилище** позволяет управлять устройствами хранения данных на компьютере или сервере.

### <a name="features"></a>Возможности

В хранилище поддерживаются следующие функции:

- Просмотр и поиск существующих дисков на сервере
- Просмотреть сведения о диске
- Создание тома
- Инициализация диска
- Создание, присоединение и отсоединение виртуального жесткого диска (VHD)
- Отключение диска от сети
- Форматирование тома
- Изменение размера тома
- Изменить свойства тома
- Удаление тома
- Установка управления квотами
- Управление хранилищем квот диспетчер ресурсов файлового сервера [-> создание или обновление квоты](https://docs.microsoft.com/windows-server/storage/fsrm/quota-management)

[**Просмотр отзывов и предлагаемых функций для хранилища**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BStorage%5D)

## <a name="storage-migration-service"></a>Служба миграции хранилища

**Служба миграции хранилища** позволяет переносить серверы и файловые ресурсы в Azure или Windows Server 2019 — не требуя от приложений или пользователей изменять что-либо.
[Обзор службы миграции хранилища](https://go.microsoft.com/fwlink/?linkid=2016155)

>[!NOTE]
>Для службы миграции хранилища требуется Windows Server 2019.

## <a name="storage-replica"></a>Реплика хранилища

Используйте **реплику хранилища** для управления репликацией хранилища "сервер-сервер".
[Дополнительные сведения о реплике хранилища](https://docs.microsoft.com/windows-server/storage/storage-replica/storage-replica-ui)

## <a name="system-insights"></a>Системная аналитика

**System Insights** предоставляет прогнозную аналитику изначально в Windows Server, чтобы помочь вам получить представление о работе сервера.
[Обзор System Insights](https://aka.ms/systeminsights)

>[!NOTE]
>Для работы System Insights требуется Windows Server 2019.

## <a name="updates"></a>Обновления

**Обновления** позволяют управлять обновлениями Microsoft и (или) Windows на компьютере или сервере.

### <a name="features"></a>Возможности

В обновлениях поддерживаются следующие функции:

- Просмотр доступных обновлений Windows или Майкрософт
- Просмотр списка журнала обновлений
- Установить обновления
- Проверка обновлений в Интернете с Центр обновления Майкрософт
- Управление интеграцией [Управление обновлениями Azure](https://docs.microsoft.com/azure/automation/automation-update-management)

[**Просмотр отзывов и предлагаемых компонентов для обновлений**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BUpdates%5D)

## <a name="virtual-machines"></a>Виртуальные машины

См. раздел [Управление виртуальными машинами с помощью центра администрирования Windows](manage-virtual-machines.md) .

## <a name="virtual-switches"></a>Виртуальные коммутаторы

**Виртуальные коммутаторы** позволяют управлять виртуальными коммутаторами Hyper-V на компьютере или сервере.

### <a name="features"></a>Возможности

Виртуальные коммутаторы поддерживают следующие функции.

- Просмотр и поиск виртуальных коммутаторов на сервере
- Создание нового виртуального коммутатора
- Переименование виртуального коммутатора
- Удаление существующего виртуального коммутатора
- Изменение свойств виртуального коммутатора

[**Просмотр отзывов и предлагаемых функций для виртуальных коммутаторов**](https://windowsserver.uservoice.com/forums/295071/filters/top?category_id=319162&query=%5BVirtual%20Switch%5D)
