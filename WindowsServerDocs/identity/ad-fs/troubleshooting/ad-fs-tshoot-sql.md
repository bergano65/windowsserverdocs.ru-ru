---
title: Устранение неполадок AD FS. Подключение SQL
description: В этом документе описывается устранение различных аспектов AD FS
author: billmath
ms.author: billmath
manager: mtillman
ms.date: 01/12/2017
ms.topic: article
ms.prod: windows-server
ms.technology: identity-adfs
ms.openlocfilehash: 09d61292b91c83466f9770184d431b3e6d627dca
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71385439"
---
# <a name="ad-fs-troubleshooting---sql-connectivity"></a>Устранение неполадок AD FS. Подключение SQL
AD FS предоставляет возможность использовать удаленный SQL Server для данных AD FS фермы.  Если серверы AD FS в ферме не могут взаимодействовать с серверными серверами SQL Server, вы увидите проблемы.  В следующем документе приводятся некоторые основные шаги по проверке взаимодействия с внутренними серверами.

## <a name="acquire-the-sql-database-connection-string"></a>Получение строки подключения к базе данных SQL
Первое, что нужно проверить при проверке возможности подключения к SQL, — это, если AD FS имеет правильные сведения о соединении SQL.  Это можно сделать с помощью PowerShell.

### <a name="to-acquire-the-sql-connection-string"></a>Получение строки подключения SQL
1.  Открыть Windows PowerShell
2. Введите следующее: `$adfs = gwmi -Namespace root/ADFS -Class SecurityTokenService` и нажмите клавишу ВВОД.
3. Введите следующее: `$adfs.ConfigurationDatabaseConnectionString` и нажмите клавишу ВВОД.
4. Вы должны увидеть сведения о строке подключения.
![](media/ad-fs-tshoot-sql/sql2.png)

## <a name="create-a-universal-data-link-udl-file-to-test-connectivity"></a>Создайте файл универсальной связи данных (UDL) для проверки подключения.
Файл универсальной связи данных или UDL-файл — это, по сути, текстовый файл, содержащий строку подключения к базе данных.  Используя полученные данные, можно проверить, отвечает ли SQL Server на подключения.

### <a name="to-create-a-udl-file-to-test-connectivity"></a>Создание файла UDL для проверки подключения

1. Откройте Блокнот и сохраните файл с именем Test. udl.  Убедитесь, что **все файлы** выбраны из раскрывающегося списка для **типа "Сохранить как**".
2. Дважды щелкните Test. udl.
3. Введите следующие сведения: a. **Выберите или введите имя сервера:**  Используйте источник данных из строки подключения выше b. **Введите данные для входа на сервер:**  Используйте учетную запись службы AD FS или учетную запись с разрешениями на удаленный вход.  Если учетная запись является учетной записью Windows, используйте встроенную проверку подлинности, введите имя пользователя и пароль.
    в. **Выберите базу данных на сервере:** Используйте исходный каталог из приведенной выше строки.  Пример: AdfsConfigurationV3.
   ![проверить](media/ad-fs-tshoot-sql/sql4.png) подключения
1. Нажмите кнопку **проверить соединение**.</br>
![успешно](media/ad-fs-tshoot-sql/sql3.png)

## <a name="use-sql-server-management-studio-to-test-connectivity"></a>Использование SQL Server Management Studio для проверки подключения
Кроме того, можно [скачать](https://go.microsoft.com/fwlink/?linkid=864329) и установить SSMS для проверки подключения к базе данных.

### <a name="to-test-connectivity-with-ssms"></a>Проверка подключения с помощью SSMS
1. Скачайте и установите SQL Server Management Studio.
![Установить](media/ad-fs-tshoot-sql/sql5.png)
1. Откройте SSMS, введите имя сервера.  Источник данных выше.
2. Используйте учетную запись службы AD FS или учетную запись с разрешениями на удаленный вход.  Если учетная запись является учетной записью Windows, используйте встроенную проверку подлинности, введите имя пользователя и пароль.
![подключиться](media/ad-fs-tshoot-sql/sql6.png)
1. Вы должны увидеть заполненную левую часть.  Разверните узел базы данных и убедитесь, что отображаются AD FS базы данных.
базы данных AD FS ![](media/ad-fs-tshoot-sql/sql7.png)

## <a name="next-steps"></a>Дальнейшие действия

- [Устранение неполадок в AD FS](ad-fs-tshoot-overview.md)