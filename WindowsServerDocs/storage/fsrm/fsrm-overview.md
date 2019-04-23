---
title: "Обзор диспетчера ресурсов файлового сервера (FSRM)"
ms.prod: windows-server-threshold
ms.author: jgerend
ms.manager: brianlic
ms.technology: storage
ms.topic: article
author: jasongerend
ms.date: 7/7/2017
description: "Диспетчер ресурсов файлового сервера (FSRM) представляет собой инструмент для классификации данных на файловом сервере Windows Server и управления этими данными."
ms.openlocfilehash: ddfc0a0f4bede89a3c3a624d4f128717d0f1ac08
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="file-server-resource-manager-fsrm-overview"></a>Обзор диспетчера ресурсов файлового сервера (FSRM)

> Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2

Диспетчер ресурсов файлового сервера (FSRM)— это служба роли в Windows Server, которая позволяет классифицировать данные, хранящиеся на файловых серверах, и управлять этими данными. Диспетчер ресурсов файлового сервера включает следующие компоненты.
  
-   **Инфраструктура классификации файлов** . Инфраструктура классификации файлов обеспечивает представление о данных, автоматизируя процессы классификации. Это позволяет более эффективно управлять данными. На основании классификации файлов можно применять политики. Примерами политик могут служить динамический контроль доступа для ограничения доступа к файлам, шифрование файлов и установка срока действия файлов. Классификация файлов может производиться автоматически с помощью правил классификации или вручную — изменением свойств выбранного файла или папки.  
  
-   **Задачи управления файлами** . Задачи управления файлами позволяют применять условные политики или действия к файлам на основании их классификации. Условия задачи управления файлами включают расположение файла, свойства классификации, дату создания файла, дату последнего изменения файла или время последнего доступа к файлу. Действия, доступные в задаче управления файлами, включают прекращение срока действия файлов, их шифрование или выполнение пользовательской команды.  
  
-   **Управление квотами** . Квоты позволяют ограничить пространство, разрешенное для тома или папки. Они могут автоматически применяться к новым папкам, создаваемым в томе. Можно также определить шаблоны квот, которые могут применяться к новым томам или папкам.  
  
-   **Управление фильтрами блокировки файлов** . Фильтры блокировки файлов помогают контролировать типы файлов, которые пользователь может сохранять на файловом сервере. Можно ограничить расширения, допустимые при сохранении файлов с общим доступом. Например, можно создать фильтр блокировки файлов, который не позволит сохранять файлы с расширением MP3 в личных папках с общим доступом на файловом сервере.  
  
-   **Отчеты хранилища** . Отчеты хранилища помогают определить тенденции использования диска и способы классификации данных. Можно также контролировать попытки сохранять запрещенные файлы пользователями выбранной группы.  
  
 Для настройки компонентов диспетчера ресурсов файлового сервера и управления ими можно использовать консоль управления (MMC) "Диспетчер ресурсов файлового сервера" или Windows PowerShell.  
  
> [!IMPORTANT]
>  Диспетчер ресурсов файлового сервера поддерживает только тома, отформатированные с файловой системой NTFS. Файловая система Resilient File System не поддерживается.  
  
## <a name="practical-applications"></a>Практическое применение  
 Ниже приведены возможности практического применения диспетчера ресурсов файлового сервера.  
  
-   Использование инфраструктуры классификации файлов со сценарием динамического контроля доступа для создания политики, предоставляющей доступ к файлам и папкам на основании классификации файлов на файловом сервере.  
  
-   Создание правила классификации файлов, которое отмечает как содержащие персональные данные файлы, включающие хотя бы 10 номеров социального обеспечения.  
  
-   Прекращение срока действия файлов, которые не изменялись за последние 10лет.  
  
-   Создание квоты размером 200 МБ для домашнего каталога каждого пользователя с уведомлением при заполнении 180 МБ.  
  
-   Запрет сохранения музыкальных файлов в личных папках с общим доступом.  
  
-   Создание в расписании отчета, который будет выполняться в полночь по воскресеньям и создавать список файлов, открывавшихся за предыдущие два дня. Это поможет обнаружить действия по сохранению файлов в выходные и соответственно планировать время отключения сервера.  

## <a name="see-also"></a>См. также:

- [Новые возможности диспетчера ресурсов файлового сервера](https://technet.microsoft.com/library/dn383587.aspx)
- [Динамический контроль доступа](https://technet.microsoft.com/library/dn408191(v=ws.11).aspx) 