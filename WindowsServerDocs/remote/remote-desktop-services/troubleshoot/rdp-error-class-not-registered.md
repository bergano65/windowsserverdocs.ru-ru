---
title: Клиенты не могут подключиться и получают сообщение об ошибке "Класс не зарегистрирован"
description: Узнайте, как устранить ошибку "Класс не зарегистрирован", возникающую при подключении к удаленному рабочему столу.
audience: itpro
ms.custom: na
ms.reviewer: rklemen
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: troubleshooting
ms.assetid: ''
author: kaushika-msft
manager: dcscontentpm
ms.author: delhan
ms.date: 07/24/2019
ms.localizationpriority: medium
ms.openlocfilehash: 7a98e894f3eaf47e257ab39c640e93101fd76fc8
ms.sourcegitcommit: c5709021aa98abd075d7a8f912d4fd2263db8803
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2020
ms.locfileid: "76265906"
---
# <a name="clients-cant-connect-and-get-the-class-not-registered-error"></a>Клиенты не могут подключиться и получают сообщение об ошибке "Класс не зарегистрирован"

Когда вы пытаетесь подключиться к удаленному компьютеру с помощью клиента под управлением Windows 10 версии после 1709, клиент не сможет подключиться. Сервер узла сеансов Удаленных рабочих столов (RDSH) выдаст сообщение, содержащее код ошибки 0x80040154 (Класс не зарегистрирован).

Такая проблема возникает, если пользователь, который пытается подключиться, использует обязательный профиль пользователя. Чтобы устранить эту проблему, установите обновление Windows 10 [за 24 июля 2018 г. — KB4338817 (ОС сборки 16299.579)](https://support.microsoft.com/help/4338817/windows-10-update-kb4338817).
