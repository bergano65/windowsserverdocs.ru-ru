---
title: Настройка WEB1 для распространения списков отзыва сертификатов (CRL)
description: Этот раздел является частью руководства развертывание сервера сертификатов для развертывания беспроводных и проводных сетей 802.1 X
manager: brianlic
ms.topic: article
ms.assetid: fa4a8c41-8c2a-425c-8511-736fe5d196ac
ms.prod: windows-server-threshold
ms.technology: networking
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 57fa45eff87a1f0cdaae8b780d7f605e54ff6871
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839195"
---
# <a name="configure-web1-to-distribute-certificate-revocation-lists-crls"></a>Настройка WEB1 для распространения списков отзыва сертификатов (CRL)

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Эту процедуру можно использовать для настройки WEB1 для распространения списков отзыва сертификатов веб-сервера.  
  
В расширениях корневого ЦС, было отмечено, что список отзыва Сертификатов из корневого ЦС будет доступен по https://pki.corp.contoso.com/pki. В настоящее время не виртуального каталога PKI на WEB1, поэтому его необходимо создать.  
  
Для выполнения этой процедуры необходимо быть членом **"Администраторы домена"**.  
  
> [!NOTE]  
> В следующей процедуре замените имя учетной записи пользователя, имя веб-сервера, имена папок и расположения и других значений те, которые подходят для развертывания.  
  
#### <a name="to-configure-web1-to-distribute-certificates-and-crls"></a>Для настройки WEB1 для распределения сертификатов и списков отзыва сертификатов  
  
1.  На WEB1 запустите Windows PowerShell от имени администратора, введите `explorer c:\`, и нажмите клавишу ВВОД. Проводник Windows открывает на диске C.   
  
2.  Создайте новую папку PKI на диске C:. Для этого щелкните **Домой**, затем щелкните **Создать папку**. Новая папка создается с временной выделенным именем. Введите **pki** и нажмите клавишу ВВОД.  
  
3.  В обозревателе Windows щелкните правой кнопкой мыши папку, вы только что создали, наведите курсор мыши **совместное использование с**, а затем нажмите кнопку **конкретные пользователи**. **Общий доступ к файлам** откроется диалоговое окно.  
  
4.  В **общий доступ к файлам**, тип **Издатели сертификатов**, а затем нажмите кнопку **добавить**. Издатели сертификатов группа будет добавлена в список. В списке в **уровень разрешений**, щелкните стрелку рядом с полем **Издатели сертификатов**, а затем нажмите кнопку **чтения и записи**. Нажмите кнопку **общего ресурса**, а затем нажмите кнопку **сделать**.  
  
5.  Закройте Windows Explorer.  
  
6.  Откройте консоль IIS. В Диспетчере серверов щелкните **Средства** и выберите **Диспетчер Internet Information Services (IIS)**.  
  
7.  В дереве консоли диспетчера Internet Information Services (IIS), разверните **WEB1**. Если появится приглашение приступить к работе с веб-платформой Майкрософт, щелкните **Отмена**.  
  
8.  Разверните **Сайты**, щелкните правой кнопкой мыши **Веб-сайт по умолчанию**, затем щелкните **Добавить виртуальный каталог**.  
  
9. В **псевдоним**, тип **pki**. В **физический путь** тип **C:\pki**, затем нажмите кнопку **ОК**.  
  
10. Разрешите анонимный доступ к виртуальному каталогу инфраструктуры открытых ключей, чтобы любой клиент мог проверить срок действия сертификатов ЦС и списки отзыва сертификатов. Для этого сделайте следующее:  
  
    1.  В области **Подключения** убедитесь, что выбрано **pki**.  
  
    2.  В разделе **Домашняя страница pki** щелкните **Проверка подлинности**.  
  
    3.  В области **Действия** щелкните **Изменение разрешений**.  
  
    4.  На вкладке **Безопасность** щелкните **Изменить**.  
  
    5.  В диалоговом окне **Разрешения для pki** щелкните **Добавить**.  
  
    6.  В **Выбор пользователей, компьютеров, учетных записей служб или групп**, тип **анонимный вход; Все** и нажмите кнопку **проверить имена**. Нажмите кнопку **ОК**.  
  
    7.  Нажмите кнопку **OK** в диалоговом окне **Выбор пользователей, компьютеров, учетных записей служб или групп**.  
  
    8.  Нажмите кнопку **OK** в диалоговом окне **Разрешения для pki**.  
  
11. Нажмите кнопку **OK** в диалоговом окне **Свойства pki**.  
  
12. В области **Домашняя страница pki** дважды щелкните **Фильтрация запросов**.  
  
13. Вкладка **Расширения имен файлов** выбирается по умолчанию в области **Фильтрация запросов**. В области **Действия** щелкните **Изменить параметры компонента**.  
  
14. Во вкладке **Изменение параметров фильтрации запросов**выберите **Разрешить двойное преобразование** и нажмите кнопку **OK**.  
  
15. В консоли MMC диспетчера Internet Information Services (IIS) щелкните имя вашего веб-сервера. Например, если веб-сервер имеет имя WEB1, щелкните **WEB1**.  
  
16. В **действия**, нажмите кнопку **перезапустите**. Интернет-служб остановки и перезапуска.  
  
