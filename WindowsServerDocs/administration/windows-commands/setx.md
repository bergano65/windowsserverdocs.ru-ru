---
title: setx
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef37482f-f8a8-4765-951a-2518faac3f44
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c206f36e2d0bc947329124b08fb797091e838bcd
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71384028"
---
# <a name="setx"></a>setx



Создает или изменяет переменные среды в пользовательской или системной среде без необходимости программирования или написания сценариев. Команда **Setx** также извлекает значения разделов реестра и записывает их в текстовые файлы.

В разделе [Примеры](#BKMK_examples) показан принцип использования этой команды.

## <a name="syntax"></a>Синтаксис

```
setx [/s <Computer> [/u [<Domain>\]<User name> [/p [<Password>]]]] <Variable> <Value> [/m]
setx [/s <Computer> [/u [<Domain>\]<User name> [/p [<Password>]]]] [<Variable>] /k <Path> [/m]
setx [/s <Computer> [/u [<Domain>\]<User name> [/p [<Password>]]]] /f <FileName> {[<Variable>] {/a <X>,<Y> | /r <X>,<Y> "<String>"} [/m] | /x} [/d <Delimiters>]
```

## <a name="parameters"></a>Параметры

|         Параметр          |                                                                                                                                              Описание                                                                                                                                              |
|----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|       /s \<> компьютера       |                                                                                  Указывает имя или IP-адрес удаленного компьютера. Не используйте обратные косые черты. Значение по умолчанию — имя локального компьютера.                                                                                  |
| /u [\<> домена\]<User name> |                                                                                           Запускает скрипт с учетными данными указанной учетной записи пользователя. Значение по умолчанию — системные разрешения.                                                                                            |
|      /p [\<пароль >]      |                                                                                                         Указывает пароль учетной записи пользователя, указанной в параметре **/u** .                                                                                                         |
|        Переменная \<>         |                                                                                                                 Задает имя переменной среды, которую необходимо задать.                                                                                                                  |
|          \<значение >          |                                                                                                                Задает значение, для которого необходимо задать переменную среды.                                                                                                                 |
|         /k \<путь >         | Указывает, что переменная задается на основе сведений из раздела реестра. В p*ь* используется следующий синтаксис:</br>`\\<HIVE>\<KEY>\...\<Value>`</br>Например, можно указать следующий путь:</br>`HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName` |
|      /f \<имя файла >       |                                                                                                                               Указывает файл, который вы хотите использовать.                                                                                                                                |
|        /a \<X >,<Y>         |                                                                                                                    Задает абсолютные координаты и смещение в качестве параметров поиска.                                                                                                                    |
|   /r \<X >,<Y> "<String>"   |                                                                                                            Задает относительные координаты и смещение от **строки** в качестве параметров поиска.                                                                                                            |
|             /m             |                                                                                                Указывает, что переменная должна быть задана в системной среде. Значение по умолчанию — локальная среда.                                                                                                 |
|             /x             |                                                                                                       Отображает координаты файлов, игнорируя параметры командной строки **/a**, **/r**и **/d** .                                                                                                        |
|      /d \<разделители >      |                    Задает использование разделителей, таких как " **,** " или " **\\** ", в дополнение к четырем встроенным разделителям — пробел, табуляция, ввод и перевод строки. Допустимые разделители включают любой символ ASCII. Максимальное число разделителей равно 15, включая встроенные разделители.                    |
|             /?             |                                                                                                                                 Отображение справки в командной строке.                                                                                                                                  |

## <a name="remarks"></a>Замечания

-   Команда **Setx** аналогична служебной программе UNIX setenv.
-   **Setx** предоставляет единственную командную строку или программный способ для прямого и окончательного задания значений системной среды. Системные переменные среды можно настраивать вручную с помощью **панели управления** или редактора реестра. Команда **Set** , которая является внутренней для интерпретатора команд (cmd. exe), устанавливает переменные среды пользователя только для текущего окна консоли.
-   Команду **Setx** можно использовать для задания значений переменных среды пользователя и системы из одного из трех источников (режимов): режим командной строки, режим реестра или файловый режим.
-   **Setx** записывает переменные в главную среду в реестре. Переменные, заданные с помощью переменных **Setx** , доступны только в окнах командной строки в будущем, а не в текущем командном окне.
-   Единственными поддерживаемыми Hive являются **HKEY_CURRENT_USER** и **HKEY_LOCAL_MACHINE** . REG_DWORD, REG_EXPAND_SZ, REG_SZ и REG_MULTI_SZ являются допустимыми типами данных **RegKey** .
-   Когда вы получаете доступ к **REG_MULTI_SZ** значениям в реестре, извлекается и используется только первый элемент.
-   Нельзя использовать команду **Setx** для удаления значений, которые были добавлены в локальную или системную среду. Для удаления соответствующего значения из локальной среды можно использовать **Set** с именем переменной и без значения.
-   REG_DWORD значения реестра извлекаются и используются в шестнадцатеричном режиме.
-   Файловый режим поддерживает синтаксический анализ только текстовых файлов возврата каретки и перевода строки (CRLF).

## <a name="BKMK_examples"></a>Примеров

Чтобы задать для переменной среды машины в локальной среде значение Brand1, введите:
```
setx MACHINE Brand1
```
Чтобы задать переменную среды компьютера в системной среде на значение Brand1 Computer, введите:
```
setx MACHINE "Brand1 Computer" /m
```
Чтобы задать переменную среды MYPATH в локальной среде для использования пути поиска, определенного в переменной среды PATH, введите:
```
setx MYPATH %PATH%
```
Чтобы задать переменную среды MYPATH в локальной среде для использования пути поиска, определенного в переменной среды PATH, после замены **~** **%** , введите:
```
setx MYPATH ~PATH~ 
```
Чтобы задать переменную среды компьютера в локальной среде для Brand1 на удаленном компьютере с именем COMPUTER1, введите:
```
setx /s computer1 /u maindom\hiropln /p p@ssW23 MACHINE Brand1
```
Чтобы задать переменную среды MYPATH в локальной среде для использования пути поиска, определенного в переменной среды PATH на удаленном компьютере с именем COMPUTER1, введите:
```
setx /s computer1 /u maindom\hiropln /p p@ssW23 MYPATH %PATH%
```
Чтобы задать переменную среды ТЗОНЕ в локальной среде в качестве значения, находящихся в разделе реестра **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\тимезонеинформатион\стандарднаме** , введите:
```
setx TZONE /k HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName 
```
Чтобы задать переменную среды ТЗОНЕ в локальной среде удаленного компьютера с именем COMPUTER1, в значение, найденное в разделе реестра **HKEY_LOCAL_MACHINE \систем\куррентконтролсет\контрол\тимезонеинформатион\стандарднаме** , введите:
```
setx /s computer1 /u maindom\hiropln /p p@ssW23 TZONE /k HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName 
```
Чтобы задать переменную среды сборки в системной среде в качестве значения, находящихся в разделе реестра **HKEY_LOCAL_MACHINE \софтваре\микрософт\виндовснт\куррентверсион\куррентбуилднумбер** , введите:
```
setx BUILD /k "HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\CurrentBuildNumber" /m
```
Чтобы задать переменную среды сборки в системной среде удаленного компьютера с именем COMPUTER1, в качестве значения, находящихся в разделе реестра **HKEY_LOCAL_MACHINE \софтваре\микрософт\виндовснт\куррентверсион\куррентбуилднумбер** , введите:
```
setx /s computer1 /u maindom\hiropln /p p@ssW23  BUILD /k "HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\CurrentBuildNumber" /m
```
Чтобы отобразить содержимое файла с именем ipconfig. out, а также соответствующие координаты содержимого, введите:
```
setx /f ipconfig.out /x
```
Чтобы задать переменную среды reduce в локальной среде до значения, находящейся в координате 5, 11 в файле ipconfig. out, введите:
```
setx IPADDR /f ipconfig.out /a 5,11
```
Чтобы задать переменную среды OCTET1 в локальной среде до значения, находящейся в координате 5, 3 в файле ipconfig. out с разделителями **"# $\*."** , введите:
```
setx OCTET1 /f ipconfig.out /a 5,3 /d "#$*." 
```
Чтобы задать переменную среды ИПГАТЕВАЙ в локальной среде до значения, находящейся в координате 0, 7 по отношению к координате "шлюз" в файле ipconfig. out, введите:
```
setx IPGATEWAY /f ipconfig.out /r 0,7 Gateway 
```
Чтобы отобразить содержимое файла с именем ipconfig. out, а также соответствующие координаты содержимого, на компьютере с именем COMPUTER1 введите:
```
setx /s computer1 /u maindom\hiropln /p p@ssW23 /f ipconfig.out /x 
```

#### <a name="additional-references"></a>Дополнительная справка

[Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)