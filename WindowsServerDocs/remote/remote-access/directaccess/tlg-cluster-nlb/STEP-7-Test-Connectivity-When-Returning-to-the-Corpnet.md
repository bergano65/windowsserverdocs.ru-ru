---
title: Шаг 7. Проверка подключения при возврате к корпоративной сети
description: Этот раздел является частью руководства по тестовой лаборатории. демонстрация DirectAccess в кластере с Windows NLB для Windows Server 2016
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-da
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5a7252d0-6db8-4a9d-98ee-75082ecd2929
ms.author: pashort
author: shortpatti
ms.openlocfilehash: fa89745d6efcae3591bba2aa5a694ee651bc9912
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404851"
---
# <a name="step-7-test-connectivity-when-returning-to-the-corpnet"></a>Шаг 7. Проверка подключения при возврате к корпоративной сети

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

Многие пользователи переходят между удаленными расположениями и корпоративной сети, поэтому при возврате к корпоративной сети важно, чтобы они могли получить доступ к ресурсам без каких бы то ни было изменений в конфигурации. Удаленный доступ делает это возможным, так как когда клиент DirectAccess возвращается в корпоративную сеть, он может установить соединение с сервером сетевого расположения. После успешной установки HTTPS-подключения к серверу сетевых расположений клиент DirectAccess отключает конфигурацию клиента DirectAccess и использует прямое подключение к корпоративной сети.  
  
### <a name="test-connectivity-on-client1"></a>Проверка подключения на компьютере КЛИЕНТ1  
  
1. Выключите компьютер КЛИЕНТ1, а затем отсоедините компьютер КЛИЕНТ1 от подсети Хоменет или виртуального коммутатора и подключите его к подсети или виртуальному коммутатору. Включите CLIENT1 и войдите в систему как CORP\User1.  
  
2. Откройте окно Windows PowerShell с повышенными привилегиями, введите **ipconfig/all**и нажмите клавишу ВВОД. В выходных данных будет указано, что у компьютера КЛИЕНТ1 есть локальный IP-адрес, а также нет ни одного активного туннеля 6to4, Teredo или IP-HTTPS.  
  
3. Проверьте возможность подключения к сетевой папке в. На **начальном** экране введите<strong>\\ \ APP2\Files</strong>и нажмите клавишу ВВОД. Вы сможете открыть файл в этой папке.  
  


