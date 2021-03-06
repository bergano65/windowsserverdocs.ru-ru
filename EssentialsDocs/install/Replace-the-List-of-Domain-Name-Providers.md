---
title: Замена списка поставщиков доменных имен
description: Описывает способ использования Windows Server Essentials
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 104d0412-2d77-4cd4-99f7-65a885522850
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: c087cdad4d2c047db40b370673fb04b232036b61
ms.sourcegitcommit: eaf071249b6eb6b1a758b38579a2d87710abfb54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/31/2019
ms.locfileid: "66433492"
---
# <a name="replace-the-list-of-domain-name-providers"></a>Замена списка поставщиков доменных имен

>Область применения. Windows Server 2016 Essentials, Windows Server 2012 R2 Essentials, Windows Server 2012 Essentials

Список поставщиков доменных имен, отображаемый в мастере настройки доменных имен, можно заменить, выполнив следующие задачи.  


-   [Создание справочной службы файлов](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)  

-   [Добавить запись в реестр на компьютере-образце](Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)  

-   [Создание справочной службы файлов](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles)  

-   [Добавить запись в реестр на компьютере-образце](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_AddRegistry)  


###  <a name="BKMK_ReferralFiles"></a> Создание справочной службы файлов  
 Средством администрирования справочной службы создается набор файлов, которые используются для определения списка поставщиков доменных имен, отображаемого в мастере настройки доменных имен. Для каждого региона мира создается XML-файл, который содержит сведения для поставщиков доменных имен, указанных в данном средстве. Созданные средством файлы должны располагаться в папке, доступ к которой можно получить с помощью безопасной ссылки (HTTPS), управляемой из Интернета.  

##### <a name="to-create-the-referral-files"></a>Создание справочных файлов  

1.  Откройте средство администрирования справочной службы.  

2.  Нажмите кнопку **Добавить**.  

3.  В диалоговом окне Add a Domain Name Provider (Добавление поставщика доменных имен) введите имя поставщика доменных имен.  

4.  Добавьте домены верхнего уровня, которые поддерживаются поставщиком доменных имен. Для этого нажмите кнопку **Добавить**, введите идентификатор домена верхнего уровня, а затем выберите поддерживаемые регионы. Можно выбрать **All Regions** (Все регионы).  

5.  Введите описание поставщика доменных имен.  

6.  Добавьте URL-адреса всех веб-сайтов, связанных с данным поставщиком доменных имен.  

7.  Если у поставщика доменных имен имеется эмблема, добавьте ее, щелкнув **Change Logo**(Изменить эмблему).  

8.  Нажмите кнопку **Сохранить**.  

9. Повторите шаги 2-8 для каждого поставщика доменных имен, отображаемого в списке мастера.  

10. После добавления всех поставщиков доменных имен выберите папку, в которой должны располагаться справочные файлы. При выборе папки следует учитывать, что доступ к справочным файлам должен осуществляться с помощью ссылки HTTPS.  

11. Щелкните **Generate Files to File System** (Создать файлы в файловой системе).  

###  <a name="BKMK_AddRegistry"></a> Добавить запись в реестр на компьютере-образце  
 Чтобы указать расположение файлов справочной службы, доступных для операционной системы, необходимо добавить запись в реестр.  

##### <a name="to-add-a-key-to-the-registry"></a>Добавление раздела в реестр  

1.  На компьютере-образце нажмите кнопку **Пуск**, введите команду **regedit**и нажмите клавишу **ВВОД**.  

2.  В левой области последовательно разверните узлы **HKEY_LOCAL_MACHINE**, **SOFTWARE**, **Microsoft**, **Windows Server**, **Domain Managers** и **Providers**.  

3.  Щелкните правой кнопкой мыши раздел **E423C85D-6B1F-4583-95E0-449D8263BAC4** и выберите пункт **Строковый параметр**.  

4.  В качестве имени строки введите **ReferralServerHttpsUri** и нажмите клавишу **ВВОД**.  

5.  Щелкните правой кнопкой мыши строку **ReferralServerHttpsUri** в правой области и выберите команду **Изменить**.  


6.  Введите URL-адрес HTTPS, используемый для доступа к справочным файлам, которые были созданы при выполнении процедуры, описанной в разделе [Создание файлов справочной службы](Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles), и нажмите кнопку **ОК**.  

6.  Введите URL-адрес HTTPS, используемый для доступа к справочным файлам, которые были созданы при выполнении процедуры, описанной в разделе [Создание файлов справочной службы](../install/Replace-the-List-of-Domain-Name-Providers.md#BKMK_ReferralFiles), и нажмите кнопку **ОК**.  


~~~
> [!IMPORTANT]
>  A slash (/) is required at the end of the URL.  
~~~

###  <a name="BKMK_ReplaceDomainNameProviders"></a> Проблемы состояния имени домена  
 Если партнер добавляет поставщиков доменных имен и использует интерфейс программирования (API) в пакете SDK для Windows Server Essentials для установки состояний сертификата Unknown, Failed и certificaterequestnotsubmitted, пользователь, клиент получает неправильный сообщение о результате настройки. Это происходит потому, что эти случаи обрабатываются исключениями и состояние не возвращается.  

 Следующие состояния домена являются ошибками и должны сопровождаться соответствующими сообщениями:  

- Failed  

- PendingCustomerInterventionRequired  

- PurchaseFailed  

- DomainNotFound  

- InRenewalCustomerInterventionRequired  

- RenewalFailed  

  Следующие состояния домена являются успешными и должны сопровождаться соответствующими сообщениями:  

- Готово  

- Pending  

- InRenewal  

## <a name="see-also"></a>См. также  

 [Создание и настройка образа](Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](Additional-Customizations.md)   
 [Подготовка образа для развертывания](Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](Testing-the-Customer-Experience.md)

 [Создание и настройка образа](../install/Creating-and-Customizing-the-Image.md)   
 [Дополнительные настройки](../install/Additional-Customizations.md)   
 [Подготовка образа для развертывания](../install/Preparing-the-Image-for-Deployment.md)   
 [Тестирование работы пользователей](../install/Testing-the-Customer-Experience.md)

