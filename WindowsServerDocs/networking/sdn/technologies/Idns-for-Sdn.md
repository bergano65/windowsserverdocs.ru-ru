---
title: Внутренняя служба DNS (iDNS) для SDN
description: В этом разделе объясняется, как можно предоставить службы DNS для рабочих нагрузок размещенной клиентов с помощью внутреннего DNS (IDN), который интегрирован с программно-Конфигурируемую сеть в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: networking-sdn
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ad848a5b-0811-4c67-afe5-6147489c0384
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 4d4ae5ee5f5600d86349ca26b7acbdb284b45bac
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824085"
---
# <a name="internal-dns-service-idns-for-sdn"></a>Внутренняя служба DNS (iDNS) для SDN

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Если вы работаете поставщика облачных служб \(CSP\) или Enterprise, который планирует развертывание программно-Конфигурируемую сеть \(SDN\) в Windows Server 2016, вы можете предоставить службы DNS для рабочих нагрузок размещенной клиентов с помощью внутренней службы DNS \(iDNS\), который интегрирован с SDN.

Размещенных виртуальных машин \(виртуальных машин\) и приложениям требуется DNS для обмена данными внутри их собственных сетей и внешние ресурсы в Интернете. С iDNS вы можете предоставить клиентам службы разрешения имен DNS для их пространство имен изолированной, локальные и Интернет-ресурсов.

Так как служба iDNS не доступно из клиента виртуальных сетей, отличное от через прокси международных доменных имен, сервер не уязвимой для вредоносных действий в сетях клиента.

**Основные функции**

Ниже перечислены основные функции для международных доменных имен.

- Предоставляет общий DNS-имени службы разрешения для клиента рабочих нагрузок
- Полномочная служба DNS для разрешения имен и регистрации DNS в пространстве имен клиента
- Рекурсивная служба DNS для разрешения имен Интернета из клиентских виртуальных машин.
- При желании можно настроить размещение одновременных имен структуры и клиента
- Это экономичное решение DNS - клиентов не нужно развертывать инфраструктуру DNS
- Высокий уровень доступности с интеграцией Active Directory, который обязателен.

Помимо этих функций Если вы беспокоитесь о хранении в AD интегрированных откройте DNS-серверы к Интернету, можно развернуть международных доменных имен серверов в зоне действия другой рекурсивного сопоставителя в сети периметра.

Поскольку имена IDN централизованный сервер для всех запросов DNS, CSP или Enterprise можно также реализовать клиента DNS брандмауэры, применять фильтры, обнаружения вредоносных действий и аудита транзакций в центральном расположении

## <a name="idns-infrastructure"></a>iDNS инфраструктуры
В инфраструктуру международных доменных имен входит международных доменных имен серверов и имена IDN прокси-сервера.

### <a name="idns-servers"></a>международных доменных имен серверов
iDNS включает набор DNS-серверы, на которых размещены данные конкретного клиента, такие как записи ресурсов DNS для виртуальной Машины.

iDNS заслуживающих доверия серверов для их внутренней зоны DNS и серверов также выступать в качестве арбитра для общедоступных имен при клиента виртуальных машин, попытка подключения к внешним ресурсам.

Все имена узлов для виртуальных машин в виртуальных сетях хранятся как записи ресурса DNS в той же зоне. Например если вы развертываете международных доменных имен для зоны, с именем contoso.local, записи ресурсов DNS для виртуальных машин в этой сети хранятся в зоне contoso.local.

Клиент виртуальной Машины полные доменные имена \(полные доменные имена\) состоят из имени компьютера и строка суффикса DNS для виртуальной сети, в формате GUID. Например если у вас есть клиент виртуальной Машины с именем клиента (1), в contoso виртуальной сети, локально, полное доменное имя виртуальной Машины — клиента (1). *vn-guid*. contoso.local, где *vn-guid* является строка суффикса DNS для виртуальной сети.

>[!NOTE]
>Если вы являетесь администратором структуры, можно использовать инфраструктуры CSP или корпоративный DNS как серверы международных доменных имен, вместо развертывания новых серверов DNS, специально для использовать в качестве международных доменных имен серверов. Развертывание новых серверов для международных доменных имен или использовать существующую инфраструктуру, имена IDN зависит от Active Directory для обеспечения высокой доступности. Таким образом, международных доменных имен серверов должны быть интегрированы с Active Directory.

