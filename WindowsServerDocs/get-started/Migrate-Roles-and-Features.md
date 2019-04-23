---
title: Перенос ролей и компонентов
description: ''
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.date: 04/03/2017
ms.technology: server-general
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0f78ef4c-dd12-4b1b-8c6e-251dd803c5d1
author: jaimeo
ms.author: jaimeo
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 7469171005164d9ff823dad7de230d877c874dc9
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59840885"
---
# <a name="migrating-roles-and-features-in-windows-server"></a>Миграция ролей и функций в Windows Server

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Эта страница содержит ссылки на информацию и средства, которые помогут вам в процессе миграции ролей и компонентов в Windows Server 2016, Windows Server 2012 R2 и Windows Server 2012. Многие роли и компоненты могут быть перенесены с помощью средства миграции Windows Server, набора пяти командлетов Windows PowerShell, которые появились в Windows Server 2008 R2, для упрощения переноса элементов и данных ролей и компонентов.

Руководства по миграции поддерживают миграции определенных ролей и компонентов с одного сервера на другой (не обновления на месте). Если не указано иное в руководствах, миграции поддерживаются между физическими и виртуальными компьютерами и между параметры полной установки Windows Server и серверами под управлением варианта установки Server Core.  

## <a name="before-you-begin"></a>Перед началом работы

