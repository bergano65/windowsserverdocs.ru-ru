---
title: Очистка метаданных сервера AD DS
description: Использование встроенных средств для очистки метаданных от удаленных контроллеров домена
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 11/14/2018
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adds
ms.openlocfilehash: 7c9750a4f59cd17d0495e58dbc2fd8b2d2802c89
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71369534"
---
# <a name="clean-up-active-directory-domain-controller-server-metadata"></a>Очистка метаданных сервера контроллера домен Active Directory

Область применения. Windows Server

Очистка метаданных — это обязательная процедура после принудительного удаления служб домен Active Directory (AD DS). Очистка метаданных выполняется на контроллере домена в домене контроллера домена, который был принудительно удален. Очистка метаданных удаляет данные из AD DS, которые идентифицируют контроллер домена в системе репликации. Очистка метаданных также удаляет подключения репликации файлов (FRS) и распределенная файловая система (DFS) и пытается передавать или захватить роли хозяина операций (также называемых одними гибкими основными операциями или FSMO), которые были отменены доменом Контроллер содержит.

Существует три варианта очистки метаданных сервера.

- Очистка метаданных сервера с помощью средств графического пользовательского интерфейса
- Очистка метаданных сервера с помощью командной строки
- Очистка метаданных сервера с помощью скрипта

> [!NOTE]
> Если при использовании любого из этих методов для очистки метаданных появляется сообщение об ошибке "доступ запрещен", убедитесь, что объект компьютера и объект параметров NTDS контроллера домена не защищены от случайного удаления. Чтобы проверить это, щелкните правой кнопкой мыши объект компьютера или объект NTDS Settings, выберите пункт **Свойства**, щелкните **объект**и снимите флажок **защитить объект от случайного удаления** . В Active Directory "пользователи и компьютеры" откроется вкладка " **объект** " объекта, если щелкнуть " **вид** ", а затем " **Дополнительные функции**".

## <a name="clean-up-server-metadata-using-gui-tools"></a>Очистка метаданных сервера с помощью средств графического пользовательского интерфейса

При использовании средства удаленного администрирования сервера (RSAT) или консоли Active Directory пользователи и компьютеры (DSA. msc), включенной в Windows Server для удаления учетной записи компьютера контроллера домена из подразделения Контроллеры домена (OU), Очистка метаданных сервера выполняется автоматически. До выхода Windows Server 2008 необходимо было выполнить отдельную процедуру очистки метаданных.

Можно также использовать консоль сайтов и служб Active Directory (Dssite. msc) для удаления учетной записи компьютера контроллера домена, которая также автоматически завершает очистку метаданных. Однако Active Directory сайты и службы удаляют метаданные автоматически только при первом удалении объекта NTDS Settings под учетной записью компьютера в Dssite. msc.

Если вы используете версии DSA. msc или Dssite. msc для Windows Server 2008 или более поздних версий, метаданные можно автоматически очищать для контроллеров домена под управлением более ранних версий операционных систем Windows.

Членство в группах **"Администраторы домена" или "** эквивалентное" является минимальным требованием для выполнения этих процедур.

## <a name="clean-up-server-metadata-using-activedirectory-users-and-computers"></a>Очистка метаданных сервера с помощью Active Directory пользователей и компьютеров

1. Откройте оснастку **Пользователи и компьютеры Active Directory**.
2. Если вы определили партнеров репликации при подготовке к этой процедуре и не подключены к партнеру репликации удаленного контроллера домена, чьи метаданные будут удалены, щелкните правой кнопкой мыши узел **Active Directory пользователи и компьютеры** . , а затем выберите пункт **изменить контроллер домена**. Щелкните имя контроллера домена, из которого необходимо удалить метаданные, а затем нажмите кнопку **ОК**.
3. Разверните домен контроллера домена, который был принудительно удален, и выберите пункт **контроллеры домена**.
4. В области сведений щелкните правой кнопкой мыши объект компьютера контроллера домена, метаданные которого необходимо очистить, и выберите команду **Удалить**.
5. В диалоговом окне **домен Active Directory службы** убедитесь, что отображается имя контроллера домена, который вы хотите удалить, и нажмите кнопку **Да** , чтобы подтвердить удаление объекта компьютера.
6. В диалоговом окне **Удаление контроллера домена** выберите **этот контроллер домена постоянно в автономном режиме, и его нельзя будет понизить с помощью мастер установки доменных служб Active Directory (Dcpromo)** , а затем нажать кнопку **Удалить**.
7. Если контроллер домена является сервером глобального каталога, в диалоговом окне **Удаление контроллера домена** нажмите кнопку **Да** , чтобы продолжить удаление.
8. Если контроллер домена в настоящее время содержит одну или несколько ролей хозяина операций, нажмите кнопку **ОК** , чтобы переместить роль или роли на отображаемый контроллер домена. Этот контроллер домена нельзя изменить. Если вы хотите переместить роль на другой контроллер домена, необходимо переместить роль после завершения процедуры очистки метаданных сервера.

