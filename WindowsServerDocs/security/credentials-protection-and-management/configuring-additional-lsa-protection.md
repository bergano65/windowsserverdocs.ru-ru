---
title: Настройка дополнительной защиты LSA
description: Безопасность Windows Server
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: security-credential-protection
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 038e7c2b-c032-491f-8727-6f3f01116ef9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/12/2016
ms.openlocfilehash: bd5863a46f77fd4ac53c8559ff17279271dc5c46
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849695"
---
# <a name="configuring-additional-lsa-protection"></a>Настройка дополнительной защиты LSA

>Область применения. Windows Server (полугодовой канал), Windows Server 2016

В этом разделе, предназначенном для ИТ-специалистов, описывается настройка дополнительной защиты для процесса локальной системы безопасности (LSA), чтобы предотвратить внедрение кода, которое может скомпрометировать учетные данные.

Система LSA, в которую входит процесс службы LSASS, проверяет пользователей во время локального и удаленного входа и применяет локальные политики безопасности. Операционная система Windows 8.1 предоставляет дополнительную защиту для LSA, предотвращая считывание памяти и внедрение кода незащищенными процессами. Это усиливает безопасность учетных данных, которые хранит LSA и которыми управляет LSA. Параметр защищенного процесса для LSA можно настроить в Windows 8.1, но ее нельзя настроить в Windows RT 8.1. Если этот параметр используется в сочетании с безопасной загрузкой, то обеспечивается дополнительная защита, поскольку не действует отключение раздела реестра HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa.

### <a name="protected-process-requirements-for-plug-ins-or-drivers"></a>Требования к защищенным процессам для подключаемых модулей и драйверов
Для успешной загрузки подключаемого модуля или драйвера LSA в качестве защищенного процесса он должен соответствовать следующим условиям.

