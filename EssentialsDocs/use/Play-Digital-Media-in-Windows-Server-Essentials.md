---
title: "Воспроизведение мультимедиа в Windows Server Essentials"
description: "Описывается, как использовать Windows Server Essentials"
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5f570492-ee21-471b-92c1-3fd9bfb84f55
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 8228d0b17a58858ed893181ddceb465715ffdeb5
ms.sourcegitcommit: db290fa07e9d50686667bfba3969e20377548504
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/12/2017
---
# <a name="play-digital-media-in-windows-server-essentials"></a>Воспроизведение мультимедиа в Windows Server Essentials

>Область применения: Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Цифрового мультимедиа понимается аудио, видео и фотографий содержимое, которое цифровой сжатых.  Windows Server Essentials позволяет сетевым компьютерам и некоторым сетевым устройствам мультимедиа воспроизводить файлы цифрового мультимедиа, которые хранятся на сервере.  
  
 Следующие разделы содержат сведения о доступе и воспроизведение файлов мультимедиа, которые хранятся на Windows Server Essentials:  
  

-   [Обзор цифрового мультимедиа](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_1)  
  
-   [Воспроизведение и общий доступ к цифровому мультимедиа](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2)  
  
-   [Воспроизведение общих файлов мультимедиа из удаленного расположения](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [Добавление файлов цифрового мультимедиа на сервер](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_4)  
  
-   [Параметры формата загрузки](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [Средство отправки файлов](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_6)  
  
-   [Просматривать общие файлы цифрового мультимедиа](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_7)  

-   [Обзор цифрового мультимедиа](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_1)  
  
-   [Воспроизведение и общий доступ к цифровому мультимедиа](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2)  
  
-   [Воспроизведение общих файлов мультимедиа из удаленного расположения](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_3)  
  
-   [Добавление файлов цифрового мультимедиа на сервер](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_4)  
  
-   [Параметры формата загрузки](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_5)  
  
-   [Средство отправки файлов](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_6)  
  
-   [Просматривать общие файлы цифрового мультимедиа](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_7)  

  
##  <a name="BKMK_1"></a>Обзор цифрового мультимедиа  
 Цифрового мультимедиа понимается аудио, видео и фотографий содержимое, прошедшее (цифровое сжатие). Кодирование содержимого подразумевает преобразование аудио и видео в файл цифрового мультимедиа, например файл Windows Media. После кодирования цифрового мультимедиа его легко управлять, распределенных и воспроизводить на компьютерах, а также передавать по компьютерным сетям.  
  
 Примеры типов цифрового мультимедиа: Windows Media Audio (WMA), Windows Media Video (WMV), MP3, JPEG и AVI. Сведения о поддерживаемых проигрывателем Windows Media типах цифрового мультимедиа см. в разделе [типы файлов, поддерживаемые проигрывателем Windows Media](https://support.microsoft.com/kb/316992).  
  
### <a name="why-would-i-want-to-stream-my-digital-media"></a>Зачем выполнять потоковую передачу цифрового мультимедиа?  
 Многие хранят музыку, видео и изображения в общих папках в Windows Server Essentials. Могут возникнуть ситуации, когда нужно сделать следующие:  
  
-   **Смотреть видео**. Сервер можно использовать для хранения и потоковой передачи крупных коллекций видео и записанных ТВ-шоу на компьютер или другие воспроизведения устройств в сети. Можно осуществлять потоковую передачу видео на Xbox 360 или на компьютер с помощью проигрывателя Windows Media.  
  
-   **Воспроизведение музыки**. При включении общего доступа к мультимедиа для **Музыка** общей папки осуществлять доступ к музыке с устройств, поддерживающих Windows Media Connect. Необходимо включить или не настроить все учетные записи пользователей для потоковой передачи из **Музыка** общей папки, после включения общего доступа.  
  
-   **Представить слайдшоу из фото**. Вы можете хранить цифровые фотографии в **фотографии** общей папки на сервере, а затем получить к ним доступ с любого компьютера или с Xbox 360, подключенного к ТВ дома или в офисе. После можно просматривать слайдшоу из фото, а экран ТВ превращается в огромную рамку для фотографий.  
  
### <a name="sharing-copy-protected-media"></a>Общий доступ к защищенному от копирования мультимедиа  
  Windows Server Essentials не поддерживает общий доступ к защищенному от копирования мультимедиа. Сюда относится музыка, приобретенная через музыкальные онлайн-магазины.  
  
 Copy-protected мультимедиа можно воспроизвести только на компьютере или устройстве, использованном для его приобретения. Защита от копирования не позволяет воспроизводить мультимедиа более чем на одном компьютере или устройстве, даже если копировать мультимедиа на сервер и воспроизводить его оттуда. Тем не менее можно сохранить защищенное от копирования мультимедиа на Windows Server Essentials и продолжить воспроизведение мультимедиа на компьютере или устройстве, использованном для его приобретения.  
  
##  <a name="BKMK_2"></a>Воспроизведение и общий доступ к цифровому мультимедиа  
 После настройки сети и успешного подключения компьютеров и мультимедийных устройств к сети сервера, поиск любых файлов мультимедиа, которые вы храните и совместно использовать на сервере.  
  
> [!NOTE]
>  Текущий список устройств воспроизведения и приема мультимедиа, совместимых с Windows Server Essentials см. в разделе [центре совместимости Windows](https://www.microsoft.com/windows/compatibility/CompatCenter/Home).  
  
 Можно использовать любой из следующих способов для поиска и воспроизведения файлов мультимедиа, которые хранятся на вашем сервере:  
  

-   [Поиск и воспроизведение файлов мультимедиа в Windows Server Essentials с компьютера или из мультимедийного проигрывателя в сети](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1)  
  
-   [Отправка файлов мультимедиа на Windows Server Essentials в проигрыватель Windows Media, Xbox 360 или сетевой мультимедийный проигрыватель в сети](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SendToDevice)  

-   [Поиск и воспроизведение файлов мультимедиа в Windows Server Essentials с компьютера или из мультимедийного проигрывателя в сети](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1)  
  
-   [Отправка файлов мультимедиа на Windows Server Essentials в проигрыватель Windows Media, Xbox 360 или сетевой мультимедийный проигрыватель в сети](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SendToDevice)  

  
###  <a name="BKMK_2.1"></a>Поиск и воспроизведение файлов мультимедиа в Windows Server Essentials с компьютера или из мультимедийного проигрывателя в сети  
 Если ваше устройство присоединяется к сети Windows Server Essentials, можно найти и воспроизведение файлов мультимедиа в любой из следующих способов:  
  

-   [Поиск и воспроизведение файлов мультимедиа с компьютера, на котором работает Windows Media Center](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_WMC)  
  
-   [Поиск и воспроизведение файлов мультимедиа с компьютера под управлением Windows с помощью проигрывателя Windows Media](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_MWP)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью Xbox 360](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Xbox)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью других цифровой проигрывателей или приемников мультимедиа, совместимых с Windows Server Essentials](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Other)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью функции общих папок панели запуска](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SharedFolders)  
  
-   [Поиск и воспроизведение общего мультимедийного содержимого с помощью удаленного веб-доступа](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_RWA2)  

-   [Поиск и воспроизведение файлов мультимедиа с компьютера, на котором работает Windows Media Center](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_WMC)  
  
-   [Поиск и воспроизведение файлов мультимедиа с компьютера под управлением Windows с помощью проигрывателя Windows Media](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_MWP)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью Xbox 360](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Xbox)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью других цифровой проигрывателей или приемников мультимедиа, совместимых с Windows Server Essentials](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_Other)  
  
