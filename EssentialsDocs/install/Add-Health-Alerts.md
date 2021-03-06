---
title: Добавление оповещений о работоспособности
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 270e0aac-dc42-46f3-a20b-a68ffbded06d
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 8c3ba4746211690ad52f775b8bdc1ccf9b6c74b7
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433727"
---
# <a name="add-health-alerts"></a>Добавление оповещений о работоспособности

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Надстройка работоспособности предоставляет определения для оповещений, проверок работоспособности и исправления сетевых неполадок. Надстройка работоспособности состоит из XML-файлов, в которых содержатся заметки для кода или данных, используемых для оценки работоспособности определенных компонентов. Надстройки работоспособности создаются разработчиками и устанавливаются на сервере и клиентских компьютерах администратором.  
  
 Сведения о создании надстройки работоспособности см. в разделе [Пакет SDK Windows Server Solutions](https://go.microsoft.com/fwlink/?LinkID=248648) .  
  
## <a name="installing-health-add-in-files"></a>Установка файлов надстройки работоспособности  
 После создания XML-файлов разработчиком необходимо разместить копию этих файлов в соответствующих папках на сервере и клиентских компьютерах.  
  
#### <a name="to-install-the-xml-files-on-the-server"></a>Установка XML-файлов на сервере  
  
1. В папке **%ProgramFiles%\Windows Server\Bin\Feature Definitions** создайте новую папку с именем **MyHealthAddIn**. Этой папке можно присвоить любое имя. Рекомендуется задать для нее имя компонента.  
  
2. Скопируйте файлы Definition.xml.config и Definition.xml.config в новую папку.  
  
3. При создании двоичных файлов для условий или действий необходимо также скопировать эти файлы в папку **%ProgramFiles%\Windows Server\Bin**.  
  
   Клиентские компьютеры выполняют каждые 6 часов запланированные задачи, которые помещают XML-файлы в соответствующие папки. Можно выполнить принудительную синхронизацию между клиентским компьютером и сервером, запустив задачу вручную.  
  
#### <a name="to-install-the-xml-files-on-the-client-computer"></a>Установка XML-файлов на клиентском компьютере  
  
1.  Откройте планировщик заданий.  
  
2.  Запустите задачу **HealthDefintionUpdateTask** в планировщике заданий.  
  
    > [!NOTE]
    >  При выполнении этой задачи не производится установка двоичных файлов. Двоичные файлы необходимо вручную скопировать в папку **%ProgramFiles%\Windows Server\Bin** на клиентском компьютере.  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)