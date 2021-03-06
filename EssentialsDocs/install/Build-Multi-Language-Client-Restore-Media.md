---
title: Создание многоязычного носителя для восстановления клиентов
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2fdbc016-d464-43cb-bd75-8a63e61588a2
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 1ad934d297c3092050bd6adbb6bb0f50d1ec6f36
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59879875"
---
# <a name="build-multi-language-client-restore-media"></a>Создание многоязычного носителя для восстановления клиентов

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

> [!NOTE]
>  Необходимо сначала создать многоязыковой образ Windows, как описано в разделе [Пошаговое руководство: Создание многоязыкового образа Windows](https://technet.microsoft.com/library/jj126995) перед добавлением в install.wim языковой пакет Windows Server Essentials.  
  
 При создании многоязычного установочного DVD-диска для сервера языковые пакеты устанавливаются в файл install.wim. сервера. Локализованные ресурсы для мастера восстановления устанавливаются в составе языковых пакетов.  
  
### <a name="to-build-a-multi-language-client-restore-media"></a>Создание многоязычного носителя для восстановления клиента  
  
1.  Вставьте install.wim в папку c:\mount, папка c:\mount\Program Files\Windows Server\bin\ClientRestore вызывается в качестве корневой для носителя восстановления клиента: [RestoreMediaRoot] ниже:  
  
    ```  
    dism /mount-wim /wimfile:install.wim /index:1 /mountdir:c:\mount  
    ```  
  
2.  Поместите WIM-файл восстановления клиента в папку [RestoreMediaRoot]\Sources\Boot.wim (те же шаги следует также выполнить для файла boot_x86.wim). Командная строка выглядит следующим образом:  
  
    ```  
    dism /mount-wim /wimfile:boot.wim /index:1 /mountdir:c:\mountRestore  
    ```  
  
3.  Добавьте пакет WinPE-Setup.cab на носитель восстановления, запустив следующую процедуру:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:WinPE-Setup.cab  
    ```  
  
4.  С помощью блокнота отредактируйте c:\mountRestore\windows\system32\winpeshl.ini, впишите следующее:  
  
    ```  
    [LaunchApp]  
    AppPath = %SYSTEMDRIVE%\sources\SelectLanguage.exe  
    ```  
  
5.  Добавьте языковые пакеты на носитель для восстановления. Чтобы добавить языковые пакеты, введите следующую команду:  
  
    ```  
    dism /image:c:\mountRestore /add-package /packagepath:[language pack path]  
    ```  
  
     Необходимо добавить следующие языковые пакеты:  
  
    1.  Языковой пакет среды предустановки Windows (lp.cab)  
  
    2.  Языковой пакет установки среды предустановки Windows (WinPE-Setup_[lang].cab, например, WinPE-Setup_en-us.cab)  
  
    3.  Для Восточно-азиатских шрифтов, включая zh-cn, zh-tw, zh-hk, ko-kr, ja-jp, необходимо установить дополнительный пакет шрифтов (winpe-fontsupport-[lang].cab, например, winpe-fontsupport-zh-cn.cab)  
  
6.  Создайте новый файл Lang.ini следующей командой:  
  
    ```  
    dism /image:c:\mountRestore /Gen-LangINI /distribution:mount  
    ```  
  
7.  Зафиксируйте и отсоедините образ следующей командой:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mountRestore /commit  
    ```  
  
8.  Повторите шаги 2 – 7 для [RestoreMediaroot]\Sources\Boot_x86.wim.  
  
9. Зафиксируйте и отсоедините образ следующей командой:  
  
    ```  
    dism /unmount-wim /mountdir:c:\mount /commit  
    ```  
  
## <a name="see-also"></a>См. также  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

