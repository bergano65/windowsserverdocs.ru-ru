---
title: Восстановление леса Active Directory — резервное копирование всего сервера
description: ''
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/09/2018
ms.topic: article
ms.prod: windows-server
ms.assetid: 398918dc-c8ab-41a6-a377-95681ec0b543
ms.technology: identity-adds
ms.openlocfilehash: 4377c1d993b4f6d30cf8ca8a7d149b741d7f8d2f
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369358"
---
# <a name="ad-forest-recovery---backing-up-a-full-server"></a>Восстановление леса Active Directory — резервное копирование всего сервера  

>Область применения: Windows Server 2016, Windows Server 2012 и 2012 R2, Windows Server 2008 и 2008 R2

Для подготовки к восстановлению леса рекомендуется выполнить полное резервное копирование сервера, так как оно может быть восстановлено на другом оборудовании или на другом экземпляре операционной системы.  С помощью cистема архивации данных Windows Server можно выполнить полное резервное копирование сервера. 

## <a name="windows-server-backup"></a>Система архивации данных Windows Server

Cистема архивации данных Windows Server не устанавливается по умолчанию. В Windows Server 2016 и Windows Server 2012 R2 установите его, выполнив следующие действия.

>[!NOTE]
>Имейте в виду, что действия могут незначительно отличаться в Windows Server 2016 и Windows Server 2012 R2.

Инструкции по установке в Windows Server 2008 и Windows Server 2008 R2 см. в разделе [установка Cистема архивации данных Windows Server](https://technet.microsoft.com/library/cc771232.aspx).  

### <a name="to-install-windows-server-backup"></a>Установка cистема архивации данных Windows Server

1. Откройте **Диспетчер сервера** и щелкните **Добавить роли и компоненты**.
2. В **мастере добавления ролей и компонентов** нажмите кнопку **Далее**.
3. На экране **тип установки** оставьте установку по умолчанию на основе **ролей или компонентов** и нажмите кнопку **Далее**.
4. На экране **выбора сервера** нажмите кнопку **Далее**.
5. На экране **роли сервера** нажмите кнопку **Далее**.
6. На экране **компоненты** выберите **Cистема архивации данных Windows Server** и нажмите кнопку **Далее**
   ![установить резервное копирование](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup2.png)
7. Нажмите кнопку **Установить**.
8. После завершения установки нажмите кнопку **Закрыть**.

### <a name="to-perform-a-backup-with-windows-server-backup"></a>Выполнение резервного копирования с помощью cистема архивации данных Windows Server

1. Откройте **Диспетчер сервера**, выберите **Сервис**, а затем щелкните **Cистема архивации данных Windows Server**.
   - В Windows Server 2008 R2 и Windows Server 2008 нажмите кнопку **Пуск**, выберите пункт **Администрирование**, а затем щелкните **Cистема архивации данных Windows Server**.

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup1.png) 

2. При появлении запроса в диалоговом окне **контроль учетных записей** укажите учетные данные оператора архивации и нажмите кнопку **ОК**.
3. Щелкните **Локальная Архивация**.
4. В меню **Действие** выберите команду **Однократная архивация**.
5. В мастере однократной архивации на странице **Параметры резервного копирования** выберите **другие параметры**, а затем нажмите кнопку **Далее**.

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup3.png)

6. На странице **Выбор конфигурации архивации** щелкните **полный сервер (рекомендуется)** , а затем нажмите кнопку **Далее**.
7. На странице **Укажите тип назначения** выберите **локальные диски** или **Удаленная общая папка**, а затем нажмите кнопку **Далее**.
8. На странице **Выбор места расположения резервной копии** выберите расположение резервной копии.  Если выбран вариант Локальный диск выберите локальный диск или если выбран параметр Удаленная общая папка, выберите общую сетевую папку.
9. На экране подтверждения нажмите кнопку **резервное копирование**.

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup4.png)

10. После завершения нажмите кнопку **Закрыть**.
11. Закройте cистема архивации данных Windows Server.

>[!NOTE]
>Если появится сообщение о том, что расположение хранилища резервных копий недоступно, необходимо либо исключить один из выбранных томов, либо добавить новый том или удаленную общую папку.
>Если появится предупреждение о том, что выбранный том также включен в список элементов для резервного копирования, определите, нужно ли удалить, и нажмите кнопку **ОК**.

## <a name="using-wbadminexe-to-backup-a-windows-server"></a>Использование программы WBADMIN. exe для резервного копирования Windows Server

Wbadmin. exe — это служебная программа командной строки, которая позволяет выполнять резервное копирование и восстановление операционной системы, томов, файлов, папок и приложений в командной строке.

### <a name="to-perform-a-full-server-backup-using-wbadminexe"></a>Выполнение полного резервного копирования сервера с помощью WBADMIN. exe
  
- Откройте командную строку с повышенными привилегиями, введите следующую команду и нажмите клавишу ВВОД:  

   ```
   wbadmin start backup -backuptarget:<Drive_letter_to store_backup>: -include:<Drive_letter_to_include>:
   ```

   ![Установка резервной копии](media/AD-Forest-Recovery-Backing-up-a-Full-Server/fullbackup5.png)

## <a name="next-steps"></a>Дальнейшие действия

- [Руководство по восстановлению леса AD](AD-Forest-Recovery-Guide.md)
- [Восстановление леса AD — процедуры](AD-Forest-Recovery-Procedures.md)
