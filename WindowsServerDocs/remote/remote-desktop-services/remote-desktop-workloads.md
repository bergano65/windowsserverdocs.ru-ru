---
title: Рабочие нагрузки Удаленного рабочего стола
description: Краткий обзор различных типов рабочих нагрузок для виртуальных машин, управляемых с помощью удаленного рабочего стола.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: helohr
ms.date: 12/02/2019
ms.tgt_pltfrm: na
ms.topic: article
author: Heidilohr
manager: daveba
ms.openlocfilehash: 32781946ad2c49ec51e11dfe1e8af078425d35b0
ms.sourcegitcommit: cbf0c7c37797c22af989639fac82fc0eee94497f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/02/2019
ms.locfileid: "74700933"
---
# <a name="remote-desktop-workloads"></a>Рабочие нагрузки Удаленного рабочего стола

Пользователи могут запускать различные типы рабочих нагрузок на виртуальных машинах, управляемых службой удаленных рабочих столов или Виртуальным рабочим столом Windows. Масштабируйте свое развертывание в зависимости от ожидаемых потребностей каждого из типов пользователей. В следующей таблице приведены примеры различных типов рабочих нагрузок, которые помогут определить необходимый размер виртуальной машины. После настройки виртуальных машин необходимо постоянно следить за их фактическим использованием и соответствующим образом изменять их размер. Если вам необходима виртуальная машина с большим или меньшим размером, вы можете легко масштабировать существующее развертывание в Azure.

В следующей таблице рассматриваются все рабочие нагрузки. "Example Users" (Примеры пользователей) — это типы пользователей, которые могут найти наиболее полезную рабочую нагрузку. "Example apps" (Примеры приложений) — это типы приложений, которые хорошо подходят для каждой рабочей нагрузки.

| Тип рабочей нагрузки | Примеры пользователей | Примеры приложений |
| --- | --- | --- |
| Светлая | Пользователи, выполняющие основные задачи ввода данных | Приложения для ввода данных в базу данных, интерфейсы командной строки |
| Средний | Консультанты и исследователи рынка | Приложения для ввода данных в базу данных, интерфейсы командной строки, Microsoft Word, статические веб-страницы |
| Тяжелый | Разработчики программного обеспечения, создатели содержимого | Приложения для ввода данных в базу данных, интерфейсы командной строки, Microsoft Word, статические веб-страницы, Microsoft Outlook, Microsoft PowerPoint, динамические веб-страницы. |
| Питание | Конструкторы графики, создатели трехмерных моделей, исследователи машинного обучения | Приложения для ввода данных в базу данных, интерфейсы командной строки, Microsoft Word, статические веб-страницы, Microsoft Outlook, Microsoft PowerPoint, динамические веб-страницы, Adobe Photoshop, Adobe Illustrator, автоматизированное проектирование, автоматизированное производство |

Информацию о рекомендациях по определению размеров см. в [Virtual machine sizing guidance](virtual-machine-recs.md) (Руководство по определению размеров виртуальной машины).