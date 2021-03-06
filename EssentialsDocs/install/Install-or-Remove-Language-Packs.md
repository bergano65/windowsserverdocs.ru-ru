---
title: Установка и удаление языковых пакетов
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98f13f63-4480-40ba-a7ef-d1d9b7582e5f
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: a41b491bbe4b4a8ee7f9743dc85e5bdaffb08496
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59860095"
---
# <a name="install-or-remove-language-packs"></a>Установка и удаление языковых пакетов

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Необходимо сначала создать многоязыковой образ Windows, как описано в разделе [языковые пакеты и развертывание](https://technet.microsoft.com/library/hh824829) перед добавлением языкового пакета Windows Server Essentials.  
  
 Для создания многоязычных образов предусмотрены языковые пакеты. Информация в этом разделе относится только к установке и удалению языковых пакетов на Windows Server Essentials.  
  
> [!NOTE]
>  Если предполагается выполнить начальную настройку (IC) с клиентского компьютера, не поддерживающего восточноазиатские языки (например, ja-jp), а английский язык не включен в многоязычный образ на сервере, веб-страница начальной настройки будет отображаться квадратами. Для отображения веб-страницы начальной настройки на английском языке по умолчанию необходимо, чтобы созданный многоязыковой образ включал английский язык.  
  
## <a name="adding-language-packs-to-an-image"></a>Добавление языковых пакетов в образ  
 Языковые пакеты доступны на DVD-диске с OEM-модулем настройки. Перед добавлением языковых пакетов в образ рекомендуется скопировать их на обслуживающий компьютер.  
  
 Для установки языковых пакетов необходимо использовать следующую команду:  
  
 **DISM.exe / online/Add-Package /PackagePath:C:\\< полный путь к каталогу cab-файлов\>\lp.cab**  
  
 В следующей команде показан пример добавления немецкого языкового пакета:  
  
 **DISM.exe / online/Add-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
> [!IMPORTANT]
>  Необходимо также применить языковые пакеты для Windows Server Essentials для полной локализации этой операционной системы.  
  
## <a name="removing-language-packs-from-an-image"></a>Удаление языковых пакетов из образа  
 Чтобы удалить языковой пакет, который больше не нужно включать в образ, можно использовать следующую команду:  
  
 **DISM.exe / online/Remove-Package /PackagePath:C:\\< полный путь к каталогу cab-файлов\>\lp.cab**  
  
 В следующей команде показан пример удаления немецкого языкового пакета:  
  
 **DISM.exe / online/Remove-Package /PackagePath:C:\Users\Administrator\Desktop\WindowsHomeServer-Product-r\de-de\lp.cab**  
  
## <a name="see-also"></a>См. также  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

