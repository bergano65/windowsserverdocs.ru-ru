---
title: RDS - запуск и настройка
description: Сведения управления для служб удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.author: spatnaik
ms.date: 02/08/2017
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79909767-a4c3-4ecf-8d3f-77d37a663153
author: spatnaik
manager: scottman
ms.openlocfilehash: 40f8dbd560da359e8764ed715e7776cc2d230a7f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862185"
---
# <a name="run-and-tune-your-remote-desktop-services-environment"></a>Запуск и настройка среды служб удаленных рабочих столов

Помощник по настройке развертывания требует времени и требует инструментирования и мониторинга. Используйте следующие процедуры для уточнения развертывания удаленного рабочего стола, обеспечение его работы и включить масштабирование увеличением (или в), при необходимости. 

Рекомендуется непрерывно оценивают метрики и баланс к выполняемым затраты.

## <a name="management-and-monitoring"></a>Управление и мониторинг

Ознакомьтесь с [Управление пользователями в вашей коллекции служб удаленных рабочих СТОЛОВ](rds-user-management.md) сведения о том, как управлять доступом к рабочим столам и удаленным ресурсам.

Используйте **Microsoft Operations Management Suite (OMS)** для мониторинга развертывания удаленных рабочих столов для потенциальные узкие места и управлять ими с помощью одного из следующих способов: 

- **Диспетчер серверов**: Используйте средства управления удаленным рабочим Столам, встроенной в Windows Server для управления развертываниями с до 500 параллельных удаленных конечных пользователей. 
- **PowerShell**: Используйте модуль PowerShell к удаленному рабочему Столу, также встроена в Windows Server для управления развертываниями с до 5000 одновременных удаленных конечных пользователей.

## <a name="scale-bigger-better-faster"></a>Масштаб: Больше, быстрее и лучше

С видимостью в развертывание вы можете управлять масштабирования с более высокой точностью. Простое добавление и удаление серверов узла удаленного рабочего стола, исходя из потребностей масштабирования. 

Можно сделать развертывания удаленных рабочих столов, которые основаны на Azure использование служб Azure, как Azure SQL автоматически масштабировать по запросу.

## <a name="automation-script-for-success"></a>Служба автоматизации: Скрипт для достижения успеха

Обслуживание выполняющегося приложения с высокой степенью масштабируемости многократный повтор операции на регулярной основе. При разработке скриптов, которые могут выполняться на нескольких развертываний, при необходимости можно используйте командлеты PowerShell служб удаленных рабочих столов и поставщиков WMI. Использовать правила рекомендации анализатора соответствия рекомендациям (BPA) для служб удаленных рабочих столов развертываний для настройки развертываний.

## <a name="load-testing-avoid-surprises"></a>Тестирование нагрузки: Избежать сюрпризов

Нагрузочное тестирование, развертывание с нагрузочные тесты и моделирование реальных использования. Изменить размер нагрузки, чтобы избежать непредвиденных проблем! Убедитесь, что скорость реагирования требованиям пользователей и что устойчив всей системы. Создание нагрузочных тестов с помощью средств моделирования, например LoginVSI, которые проверяют возможности развертывания в соответствии с потребностями пользователей. 