---
ms.assetid: cf32926a-2083-408b-a264-2cad179ed18a
title: Распространения сертификатов на клиентских компьютерах с помощью групповой политики
description: ''
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.author: billmath
ms.openlocfilehash: d3a7e05e4d16565b17b69de254e353df749bbc3a
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59839235"
---
# <a name="distribute-certificates-to-client-computers-by-using-group-policy"></a>Распространения сертификатов на клиентских компьютерах с помощью групповой политики

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012


Чтобы свалить соответствующий протокол SSL можно использовать следующую процедуру \(SSL\) сертификаты \(или эквивалент сертификаты, которые восходят по цепочке с доверенным корневым расположением\) учетной записи серверов федерации серверам федерации и веб-серверы на каждом клиентском компьютере в лесу партнера по учетным записям с помощью групповой политики.  
  
Членство в группе **"Администраторы домена"** или **"Администраторы предприятия"**, или наличие эквивалентных прав в доменных службах Active Directory \(AD DS\) является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477) \(http:\/\/go.microsoft.com\/fwlink\/? LinkId\=83477\).   
  
### <a name="to-distribute-certificates-to-client-computers-by-using-group-policy"></a>Для распределения сертификатов на клиентских компьютерах с помощью групповой политики  
  
1.  На контроллере домена в лесу организации партнера по учетным записям запуска **Управление групповой политикой** привязать\-в.  
  
2.  Найти существующий объект групповой политики \(GPO\) или создайте новый объект групповой Политики с настройками сертификата. Убедитесь, что объект групповой Политики связан с домена, сайта или подразделения \(Подразделение\) где находятся соответствующие учетные записи пользователей и компьютеров.  
  
3.  Справа\-щелкните объект групповой Политики, а затем нажмите кнопку **изменить**.  
  
4.  В дереве консоли откройте **Конфигурация компьютера\\политики\\параметры Windows\\параметры безопасности\\политики открытого ключа**, правой кнопкой мыши\-щелкните **Доверенные корневые центры сертификации**, а затем нажмите кнопку **импорта**.  
  
5.  На **Добро пожаловать в мастер импорта сертификатов** щелкните **Далее**.  
  
6.  На **импортируемый файл** введите путь к файлам соответствующий сертификат \(к примеру, \\ \\fs1\\c$\\fs1.cer\), а затем нажмите кнопку **Далее**.  
  
7.  На **Certificate Store** щелкните **поместить все сертификаты в следующее хранилище**, а затем нажмите кнопку **Далее**.  
  
8.  На **завершение работы мастера импорта сертификатов** странице, проверьте указанные сведения и нажмите кнопку **Готово**.  
  
9. Повторите шаги 2 – 6 для добавления дополнительных сертификатов для каждого из серверов федерации в ферме.  