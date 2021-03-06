---
title: Развертывание нескольких серверов удаленного доступа в многосайтовом развертывании
description: Эта статья является частью руководств по развертыванию нескольких серверов удаленного доступа в многосайтовом развертывании в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac2f6015-50a5-4909-8f67-8565f9d332a2
ms.author: pashort
author: shortpatti
ms.openlocfilehash: da23f3082e1d97f1bcfbee7365b863d29ba2d020
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404498"
---
# <a name="deploy-multiple-remote-access-servers-in-a-multisite-deployment"></a>Развертывание нескольких серверов удаленного доступа в многосайтовом развертывании

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

 Windows Server 2016 и Windows Server 2012 объединяют VPN-подключение DirectAccess и службы удаленного доступа (RAS) к одной роли удаленного доступа. Развертывание удаленного доступа возможно в нескольких корпоративных сценариях. В этом обзоре содержатся общие сведения о корпоративном сценарии развертывания серверов удаленного доступа в многосайтовой конфигурации.  
  
## <a name="BKMK_OVER"></a>Описание сценария  
В многосайтовом развертывании два или более серверов удаленного доступа или кластеров серверов развертываются и настраиваются в качестве различных точек входа в одном расположении или в распределенных географических расположениях. Развертывание нескольких точек входа в одном расположении обеспечивает избыточность сервера или выравнивание серверов удаленного доступа с существующей сетевой архитектурой. Развертывание по географическому расположению обеспечивает эффективное использование ресурсов, так как удаленные клиентские компьютеры могут подключаться к внутренним сетевым ресурсам с помощью ближайших к ним точек входа. Трафик в многосайтовом развертывании можно распределить и сбалансировать с помощью внешней глобальной подсистемы балансировки нагрузки.  
  
Многосайтовое развертывание поддерживает клиентские компьютеры под управлением Windows 10, Windows 8 или Windows 7. Клиентские компьютеры под управлением Windows 10 или Windows 8 автоматически указывают точку входа, или пользователь может вручную выбрать точку входа. Автоматическое назначение происходит в следующем порядке приоритета:  
  
1.  Используйте точку входа, выбранную вручную пользователем.  
  
2.  Используйте точку входа, определяемую внешней глобальной подсистемой балансировки нагрузки, если она развернута.  
  
3.  Используйте ближайшую точку входа, определяемую клиентским компьютером, используя механизм автоматического пробы.  
  
Поддержка клиентов под управлением Windows 7 должна быть включена вручную в каждой точке входа, а выбор точек входа этими клиентами не поддерживается.  
  
## <a name="prerequisites"></a>Предварительные условия  
Перед началом развертывания этого сценария ознакомьтесь со списком важных требований.  
  
-   [Разверните один сервер DirectAccess с дополнительными параметрами](../../directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md) , который должен быть развернут перед многосайтовым развертыванием.  
  
-   Клиенты Windows 7 всегда будут подключаться к определенному сайту. Они не смогут подключаться к ближайшему сайту на основе расположения клиента (в отличие от клиентов Windows 10, 8 или 8,1).  
  
-   Изменение политик вне консоли управления DirectAccess или командлетов PowerShell не поддерживается.  
  