## <a name="clean-up-server-metadata-using-activedirectory-sites-and-services"></a>Очистка метаданных сервера с помощью Active Directory сайтов и служб

1. Откройте компонент "Active Directory — сайты и службы".
2. Если вы определили партнеров репликации в процессе подготовки к этой процедуре и если вы не подключены к партнеру репликации удаленного контроллера домена, чьи метаданные удаляются, щелкните правой кнопкой мыши **Active Directory сайты и службы**, а затем затем щелкните **изменить контроллер домена**. Щелкните имя контроллера домена, из которого необходимо удалить метаданные, а затем нажмите кнопку **ОК**.
3. Разверните узел контроллера домена, который был принудительно удален, разверните узел **серверы**, разверните имя контроллера домена, щелкните правой кнопкой мыши объект Параметры NTDS и выберите команду **Удалить**.
4. В диалоговом окне **Active Directory сайты и службы** нажмите кнопку **Да** , чтобы подтвердить удаление параметров NTDS.
5. В диалоговом окне **Удаление контроллера домена** выберите **этот контроллер домена постоянно в автономном режиме, и его нельзя будет понизить с помощью мастер установки доменных служб Active Directory (Dcpromo)** , а затем нажать кнопку **Удалить**.
6. Если контроллер домена является сервером глобального каталога, в диалоговом окне **Удаление контроллера домена** нажмите кнопку **Да** , чтобы продолжить удаление.
7. Если контроллер домена в настоящее время содержит одну или несколько ролей хозяина операций, нажмите кнопку **ОК** , чтобы переместить роль или роли на отображаемый контроллер домена.
8. Щелкните правой кнопкой мыши контроллер домена, который был принудительно удален, и выберите команду Удалить.
9. В диалоговом окне **домен Active Directory службы** нажмите кнопку **Да** , чтобы подтвердить удаление контроллера домена.

## <a name="clean-up-server-metadata-using-the-command-line"></a>Очистка метаданных сервера с помощью командной строки

В качестве альтернативы можно очищать метаданные с помощью программы Ntdsutil. exe, программы командной строки, устанавливаемой автоматически на всех контроллерах домена и серверах, на которых установлены службы Active Directory облегченного доступа к каталогам (AD LDS). Ntdsutil. exe также доступен на компьютерах с установленным RSAT.

## <a name="to-clean-up-server-metadata-by-using-ntdsutil"></a>Очистка метаданных сервера с помощью программы Ntdsutil

1. Откройте командную строку от имени администратора: В меню **Пуск** щелкните правой кнопкой мыши пункт **Командная строка**и выберите команду **Запуск от имени администратора**. Если откроется диалоговое окно **контроль учетных записей пользователей** , укажите учетные данные администратора предприятия, если это необходимо, а затем нажмите кнопку **продолжить**.
2. В командной строке введите следующую команду и нажмите клавишу ВВОД:

   `ntdsutil`

3. В командной строке `ntdsutil:` введите следующую ниже команду, а затем нажмите клавишу ВВОД.

   `metadata cleanup`

4. В командной строке `metadata cleanup:` введите следующую ниже команду, а затем нажмите клавишу ВВОД.

   `remove selected server <ServerName>`

5. В **диалоговом окне Конфигурация удаления сервера**просмотрите сведения и предупреждение, а затем нажмите кнопку **Да** , чтобы удалить объект сервера и метаданные.

   На этом этапе программа Ntdsutil подтверждает, что контроллер домена был успешно удален. Если появится сообщение об ошибке, указывающее, что объект не найден, возможно, контроллер домена был удален ранее.

6. В приглашении введите`quit`и нажмите клавишу ВВОД. `ntdsutil:` `metadata cleanup:`

7. Чтобы подтвердить удаление контроллера домена, выполните следующие действия.

   Откройте Active Directory пользователи и компьютеры. В домене удаленного контроллера домена щелкните **контроллеры домена**. В области сведений не должен отображаться объект для удаляемого контроллера домена.

   Откройте Active Directory сайты и службы. Перейдите к контейнеру **серверы** и убедитесь, что объект сервера для контроллера домена, который вы удалили, не содержит объект параметров NTDS. Если под объектом сервера не отображаются дочерние объекты, можно удалить объект сервера. Если отображается дочерний объект, не удаляйте серверный объект, так как этот объект используется другим приложением.

## <a name="see-also"></a>См. также

* [Понижение уровня контроллеров доменов](Demoting-Domain-Controllers-and-Domains--Level-200-.md)
* [Справочник по командам Ntdsutil](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753343(v=ws.10))
