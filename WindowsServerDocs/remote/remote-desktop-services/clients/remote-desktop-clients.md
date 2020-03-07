---
title: Клиенты удаленного рабочего стола
description: Узнайте о различных клиентах удаленного рабочего стола, доступных для всех ваших устройств.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b7d8158c-aee1-4c60-8a46-40ce5595b8e8
author: HeidiLohr
manager: lizross
ms.author: helohr
ms.date: 01/07/2020
ms.localizationpriority: medium
ms.openlocfilehash: ccf6fa376bfb54498851407bfae175736e75ebc9
ms.sourcegitcommit: 76469d1b7465800315eaca3e0c7f0438fc3939ed
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919843"
---
# <a name="remote-desktop-clients"></a>Клиенты удаленного рабочего стола

>Применяется к: Windows 10, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2

Вы можете использовать клиент удаленного доступа к рабочему столу (Майкрософт) для подключения к удаленному компьютеру и рабочим ресурсам практически из любой точки и с любого устройства. Вы можете подключаться к своему рабочему ПК и получать доступ ко всем своим приложениям, файлам и сетевым ресурсам, как если бы вы сидели за своим столом. Можно оставить открытыми приложения на работе, а затем увидеть те же приложения дома с помощью клиента удаленных рабочих столов.

Прежде чем начать, прочитайте статью о [поддерживаемой конфигурации](remote-desktop-supported-config.md), в которой описываются компьютеры, подходящие для подключения с помощью клиентов удаленного доступа к рабочему столу. Кроме того, ознакомьтесь с [часто задаваемыми вопросами о клиентах](remote-desktop-client-faq.md).

Доступны следующие клиентские приложения.

| Устройство          | Получить приложение                                                                                                  | Инструкции по установке                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| Настольный компьютер с Windows | [Клиент Удаленного рабочего стола](windowsdesktop.md#install-the-client)                                               | [Приступая к работе с клиентом Удаленного рабочего стола](windowsdesktop.md) |
| Магазин Windows Store   | [Клиент Windows 10 в Microsoft Store](https://go.microsoft.com/fwlink/?LinkID=616709)                   | [Приступая к работе с клиентом Microsoft Store](windows.md)          |
| Android         | [Клиент Android в Google Play](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android)     | [Приступая к работе с клиентом Android](remote-desktop-android.md) |
| iOS             | [Клиент iOS в магазине iTunes](https://itunes.apple.com/app/microsoft-remote-desktop/id714464092?mt=8)     | [Приступая к работе с клиентом iOS](remote-desktop-ios.md)         |
| macOS           | [Клиент macOS в магазине iTunes](https://itunes.apple.com/app/microsoft-remote-desktop/id1295203466?mt=12) | [Приступая к работе с клиентом macOS](remote-desktop-mac.md)       |

## <a name="configuring-the-remote-pc"></a>Настройка удаленного компьютера

Чтобы настроить удаленный компьютер перед осуществлением к нему удаленного доступа, [разрешите доступ к этому компьютеру](remote-desktop-allow-access.md).

## <a name="remote-desktop-client-uri-scheme"></a>Схема URI для клиента удаленногодоступа к рабочему столу

Вы можете интегрировать функции клиентов удаленного доступа к рабочему столу на всех платформах с помощью схемы URI. Ознакомьтесь с [поддерживаемыми атрибутами URI](remote-desktop-uri.md), которые можно использовать с клиентами для iOS, Mac и Android.
