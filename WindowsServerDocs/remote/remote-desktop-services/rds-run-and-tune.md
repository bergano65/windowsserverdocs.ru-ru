---
title: RDS. Запуск и настройка
description: Предоставление информации управления для служб удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server
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
ms.openlocfilehash: 5a2aa5c166b41ed8bd04ccfb92911368c07a5459
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71387164"
---
# <a name="run-and-tune-your-remote-desktop-services-environment"></a>Запуск и настройка среды служб удаленных рабочих столов

Настройка вашего развертывания занимает много времени и требует мониторинга и использования инструментария. Используйте следующие процедуры для уточнения развертывания удаленного рабочего стола, обеспечения его работы и включения масштабирования увеличением (или уменьшением) при необходимости. 

Рекомендуется постоянно оценивать показатели и балансировать с текущими затратами.

## <a name="management-and-monitoring"></a>Управление и мониторинг

Ознакомьтесь со статьей [Управление пользователями в вашей коллекции служб удаленных рабочих столов](rds-user-management.md), чтобы узнать о том, как управлять доступом к рабочим столам и удаленным ресурсам.

Используйте **Microsoft Operations Management Suite (OMS)** для отслеживания развертывания удаленных рабочих столов на предмет возможных узких мест. Управляйте ими одним из следующих способов. 

- **Диспетчер серверов** Используйте средство управления удаленными рабочими столами, встроенное в Windows Server, для управления развертыванием с 500 одновременными удаленными конечными пользователями. 
- **PowerShell** Используйте модуль RD PowerShell, также встроенный в Windows Server, для управления развертыванием с 5000 одновременными удаленными конечными пользователями.

## <a name="scale-bigger-better-faster"></a>Масштаб Больше, быстрее и лучше

Благодаря наглядности развертывания вы можете контролировать масштаб с большей точностью. Легко добавляйте или удаляйте хост-серверы удаленного рабочего стола в зависимости от масштаба. 

Развертывания удаленных рабочих столов, построенные на Azure, могут использовать службы Azure, такие как Azure SQL для автоматического масштабирования по требованию.

## <a name="automation-script-for-success"></a>Автоматизация Сценарий успеха

Поддержание работоспособного, масштабируемого приложения требует выполнения регулярных повторяющихся операций. Используйте командлеты PowerShell для служб удаленных рабочих столов и провайдеров WMI для разработки скриптов, которые при необходимости можно запускать в нескольких развертываниях. Запустите правила анализатора соответствия рекомендациям (BPA) для служб удаленных рабочих столов в своих развертываниях, чтобы настроить эти развертывания.

## <a name="load-testing-avoid-surprises"></a>Тестирование нагрузки Избегайте сюрпризов

Рекомендуется проверить развертывание с помощью нагрузочных тестов и моделирования реального использования. Изменяйте степень нагрузки, чтобы избежать непредвиденных проблем! Убедитесь, что скорость реагирования соответствует требованиям пользователей и что система работает устойчиво. С помощью инструментов моделирования, например LoginVSI, создайте нагрузочные тесты, которые покажут, будет ли развертывание соответствовать потребностям пользователей. 