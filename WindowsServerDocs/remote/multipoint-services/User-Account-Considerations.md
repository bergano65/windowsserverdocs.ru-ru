---
title: Соображения по поводу учетных записей пользователей
description: Предоставляет учетной записи пользователя, имя пользователя и пароль рекомендации по MultiPoint Services
ms.custom: na
ms.prod: windows-server-threshold
ms.technology: multipoint-services
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e225900b-cee9-48c9-b21c-394dc5e72b78
author: lizap
manager: dongill
ms.author: elizapo
ms.date: 08/04/2016
ms.openlocfilehash: 00fb5e83921ba0b8ad86a6f75bdfd7bf16419b73
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59850795"
---
# <a name="user-account-considerations"></a>Соображения по поводу учетных записей пользователей
В этом разделе описываются проблемы, пользователь с правами администратора, следует учесть при создании и администрировании учетных записей пользователей. Вы управление учетными записями пользователей на вкладке "пользователи" в MultiPoint Manager. Дополнительные сведения см. в статье [Управление учетными данными пользователей](Manage-User-Accounts.md).  
  
## <a name="user-account-types"></a>Типы учетных записей пользователей  
Учетная запись пользователя — это коллекция данных, сообщающая системе MultiPoint Services о том, какие файлы и папки доступны пользователю, какие изменения он может вносить в систему MultiPoint Services, а также предпочтения каждого пользователя, такие как фон рабочего стола. Каждый пользователь получает доступ к своей учетной записи по имени пользователя и паролю. MultiPoint Services поддерживает три типа учетных записей пользователей:  
  
-   **Учетные записи пользователя с правами администратора** предназначены для лиц, которые будут использовать MultiPoint Manager и управления системой MultiPoint Services. Дополнительные сведения см. в статье [Создание учетной записи пользователя с правами администратора](Create-an-Administrative-User-Account.md).  
  
-   **Учетные записи обычных пользователей** предназначены для лиц, которые регулярно используют станции, но не могут управлять системой. Как правило, для большинства пользователей системы MultiPoint Services создаются учетные записи обычных пользователей. Дополнительные сведения см. в статье [Создание учетной записи обычного пользователя](Create-a-Standard-User-Account.md).  
  
-   **Учетные записи пользователей MultiPoint Dashboard** предназначены для лиц, которые используют MultiPoint Dashboard для управления сеансами обычных пользователей и могут входить в систему с любой станции. Дополнительные сведения см. в статье [Создание учетной записи пользователя MultiPoint Dashboard](Create-a-MultiPoint-Dashboard-User-Account.md).  
  
## <a name="user-name-and-password-considerations"></a>Рекомендации по именам пользователей и паролям  
Пользователи с правами администратора могут выполнять задачи, затрагивающие всех остальных пользователей системы MultiPoint Services, такие как установка программного обеспечение или изменение параметров безопасности. По этой причине пользователи с правами администратора должны иметь уникальные имена и пароли, известные только им.  
  
Одна из важных особенностей учетных записей состоит в том, что каждой из них присваивается уникальная библиотека **Документы** в проводнике, в которую входит папка **Мои документы**. Если обычные пользователи в вашей системе MultiPoint Services будут хранить свои частные документы в библиотеке **Документы** в проводнике, они также должны входить в систему MultiPoint Services под уникальным именем пользователя и паролем, которые известны только им. Дополнительные сведения о хранении документов в проводнике см. в статье [Управление файлами пользователей](Manage-User-Files.md).  
  
> [!TIP]  
> Для более надежной защиты системы пароли всех пользователей должны храниться в безопасном месте. Надежный пароль — один, который не может быть легко или взломан, имеет по крайней мере восемь символов, не содержит полностью или частично имя учетной записи пользователя и содержит по крайней мере трех из следующих четырех категорий символов: прописные буквы алфавита, нижний регистр символы, цифры и символы на клавиатуре (такие как!, @, #).  
  
## <a name="see-also"></a>См. также  
[Создание учетной записи пользователя с правами администратора](Create-an-Administrative-User-Account.md)  
[Создание учетной записи обычного пользователя](Create-a-Standard-User-Account.md)  
[Управление файлами пользователя](Manage-User-Files.md)
[управление учетными записями пользователей](Manage-User-Accounts.md)