-   [Поиск и воспроизведение файлов мультимедиа с помощью функции общих папок панели запуска](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_SharedFolders)  
  
-   [Поиск и воспроизведение общего мультимедийного содержимого с помощью удаленного веб-доступа](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_RWA2)  

  
####  <a name="BKMK_WMC"></a>Поиск и воспроизведение файлов мультимедиа с компьютера, на котором работает Windows Media Center  
  
1.  Нажмите кнопку **запустить**, нажмите кнопку **все программы**, а затем нажмите кнопку **Windows Media Center**.  
  
2.  На **Windows Media Center** странице, найдите тип носителя для поиска и щелкните библиотеку мультимедиа.  
  
3.  Выполните поиск файла заинтересованы в, или нажмите кнопку вручную **поиска** и введите имя файла, который нужно найти.  
  
4.  Щелкните образ файла мультимедиа, чтобы просмотреть или воспроизвести этот файл.  
  
####  <a name="BKMK_MWP"></a>Поиск и воспроизведение файлов мультимедиа с компьютера под управлением Windows с помощью проигрывателя Windows Media  
  
-   Для компьютера или устройства мультимедиа откройте **проигрывателя Windows Media** и выполните поиск библиотеки мультимедиа.  
  
    > [!NOTE]
    >  Конкретные действия поиска зависят от версии проигрывателя Windows Media, которую вы используете. Дополнительные сведения см. в справке для используемой вами версии.  
  
