---
title: Присоединение компьютеров к новой network1 Windows Server Essentials
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d94de050-3300-4323-a5ea-c824cb9cecc9
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 62f31f859ed3fd0f77baf37d3467d4702b24ad95
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66432913"
---
# <a name="join-computers-to-the-new-windows-server-essentials-network1"></a>Присоединение компьютеров к новой network1 Windows Server Essentials

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

##  <a name="BKMK_JoinComputers"></a>   
 Следующий шаг в процессе миграции является присоединение клиентских компьютеров к новой сети Windows Server Essentials и обновление параметров групповой политики.  
  
### <a name="domain-joined-client-computers"></a>Клиентские компьютеры, присоединенные к домену  
 Перейдите по адресу **http://** <em>destination-servername</em> **/connect** и установите программное обеспечение Windows Server Connector, как если бы это был новый компьютер. Процесс установки для клиентских компьютеров, как присоединенных к домену, так и не присоединенных к нему, идентичен.  
  
> [!NOTE]
>  Программное обеспечение Windows Server Connector не поддерживает компьютеры, на которых выполняется ОС Windows XP или Windows Vista. Если у вас есть компьютеры с ОС Windows XP или Windows Vista, которые уже присоединены к домену, этот шаг можно пропустить.  
  
### <a name="non-domain-joined-client-computers"></a>Клиентские компьютеры, не присоединенные к домену  
 Перейдите по адресу **http://** <em>destination-servername</em> **/connect** и установите программное обеспечение Windows Server Connector, как если бы это был новый компьютер. Процесс установки для клиентских компьютеров, как присоединенных к домену, так и не присоединенных к нему, идентичен.  
  
> [!NOTE]
>  Программное обеспечение Windows Server Connector не поддерживает компьютеры, на которых выполняется ОС Windows XP или Windows Vista. Если у вас есть компьютеры с ОС Windows XP или Windows Vista, которые уже присоединены к домену, этот шаг можно пропустить.  
  
### <a name="ensure-that-group-policy-has-updated"></a>Убедитесь, что групповая политика обновлена  
  
> [!NOTE]
>  Это необязательный шаг, который требуется только в том случае, если исходный сервер был настроен с настраиваемыми параметрами групповой политики, например, с перенаправлением папок.  
  
 Хотя и исходный сервер, и целевой сервер все еще подключены к сети, следует убедиться, что параметры групповой политики были реплицированы с целевого сервера на клиентские компьютеры. На каждом клиентском компьютере выполните следующие действия:  
  
1.  Откройте окно командной строки.  
  
2.  В окне командной строки введите **GPRESULT /R** и нажмите клавишу ВВОД.  
  
3.  Просмотрите результат для раздела, Групповая политика была применена с: и убедитесь, что указан целевой сервер, таких как **DestinationSrv.Domain.local**. Пример:  
  
    ```  
    USER SETTINGS  
    --------------  
        CN=User,OU=Users,DC=DOMAIN,DC=Local  
        Last time Group Policy was applied: 1/24/2011 at 1:26:27 PM  
        Group Policy was applied from:      DestinationSrv.Domain.local  
        Group Policy slow link threshold:   500 kbps  
        Domain Name:                        Domain  
        Domain Type:                        Windows 2008  
  
    ```  
  
4.  Если целевой сервер не указан, то в командной строке введите **gpupdate /force**, а затем нажмите клавишу ВВОД, чтобы обновить параметры групповой политики. Затем снова выполните предыдущую процедуру.  
  
5.  Если целевой сервер по-прежнему не отображается, то может иметься ошибка в параметрах групповой политики, или ошибка произошла при применении этих параметров для данного конкретного клиентского компьютера. Если целевой сервер не отображается, выполните следующие действия:  
  
    1.  Щелкните **Пуск**, затем **Выполнить**, введите **rsop.msc** (результирующая политика) и нажмите клавишу ВВОД.  
  
    2.  Разверните дерево с крестиком на нем, пока не дойдете до узла.  
  
    3.  Щелкните правой кнопкой мыши этот узел и щелкните **Просмотр ошибки** для получения сведения о причине сбоя параметров групповой политики на указанном компьютере.
