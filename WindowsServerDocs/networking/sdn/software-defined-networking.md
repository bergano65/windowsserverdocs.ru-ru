---
title: Программно-конфигурируемая сеть (SDN)
description: Программно-определяемая сеть (SDN) позволяет централизованно настраивать и контролировать физические и виртуальные сетевые устройства, например маршрутизаторы, коммутаторы и шлюзы в центре обработки данных. Используйте этот раздел, чтобы узнать о технологиях программно определяемой сети (SDN), входящих в состав Windows Server, System Center и Microsoft Azure.
manager: dougkim
ms.prod: windows-server-threshold
ms.technology: networking-sdn
ms.topic: article
ms.assetid: 9a1ea73c-20cd-42c5-95ad-b003b9cc6d64
ms.author: pashort
author: shortpatti
ms.date: 08/09/2018
ms.openlocfilehash: a6c4db97b1c55d5114eba09251685ef0f2b840bc
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59855235"
---
# <a name="sdn-in-windows-server-overview"></a>Обзор SDN в Windows Server

>Относится к: Windows Server (полугодовой канал), Windows Server 2016


Программно-определяемая сеть (SDN) позволяет централизованно настраивать и контролировать физические и виртуальные сетевые устройства, например маршрутизаторы, коммутаторы и шлюзы в центре обработки данных. Существующие SDN совместимые устройства можно использовать для достижения более глубокую интеграцию между виртуальной сети и физической сети. Элементы виртуальной сети как виртуальный коммутатор Hyper-V, виртуализация сети Hyper-V и шлюз RAS, спроектированы как интегральные части своей инфраструктуре SDN. 

>[!Note]
>Узлы Hyper-V и виртуальных машин (ВМ) под управлением серверов инфраструктуры SDN, такие как узлы сетевого контроллера и балансировка нагрузки программного обеспечения, должен быть установлен выпуск Windows Server 2016 Datacenter. 
>
>Узлы Hyper-V, содержащего только рабочую нагрузку клиентов виртуальных машин подключаться к сетям, управляемым SDN можно использовать Windows Server 2016 Standard edition.

SDN возможен, поскольку плоскостей сети больше не привязаны к самим сетевым устройствам. Тем не менее другие сущности, такие как программное обеспечение управления центра обработки данных, например System Center 2016 используйте плоскостей сети. SDN позволяет динамически управлять сетью центра обработки данных, предоставляя автоматический централизованный подход, в соответствии с требованиями рабочих нагрузок и приложений. 

Можно использовать SDN для:

- Динамического создания, защиты и подключения сети для соответствия меняющимся нуждам ваших приложений
- Для ускорения развертывания рабочих нагрузок в виде без нарушения
- Содержать уязвимости безопасности распространение по сети
- Определения и управления политиками, которые управляют физическими и виртуальными сетями 
- Реализация политик сети постоянно в нужном масштабе

SDN позволяет выполнять все это, а также сократить расходы на общую инфраструктуру.



## <a name="contact-the-datacenter-and-cloud-networking-product-team"></a>Связаться с группой разработчиков центра обработки данных и сети в облаке

Если вы заинтересованы в обсуждения технологии SDN с Майкрософт или других клиентов SDN, существует множество методов для внесения контакта.

Дополнительные сведения см. в разделе [свяжитесь с центром обработки данных и сетевые подключения группе Cloud](contact-sdn-team.md).