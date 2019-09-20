---
title: Приступая к работе с клиентом для Windows Desktop
description: Основные сведения о клиенте для Windows Desktop.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
author: heidilohr
manager: daveba
ms.author: helohr
ms.date: 09/13/2019
ms.localizationpriority: medium
ms.openlocfilehash: c864ba0e51054a553bfd53f845bd4d1c9ff3c8ba
ms.sourcegitcommit: 61767c405da44507bd3433967543644e760b20aa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988242"
---
# <a name="get-started-with-the-windows-desktop-client"></a>Приступая к работе с клиентом для Windows Desktop

>Относится к: Windows 10 и Windows 7

Клиент удаленного рабочего стола для Windows Desktop можно использовать для удаленной работы с приложениями для Windows и рабочими столами Windows с другого устройства с Windows.

> [!NOTE]
> - Эта документация не относится к клиенту подключения к удаленному рабочему столу (MSTSC), входящему в состав Windows. Она относится к новому клиенту Удаленного рабочего стола (MSRDC).
> - Сейчас этот клиент поддерживает только доступ к удаленным приложениям и рабочим столам с [виртуального рабочего стола Windows](https://aka.ms/wvd).
> - Хотите узнать о новых выпусках для клиента Windows Desktop? Ознакомьтесь с разделом [Что нового в клиенте для Windows Desktop](windowsdesktop-whatsnew.md).

## <a name="install-the-client"></a>Установка клиента

Сейчас вы можете скачать клиент для 64-разрядной версии Windows. Мы обновим этот список, когда станут доступны клиенты для других версий Windows.

- [Клиент для Windows (64-разрядная версия)](https://go.microsoft.com/fwlink/?linkid=2068602)

Можно установить клиент для текущего пользователя, что не требует прав администратора. Кроме того, администратор может установить и настроить клиент, чтобы все пользователи устройства могли получить к нему доступ.

После установки клиент можно будет запустить из меню "Пуск", выполнив поиск фразы **Удаленный рабочий стол**.

## <a name="feeds"></a>Веб-каналы

Получите список управляемых ресурсов, к которым можно получить доступ (например, приложений и рабочих столов), подписавшись на веб-канал, предоставленный администратором. После подписки эти ресурсы станут доступными на вашем локальном компьютере. Сейчас клиент Windows Desktop поддерживает ресурсы, опубликованные с виртуального рабочего стола Windows.

### <a name="subscribe-to-a-feed"></a>Подписка на веб-канал

1. На главной странице клиента, также называемой центром подключений, выберите **Subscribe** (Подписаться).
2. При появлении запроса войдите в систему со своей учетной записью.
3. В центре подключений будут отображены ресурсы, сгруппированные по рабочей области.

Ресурсы можно запустить одним из следующих способов.

- Перейдите в центр подключений и дважды щелкните ресурс, чтобы запустить его.
- Вы также можете перейти в меню "Пуск" и найти папку с именем соответствующей рабочей области или ввести имя ресурса в строке поиска.

### <a name="workspace-details"></a>Сведения о рабочей области

После того, как вы подпишетесь, можно будет просматривать дополнительные сведения о рабочей области на панели "Details" (Сведения).

- Имя рабочей области.
- URL-адрес и имя пользователя, используемые для подписки.
- Число приложений и рабочих столов.
- Дата и время последнего обновления.
- Состояние последнего обновления.

Вот как можно перейти к панели "Details" (Сведения).

1. В центре подключений коснитесь дополнительного меню ( **…** ) рядом с рабочей областью.
2. Из раскрывающегося списка выберите **Details** (Сведения).
3. Панель "Details" (Сведения) отобразится в правой части окна клиента.

После того, как вы подпишетесь, рабочая область будет регулярно автоматически обновляться. Ресурсы могут быть добавлены, изменены или удалены в соответствии с изменениями, внесенными администратором.

При необходимости можно также вручную искать обновления для ресурсов, выбрав **Update now** (Обновить сейчас) на панели "Details" (Сведения).

### <a name="unsubscribe-from-a-feed"></a>Отмена подписки на веб-канал

В этом разделе вы узнаете, как отменить подписку на веб-канал. Вы можете отменить подписку, чтобы либо повторно подписаться на веб-канал с другой учетной записью, либо удалить ресурсы из системы.

1. В центре подключений коснитесь дополнительного меню ( **…** ) рядом с рабочей областью.
2. Из раскрывающегося меню **Unsubscribe** (Отменить подписку).
3. Просмотрите диалоговое окно и выберите **Continue** (Продолжить).

## <a name="update-the-client"></a>Обновление клиента

Вы будете уведомлены о доступности новой версии клиента, если только администратор не отключил эту функцию. Это уведомление может отображаться либо непосредственно в центре подключений, либо в центре уведомлений Windows. Выберите уведомление, чтобы начать процесс обновления.

Можно также вручную выполнить поиск новых обновлений для клиента.

1. В центре подключений коснитесь дополнительного меню ( **…** ) на панели команд в верхней части окна клиента.
2. Из раскрывающегося списка выберите **About** (О программе).
3. Коснитесь кнопки **Проверить наличие обновлений**.
4. Если доступно обновление, коснитесь **Install update** (Установить обновление), чтобы обновить клиент.

## <a name="providing-feedback"></a>Предоставление отзыва

У вас есть предложение по компоненту или вы хотите сообщить о проблеме? Сообщите нам с помощью [Центра отзывов](feedback-hub://?tabid=2&contextid=883), который также доступен из клиента.

1. В центре подключений коснитесь дополнительного меню ( **…** ) на панели команд в верхней части окна клиента.
2. Выберите **Feedback** (Обратная связь) из раскрывающегося меню, чтобы открыть Центр отзывов.