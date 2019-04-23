---
title: Включение возможности публикации хэша для файловых серверов, не входящих в домен
description: Этот раздел является частью BranchCache развертывания руководство для Windows Server 2016, который показывает, как развернуть BranchCache в режимах распределенный и размещенный кэш, чтобы оптимизировать использование пропускной способности глобальной сети в филиалах
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 11584b73-f9e2-4530-afa5-b8df970e6b24
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 00be97abbd583e4c5e762775ea563ba0720d5142
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59814955"
---
# <a name="enable-hash-publication-for-non-domain-member-file-servers"></a>Включение возможности публикации хэша для файловых серверов, не входящих в домен

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Эту процедуру можно использовать для настройки публикация хэша для BranchCache, с помощью групповой политики с локального компьютера на файловом сервере, на котором работает Windows Server 2016 с **BranchCache для сетевых файлов** службу роли файловых служб роль сервера.  
  
Эта процедура предназначена для использования на файловом сервере не входящего в домен. Если вы выполните эту процедуру на сервере файл домена, а также настроить BranchCache с помощью групповой политики домена, параметры групповой политики домена переопределяют локальные параметры групповой политики.  
  
Членство в группе **Администраторы**, или эквивалентной является минимальным требованием для выполнения этой процедуры.  
  
> [!NOTE]  
> Если у вас есть один или несколько файловых серверов члена домена, можно добавить их в подразделение (OU) в доменных службах Active Directory и затем настроить публикацию хэшей для всех файловых серверов за один раз, вместо настройки по отдельности с помощью групповой политики Каждый файловый сервер. Дополнительные сведения см. в разделе [разрешить публикацию хэшей для файловых серверов член домена](../../branchcache/deploy/Enable-Hash-Publication-for-Domain-Member-File-Servers.md).  
  
### <a name="to-enable-hash-publication-for-one-file-server"></a>Чтобы включить публикацию хэшей для одного файлового сервера  
  
1.  Откройте Windows PowerShell, введите **mmc**и затем нажмите клавишу "ВВОД". Отобразится консоль управления (MMC).  
  
2.  В MMC на **файл** меню, щелкните **Add/Remove Snap-in**. **Добавление или удаление оснасток** откроется диалоговое окно.  
  
3.  В **Добавление или удаление оснасток**в **Доступные оснастки**, дважды щелкните **редактора объектов групповой политики**. Выбрав объект с локального компьютера, откроется мастер групповой политики. Нажмите кнопку **Готово**, а затем — кнопку **ОК**.  
  
4.  В консоли MMC редактора локальных групповых политик разверните следующий путь: **Политика локального компьютера**, **Конфигурация компьютера**, **административные шаблоны**, **сети**, **сервера Lanman**. Нажмите кнопку **сервера Lanman**.  
  
5.  В области сведений дважды щелкните **публикация хэша для BranchCache**. **Публикация хэша для BranchCache** откроется диалоговое окно.  
  
6.  В **публикация хэша для BranchCache** диалоговом окне щелкните **включено**.  
  
7.  В **параметры**, нажмите кнопку **разрешить публикацию хэшей для всех общих папок**, а затем выберите один из следующих:  
  
    1.  Чтобы включить публикацию хэшей для всех общих папок на этом компьютере, щелкните **разрешить публикацию хэшей для всех общих папок**.  
  
    2.  Чтобы включить публикацию хэшей для общих папок, для которых включена BranchCache, щелкните **разрешить публикацию хэшей для всех общих папок, на которых включено BranchCache**.  
  
    3.  Чтобы отменить публикацию хэшей для всех общих папок на компьютере, даже если включены BranchCache к общим файловым ресурсам, нажмите кнопку **отменить публикацию хэшей для всех общих папок**.  
  
8.  Нажмите кнопку **ОК**.  
  