-   Должна быть развернута инфраструктура открытого ключа.  
  
    Дополнительная информация: [Мини-модуль руководства по лаборатории тестирования: Базовая PKI для Windows Server 2012.](https://social.technet.microsoft.com/wiki/contents/articles/7862.test-lab-guide-mini-module-basic-pki-for-windows-server-2012.aspx)  
  
-   В корпоративной сети должна быть включена поддержка IPv6. Если вы используете протокол ISATAP, необходимо удалить его и перейти на собственный IPv6.  
  
## <a name="in-this-scenario"></a>Содержание сценария  
Сценарий многосайтового развертывания включает ряд шагов:  
  
1. [Разверните один сервер DirectAccess с дополнительными параметрами](../../directaccess/single-server-advanced/Deploy-a-Single-DirectAccess-Server-with-Advanced-Settings.md). Перед настройкой многосайтового развертывания необходимо развернуть один сервер удаленного доступа с дополнительными параметрами.  
  
2. [Планирование многосайтового развертывания](plan/Plan-a-Multisite-Deployment.md). Для создания многосайтового развертывания с одного сервера требуется ряд дополнительных этапов планирования, включая соответствие требованиям для многосайтовых требований и планирование Active Directory групп безопасности, групповая политика объектов (GPO), DNS и параметров клиента.  
  
3. [Настройка многосайтового развертывания](configure/Configure-a-Multisite-Deployment.md). Это состоит из нескольких этапов настройки, включая подготовку инфраструктуры Active Directory, настройку существующего сервера удаленного доступа и добавление нескольких серверов удаленного доступа в качестве точек входа в многосайтовое развертывание.  
  
4. [Устранение неполадок многосайтового развертывания](troubleshoot/Troubleshoot-a-Multisite-Deployment.md). В этом разделе по устранению неполадок описываются наиболее распространенные ошибки, которые могут возникнуть при развертывании удаленного доступа в многосайтовом развертывании.
  
## <a name="BKMK_APP"></a>Практические приложения  
Многосайтовый развертывание предоставляет следующие сведения.  
  
-   Улучшенная производительность — многосайтовое развертывание позволяет клиентским компьютерам получать доступ к внутренним ресурсам с помощью удаленного доступа, используя ближайшую и наиболее подходящую точку входа. Доступ клиентов к внутренним ресурсам осуществляется эффективно, а скорость клиентских запросов к Интернету, направляемых через DirectAccess, повышается. Трафик между точками входа можно сбалансировать с помощью внешней глобальной подсистемы балансировки нагрузки.  
  
-   Простота управления. многосайтовая архитектура позволяет администраторам согласовать развертывание удаленного доступа с развертыванием Active Directory сайтов, предоставляя упрощенную архитектуру. Общие параметры можно легко задать на серверах точек входа или в кластерах. Параметрами удаленного доступа можно управлять с любого сервера в развертывании или удаленно с помощью средства удаленного администрирования сервера (RSAT). Кроме того, можно осуществлять мониторинг всего многосайтового развертывания с помощью одной консоли управления удаленным доступом.  
  
## <a name="BKMK_NEW"></a>Роли и компоненты, входящие в этот сценарий  
В следующей таблице перечислены роли и функции, используемые в этом сценарии.  
  
|Роль/компонент|Способ поддержки сценария|  
|---------|-----------------|  
|Роль удаленного доступа|Эта роль устанавливается и удаляется с помощью консоли Диспетчера серверов. В эту роль входят и DirectAccess, служивший ранее компонентом Windows Server 2008 R2, и службы маршрутизации и удаленного доступа (RRAS), которые ранее представляли собой службу в составе роли сервера служб политики сети и доступа. Роль удаленного доступа включает два компонента.<br /><br />— VPN и службы маршрутизации и удаленного доступа (RRAS). Управление DirectAccess и VPN осуществляется вместе в консоли управления удаленным доступом.<br />— Маршрутизация RRAS. Управление функциями маршрутизации RRAS осуществляется с помощью устаревшей консоли маршрутизации и удаленного доступа.<br /><br />Существуют следующие зависимости.<br /><br />-Службы IIS (IIS) веб-сервер — эта функция необходима для настройки сервера сетевых расположений и веб-проверки по умолчанию.<br />— Внутренняя база данных Windows — используется для локального учета на сервере удаленного доступа.|  
|Средства управления удаленным доступом|Этот компонент устанавливается описанным ниже образом.<br /><br />— Он устанавливается по умолчанию на сервере удаленного доступа при установке роли удаленного доступа и поддерживает пользовательский интерфейс консоли удаленного управления.<br />— Его можно дополнительно установить на сервере, на котором не запущена роль сервера удаленного доступа. В этом случае компонент используется для удаленного управления компьютером с возможностью удаленного доступа, на котором установлены DirectAccess и VPN.<br /><br />Средства управления удаленным доступом включают следующие элементы:<br /><br />— Графический интерфейс удаленного доступа и средства командной строки<br />— Модуль удаленного доступа для Windows PowerShell<br /><br />Зависимости включают следующее:<br /><br />— Консоль управления групповыми политиками<br />— Пакет администрирования диспетчера подключений RAS (CMAK)<br />— Windows PowerShell 3,0<br />-Графические средства управления и инфраструктура|  
  
## <a name="BKMK_HARD"></a>Требования к оборудованию  
Для этого сценария действуют следующие требования к оборудованию.  
  
-   По крайней мере два компьютера удаленного доступа должны быть собраны в многосайтовое развертывание.   
  
-   Чтобы протестировать сценарий, требуется по крайней мере один компьютер под управлением Windows 8 и настроенный в качестве клиента DirectAccess. Чтобы протестировать сценарий для клиентов под управлением Windows 7, требуется по крайней мере один компьютер под управлением Windows 7.  
  
-   Для балансировки нагрузки трафика между серверами точки входа требуется внешняя Глобальная подсистема балансировки нагрузки стороннего производителя.  
  
## <a name="BKMK_SOFT"></a>Требования к программному обеспечению  
Для этого сценария действуют следующие требования к программному обеспечению.  
  
-   Требования к программному обеспечению для развертывания на одном сервере.  
  
-   Помимо требований к программному обеспечению для одного сервера существует ряд требований, зависящих от нескольких сайтов:  
  
    -   Требования к проверке подлинности IPsec. в многосайтовом развертывании DirectAccess необходимо развернуть с использованием проверки подлинности с помощью сертификата компьютера IPsec. Параметр для выполнения проверки подлинности IPsec с использованием сервера удаленного доступа в качестве прокси-сервера Kerberos не поддерживается. Для развертывания сертификатов IPsec требуется внутренний ЦС.  
  
    -   Требования к серверу для IP-HTTPS и сетевого расположения — сертификаты, необходимые для IP-HTTPS и сервера сетевых расположений, должны выдаваться центром сертификации. Возможность использовать сертификаты, автоматически выданные и самозаверяющие сервером удаленного доступа, не поддерживается. Сертификаты могут выдаваться внутренним ЦС или внешним центром сертификации стороннего производителя.  
  
    -   Active Directory требования. требуется по крайней мере один Active Directory сайт. Сервер удаленного доступа должен находиться на сайте. Для более быстрого обновления рекомендуется, чтобы у каждого сайта был доступный для записи контроллер домена, хотя это не обязательно.  
  
    -   Требования к группе безопасности — требования приведены ниже.  
  
        -   Для всех клиентских компьютеров Windows 8 из всех доменов требуется отдельная группа безопасности. Рекомендуется создать уникальную группу безопасности этих клиентов для каждого домена.  
  
        -   Для каждой точки входа, настроенной для поддержки клиентов Windows 7, требуется уникальная группа безопасности, содержащая компьютеры Windows 7. Рекомендуется иметь уникальную группу безопасности для каждой точки входа в каждом домене.  
  
        -   Компьютеры должны входить только в одну группу безопасности, включающую клиентов DirectAccess. Если клиенты включены в несколько групп, разрешение имен для клиентских запросов будет работать некорректно.  
  
    -   Требования к объектам групповой политики. объекты групповой политики можно создавать вручную перед настройкой удаленного доступа или автоматически создавать во время развертывания удаленного доступа. Ниже приведены требования.  
  
        -   Для каждого домена требуется уникальный объект групповой политики клиента.  
  
        -   Объект групповой политики сервера необходим для каждой точки входа в домене, в котором находится точка входа. Поэтому, если несколько точек входа находятся в одном домене, в домене будет несколько объектов групповой политики сервера (по одному для каждой точки входа).  
  
        -   Уникальный объект групповой политики клиента Windows 7 необходим для каждой точки входа, включенной для поддержки клиентов Windows 7, для каждого домена.  
  
## <a name="KnownIssues"></a>Известные проблемы  
Ниже приведены известные проблемы, возникающие при настройке многосайтового сценария.  
  
-   **Несколько точек входа в одной подсети IPv4**. Добавление нескольких точек входа в одну подсеть IPv4 приведет к конфликту IP-адреса, а адрес DNS64 для точки входа не будет настроен должным образом. Эта проблема возникает, когда IPv6 не был развернут на внутренних интерфейсах серверов в корпоративной сети. Чтобы предотвратить эту проблему, выполните следующую команду Windows PowerShell на всех текущих и будущих серверах удаленного доступа:  
  
    ```  
    Set-NetIPInterface -InterfaceAlias <InternalInterfaceName> -AddressFamily IPv6 -DadTransmits 0  
    ```  
  
-   Если общедоступный адрес, указанный для подключения клиентов DirectAccess к серверу удаленного доступа, имеет суффикс, входящий в таблицу NRPT, DirectAccess может работать не так, как ожидалось. Убедитесь, что в NRPT есть исключение для открытого имени. В многосайтовом развертывании исключения следует добавлять для открытых имен всех точек входа. Обратите внимание, что при включении принудительного туннелирования исключения добавляются автоматически. Они удаляются, если принудительное туннелирование отключено.  
  
-   При использовании командлета Windows PowerShell **Disable-дамултисите**параметры WhatIf и Confirm не действуют, а многосайтовая работа будет отключена, а объекты групповой политики Windows 7 будут удалены.  
  
-   Когда клиенты Windows 7, использующие DCA в многосайтовом развертывании, обновляются до Windows 8, помощник по подключению к сети не будет работать. Эту проблему можно устранить перед обновлением клиента, изменив объекты групповой политики Windows 7 с помощью следующих командлетов Windows PowerShell:  
  
    ```  
    Set-GPRegistryValue -Name <Windows7GpoName> -Domain <DomainName> -Key "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\NetworkConnectivityAssistant" -ValueName "TemporaryValue" -Type Dword -Value 1  
    Remove-GPRegistryValue -Name <Windows7GpoName> -Domain <DomainName> -Key "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\NetworkConnectivityAssistant"  
    ```  
  
    В случае, если клиент уже обновлен, переместите клиентский компьютер в группу безопасности Windows 8.  
  
-   При изменении параметров контроллера домена с помощью командлета Windows PowerShell **Set-даентрипоинтдк**, если указанный параметр ComputerName является сервером удаленного доступа в точке входа, отличной от последней добавленной к многосайтовому развертыванию, будет выведено предупреждение, указывающее, что указанный сервер не будет обновлен до следующего обновления политики. Фактические серверы, которые не были обновлены, можно просмотреть с помощью **состояния конфигурации** на **панели мониторинга** **консоли управления удаленным доступом**. Однако это не приведет к функциональным проблемам, но вы можете запустить **gpupdate/Force** на серверах, которые не были обновлены, чтобы немедленно получить обновленное состояние конфигурации.  
  
-   При развертывании многосайтовой версии в корпоративной сети, предназначенной только для IPv4, изменение префикса IPv6 внутренней сети также изменяет адрес DNS64, но не обновляет адрес правил брандмауэра, который разрешает запросы DNS к службе DNS64. Чтобы устранить эту проблему, выполните следующие команды Windows PowerShell после изменения префикса IPv6 внутренней сети:  
  
    ```  
    $dns64Address = (Get-DAClientDnsConfiguration).NrptEntry | ?{ $_.DirectAccessDnsServers -match ':3333::1' } | Select-Object -First 1 -ExpandProperty DirectAccessDnsServers  
  
    $serverGpoName = (Get-RemoteAccess).ServerGpoName  
  
    $serverGpoDc = (Get-DAEntryPointDC).DomainControllerName  
  
    $gpoSession = Open-NetGPO -PolicyStore $serverGpoName -DomainController $serverGpoDc  
  
    Get-NetFirewallRule -GPOSession $gpoSession | ? {$_.Name -in @('0FDEEC95-1EA6-4042-8BA6-6EF5336DE91A', '24FD98AA-178E-4B01-9220-D0DADA9C8503')} |  Set-NetFirewallRule -LocalAddress $dns64Address  
  
    Save-NetGPO -GPOSession $gpoSession  
    ```  
  
-   Если DirectAccess был развернут при наличии существующей инфраструктуры ISATAP, при удалении точки входа, которая была узлом ISATAP, адрес IPv6 службы DNS64 будет удален из адресов DNS-серверов всех DNS-суффиксов в таблице NRPT.  
  
    Чтобы устранить эту проблему, в мастере **установки сервера инфраструктуры** на странице **DNS** удалите DNS-суффиксы, которые были изменены, и добавьте их снова с ПРАВИЛЬНЫМИ адресами DNS-серверов, нажав кнопку **обнаружить** в диалоговом окне **адреса DNS-сервера** .  
  