####  <a name="BKMK_Xbox"></a>Поиск и воспроизведение файлов мультимедиа с помощью Xbox 360  
  
1.  Подключите свою консоль Xbox 360 к домашней сети с помощью проводного или беспроводного подключения.  
  
2.  На компьютере под управлением Windows Server Essentials включите общий доступ к мультимедиа. Дополнительные сведения см. в разделе [Включение и отключение потоковой передачи мультимедиа](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md#BKMK_4).  
  
3.  Для воспроизведения файлов мультимедиа с помощью консоли Xbox 360:  
  
    1.  Перейдите в раздел **Мой Xbox**, а затем выберите **видеотека**, **фонотека**, или **Галерея**в зависимости от используемого типа носителя, вы хотите просмотреть или воспроизвести.  
  
    2.  Выберите имя вашего сервера.  
  
        > [!NOTE]
        >  Если имя сервера не указано, выберите **компьютера**, а затем нажмите кнопку **проверить подключение**.  
  
    3.  Просмотрите список файлов и выберите элемент, который требуется воспроизвести.  
  
####  <a name="BKMK_Other"></a>Поиск и воспроизведение файлов мультимедиа с помощью других цифровой проигрывателей или приемников мультимедиа, совместимых с Windows Server Essentials  
  
1.  Перейдите в раздел [центре совместимости Windows](https://www.microsoft.com/windows/compatibility/CompatCenter/Home) и убедитесь, что мультимедийный проигрыватель или приемник отображается в списке совместимых устройств.  
  
2.  Поскольку действия поиска зависят от используемого мультимедийного проигрывателя, в справке для вашего устройства, подробные инструкции.  
  
####  <a name="BKMK_SharedFolders"></a>Поиск и воспроизведение файлов мультимедиа с помощью функции общих папок панели запуска  
  
1.  Войдите в панель запуска Windows Server Essentials.  
  
2.  С помощью панели запуска щелкните **общих папок**. Окно проводника Windows открывает и отображает общие папки на сервере.  
  
3.  В **поиска** введите имя файла мультимедиа. Отображаются результаты запроса поиска.  
  
    > [!NOTE]
    >  В качестве альтернативы можно дважды щелкнуть общую папку, чтобы просмотреть ее содержимое.  
  
####  <a name="BKMK_RWA2"></a>Поиск и воспроизведение общего мультимедийного содержимого с помощью удаленного веб-доступа  
  
1.  Войдите в систему удаленного веб-доступа.  
  
2.  Нажмите кнопку **общих папок**. **Общих папок** раздел веб-страницы отображает список общих папок на сервере.  
  
3.  Дважды щелкните папку, чтобы просмотреть содержимое папки.  
  
###  <a name="BKMK_SendToDevice"></a>Отправка файлов мультимедиа на Windows Server Essentials в проигрыватель Windows Media, Xbox 360 или сетевой мультимедийный проигрыватель в сети  
 Используйте **проигрывателя Windows Media** для поиска файла мультимедиа, который вы хотите. Щелкните правой кнопкой мыши файл носителя и нажмите кнопку **воспроизведения на** отправить файл мультимедиа на сетевое мультимедийное устройство.  
  
##  <a name="BKMK_3"></a>Воспроизведение общих файлов мультимедиа из удаленного расположения  
 Можно воспроизводить файлы мультимедиа, находясь за пределами вашей сети Windows Server Essentials с помощью удаленного веб-доступа. Для поиска и воспроизведения общих файлов мультимедиа, сохраненные на сервере, можно использовать сотовый телефон, удаленный компьютер или мультимедийный проигрыватель.  
  
#### <a name="to-play-shared-media-files-when-you-are-away-from-the-network"></a>Порядок воспроизведения общих файлов мультимедиа извне сети  
  
1.  Откройте веб-браузер.  
  
2.  Перейдите на веб-сайт удаленного веб-доступа. Тип **https://<YourDomainName\>/remote** в адресной строке веб-браузера и нажмите клавишу ВВОД.  
  
    > [!NOTE]
    >  *< YourDomainName\ >* представляет собой заполнитель. Оно будет уникальное имя для сервера, поэтому адрес будет иметь вид **https://contoso.com/remote**. Если вы не знаете имя вашего домена, попросите администратора, который выбирал имя домена во время установки функции удаленного доступа на сервере. Дополнительные сведения см. в разделе [Включение удаленного веб-доступа](../manage/Manage-Remote-Web-Access-in-Windows-Server-Essentials.md#BKMK_TurnOnRWA).  
  
3.  Для удаленного доступа к веб-страницу входа введите имя учетной записи пользователя и пароль и нажмите кнопку со стрелкой.  
  
4.  Используйте любой метод для поиска файла мультимедиа, который требуется воспроизвести.  
  
    > [!NOTE]

    >  Дополнительные сведения о различных методах поиска см. в разделе [поиск и воспроизведение файлов мультимедиа в Windows Server Essentials с компьютера или из мультимедийного проигрывателя в сети](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1).  

    >  Дополнительные сведения о различных методах поиска см. в разделе [поиск и воспроизведение файлов мультимедиа в Windows Server Essentials с компьютера или из мультимедийного проигрывателя в сети](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2.1).  

  
5.  Когда появляется имя файла мультимедиа, щелкните имя файла для воспроизведения мультимедиа.  
  
##  <a name="BKMK_4"></a>Добавление файлов цифрового мультимедиа на сервер  

 Администратор сервера может добавлять цифровое мультимедиа в общие папки в библиотеке мультимедиа, путем доступа к серверу напрямую или используя сайт удаленного веб-доступа для входа на панели мониторинга. Другие пользователи могут добавлять файлы мультимедиа на сервер с помощью **общих папок** подключения на панели запуска с помощью сайта удаленного веб-доступа или с помощью приложения My Server для Windows Phone. Сведения о воспроизведении мультимедиа см. в разделе [воспроизведения и совместно использовать мультимедиа](Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2).  

 Администратор сервера может добавлять цифровое мультимедиа в общие папки в библиотеке мультимедиа, путем доступа к серверу напрямую или используя сайт удаленного веб-доступа для входа на панели мониторинга. Другие пользователи могут добавлять файлы мультимедиа на сервер с помощью **общих папок** подключения на панели запуска с помощью сайта удаленного веб-доступа или с помощью приложения My Server для Windows Phone. Сведения о воспроизведении мультимедиа см. в разделе [воспроизведения и совместно использовать мультимедиа](../use/Play-Digital-Media-in-Windows-Server-Essentials.md#BKMK_2).  

  
> [!NOTE]
>  Можно также отправить файлы мультимедиа на сервер с помощью приложения «Мой сервер» для Windows Phone. Можно загрузить приложение My Server из [магазина Windows Phone](http://www.windowsphone.com/store/app/my-server/6c2f98d5-6fcf-4e1d-b8b1-cde62ea1a94a). Дополнительные сведения о приложении My Server для Windows Phone см. в записи блога [приложение My Server для телефона для Windows Server Essentials](http://blogs.technet.com/b/sbs/archive/2012/09/18/my-server-phone-app-for-windows-server-2012-essentials.aspx).  
  
#### <a name="to-add-digital-media-files-to-shared-folders-on-the-server"></a>Добавление файлов цифрового мультимедиа в общие папки на сервере  
  
1.  Выполнить вход на сервер, используйте один из следующих методов:  
  

    1.  Сведения о входе через удаленный веб-доступ см. в разделе [использование удаленного веб-доступа](Use-Remote-Web-Access-in-Windows-Server-Essentials.md).  

    1.  Сведения о входе через удаленный веб-доступ см. в разделе [использование удаленного веб-доступа](../use/Use-Remote-Web-Access-in-Windows-Server-Essentials.md).  

  
    2.  Сведения о входе с помощью панели запуска см. в разделе [Обзор панели запуска](../manage/Overview-of-the-Launchpad-in-Windows-Server-Essentials.md).  
  
2.  Найдите и щелкните папку добавляемого мультимедиа.  
  
3.  Скопируйте и вставьте или перетащите файлы мультимедиа, что вы хотите добавить в соответствующую общую папку на сервере.  
  
##  <a name="BKMK_5"></a>Параметры формата загрузки  
 Существует два варианта загрузки файлов. Эти параметры доступны только при загрузке нескольких файлов или папку на компьютере под управлением Windows.  
  
 Выберите следующий параметр, который соответствует требованиям к загрузке:  
  
-   **Сжатый ZIP файл (.zip)**  
  
     При сжатии создается версия файла, меньше, чем исходный файл. Сжатая версия файла имеет расширение имени файла .zip. Типы файлов, которые являются уменьшено наиболее при сжатии являются текст архиватором (например, .txt, .doc и .xls), и графические файлы, используйте несжатым (например, BMP). Некоторые графические файлы, такие как файлы JPG и GIF, уже используют сжатие и уменьшения размера файла архиватора zip почти не. Кроме того документ Word, который содержит множество рисунков не сжимается хуже документа, содержащего практически один текст.  
  
    > [!NOTE]
    >  Этот параметр обеспечивает ограниченную поддержку международных имен файлов.  
  
-   **Самораспаковывающийся исполняемый файл (.exe)**  
  
     Самораспаковывающийся исполняемый файл — это файл, можно загрузить, сочетает в себе (исполняемую) программу распаковки и сжатые файлы. При запуске исполняемой программы она автоматически распаковывает сжатые файлы. Это распространенный способ распространения сжатых данных, не беспокоясь о ли у получателя подходящая программа распаковки.  
  
    > [!NOTE]
    >  Этот параметр поддерживает символы Юникода.  
  
 Перед началом фактической загрузки создается файл .exe или ZIP. В зависимости от количества файлов и общий размер файлов для загрузки это может занять несколько минут. После создания загружаемого файла загрузка выполняется в фоновом режиме. Это позволяет продолжить работу во время загрузки.  
  
##  <a name="BKMK_6"></a>Средство отправки файлов  
 Средство отправки файлов упрощает процесс передачи файлов на сервере Windows Server Essentials. Можно добавить любое число файлов в средство отправки файлов и передать их в общие папки на сервере Windows Server Essentials в одном пакете. Дополнительные сведения см. в записи блога [представление удаленного веб-доступа файла доступ](http://blogs.technet.com/b/sbs/archive/2012/04/19/understanding-remote-web-access-file-sharing.aspx).  
  
##  <a name="BKMK_7"></a>Просматривать общие файлы цифрового мультимедиа  
 Можно просмотреть или просмотреть ресурсы с помощью панели мониторинга, панели запуска, веб-сайт удаленного веб-доступа или приложение My Server для Windows Phone.  
  
#### <a name="to-view-and-browse-shared-media-from-the-dashboard"></a>Порядок просмотра общего мультимедийного содержимого с помощью панели мониторинга  
  
1.  Откройте панель мониторинга сервера.  
  
2.  На главной панели навигации, щелкните **ХРАНИЛИЩА**.  
  
3.  Нажмите кнопку **папок сервера** вкладку. Отображается список папок сервера.  
  
4.  Дважды щелкните папку, чтобы просмотреть содержимое папки.  
  
#### <a name="to-view-and-browse-shared-media-using-the-launchpad-from-a-network-computer"></a>Порядок просмотра общего мультимедийного содержимого с помощью панели запуска с компьютера в сети  
  
1.  Войдите в панель запуска.  
  
2.  Нажмите кнопку **общих папок**. Проводник Windows открывает и отображает список общих папок на сервере.  
  
3.  Дважды щелкните папку, чтобы просмотреть содержимое папки.  
  
#### <a name="to-view-and-browse-shared-media-using-remote-web-access"></a>Порядок просмотра общего мультимедийного содержимого с помощью удаленного веб-доступа  
  
1.  Войдите в систему удаленного веб-доступа.  
  
2.  Нажмите кнопку **общих папок**. **Общих папок** раздел веб-страницы отображает список общих папок на сервере.  
  
3.  Дважды щелкните папку, чтобы просмотреть содержимое папки.  
  
## <a name="see-also"></a>См. также:  
  
-   [Управление цифровым мультимедиа](../manage/Manage-Digital-Media-in-Windows-Server-Essentials.md)  
  

-   [Установка подключения](Get-Connected-in-Windows-Server-Essentials.md)  
  
-   [Использование общих папок](Use-Shared-Folders-in-Windows-Server-Essentials.md)  
  
-   [Удаленная работа](Work-Remotely-in-Windows-Server-Essentials.md)

-   [Установка подключения](../use/Get-Connected-in-Windows-Server-Essentials.md)  
  
-   [Использование общих папок](../use/Use-Shared-Folders-in-Windows-Server-Essentials.md)  
  
-   [Удаленная работа](../use/Work-Remotely-in-Windows-Server-Essentials.md)
