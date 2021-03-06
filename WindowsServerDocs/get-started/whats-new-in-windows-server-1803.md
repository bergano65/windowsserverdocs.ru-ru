---
title: Новые возможности Windows Server версии 1803
description: Новые возможности вычислений, удостоверения, управления, автоматизации, сетей, безопасности, хранения.
ms.prod: windows-server
ms.technology: server-general
ms.topic: article
author: greg-lindsay
ms.author: greg-lindsay
ms.localizationpriority: high
ms.date: 05/07/2018
ms.openlocfilehash: 211a0e2b49e9f15682a251f96dc338d124e2f998
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71391383"
---
# <a name="whats-new-in-windows-server-version-1803"></a>Новые возможности Windows Server версии 1803

>Область применения. Windows Server (Semi-Annual Channel)

<img src="../media/landing-icons/new.png" style='float:left; padding:.5em;' alt="Icon showing a newspaper">&nbsp;Подробные сведения о новых возможностях Windows приведены в этой [статье](whats-new-in-windows-server.md). В этом разделе рассказывается о новых и измененных возможностях в Windows Server версии 1803. Приведенные здесь новые возможности и изменения, скорее всего, окажут наибольшее влияние во время работы с этим выпуском. Также см. страницу [Windows Server Semi-Annual Channel update](https://cloudblogs.microsoft.com/windowsserver/2018/03/29/windows-server-semi-annual-channel-update/) (Обновление Semi-Annual Channel для Windows Server).

## <a name="windows-admin-center"></a>Windows Admin Center

Проект Honolulu теперь называется **Windows Admin Center**.
<br>&nbsp;
> [!video https://www.youtube.com/embed/WCWxAp27ERk?autoplay=false]

[Windows Admin Center](https://docs.microsoft.com/windows-server/manage/windows-admin-center/overview) объединяет все аспекты управления локальными и удаленными серверами. Windows Admin Center — это локально разворачиваемый браузерный инструмент управления, не требующий подключения к Интернету, который предоставляет полный контроль над всеми аспектами развертывания Windows Server.

## <a name="windows-server-release-strategy"></a>Стратегия выпуска Windows Server

Windows Server версии 1709 была выпущен в сентябре 2017 г. как первый выпуск Semi-Annual Channel. Semi-Annual Channel отличается повышенной частотой выпусков и отвечает на отзывы и предложения тех клиентов, которые требуют ускоренных инноваций раз в несколько месяцев. Он дополняет Long-Term Servicing Channel, частота выпусков которого составляет каждые 2–3 года.

Опираясь на данные телеметрии и отзывы и предложения, можно сказать, что эти каналы хорошо укладываются в следующую общую стратегию:
- Semi-Annual Channel идеально подходит для современных приложений и инновационных сценариев, например контейнеров и микрослужб.
- Long-Term Servicing Channel является предпочтительным способом выпуска для обеспечения основных инфраструктурных сценариев, таких как программно-определяемые центры обработки данных и гиперконвергентная инфраструктура (HCI). 

Ниже перечислены конкретные сценарии для Semi-Annual Channel и Long-Term Servicing Channel:

|   | Long-Term Servicing Channel |  Semi-Annual Channel |
| ------------- | ------------- | ------------ |
| Рекомендуемые сценарии     | Файловые серверы общего назначения, собственные и сторонние рабочие нагрузки, традиционные приложения, инфраструктурные роли, программно-определяемый центр обработки данных и гиперконвергентная инфраструктура  | Контейнерные приложения, узлы контейнеров и сценарии с приложениями, где ускоренные инновации приносят пользу |
| Новые выпуски  | Каждые 2–3 года  | Каждые 6 месяцев |
| Поддержка  | 5 лет основной поддержки + 5 лет расширенной поддержки  | 18 месяцев |
| Выпуски  | Все доступные выпуски Windows Server  | Выпуски Standard и Datacenter |
| Кто может использовать  | Все клиенты во всех каналах | Только клиенты облака и клиенты Software Assurance |
| Параметры установки  | Основные серверные компоненты и сервер с возможностями рабочего стола  | Основные серверные компоненты для узла контейнеров, образа контейнера и образа контейнера Nano Server |

## <a name="application-platform-and-containers"></a>Платформа приложений и контейнеры

- Оптимизация
    - Размер базового образа контейнера основных серверных компонентов сокращен на 30 % по сравнению с Windows Server версии 1709. 
    - Совместимость приложений также повышается для упрощения помещения обычных приложений в контейнеры.
    - Также повышена скорость загрузки контейнера и производительность среды выполнения благодаря различным исправлениям и оптимизации.
- Сетевые подключения контейнеров: добавлена поддержка Localhost и HTTP-прокси, а также улучшены масштабируемость и скорость запуска контейнера.
- Средства. Поддержка Curl.exe, Tar.exe и SSH улучшена в дополнение к PowerShell для сценариев создания и отладки.

### <a name="server-core-container-image"></a>Образ контейнера основных серверных компонентов

Теперь доступен уменьшенный контейнер основных серверных компонентов с повышенной совместимостью приложений. Подробную информацию можно найти [здесь](https://blogs.technet.microsoft.com/virtualization/2018/01/22/a-smaller-windows-server-core-container-with-better-application-compatibility/).

- Неиспользуемые необязательные компоненты и роли удалены. Подробные сведения см. в статье [Roles, Role Services, and Features not in Server Core containers - Windows Server, version 1803](../administration/server-core/server-core-container-removed-roles.md) (Роли, службы ролей и компоненты, не включенные в контейнеры основных серверных компонентов — Windows Server версии 1803).
    - Уменьшен размер скачиваемого файла до 1,58 ГБ (на 30% по сравнению с Windows Server версии 1709).
    - Уменьшен размер на диске до 3,61 ГБ (на 20% по сравнению с Windows Server версии 1709).
- Размер образа контейнера Nano Server не превышает 100 МБ

### <a name="windows-subsystem-for-linux-wsl"></a>Подсистема Windows для Linux (WSL)

WSL позволяет администраторам сервера использовать имеющиеся средства и сценарии с Linux в Windows Server. Множество усовершенствований, о которых рассказывалось в [блоге command line](https://blogs.msdn.microsoft.com/commandline/tag/wsl/), теперь входят в состав Windows Server, включая фоновые задачи, DriveFS, WSLPath и многое другое.

### <a name="kubernetes"></a>Kubernetes 

Kubernetes (часто называется K8s) — это система с открытым кодом для автоматизации развертывания, масштабирования и управления приложениями контейнерного типа, разработанными по рекомендациям [Cloud Native Computing Foundation](https://www.cncf.io). 

В Windows Server версии 1709 пользователи могли использовать преимущества Kubernetes в сетевых компонентах Windows, включая:
- Общие секции модулей pod: инфраструктурные и рабочие модули pod теперь используют общие секции сети (аналогично пространству имен Linux).
- Оптимизация конечных точек: благодаря совместному использованию секций службам контейнеров необходимо отслеживать не более половины конечных точек.
- Оптимизация пути данных: улучшения платформы виртуальной фильтрации и сетевой службы узлов позволяют реализовать балансировку нагрузки на основе ядра.

После выпуска Windows Server версии 1803 для Kubernetes будут реализованы дополнительные возможности: 
- [Подключаемые модули хранилища](https://github.com/Microsoft/K8s-Storage-Plugins) для контейнеров Windows, управляемых Kubernetes.
- Сети облачного масштаба благодаря таким инициативам, как наше партнерство с [Tigera в проекте Calico](https://cloudblogs.microsoft.com/windowsserver/2017/12/07/securing-modernized-apps-and-simplified-networking-on-windows-with-calico/).
- Поддержка платформы Windows для изолированных с помощью Hyper-V модулей pod с несколькими контейнерами в модуле.

### <a name="application-compatibility-and-feature-parity-issues-fixed"></a>Исправлены ошибки совместимости приложений и соответствия компонентов

- Очередь сообщений (Майкрософт) теперь устанавливается в контейнере основных серверных компонентов.
- Устранена проблема, вызывавшая сбои счетчиков производительности ASP.Net.
- Устранена проблема, при которой службы, работающие в контейнерах, не получали уведомление о завершении работы.
    - В частности, уведомление изменилось на CTRL_SHUTDOWN_EVENT для контейнерных образов основных серверных компонентов и Nano Server. Кроме того, оно расширяет уведомление в контейнерных образах основных серверных компонентов и воздействует на выполняемые в контейнере процессы, включая отправку уведомлений о завершении работы для служб, работающих в контейнере.
- Устранена несовместимость команд docker pull и docker load с параметром политики, который определяет, необходима ли защита BitLocker для обеспечения возможности записи на несъемных дисках данных (FDVDenyWriteAccess). 

## <a name="storage"></a>Хранилище

В этом выпуске можно запретить службе диспетчера ресурсов файлового сервера создавать журнал изменений (также известен как журнал USN) на всех томах при запуске службы. Это поможет сохранить место на каждом томе, но отключит классификацию файлов в режиме реального времени. Подробные сведения см. в статье [File Server Resource Manager (FSRM) overview](https://docs.microsoft.com/windows-server/storage/fsrm/fsrm-overview) (Обзор диспетчера ресурсов файлового сервера (FSRM)).

## <a name="features-added-to-server-core"></a>Новые основные серверные компоненты

Роль транспортного сервера в службах развертывания Windows (WDS) добавлена в основные серверные компоненты.

Транспортный сервер содержит только основные сетевые компоненты службы развертывания Windows. Транспортный сервер можно использовать для создания многоадресных пространств имен, передающих данные (включая образы операционных систем) с автономного сервера. Вы также можете использовать его, если требуется предоставить PXE-сервер, который позволяет клиентам выполнять PXE-загрузку и скачивать собственное приложение для установки. Этот параметр следует использовать, если необходимо использовать один из этих сценариев.

Чтобы включить службу транспортного сервера в основных серверных компонентах можно использовать следующую команду Windows PowerShell:

```
Install-WindowsFeature -Name WDS
```

## <a name="see-also"></a>См. также

[Информация о выпуске Windows Server](https://docs.microsoft.com/windows-server/get-started/windows-server-release-info)<br>
[Новые возможности Windows 10 версии 1803 — информация для ИТ-специалистов](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1803)
