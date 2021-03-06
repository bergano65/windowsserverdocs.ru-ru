---
title: winrs
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c370de31-5651-400a-872d-ef229aae2309
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d6ee44cb530614485f0dbd58a9ec13a4788370fe
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71361937"
---
# <a name="winrs"></a>winrs

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Удаленное управление Windows позволяет удаленно управлять и выполнять программы.   
## <a name="syntax"></a>Синтаксис  
```  
winrs [/<parameter>[:<value>]] <command>  
```  
### <a name="parameters"></a>Параметры  

|           Параметр            |                                                                                                                                                                                    Описание                                                                                                                                                                                     |
|--------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      /ремоте:\<конечная точка >       |                                                                                          Указывает целевую конечную точку, используя NetBIOS-имя или стандартное подключение:<br /><br />-   <url>: [\<транспорта>://]\<целевой>[:\<порт>]<br /><br />Если не указано, используется **/r: localhost** .                                                                                          |
|          /уненкриптед          | Указывает, что сообщения удаленной оболочки не будут зашифрованы. Это полезно для устранения неполадок или в случае, когда сетевой трафик уже зашифрован с помощью **IPSec**или когда применяется физическая безопасность.<br /><br />По умолчанию сообщения шифруются с помощью ключей Kerberos или NTLM.<br /><br />Этот параметр командной строки игнорируется, если выбран транспорт HTTPS. |
|     /username:\<имя пользователя >      |                                                                                Указывает имя пользователя в командной строке.<br /><br />Если этот параметр не указан, средство будет использовать проверку подлинности Negotiate или запросить имя.<br /><br />Если указан **/username** , необходимо также указать **/Password** .                                                                                 |
|     /Password:\<пароль >      |                                                                           Задает пароль для командной строки.<br /><br />Если параметр **/Password** не указан, но **/username** имеет значение, средство запросит пароль.<br /><br />Если указан **/Password** , необходимо также указать **/username** .                                                                            |
|      /timeout:\<секунд >       |                                                                                                                                                                             Этот параметр является устаревшим.                                                                                                                                                                             |
|       /Directory: путь к\<>       |                                                                                            Указывает начальный каталог для удаленной оболочки.<br /><br />Если этот параметр не указан, удаленная оболочка будет запускаться в домашнем каталоге пользователя, определенном переменной среды **% UserProfile%** .                                                                                             |
| /енвиронмент:\<строка > =<value> |                                                                          Задает одну переменную среды, которая должна быть задана при запуске оболочки, что позволяет изменять среду по умолчанию для оболочки.<br /><br />Для указания нескольких переменных среды необходимо использовать несколько экземпляров этого переключателя.                                                                          |
|            /ноечо             |                                                                                                    Указывает, что вывод должен быть отключен. Это может потребоваться, чтобы убедиться, что ответы пользователя на удаленные запросы не отображаются локально.<br /><br />По умолчанию echo имеет значение ON.                                                                                                    |
|           /нопрофиле           |                                              Указывает, что профиль пользователя не должен загружаться.<br /><br />По умолчанию сервер попытается загрузить профиль пользователя.<br /><br />Если удаленный пользователь не является локальным администратором в целевой системе, этот параметр будет необходим (по умолчанию это приведет к ошибке).                                               |
|         /алловделегате         |                                                                                                                  Указывает, что учетные данные пользователя можно использовать для доступа к удаленной общей папке, например, на компьютере, отличном от компьютера целевой конечной точки.                                                                                                                   |
|          /Compression          |                                                                           Включите сжатие.  Более старые установки на удаленных компьютерах могут не поддерживать сжатие, поэтому по умолчанию отключено.<br /><br />Значение по умолчанию — OFF, так как старые установки на удаленных компьютерах могут не поддерживать сжатие.                                                                           |
|            /усессл             |                                                                                                               Используйте SSL-соединение при использовании удаленной конечной точки.  Указание этого параметра вместо транспорта **https:** будет использовать порт по умолчанию для **WinRM** по умолчанию.                                                                                                                |
|               /?               |                                                                                                                                                                        Отображение справки в командной строке.                                                                                                                                                                        |

## <a name="remarks"></a>Замечания  
-   Все параметры командной строки принимают либо краткую форму, либо длинную форму. Например, допустимыми являются **/r** и **/ремоте** .  
-   Чтобы завершить команду **/ремоте** , пользователь может ввести **сочетание клавиш CTRL-C** или **Ctrl-Break**, которое будет отправлено удаленной оболочке. Вторая **клавиша CTRL-C** принудительно завершает выполнение **WinRS. exe**.  
-   Для управления активными удаленными оболочками или конфигурацией WinRS используйте средство WinRM.  Псевдоним универсального кода ресурса (URI) для управления активными оболочками — **Shell/cmd**.  Псевдоним URI для конфигурации WinRS — **WinRM/config/WinRS**.  

## <a name="BKMK_Examples"></a>Примеров  
```  
winrs /r:https://contoso.com command  
```  
```  
winrs /r:contoso.com /usessl command  
```  
```  
winrs /r:myserver command  
```  
```  
winrs /r:http://127.0.0.1 command  
```  
```  
winrs /r:http://169.51.2.101:80 /unencrypted command  
```  
```  
winrs /r:https://[::FFFF:129.144.52.38] command  
```  
```  
winrs /r:http://[1080:0:0:0:8:800:200C:417A]:80 command  
```  
```  
winrs /r:https://contoso.com /t:600 /u:administrator /p:$%fgh7 ipconfig  
```  
```  
winrs /r:myserver /env:path=^%path^%;c:\tools /env:TEMP=d:\temp config.cmd  
```  
```  
winrs /r:myserver netdom join myserver /domain:testdomain /userd:johns /passwordd:$%fgh789  
```  
```  
winrs /r:myserver /ad /u:administrator /p:$%fgh7 dir \\anotherserver\share  
```  

## <a name="additional-references"></a>Дополнительная справка  
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)  