1.  Проверка подписи

    В защищенном режиме любой подключаемый модуль, загружаемый в LSA, должен иметь цифровую подпись Майкрософт. Поэтому подключаемые модули без подписи, а также модули, не имеющие подписи Майкрософт, не будут загружаться в LSA. Примерами таких подключаемых модулей являются драйверы смарт-карт, подключаемые модули для шифрования и фильтры паролей.

    Подключаемые модули LSA, которые являются драйверами, например драйверы смарт-карт, должны заверяться с помощью сертификации WHQL. Дополнительные сведения см. в разделе [подпись выпуска WHQL](https://msdn.microsoft.com/library/windows/hardware/ff553976%28v=vs.85%29.aspx).

    LSA подключаемые модули, у которых нет в процессе сертификации WHQL, должны заверяться с помощью [служба подписей файлов для LSA](https://go.microsoft.com/fwlink/?LinkId=392590).

2.  Соответствие руководству Майкрософт по процессам жизненного цикла разработки безопасного ПО (SDL)

    Все подключаемые модули должны отвечать руководству по процессам SDL. Дополнительные сведения см. в разделе [приложение Microsoft Security Development Lifecycle (SDL)](https://msdn.microsoft.com/library/windows/desktop/cc307891.aspx).

    Несоответствие процессу SDL может сделать невозможной загрузку подключаемого модуля, даже имеющего правильную подпись Майкрософт.

#### <a name="recommended-practices"></a>Рекомендации
Перед широким применением функции тщательно проверьте наличие защиты LSA по следующему списку.

-   Определите все подключаемые модули и драйверы LSA, используемые в организации. 
    Сюда входят драйверы, не разработанные корпорацией Майкрософт, и подключаемые модули, в том числе драйверы смарт-карт и подключаемые модули шифрования, а также все разработанное внутри компании ПО, используемое для фильтрации паролей или уведомления о смене пароля.

-   Убедитесь, что все подключаемые модули LSA имеют цифровую подпись с сертификатом Майкрософт (что делает возможной их загрузку).

-   Убедитесь, что все имеющие нужные подписи подключаемые модули успешно загружаются в LSA и работают ожидаемым образом.

-   Изучите журналы аудита, чтобы определить подключаемые модули и драйверы LSA, которые не удалось загрузить в качестве защищенного процесса.

#### <a name="limitations-introduced-with-enabled-lsa-protection"></a>Ограничения, возникающие с поддержкой защиты LSA

Если включена защита LSA, не удается выполнить отладку пользовательского подключаемого модуля LSA.
Не удается подключить отладчик к LSASS, когда он является защищенным.
Вообще говоря никак не поддерживается для отладки запущенного защищенного процесса.

## <a name="how-to-identify-lsa-plug-ins-and-drivers-that-fail-to-run-as-a-protected-process"></a>Определение подключаемых модулей и драйверов LSA, которые не удалось загрузить в качестве защищенного процесса
События, описанные в этом разделе, находятся в операционном журнале в папке "Журналы приложений и служб\Microsoft\Windows\CodeIntegrity". Они помогут определить подключаемые модули и драйверы LSA, которые не удалось загрузить из-за проблем с подписями. Для управления этими событиями можно использовать программу командной строки **wevtutil**. Информацию об этой программе см. в разделе [Wevtutil](../../administration/windows-commands/Wevtutil.md).

### <a name="before-opting-in-how-to-identify-plug-ins-and-drivers-loaded-by-the-lsassexe"></a>Перед включением защиты: определение подключаемых модулей и драйверов, загружаемых процессом lsass.exe
В режиме аудита можно определить подключаемые модули и драйверы LSA, которые будет невозможно загрузить в режиме защиты LSA. В режиме аудита система будет создавать события в журнале, которые определяют все подключаемые модули и драйверы, которые будет невозможно загрузить в LSA, если включена защита LSA. Сообщения заносятся в журнал, но подключаемые модули и драйверы не блокируются.

##### <a name="to-enable-the-audit-mode-for-lsassexe-on-a-single-computer-by-editing-the-registry"></a>Включение режима аудита для процесса Lsass.exe на одиночном компьютере путем внесения изменений в реестр

1.  Откройте редактор реестра (RegEdit.exe) и перейдите к разделу HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\LSASS.exe.

2.  Задайте для раздела значение **AuditLevel=dword:00000008**.

3.  Перезагрузите компьютер.

Проанализируйте результаты события 3065 и события 3066.

После этого может просмотреть эти события в средстве просмотра событий: Microsoft-Windows-Codeintegrity/Operational:

-   **Событие 3065**: Это событие записывается, если при проверке целостности кода установлено, что процесс (обычно lsass.exe) пытался загрузить драйвер, который не отвечает требованиям безопасности для общих сеансов. Однако заданная системная политика разрешает загрузку изображения.

-   **Событие 3066**: Это событие записывается, если при проверке целостности кода установлено, что процесс (обычно lsass.exe) пытался загрузить драйвер, который не отвечает требованиям к уровню подписи Майкрософт. Однако заданная системная политика разрешает загрузку изображения.

> [!IMPORTANT]
> Такие операционные события не создаются, если подключен отладчик ядра, который включен в системе.
> 
> Если подключаемый модуль или драйвер содержит общие сеансы, то вместе с событием 3065 записывается событие 3066. После удаления общих сеансов ни одно из этих событий не должно появляться, если подключаемый модуль отвечает требованиям к уровню подписи Майкрософт.

Чтобы включить режим аудита для нескольких компьютеров в домене, можно использовать клиентское расширение групповой политики для реестра и развернуть значение реестра для уровня аудита Lsass.exe. Понадобится изменить раздел реестра HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\LSASS.exe.

##### <a name="to-create-the-auditlevel-value-setting-in-a-gpo"></a>Создание параметра AuditLevel в объекте групповой политики

1.  Откройте консоль управления групповыми политиками.

2.  Создайте новый объект групповой политики, который связан на уровне домена или связан с подразделением, которому принадлежат учетные записи компьютеров. Также можно выбрать уже развернутый объект групповой политики.

3.  Щелкните правой кнопкой мыши объект групповой политики и выберите команду **Изменить**, чтобы открыть редактор управления групповыми политиками.

4.  Разверните узлы **Конфигурация компьютера**, **Настройки** и **Параметры Windows**.

5.  Щелкните правой кнопкой мыши элемент **Реестр**, укажите пункт **Создать** и выберите пункт **Элемент реестра**. Откроется диалоговое окно **Новые свойства реестра**.

6.  В **Hive** выберите **HKEY_LOCAL_MACHINE.**

7.  В списке **Путь к разделу** перейдите к разделу **SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\LSASS.exe**.

8.  В поле **Имя параметра** введите **AuditLevel**.

9. В поле **Тип параметра** выберите **REG_DWORD**.

10. В поле **Значение** введите **00000008**.

11. Нажмите кнопку **ОК**.

> [!NOTE]
> Чтобы объект групповой политики вступил в силу, его изменение нужно реплицировать на все контроллеры домена в домене.

Чтобы включить дополнительную защиту LSA на нескольких компьютерах, можно использовать клиентское расширение групповой политики для реестра, изменив параметр HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa. Эта процедура описана далее в разделе [Настройка дополнительной защиты LSA для учетных данных](#BKMK_HowToConfigure).

### <a name="after-opting-in-how-to-identify-plug-ins-and-drivers-loaded-by-the-lsassexe"></a>После включения защиты: определение подключаемых модулей и драйверов, загружаемых процессом lsass.exe
По журналу событий можно определить подключаемые модули и драйверы LSA, которые не удалось загрузить в режиме защиты LSA. Когда включен защищенный процесс LSA, система создает журналы событий, по которым определяются все подключаемые модули и драйверы, которые не удалось загрузить в LSA.

Проанализируйте результаты события 3033 и события 3063.

После этого может просмотреть эти события в средстве просмотра событий: Microsoft-Windows-Codeintegrity/Operational:

-   **Событие 3033**: Это событие записывается, если при проверке целостности кода установлено, что процесс (обычно lsass.exe) пытался загрузить драйвер, который не отвечает требованиям к уровню подписи Майкрософт.

-   **Событие 3063**: Это событие записывается, если при проверке целостности кода установлено, что процесс (обычно lsass.exe) пытался загрузить драйвер, который не отвечает требованиям безопасности для общих сеансов.

Общие сеансы обычно образуются, когда применяются приемы программирования, позволяющие данным экземпляра взаимодействовать с другими процессами, использующими тот же контекст безопасности. Это может представлять уязвимость.

## <a name="BKMK_HowToConfigure"></a>Настройка дополнительной защиты LSA для учетных данных
На устройствах под управлением Windows 8.1 (с или без безопасной загрузкой или UEFI) конфигурация не предусмотрена, выполнив процедуры, описанные в этом разделе. Для устройств под управлением Windows RT 8.1 защита lsass.exe всегда включена, и он не может быть отключен.

### <a name="on-x86-based-or-x64-based-devices-using-secure-boot-and-uefi-or-not"></a>Устройства с архитектурой x86 или x64, использующие или не использующие безопасную загрузку и UEFI
На 32-разрядных (x86) или 64-разрядных (x64) устройствах, использующих или не использующих безопасную загрузку и UEFI, во встроенном ПО UEFI устанавливается переменная UEFI, когда защита LSA включается с помощью раздела реестра. Если параметр хранится во встроенном ПО, то переменную UEFI нельзя удалить или изменить в разделе реестра. Необходимо сбросить переменную UEFI.

На 32-разрядных (x86) или 64-разрядных (x64) устройствах, где не поддерживается UEFI или безопасная загрузка, конфигурация защиты LSA не может храниться во встроенном ПО, и для них имеет значение только наличие раздела реестра. В таком сценарии есть возможность отключить защиту LSA, получив удаленный доступ к устройству.

Для включения и отключения защиты LSA используются следующие процедуры.

##### <a name="to-enable-lsa-protection-on-a-single-computer"></a>Включение защиты LSA на отдельном компьютере

1.  Откройте редактор реестра (RegEdit.exe) и перейдите к разделу HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa.

2.  Задайте для раздела значение RunAsPPL=dword:00000001.

3.  Перезагрузите компьютер.

##### <a name="to-enable-lsa-protection-using-group-policy"></a>Включение защиты LSA с помощью групповой политики

1.  Откройте консоль управления групповыми политиками.

2.  Создайте новый объект групповой политики, который связан на уровне домена или связан с подразделением, которому принадлежат учетные записи компьютеров. Также можно выбрать уже развернутый объект групповой политики.

3.  Щелкните правой кнопкой мыши объект групповой политики и выберите команду **Изменить**, чтобы открыть редактор управления групповыми политиками.

4.  Разверните узлы **Конфигурация компьютера**, **Настройки** и **Параметры Windows**.

5.  Щелкните правой кнопкой мыши элемент **Реестр**, укажите пункт **Создать** и выберите пункт **Элемент реестра**. Откроется диалоговое окно **Новые свойства реестра**.

6.  В списке **Куст** выберите **HKEY_LOCAL_MACHINE**.

7.  В **путь к ключу** списке, перейдите в папку **SYSTEM\CurrentControlSet\Control\Lsa**.

8.  В **имя значения** введите **RunAsPPL**.

9. В поле **Тип параметра** выберите **REG_DWORD**.

10. В **значение** введите **00000001**.

11. Нажмите кнопку **ОК**.

##### <a name="to-disable-lsa-protection"></a>Отключение защиты LSA

1.  Откройте редактор реестра (RegEdit.exe) и перейдите к разделу HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Lsa.

2.  Удалите из раздела реестра параметр RunAsPPL=dword:00000001.

3.  Если на устройстве используется безопасная загрузка, используйте средство отключения защищенного процесса локальной системы безопасности (LSA), чтобы удалить переменную UEFI.

    Дополнительные сведения о средстве отказа см. в разделе [скачать Local Security Authority (LSA) защищенного процесса выхода в официальном центре загрузки Microsoft](https://www.microsoft.com/download/details.aspx?id=40897).

    Дополнительные сведения об управлении безопасной загрузкой см. в разделе [встроенное по UEFI](https://technet.microsoft.com/library/hh824898.aspx).

    > [!WARNING]
    > Когда выключается безопасная загрузка, сбрасываются все параметры конфигурации, относящиеся к UEFI и безопасной загрузке. Выключать безопасную загрузку следует только в том случае, если не удалось отключить защиту LSA ни одним из других способов.

### <a name="verifying-lsa-protection"></a>Проверка защиты LSA
Чтобы определить, запущена ли система LSA в защищенном режиме при загрузке Windows, найдите следующее событие WinInit в журнале **Система** в папке **Журналы Windows**:

-   12: LSASS.exe запущен как защищенный процесс уровня: 4

## <a name="additional-resources"></a>Дополнительные ресурсы
[Защита учетных данных и управление ими](credentials-protection-and-management.md)

[Служба подписей файлов для LSA](https://go.microsoft.com/fwlink/?LinkId=392590)

