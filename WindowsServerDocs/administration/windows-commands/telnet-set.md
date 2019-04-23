---
title: набор Telnet
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 67316b5f-9c6f-43e3-86d5-dcff9ae2ac3e vhorne
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 18a49f2e4629b1410a1cec40fe77077c2988dce2
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59836125"
---
# <a name="telnet-set"></a>Telnet: задать

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Задает параметры.   
## <a name="syntax"></a>Синтаксис  
```  
set [bsasdel] [crlf] [delasbs] [escape <Char>] [localecho] [logfile <FileName>] [logging] [mode {console | stream}] [ntlm] [term {ansi | vt100 | vt52 | vtnt}] [?]  
```  
### <a name="parameters"></a>Параметры  
|Параметр|Описание|  
|-------|--------|  
|bsasdel|Отправляет **Backspace** как **удалить**.|  
|CRLF|Отправляет CR и LF (0x0D, 0 x 0A) при **ввод** клавиши. Известный как новый режим строки.|  
|delasbs|Отправляет **удалить** как **Backspace**.|  
|escape <Character>|Задает escape-символа, используемое для ввода строки клиента telnet. Escape-символ может быть один символ, или он может представлять собой сочетание **CTRL** ключа и символ. Чтобы задать сочетание ключ элемента управления, удерживая нажатой **CTRL** ключа при вводе символ, который вы хотите назначить.|  
|локального|Включает отображение ввода.|  
|файл журнала <FileName>|Журналы в текущем сеансе telnet к локальному файлу. Ведение журнала начинается автоматически, если выбран этот параметр.|  
|logging|Включение ведения журнала. Если файл журнала не установлен, появится сообщение об ошибке.|  
|Режим {консоли &#124; экрана}|Задает режим работы.|  
|NTLM|Включает проверку подлинности NTLM.|  
|Термин {ansi &#124; vt100 &#124; vt52 &#124; vtnt}|Задает тип терминала.|  
|?|Отображает справку для этой команды.|  
## <a name="remarks"></a>Примечания  
1.  Можно использовать **незаданного** команду, чтобы отключить параметр, который был ранее установлен.  
2.  В локализованных версиях telnet **набор кодов** <option> доступен. **Набор кодов** <option> задает текущий код, задайте параметру, который может принимать одно из следующих: **shift JIS**, **японский EUC**, **кандзи JIS**, **JIS Кандзи (78)**, **кандзи DEC**, **кандзи NEC**. Следует задать тот же код на удаленном компьютере.  
## <a name="BKMK_Examples"></a>Примеры  
Задать файл журнала и начать протоколирование для tnlog.txt локального файла  
```  
set logfile tnlog.txt  
```  
## <a name="additional-references"></a>Дополнительные ссылки  
-   [Ключ синтаксиса командной строки](command-line-syntax-key.md)  