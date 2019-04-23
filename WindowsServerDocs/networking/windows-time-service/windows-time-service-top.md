---
ms.assetid: e34622ff-b2d0-4f81-8d00-dacd5d6c215e
title: Служба времени Windows
description: ''
author: shortpatti
ms.author: pashort
manager: dougkim
ms.date: 05/08/2018
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: networking
ms.openlocfilehash: a86c2bdde9c65878b228f153009734da8f03960d
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59856835"
---
# <a name="windows-time-service-w32time"></a>Служба времени Windows (W32Time)

>Относится к: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows 10 или более поздней версии

Служба времени Windows (W32Time) синхронизирует дату и время для всех компьютеров под управлением в доменных службах Active Directory (AD DS). Синхронизация времени очень важна для правильной работы многих служб Windows и приложений line-of-business (LOB). Служба времени Windows использует протокол сетевого времени (NTP) для синхронизации часов компьютера в сети. NTP гарантирует, что точное значение или метка времени, могут быть назначены сетевые запросы доступа для проверки и ресурсов.

В разделе службы времени Windows (W32Time) доступно следующее содержимое:
- **[Windows Server 2016 точное время](accurate-time.md).** Точность времени синхронизации в Windows Server 2016 значительно улучшена, сохраняя полностью обратно NTP более ранних версий Windows. При разумным рабочих условиях может поддерживать 1 мс точность по отношению к часовому поясу UTC или лучше для членов домена Windows Server 2016 и Юбилейное обновление Windows 10.
- **[Поддержка границ для сред с высокой точностью](support-boundary.md).** В этой статье описывается поддержка границы службы времени Windows (W32Time) в средах, требующих очень точные и стабильной системного времени.
- **[Настройка системы для высокая точность](configuring-systems-for-high-accuracy.md).** Синхронизация времени в Windows 10 и Windows Server 2016 были значительно улучшены.  При разумным рабочих условиях, системы можно настроить для поддержания 1 мс (миллисекунды) точности или выше (с точки зрения в формате UTC).
- **[Время Windows для отслеживания](windows-time-for-traceability.md).** Законы множества секторы требуют систем, чтобы четко прослеживаться в формат UTC.  Это означает, что можно аттестовать системы смещение относительно UTC.  Чтобы включить сценарии соответствия нормативным требованиям, Windows 10 и Server 2016 предоставляет новые журналы событий для получения картины с точки зрения операционной системы, чтобы сформировать представление о действиях, выполненных от системных часов.  Эти журналы событий создаются постоянно для службы времени Windows и можно проверить или в архив для последующего анализа.
- **[Технический справочник службы времени Windows](windows-time-service-tech-ref.md).** Служба W32Time обеспечивает синхронизацию часов сети для компьютеров без необходимости больших усилий по настройке. Служба W32Time важно для успешной работы проверки подлинности Kerberos V5 и, следовательно, для проверки подлинности на основе доменных служб Active Directory AD.
    - **[Как работает служба времени Windows](How-the-Windows-Time-Service-Works.md).** Несмотря на то, что служба времени Windows не точное реализацию протокола сетевого времени (NTP), он использует сложный набор алгоритмов, определенный в спецификациях NTP для обеспечения максимальной точности часы на компьютерах в сети.
    - **[Средства службы времени Windows и параметры](Windows-Time-Service-Tools-and-Settings.md).** Тип клиента времени NT5DS, это означает, что их синхронизации времени в иерархии домена у большинства компьютеров члена домена. Только типичные исключением из этого — контроллер домена, который работает как хозяин операций эмулятора основного контроллера основного домена корневого домена леса, который обычно настраивают для синхронизации времени с внешним источником времени.


## <a name="related-topics"></a>Связанные разделы
Дополнительные сведения о иерархии доменов и оценки системы, см. в разделе [«Что такое служба времени Windows?»](https://blogs.msdn.microsoft.com/w32time/2007/07/07/what-is-windows-time-service/) .

Модель подключаемого модуля windows время поставщика — [приведенной на сайте TechNet](https://msdn.microsoft.com/library/windows/desktop/ms725475%28v=vs.85%29.aspx).

Дополнение ссылается статья время Accurate Windows 2016 можно скачать [здесь](https://windocs.blob.core.windows.net/windocs/WindowsTimeSyncAccuracy_Addendum.pdf)

Краткий обзор службы времени Windows, взгляните на это [общий обзор видео](https://aka.ms/WS2016TimeVideo).

<!-- In this guide
In this guide:
Windows Accurate Time
High Accuracy
Support Boundary
Configuration for High Accuracy
Traceability for Compliance
Best Practices
Technical Reference
How the Windows Time Service Works
Windows Time Service Tools and Settings
-->
