---
title: Отмена регистрации сервера политики сети в домене Active Directory
description: Этот раздел можно использовать для регистрации сервера, на котором выполняется сервер политики сети, в Windows Server 2016 в домене по умолчанию NPS или в другом домене.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 68a94616-3c29-45bd-bd33-e4c578f119e1
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 3225c42ab14e2ea1bc283f520b14c09ebc2254c4
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396081"
---
# <a name="unregister-an-nps-from-an-active-directory-domain"></a>Отмена регистрации сервера политики сети в домене Active Directory

>Относится к: Windows Server (Semi-Annual Channel), Windows Server 2016

В процессе управления развертыванием NPS может оказаться полезным переместить сервер политики сети в другой домен, заменить NPS или снять с учета NPS. 

При перемещении или списании NPS можно отменить регистрацию сервера политики сети в доменах Active Directory, в которых NPS имеет разрешение на чтение свойств учетных записей пользователей в Active Directory.

Выполнить эти операции может только член группы **Администраторы** или пользователь с аналогичными правами.

## <a name="to-unregister-an-nps"></a>Отмена регистрации сервера политики сети

1. На контроллере домена в диспетчер сервера выберите **средства**, а затем **Active Directory пользователи и компьютеры**. Откроется консоль Active Directory пользователи и компьютеры.

2. Щелкните **Пользователи**, а затем дважды щелкните **Серверы RAS и IAS**.

3. Перейдите на вкладку **члены** , а затем выберите NPS, для которого требуется отменить регистрацию.

4. Нажмите кнопку **Удалить**, выберите **Да**, а затем нажмите кнопку **ОК**.