Перед началом миграции ролей и компонентов убедитесь, что исходный и целевой серверы работают под управлением последних пакетов обновления, доступных для их операционных систем.
Теперь доступна электронная книга руководства по переносу Windows Server 2012 R2 и Windows Server 2012. Для получения дополнительных сведений и скачивания электронной книги см. статью [Коллекция электронных книг по технологиям Майкрософт](https://social.technet.microsoft.com/wiki/contents/articles/11608.e-book-gallery-for-microsoft-technologies.aspx#MigrateRoles). 

>[!NOTE]
>При миграции или обновлении до любой версии Windows Server следует просмотреть и понять [политику сроков поддержки](https://support.microsoft.com/lifecycle) и период времени для этой версии и плана, соответственно. Вы можете [найти информацию о сроках](https://support.microsoft.com/lifecycle) для определенного выпуска Windows Server, который вас интересуют.
 
## <a name="windows-server-2016"></a>Windows Server 2016

### <a name="migration-guides"></a>Руководства по миграции
Обновленные руководства по миграции для Windows Server 2016 находятся на стадии разработки. Вернитесь в это расположение, чтобы получить обновления, когда они станут доступными. Во многих случаях действия в руководствах по миграции Windows Server 2012 R2 применимы к Windows Server 2016.

- [Службы удаленных рабочих столов](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/migrate-rds-role-services)
- [Веб-сервер (IIS)](https://www.iis.net/downloads/microsoft/web-deploy)
- [Windows Server Update Services](https://technet.microsoft.com/library/hh852339.aspx)
- [MultiPoint Services](https://technet.microsoft.com/windows-server-docs/compute/remote-desktop-services/multipoint-services/multipoint-services-migrate)
 
## <a name="windows-server-2012-r2"></a>Windows Server 2012 R2

### <a name="migration-guides"></a>Руководства по миграции
Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008, Windows Server 2008 R2, Windows Server 2012 или Windows Server 2012 R2 на Windows Server 2012 R2. Средства миграции Windows Server в Windows Server 2012 R2 поддерживают перенос между различными подсетями.

- [Установка, использование и удаление средств миграции Windows Server](https://technet.microsoft.com/library/jj134202.aspx)
- [Руководство по миграции сертификатов Active Directory с служб для Windows Server 2012 R2](https://technet.microsoft.com/library/dn486797.aspx)
- [Миграция службы роли служб федерации Active Directory в Windows Server 2012 R2](https://technet.microsoft.com/library/dn486815.aspx)
- [Руководство по обновлению и миграции служб управления правами Active Directory](https://technet.microsoft.com/library/cc754277.aspx)
- [Перенос файловых служб и служб хранилища в Windows Server 2012 R2](https://technet.microsoft.com/library/dn479292.aspx)
- [Перенос Hyper-V в Windows Server 2012 R2 с Windows Server 2012](https://technet.microsoft.com/library/dn486799.aspx)
- [Перенос сервера политики сети в Windows Server 2012](https://technet.microsoft.com/library/hh831652)
- [Перенос служб удаленных рабочих столов в Windows Server 2012 R2](https://technet.microsoft.com/library/dn479239.aspx)
- [Перенос Windows Server Update Services в Windows Server 2012 R2](https://technet.microsoft.com/library/hh852339.aspx)
- [Перенос кластерных ролей на Windows Server 2012 R2](https://technet.microsoft.com/library/dn530779.aspx)
- [Перенос DHCP-сервера в Windows Server 2012 R2](https://technet.microsoft.com/library/dn495425.aspx)
 
## <a name="windows-server-2012"></a>Windows Server 2012

### <a name="migration-guides"></a>Руководства по миграции
Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008, Windows Server 2008 R2 или Windows Server 2012 на Windows Server 2012. Средства миграции Windows Server в Windows Server 2012 поддерживают перенос между различными подсетями.

- [Установка, использование и удаление средств миграции Windows Server](https://technet.microsoft.com/library/jj134202)
- [Перенос служб ролей для служб федерации Active Directory в Windows Server 2012](https://technet.microsoft.com/library/jj647765)
- [Миграция центра регистрации работоспособности в Windows Server 2012](https://technet.microsoft.com/library/hh831513)
- [Перенос Hyper-V в Windows Server 2012 с Windows Server 2008 R2](https://technet.microsoft.com/library/jj574113)
- [Перенос конфигурации IP в Windows Server 2012](https://technet.microsoft.com/library/jj574133)
- [Перенос сервера политики сети в Windows Server 2012](https://technet.microsoft.com/library/hh831652)
- [Миграция печати и документов служб в Windows Server 2012](https://technet.microsoft.com/library/jj134150)
- [Миграция удаленного доступа в Windows Server 2012](https://technet.microsoft.com/library/hh831423)
- [Миграция Windows Server Update Services в Windows Server 2012](https://technet.microsoft.com/library/hh852339)
- [Обновление контроллеров домена Active Directory в Windows Server 2012](https://technet.microsoft.com/library/hh994618.aspx)
- [Перенос кластеризованных служб и приложений на Windows Server 2012](https://technet.microsoft.com/library/dn486790.aspx)
 

Для получения дополнительных ресурсов по миграции см. статью [Перенос ролей и компонентов на Windows Server 2012](https://technet.microsoft.com/library/jj134039).

## <a name="windows-server-2008-r2"></a>Windows Server 2008 R2

### <a name="migration-guides"></a>Руководства по миграции
Следуйте инструкциям в этих руководствах для переноса ролей и компонентов с серверов под управлением Windows Server 2003, Windows Server 2008 или Windows Server 2008 R2 на Windows Server 2008 R2. Средства миграции Windows Server в Windows Server 2008 R2 не поддерживают перенос между различными подсетями.

- [Установка, использование и удаление средства миграции Windows Server](https://technet.microsoft.com/library/dd379545)
- [Руководство по миграции служб сертификации Active Directory](https://technet.microsoft.com/library/ee126170)
- [Доменные службы Active Directory и руководство по миграции сервера домена имя системы (DNS)](https://technet.microsoft.com/library/dd379558)
- [Руководство по миграции BranchCache](https://technet.microsoft.com/library/dd548365)
- [Руководство по миграции сервера Dynamic Host Configuration Protocol (DHCP)](https://technet.microsoft.com/library/dd379535)
- [Руководство по миграции служб файла](https://technet.microsoft.com/library/dd379487)
- [Руководство по миграции HRA](https://technet.microsoft.com/library/ee791829)
- [Руководство по миграции Hyper-V](https://technet.microsoft.com/library/ee849855)
- [Руководство по миграции конфигурации IP-адрес](https://technet.microsoft.com/library/dd379537)
- [Локальные пользователи и группы руководство по миграции](https://technet.microsoft.com/library/dd379531)
- [Руководство по миграции NPS](https://technet.microsoft.com/library/ee791849)
- [Руководство по миграции служб печати](https://technet.microsoft.com/library/dd379488)
- [Руководство по миграции служб удаленных рабочих столов](https://technet.microsoft.com/library/ff849223)
- [Руководство по миграции RRAS](https://technet.microsoft.com/library/ee822825)
- [Windows Server миграции задач и сведения](https://technet.microsoft.com/library/ff400258)
- [Windows Server Update Services 3.0 руководство по миграции с пакетом обновления 2](https://technet.microsoft.com/library/ee822826)  
Для получения дополнительных ресурсов по миграции см. статью [Перенос ролей и компонентов на Windows Server 2008 R2](https://technet.microsoft.com/library/dd365353).