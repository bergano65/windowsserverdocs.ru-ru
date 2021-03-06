---
title: Защита развертывания RDS с помощью аварийного восстановления
description: Узнайте о возможностях аварийного восстановления служб удаленных рабочих столов.
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: remote-desktop-services
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9ff6a3b0-ea14-424e-9524-209252e9f1a8
author: lizap
ms.author: elizapo
ms.date: 06/12/2017
ms.openlocfilehash: 6691a6ab0e8762840faf3dd7fa8a8aea8cae0e47
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403994"
---
# <a name="configure-disaster-recovery-for-remote-desktop-services"></a>Настройка аварийного восстановления для служб удаленных рабочих столов

При развертывании служб удаленных рабочих столов в среде они становятся важной частью инфраструктуры. Особенно это касается приложений и ресурсов, которые совместно используются пользователями. Если развертывание RDS выходит из строя из-за чего угодно: от сбоя сети до стихийного бедствия, то пользователи не могу получить доступ к этим приложениям и ресурсам, что отрицательно влияет на вашу организацию. Чтобы избежать этого, можно настроить решение для аварийного восстановления, позволяющее осуществлять отработку отказа развертывания: если развертывание RDS по какой-либо причине станет недоступным, его функции автоматически возьмет на себя резервное развертывание.

Чтобы обеспечить работу развертывания RDS в случае сбоя отдельного компонента или компьютера, рекомендуется настроить развертывание RDS для обеспечения высокой доступности. Это можно сделать, настроив [ферму RDSH](rds-scale-rdsh-farm.md) и убедившись, что ваши [посредники подключений кластеризованы для обеспечения высокой доступности](rds-connection-broker-cluster.md). 

Рекомендуемые здесь решения для аварийного восстановления обеспечивают защиту развертывания на случай неустранимого сбоя: например, если все развертывание RDS выйдет из строя (включая избыточные роли, настроенные для обеспечения высокой доступности). В случае такой катастрофы решение для аварийного восстановления, встроенное в развертывание, позволит выполнить отработку отказа всего развертывания и быстро восстановить работу приложений и ресурсов для пользователей.

Используйте следующие сведения, чтобы развернуть решение для аварийного восстановления в RDS.

- [Использование нескольких центров обработки данных Azure для обеспечения доступа пользователей к развертыванию RDS, даже если один центр обработки данных Azure вышел из строя (геоизбыточность)](rds-multi-datacenter-deployment.md)
- [Настройка аварийного восстановления для служб удаленных рабочих столов с помощью Azure Site Recovery](rds-disaster-recovery-with-azure.md)


