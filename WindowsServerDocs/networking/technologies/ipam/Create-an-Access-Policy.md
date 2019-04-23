---
title: Создание политики доступа
description: Этот раздел входит руководство по управлению управления IP-адресами (IPAM) в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology:
- networking-ipam
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 854bd064-2f86-4678-a940-a04b3e48ae10
ms.author: pashort
author: shortpatti
ms.openlocfilehash: ac8229952c7e038f9af8fc4f9287b1821db887ac
ms.sourcegitcommit: 19d9da87d87c9eefbca7a3443d2b1df486b0b010
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/28/2018
---
# <a name="create-an-access-policy"></a>Создание политики доступа

>Область применения: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе можно использовать для создания политики доступа в консоли IPAM-клиента.  
  
Членство в группе **Администраторы**, или в эквивалентной минимальным требованием для выполнения этой процедуры.  
  
> [!NOTE]  
> Можно создать политику доступа для конкретного пользователя или группы пользователей в Active Directory. При создании политики доступа, необходимо выбрать встроенная роль IPAM или пользовательской роли, созданная вами. Дополнительные сведения о пользовательских ролях см. в разделе [Создание роли пользователя для управления доступом](../../technologies/ipam/Create-a-User-Role-for-Access-Control.md).  
  
### <a name="to-create-an-access-policy"></a>Создание политики доступа  
  
1.  В диспетчере серверов щелкните **IPAM**. Откроется консоль IPAM-клиента.  
  
2.  В области навигации щелкните **КОНТРОЛЯ доступа**. В нижней области навигации щелкните правой кнопкой мыши **политик доступа**, а затем нажмите кнопку **добавить политику доступа**.  
  
    ![Добавить политику доступа](../../media/Create-an-Access-Policy/ipam_CreateAP_01.jpg)  
  
3.  **Добавить политику доступа** откроется диалоговое окно. В **параметры пользователя**, нажмите кнопку **добавить**.  
  
    ![Добавить политику доступа](../../media/Create-an-Access-Policy/ipam_CreateAP_02.jpg)  
  
4.  **Выбрать пользователя или группу** откроется диалоговое окно. Нажмите кнопку **расположения**.  
  
    ![Пользователь или группа расположения](../../media/Create-an-Access-Policy/ipam_CreateAP_03.jpg)  
  
5.  **Расположения** откроется диалоговое окно. Перейдите в расположение, в котором находится учетная запись пользователя, выберите расположение и нажмите кнопку **ОК**. **Расположения** закрывает диалоговое окно.  
  
    ![Выбор расположения](../../media/Create-an-Access-Policy/ipam_CreateAP_04.jpg)  
  
6.  В **выбрать пользователя или группу** диалогового окна **введите имена выбираемых объектов**, введите имя учетной записи пользователя, для которого требуется создать политику доступа. Нажмите кнопку **ОК**.  
  
7.  В **добавить политику доступа**в **параметры пользователя**, **псевдоним пользователя** теперь содержит учетную запись пользователя, к которому применяется политика. В **параметры доступа**, нажмите кнопку **New**.  
  
    ![Новый параметр доступа](../../media/Create-an-Access-Policy/ipam_CreateAP_05.jpg)  
  
8.  В **добавить политику доступа**, **параметры доступа** изменения **новый параметр**.  
  
    ![Измените имя параметра в диалоговом окне на новый параметр](../../media/Create-an-Access-Policy/ipam_CreateAP_06.jpg)  
  
9. Нажмите кнопку **выберите роль** для открытия списка ролей. Выберите один из встроенных ролей, или при создании новых ролей, выберите один из роли, которые вы создали. Например, если вы создали роли IPAMSrv для применения к пользователю, щелкните **IPAMSrv**.  
  
    ![Выберите роль](../../media/Create-an-Access-Policy/ipam_CreateAP_07.jpg)  
  
10. Нажмите кнопку **добавить параметр**.  
  
    ![Добавьте новый параметр](../../media/Create-an-Access-Policy/ipam_CreateAP_08.jpg)  
  
11. Роль будет добавлено в политику доступа. Для создания политик дополнительный доступ, щелкните **применить**, а затем повторите эти действия для каждой политики, который вы хотите создать. Если вы не хотите создать дополнительные политики, щелкните **ОК**.  
  
    ![Нажмите кнопку Применить или ОК](../../media/Create-an-Access-Policy/ipam_CreateAP_09.jpg)  
  
12. На панели отображения консоли клиента IPAM убедитесь, что создается новая политика доступа.  
  
    ![Новая политика доступа](../../media/Create-an-Access-Policy/ipam_CreateAP_09a.jpg)  
  
## <a name="see-also"></a>См. также:  
[Управление доступом на основе ролей](Role-based-Access-Control.md)  
[Управление IPAM](Manage-IPAM.md)  
  