### <a name="idns-proxy"></a>iDNS прокси-сервера
iDNS прокси-сервер — это служба Windows, которое будет выполняться на каждом узле, и который перенаправляет клиента DNS виртуальной сети трафик международные доменные имена сервера.

На следующем рисунке показано путей трафик DNS из клиента с виртуальными сетями через прокси-сервера, имена IDN международные доменные имена сервера и Интернета.

![iDNS инфраструктуры](../../media/Internal-Dns/Internal-Dns.jpg)

## <a name="how-to-deploy-idns"></a>Как развернуть международных доменных имен
При развертывании SDN в Windows Server 2016 с помощью сценариев, международных доменных имен, автоматически включается в вашем развертывании.

Дополнительные сведения см. в следующих статьях.

- [Развертывание инфраструктуры программно-определяемой сети с помощью сценариев](https://docs.microsoft.com/windows-server/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts)


## <a name="understanding-idns-deployment-steps"></a>Основные сведения о международных доменных имен шагов развертывания
Чтобы получить представление о том, как устанавливается и настраивается при развертывании SDN с помощью скриптов iDNS можно использовать в этом разделе.

Ниже приводится сводка шагов, необходимых для развертывания международных доменных имен.

>[!NOTE]
>Если вы развернули SDN с помощью сценариев, вы не обязательно для выполнения любого из этих шагов. Эти действия представлены сведения и только в целях устранения неполадок.

### <a name="step-1-deploy-dns"></a>Шаг 1. Развертывание DNS
DNS-сервер можно развернуть с помощью в следующем примере команды Windows PowerShell.
    
    Install-WindowsFeature DNS -IncludeManagementTools
    
### <a name="step-2-configure-idns-information-in-network-controller"></a>Шаг 2. Настройка сведений о международных доменных имен в сетевой контроллер
Этот скрипт сегмент является вызов REST, который выполняется администратором сетевой контроллер, сообщая ей о конфигурации зоны iDNS — такие как IP-адрес iDNSServer и зоны, который используется для имена IDN-имена узлов. 

```
    Url: https://<url>/networking/v1/iDnsServer/configuration
Method: PUT
{
      "properties": {
        "connections": [
          {
            "managementAddresses": [
              "10.0.0.9"
            ],
            "credential": {
              "resourceRef": "/credentials/iDnsServer-Credentials"
            },
            "credentialType": "usernamePassword"
          }
        ],
        "zone": "contoso.local"
      }
    }
```

>[!NOTE]
>Это является выдержкой из раздела **ConfigureIDns конфигурации** в SDNExpress.ps1. Дополнительные сведения см. в разделе [развертывание инфраструктуры программно-определяемой сети с помощью скриптов](https://technet.microsoft.com/windows-server-docs/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts).

### <a name="step-3-configure-the-idns-proxy-service"></a>Шаг 3. Настройка прокси-служба международные доменные имена
Международные доменные имена службы прокси-сервера выполняется на каждом узле Hyper-V, предоставляя мост между виртуальными сетями клиентов и физической сети, где находятся серверы международных доменных имен. Следующие разделы реестра должны создаваться на каждом узле Hyper-V.


**Порт DNS:** Фиксированный порт 53

- Registry Key = HKLM\SYSTEM\CurrentControlSet\Services\NcHostAgent\Parameters\Plugins\Vnet\InfraServices\DnsProxyService"
- ValueName = "Port"
- ValueData = 53
- ValueType = "Dword"
       

**Порт прокси-сервера DNS:** Фиксированный порт 53

- Registry Key = HKLM\SYSTEM\CurrentControlSet\Services\NcHostAgent\Parameters\Plugins\Vnet\InfraServices\DnsProxyService"
- ValueName = "ProxyPort"
- ValueData = 53
- ValueType = "Dword"
        
**IP-АДРЕС DNS:** Фиксированный IP-адрес, настроенный в сетевом интерфейсе, в случае, если клиент выбирает использование международных доменных имен службы

- Registry Key = HKLM\SYSTEM\CurrentControlSet\Services\NcHostAgent\Parameters\Plugins\Vnet\InfraServices\DnsProxyService"
- ValueName = "IP"
- ValueData = "169.254.169.254"
- ValueType = "String"

        
**MAC-адрес:** МАС-адрес DNS-сервера

- Registry Key = HKLM\SYSTEM\CurrentControlSet\Services\NcHostAgent\Parameters\Plugins\Vnet\InfraServices\DnsProxyService
- ValueName = "MAC"
- ValueData = «aa-bb-cc-aa-bb-cc»
- ValueType = "String"

**Адрес сервера международных доменных ИМЕН:** Разделенный запятыми список международных доменных имен серверов.

- Раздел реестра: HKLM\SYSTEM\CurrentControlSet\Services\DNSProxy\Parameters
- ValueName = "Forwarders"
- ValueData = “10.0.0.9”
- ValueType = "String"



>[!NOTE]
>Это является выдержкой из раздела **ConfigureIDnsProxy конфигурации** в SDNExpress.ps1. Дополнительные сведения см. в разделе [развертывание инфраструктуры программно-определяемой сети с помощью скриптов](https://technet.microsoft.com/windows-server-docs/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts).

### <a name="step-4-restart-the-network-controller-host-agent-service"></a>Шаг 4. Перезапуск службы агента узла сетевого контроллера
Можно использовать следующую команду Windows PowerShell, чтобы перезапустить службу агента узла сетевого контроллера.
    
    Restart-Service nchostagent -Force
    
Дополнительные сведения см. в разделе [Restart-Service](https://technet.microsoft.com/library/hh849823.aspx).

### <a name="enable-firewall-rules-for-the-dns-proxy-service"></a>Включить правила брандмауэра для прокси-службы DNS
Чтобы создать правило брандмауэра, которое разрешает исключения для прокси-сервера для взаимодействия с виртуальной Машины и международных доменных имен сервера, можно использовать следующую команду Windows PowerShell.
    
    Enable-NetFirewallRule -DisplayGroup 'DNS Proxy Firewall'

Дополнительные сведения см. в разделе [Enable-NetFirewallRule](https://technet.microsoft.com/library/jj554869.aspx).
    
### <a name="validate-the-idns-service"></a>Проверка службы международные доменные имена
Чтобы проверить международные доменные имена службы, необходимо развернуть на примере рабочей нагрузки клиента.

Дополнительные сведения см. в разделе [Создание виртуальной Машины и подключение к виртуальной сети клиента или виртуальной локальной сети](https://technet.microsoft.com/windows-server-docs/networking/sdn/manage/create-a-tenant-vm).

Если вы хотите, чтобы клиент виртуальной Машины для использования службы международных доменных имен, необходимо Конфигурация DNS-сервер интерфейсы сети виртуальных Машин не указывайте и разрешить интерфейсы, используемые DHCP. 

После запуска виртуальной Машины с такой сетевой интерфейс, она автоматически получает конфигурацию, которая позволяет использовать имена IDN виртуальной Машине и виртуальной Машины немедленно начинает выполнять разрешение имен с помощью международных доменных имен службы.

Если настраивается на виртуальную Машину для использования службы международных доменных имен, если оставить пустым DNS-сервер и Альтернативный DNS-сервер сведения о сетевом интерфейсе клиента, сетевой контроллер предоставляет виртуальную Машину с IP-адресом и выполняет регистрации имени DNS от имени виртуальной Машины с сервера международные доменные имена . 

Сетевой контроллер также предоставляет прокси международных доменных имен сведения о виртуальной Машины и необходимые сведения, чтобы выполнять разрешение имен для виртуальной Машины. 

Когда виртуальная машина инициирует запрос DNS, прокси-сервер выступает в качестве сервера пересылки запроса из виртуальной сети к службе международных доменных имен. 

DNS-прокси также гарантирует, что запросы клиента виртуальной Машины изолированы. Если сервер iDNS заслуживает запрос, сервер iDNS отвечает полномочный ответ. Если сервер международных доменных имен не является полномочным для запроса, он выполняет рекурсия DNS для разрешения имен Интернета.

>[!NOTE]
>Указанная информация входит в разделе **AttachToVirtualNetwork конфигурации** в SDNExpressTenant.ps1. Дополнительные сведения см. в разделе [развертывание инфраструктуры программно-определяемой сети с помощью скриптов](https://technet.microsoft.com/windows-server-docs/networking/sdn/deploy/deploy-a-software-defined-network-infrastructure-using-scripts).
