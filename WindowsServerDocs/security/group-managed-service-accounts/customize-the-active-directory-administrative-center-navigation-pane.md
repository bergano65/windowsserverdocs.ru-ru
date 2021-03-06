---
title: Настройка области навигации центр администрирования Active Directory
ms.prod: windows-server
description: Безопасность Windows Server
ms.custom: na
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.assetid: c9933d16-e153-435a-b5b7-3e594db42d5c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: 63038014207acd3846cb8db20c7836718615df51
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403757"
---
# <a name="customize-the-active-directory-administrative-center-navigation-pane"></a>Настройка области навигации центр администрирования Active Directory

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

  Просмотреть панель навигации центр администрирования Active Directory можно с помощью древовидного представления, похожего на дерево консоли Active Directory пользователи и компьютеры, или с помощью представления списка.

 Независимо от того, используется ли представление в виде дерева или списка, вы можете настроить панель навигации центр администрирования Active Directory в любое время, добавив различные контейнеры из локального домена или любого внешнего домена \(другими доменами, которые имеют установленное отношение доверия с локальным доменом\) в область навигации в качестве отдельных узлов. Настройка области навигации центр администрирования Active Directory обеспечивает более быстрый доступ к Active Directory объектам. Дополнительные сведения см. [в разделе Управление различными доменами в центр администрирования Active Directory](manage-different-domains-in-active-directory-administrative-center.md).

 Для более подробной настройки области навигации можно переименовывать или удалять добавленные вручную узлы области, создавать копии узлов или перемещать их вверх и вниз в области.

> [!NOTE]
>  Узел локального домена по умолчанию нельзя настроить.

### <a name="to-customize-the-active-directory-administrative-center-navigation-pane"></a>Настройка области навигации центр администрирования Active Directory

1. В области навигации центр администрирования Active Directory правой кнопкой мыши\-щелкните узел, который нужно изменить. Можно изменить расположение или имя узла, а также создать его копию.

2. Щелкните одну из следующих команд:

   -   **Имени**

   -   **Создание повторяющегося узла**

   -   **Удалить**

   -   **Вверх**

   -   **Переместить вниз**

   Используя представление списка, можно воспользоваться преимуществами недавно использовавшихся \(списка MRU\). Список MRU автоматически появится в узле навигации при посещении хотя бы одного контейнера в этом узле навигации. Можно также просмотреть текущий список MRU, развернув панель навигации в верхней части окна центр администрирования Active Directory. Список MRU всегда содержит последние три контейнера, посещенных в определенном узле навигации. При выборе любого контейнера он добавляется на верхнюю позицию списка часто используемых элементов, а последний контейнер удаляется из списка.

  

