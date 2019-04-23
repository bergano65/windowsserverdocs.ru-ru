---
title: Подкоманды set-Server
description: 'Раздел Windows команды для ***- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da55c29d-a94a-4d73-877b-af480f906ca0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: abc3fe23558f077e0ba9ac69f2641e3b8c9cde4f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59858385"
---
# <a name="subcommand-set-server"></a>Подкоманда: set-Server

>Область применения. Windows Server (полугодовой канал), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Настраивает параметры для сервера служб развертывания Windows.
## <a name="syntax"></a>Синтаксис
```
wdsutil [Options] /Set-Server [/Server:<Server name>]
    [/Authorize:{Yes | No}]
    [/RogueDetection:{Yes | No}]
    [/AnswerClients:{All | Known | None}]
    [/Responsedelay:<time in seconds>]
    [/AllowN12forNewClients:{Yes | No}]
    [/ArchitectureDiscovery:{Yes | No}]
    [/resetBootProgram:{Yes | No}]
    [/DefaultX86X64Imagetype:{x86 | x64 | Both}]
    [/UseDhcpPorts:{Yes | No}]
    [/DhcpOption60:{Yes | No}]
    [/RpcPort:<Port number>]
    [/PxepromptPolicy 
        [/Known:{OptIn | Noprompt | OptOut}]
        [/New:{OptIn | Noprompt | OptOut}] 
    [/BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/N12BootProgram:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/BootImage:<Relative path>]
         /Architecture:{x86 | ia64 | x64}
    [/PreferredDC:<DC Name>]
    [/PreferredGC:<GC Name>]
    [/PrestageUsingMAC:{Yes | No}]
    [/NewMachineNamingPolicy:<Policy>]
    [/NewMachineOU]
         [/type:{Serverdomain | Userdomain | UserOU | Custom}]
         [/OU:<Domain name of OU>]
    [/DomainSearchOrder:{GCOnly | DCFirst}]
    [/NewMachineDomainJoin:{Yes | No}]
    [/OSCMenuName:<Name>]
    [/WdsClientLogging]
         [/Enabled:{Yes | No}]
         [/LoggingLevel:{None | Errors | Warnings | Info}]
    [/WdsUnattend]
         [/Policy:{Enabled | Disabled}]
         [/CommandlinePrecedence:{Yes | No}]
         [/File:<path>]
             /Architecture:{x86 | ia64 | x64}
    [/AutoaddPolicy]
         [/Policy:{AdminApproval | Disabled}]
         [/PollInterval:{time in seconds}]
         [/MaxRetry:{Retries}]
         [/Message:<Message>]
         [/RetentionPeriod]
             [/Approved:<time in days>]
             [/Others:<time in days>]
    [/AutoaddSettings]
         /Architecture:{x86 | ia64 | x64}
         [/BootProgram:<Relative path>]
         [/ReferralServer:<Server name>
         [/WdsClientUnattend:<Relative path>]
         [/BootImage:<Relative path>]
         [/User:<Owner>]
         [/JoinRights:{JoinOnly | Full}]
         [/JoinDomain:{Yes | No}]
    [/BindPolicy]
         [/Policy:{Include | Exclude}]
         [/add]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
         [/remove]
              /address:<IP or MAC address>
              /addresstype:{IP | MAC}
    [/RefreshPeriod:<time in seconds>]
    [/BannedGuidPolicy]
         [/add]
              /Guid:<GUID>
         [/remove]
             /Guid:<GUID>
    [/BcdRefreshPolicy]
         [/Enabled:{Yes | No}]
         [/RefreshPeriod:<time in minutes>]
    [/Transport]
         [/ObtainIpv4From:{Dhcp | Range}]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/ObtainIpv6From:Range]
             [/start:<start IP address>]
             [/End:<End IP address>]
         [/startPort:<start Port>
             [/EndPort:<start Port>
        [/Profile:{10Mbps | 100Mbps | 1Gbps | Custom}]
        [/MulticastSessionPolicy]
             [/Policy:{None | AutoDisconnect | Multistream}]
                 [/Threshold:<Speed in KBps>]
                 [/StreamCount:{2 | 3}]
                 [/Fallback:{Yes | No}]    
        [/forceNative]
```
## <a name="parameters"></a>Параметры
|Параметр|Описание|
|-------|--------|
|[/ Server:<Server name>]|Указывает имя сервера. Это может быть имя NetBIOS или полное доменное имя (FQDN). Если имя сервера не указан, будет использоваться локальный сервер.|
|[/ Authorize: {Да &#124; No}]|Указывает, следует ли авторизовать этот сервер в элемент управления протокола DHCP (Dynamic Host).|
|[/ RogueDetection: {Да &#124; No}]|Включает или отключает Обнаружение посторонних подключений DHCP.|
|[/ AnswerClients: {все &#124; известные &#124; None}]|Указывает, какие клиенты, этот сервер будет отвечать. Если это значение равно **известные**, компьютер должен быть предварительно настроен в доменных службах active directory (AD DS), прежде чем он будет получать ответ на сервер служб развертывания Windows.|
|[/ Responsedelay:<time in seconds>]|Количество времени, сервер будет ожидать до ответа Загружающийся клиент. Этот параметр не применяется к компьютерам с предварительно подготовленным.|
|[/ AllowN12forNewClients: {Да &#124; No}]|для Windows Server 2008 указывает, что неизвестных клиентов не придется клавишу F12, чтобы инициировать загрузку из сети. Известные клиенты будут получать программы загрузки, заданной для него, или, если не указан, программа boot, указанная для архитектуры.<br /><br />для Windows Server 2008 R2, этот параметр был заменен с помощью следующей команды: /PxepromptPolicy команду wdsutil /New:Noprompt|
|[/ ArchitectureDiscovery: {Да &#124; No}]|Включает или отключает обнаружение архитектуры. Это позволяет обнаруживать x64 клиентов, которые не передают их архитектура правильно.|
|[/ resetBootProgram: {Да &#124; No}]|Определяет, будут ли удалены путь загрузки для клиента, который только что была загружена без необходимости нажимать эту клавишу F12.|
|[/ DefaultX86X64Imagetype: {x86 &#124; x64 &#124; оба}]|Определяет, какие образы загрузки отображаются x64 клиентам.|
|[/ UseDhcpPorts: {Да &#124; No}]|Указывает ли PXE-сервер следует попытаться выполнить привязку к порту DHCP, TCP порт 67. Если DHCP и служб развертывания Windows работают на одном компьютере, следует устанавливать этот параметр, **нет** включить DHCP-сервера использовать порт и задайте **/DhcpOption60** параметр **Да**. Значение по умолчанию для этого параметра равно **Да**.|
|[/ DhcpOption60: {Да &#124; No}]|Указывает, следует ли настроить параметр 60 DHCP для поддержки PXE. Если DHCP и служб развертывания Windows выполняются на одном сервере, для этого параметра **Да** и задайте **/UseDhcpPorts** равным **нет**. Значение по умолчанию для этого параметра равно **нет**.|
|[/ RpcPort:<Port number>]|Указывает номер порта TCP, который будет использоваться для обслуживания клиентских запросов.|
|[/PxepromptPolicy]|Настраивает как известные (предварительно) и новые клиенты инициируют загрузку PXE. Этот параметр применяется только к Windows Server 2008 R2. Можно задать параметры, используя следующие параметры:<br /><br />-[/ Известные: {OptIn&#124;OptOut&#124;Noprompt}] — Задает политику для предварительно настроенным клиентам.<br />-[/ New: {OptIn&#124;OptOut&#124;Noprompt}] — Задает политику для новых клиентов.<br /><br />**OptIn** означает, что клиент должен нажать любую клавишу в порядке загрузки PXE, в противном случае она вернется к следующего загрузочного устройства.<br /><br />**Noprompt** означает, что клиент всегда будет PXE-загрузки.<br /><br />**OptOut** означает, что клиент будет PXE-загрузки, пока не нажата клавиша Esc.|
|[/ BootProgram:<Relative path>] /Architecture: {x86 &#124; ia64 &#124; x64}|Указывает относительный путь к программе загрузки из папки remoteInstall (например, **boot\x86\pxeboot.n12**) и указывает архитектура загрузочной программы.|
|[/ N12BootProgram:<Relative path>] /Architecture: {x86 &#124; ia64 &#124; x64}|Указывает относительный путь к программе загрузки, нажав клавишу F12 не требуется (например, **boot\x86\pxeboot.n12**) и указывает архитектура загрузочной программы.|
|[/ Это:<Relative path>] /Architecture: {x86 &#124; ia64 &#124; x64}|Указывает относительный путь в образ загрузки, загружающимся клиентам должны получать что указывает архитектура загрузочного образа. Это можно указать для каждой архитектуры.|
|[/ PreferredDC:<DC Name>]|Задает имя контроллера домена, который следует использовать службы развертывания Windows. Это может быть имя NetBIOS или полное доменное имя.|
|[/ PreferredGC:<GC Name>]|Задает имя сервера глобального каталога, который следует использовать службы развертывания Windows. Это может быть имя NetBIOS или полное доменное имя.|
|[/ PrestageUsingMAC: {Да &#124; No}]|Указывает, должен ли служб развертывания Windows, при создании учетных записей компьютеров в Доменных службах Active Directory, использовать MAC-адрес, а не идентификатор GUID/UUID для идентификации компьютера.|
|[/ NewMachineNamingPolicy:<Policy>]|Указывает формат, используемый при создании имен компьютеров для клиентов. Сведения о формате для использования для <policy>, щелкните правой кнопкой мыши сервер в оснастке mmc, щелкните **свойства**и просмотреть **службы каталогов** вкладки. Например **/NewMachineNamingPolicy: % 61Username % #**.|
|[/NewMachineOU]|Используется для указания расположения в Доменных службах Active Directory, где создаются учетные записи компьютеров. Указать расположение, используя следующие параметры.<br /><br />-[/ type: Serverdomain &#124; Userdomain &#124; UserOU &#124; Custom] Указывает тип расположения. **Serverdomain** создает учетные записи в том же домене, что и сервер служб развертывания Windows. **USERDOMAIN** создает учетные записи в том же домене, имени пользователя, выполняющего установку. **UserOU** создает учетные записи в подразделение пользователя, выполняющего установку. **Пользовательские** можно указать пользовательское расположение (необходимо также указать значение для **/ou** с этим параметром).<br />-[/ OU:<Domain name of OU>] — при указании **Custom** для **/type** параметр, этот параметр указывает подразделение, где следует создать учетные записи компьютеров.|
|[/DomainSearchOrder:{GCOnly &#124; DCFirst}]|Указывает политику для поиска учетных записей компьютеров в Доменных службах Active Directory (глобального каталога или контроллер домена).|
|[/ NewMachineDomainJoin: {Да &#124; No}]|Указывает, должны ли компьютере, который не был уже предварительно настроен в Доменных службах Active Directory присоединены к домену во время установки. Значение по умолчанию — **Да**.|
|[Wdsclientlogging /]|Указывает уровень ведения журнала для сервера.<br /><br />-[/ Включен: {Да &#124; No}] - включает или отключает ведение журнала действий клиента служб развертывания Windows.<br />-[/ LoggingLevel: {None &#124; ошибки &#124; предупреждения &#124; Info} — задает уровень ведения журнала. **Нет** эквивалентен отключение ведения журнала. **Ошибки** самый низкий уровень ведения журнала и указывает, что будут регистрироваться только ошибки. **Предупреждения** включает в себя предупреждения и ошибки. **Сведения о** является высшим уровнем ведения журнала и включает в себя ошибки, предупреждения и информационные события.|
|[/WdsUnattend]|Эти параметры управляют поведением автоматической установки клиента служб развертывания Windows. Можно задать параметры, используя следующие параметры:<br /><br />-[/ Политики: {включено &#124; отключенные}]-Указывает, используется ли автоматической установки.<br />-[/ CommandlinePrecedence: {Да &#124; No}]-Указывает, будет ли использоваться файла Autounattend.xml (при наличии на клиенте) или файл автоматической установки, который был передан непосредственно клиенту служб развертывания Windows с параметром /Unattend вместо файл автоматической установки образа во время установки клиента. Значение по умолчанию — **нет**.<br />-[/ File:<Relative path> /Architecture: {x86 &#124; ia64 &#124; x64}] — Задает имя файла, путь и архитектура файла автоматической установки.|
|[/AutoaddPolicy]|Эти параметры управляют политики автоматического добавления. Определения параметров, используя следующие параметры:<br /><br />-[/ Политики: {AdminApproval &#124; отключенные}]- **AdminApprove** вызывает все неизвестные компьютеры для добавления в очередь ожидания, где администратор может просмотреть список компьютеров и утверждать или отклонять каждый запрос как соответствующие. **Отключенные** указывает, что никакие дополнительные действия не выполняются, когда неизвестный компьютер пытается получить загрузки на сервер.<br />-[/ PollInterval: {время в секундах}] — Задает интервал (в секундах), по которому программу сетевой загрузки должно проверять, передаваемых на сервер служб развертывания Windows.<br />-[/ MaxRetry: <Number>] — Указывает, сколько раз программу сетевой загрузки должно проверять, передаваемых на сервер служб развертывания Windows. Это значение, наряду с **/PollInterval**, определяет время ожидания программы сетевой загрузки администратор может утвердить или отклонить компьютера до истечения времени ожидания. Например **MaxRetry** значение 10 и **PollInterval** vlue 60, означает, что клиент должен опроса сервера 10 раз ожидания 60 секунд между попытками. Таким образом клиент будет время ожидания после 10 минут (10 x 60 секунд = 10 минут).<br />-[/ Сообщения: <Message>] — Задает сообщение, отображаемое для клиента на странице диалогового окна программы загрузки сети.<br />-[/RetentionPeriod] — Указывает количество дней, которые компьютер может находиться в состоянии ожидания перед автоматически очищаются.<br />-[/ Утвержденные: <time in days>] — Задает срок хранения для утвержденных компьютеров. Необходимо использовать этот параметр с **/RetentionPeriod** параметр.<br />-[/ Другими пользователями: <time in days>] — Задает срок хранения для недоверенных компьютеров ("Отклонено" или "Ожидание"). Необходимо использовать этот параметр с **/RetentionPeriod** параметр.|
|[/AutoaddSettings]|Задает параметры по умолчанию для применения к каждому компьютеру. Определения параметров, используя следующие параметры:<br /><br />-/Architecture: {x86 &#124; ia64 &#124; x64}-задает архитектуру.<br />-[/ BootProgram: <Relative path>] — Указывает программу загрузки, отправляются на утвержденные компьютеры. Если программа загрузки не указан, будет использоваться значение по умолчанию для архитектуры компьютера (как указано на сервере).<br />-[/ WdsClientUnattend: <Relative path>] — Задает относительный путь в файл автоматической установки, который должен получать утвержденное клиентское.<br />-[/ ReferralServer: <Server name>] — указывает на сервер служб развертывания Windows, который клиент будет использовать для загрузки изображения.<br />-[/ Это: <Relative path>] — указывает образ загрузки, утвержденных клиент получит.<br />-[/ Пользователя: < домен\пользователь &#124; User@Domain>] — задает разрешения для объекта учетной записи компьютера, чтобы предоставить пользователю права, необходимые для присоединения компьютера к домену.<br />-[JoinRights: {JoinOnly &#124; полный}]-тип прав для назначения пользователю. **JoinOnly** требует от администратора для сброса учетной записи компьютера, прежде чем пользователь может подключить компьютер к домену. **Полный** дает полный доступ для пользователя, включая право на присоединение компьютера к домену.<br />-[/ JoinDomain: {Да &#124; No}]-указывает ли компьютер должен быть присоединен к домену как эта учетная запись компьютера во время установки служб развертывания Windows. Значение по умолчанию — **Да**.|
|[Bindpolicy/Policy]|Настройка сетевых интерфейсов для PXE-поставщик для прослушивания. Можно определить политику с помощью следующих параметров:<br /><br />-[/ Политики: {Include &#124; исключить}] — Задает политику привязки интерфейса для включения или исключения адресов в списке интерфейсов.<br />-[/ add] - добавляет интерфейс к списку. Кроме того, необходимо также указать/addressType и/Address.<br />-[/ Remove] — Удаляет интерфейс из списка. Кроме того, необходимо также указать/addressType и/Address.<br />- и адресов:<IP or MAC address> -указывает IP-адрес или MAC-адрес интерфейса для добавления или удаления.<br />-/ addressType: {IP-адрес &#124; MAC}-тип адреса, указанного в **и адресов** параметр.|
|[/ RefreshPeriod: <seconds>]|Указывает частоту (в секундах), сервер будет обновления параметров.|
|[/BannedGuidPolicy]|Управляет список запрещенных GUID, используя следующие параметры:<br /><br />-[/ add] /Guid:<GUID> -добавляет в список запрещенных GUID указанным GUID. Любой клиент с этим идентификатором GUID позволит определить, его MAC-адрес.<br />-/Guid [/ Remove]:<GUID> — Удаляет указанный идентификатор GUID из списка запрещенных идентификаторов GUID.|
|[/BcdRefreshPolicy]|Настраивает параметры для обновления файлов Bcd, используя следующие параметры:<br /><br />-[/ Включен: {Да &#124; No}]-указывает Bcd обновлении политики. Когда **и включения** присваивается **Да**, обновлении файлов Bcd в заданный интервал времени.<br />-[/ RefreshPeriod:<time in minutes>] — Задает интервал времени, в какие Bcd обновлении файлов.|
|[/Transport]|Настраивает следующие параметры:<br /><br /><ul><li>[/ ObtainIpv4From: {Dhcp &#124; диапазон}] — указывает источник IPv4-адреса.<br /><br /><ul><li>[/ start: <starting Ipv4 address>] — указывает на начало диапазона IP-адресов. Этот параметр является обязательным и допустимо, только если **/ObtainIpv4From** присваивается **диапазона**</li><li>[/ End: <Ending Ipv4 address>] — Задает конец диапазона IP-адресов. Этот параметр является обязательным и допустимо, только если **/ObtainIpv4From** присваивается **диапазон**.</li></ul></li><li>[/ ObtainIpv6From:Range] [/ start:<start IP address>] [/ End:<End IP address>] указывает источник IPv6-адресов. Этот параметр применяется только к Windows Server 2008 R2 и единственным поддерживаемым значением является диапазон.</li><li>[/ значение startPort: <starting port>] — указывает на начало диапазона портов.</li><li>[/ Значения EndPort: <Ending port>] — Задает конец диапазона портов.</li><li>[/ Profile: {10 Мбит/с &#124; 100 Мбит/с &#124; 1 Гбит/с &#124; Custom}] — задает профиль сети, который будет использоваться. Этот параметр доступен только поддерживаемые forservers под управлением Windows Server 2008.</li><li>[/MulticastSessionPolicy]  Настройка параметров передачи процесса многоадресной передачи. Эта команда доступна только для Windows Server 2008 R2.<br /><br /><ul><li>[/ Политики: {None &#124; автоматического отключения &#124; Multistream}]-определяет способ обработки медленных клиентов. None означает, что для сохранения всех клиентов в одном сеансе с той же скоростью. Параметра означает, что все клиенты, опустится ниже заданного /Threshold будут отключены. Multistream означает, что клиенты будут разделены на несколько сеансов, в соответствии с /StreamCount.</li><li>[/ Пороговое значение:<Speed in KBps>] — для /Policy:AutoDisconnect, параметр задает минимальный передачи скорости в Кбит/с. Клиенты, которые опустится ниже такой скорости будут отключены от многоадресные передачи.</li><li>[/ StreamCount: {2 &#124; 3}] [/ Резервный: {Да &#124; No}]-для /Policy:Multistream, этот параметр определяет количество сеансов. 2 означает, что два сеанса (быстрых и медленных запросов) 3 означает, что трех сеансов (медленно, средний, быстро).</li><li>[/ Резервный: {Да&#124; No}]-определяет, будет ли Отключенные клиенты перемещения с помощью другого метода (если поддерживается клиентом). Если вы используете клиент WDS, компьютер будет одноадресную. Wdsmcast.exe не поддерживает резервный механизм. Этот параметр также применяется к клиентам, не поддерживающих Multistream. В этом случае компьютер вернется к другой метод вместо перемещения медленнее сеанса передачи.</li></ul></li></ul>|
## <a name="BKMK_examples"></a>Примеры
Чтобы настроить сервер для ответа только доверенные клиенты, с помощью задержку ответа, равному 4 минутам, введите:
```
wdsutil /Set-Server /AnswerClients:Known /Responsedelay:4
```
Чтобы установить программу загрузки и архитектура для сервера, введите:
```
wdsutil /Set-Server /BootProgram:boot\x86\pxeboot.n12 /Architecture:x86
```
Чтобы включить ведение журнала на сервере, введите:
```
wdsutil /Set-Server /WdsClientLogging /Enabled:Yes /LoggingLevel:Warnings
```
Для включения автоматической установки на сервере, а также архитектуру и файл автоматической установки клиента, тип:
```
wdsutil /Set-Server /WdsUnattend /Policy:Enabled /File:WDSClientUnattend \unattend.xml /Architecture:x86
```
Чтобы настроить сервер Environment (PXE) предзагрузочного выполнения для пытаются выполнить привязку к TCP-порты 67 и 60, введите:
```
wdsutil /Set-server /UseDhcpPorts:No /DhcpOption60:Yes
```
#### <a name="additional-references"></a>Дополнительные ссылки
[Ключ синтаксиса команд](command-line-syntax-key.md)
[с помощью команды отключения сервера](using-the-disable-server-command.md)
[с помощью команды enable-Server](using-the-enable-server-command.md)
[Using Команда Get-Server](using-the-get-server-command.md)
[с помощью команды Initialize-Server](using-the-initialize-server-command.md)
[подкоманда: запустить сервер](subcommand-start-server.md) 
 [ Подкоманда: stop-Server](subcommand-stop-server.md)
[параметр uninitialize сервера](the-uninitialize-server-option.md)