---
title: Получение интеллектуальных ответов DNS на основе времени дня с помощью политики DNS
description: Этот раздел является частью DNS политики сценария руководство для Windows Server 2016
manager: brianlic
ms.prod: windows-server-threshold
ms.technology: networking-dns
ms.topic: article
ms.assetid: 161446ff-a072-4cc4-b339-00a04857ff3a
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 33fd9447a79346127714a5e5e73977611eba483c
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59829475"
---
# <a name="use-dns-policy-for-intelligent-dns-responses-based-on-the-time-of-day"></a>Получение интеллектуальных ответов DNS на основе времени дня с помощью политики DNS

>Относится к: Windows Server (полугодовой канал), Windows Server 2016

Чтобы узнать, как для распределения трафика приложения для различных экземпляров географически распределенного приложения с помощью политики DNS, которые основаны на время суток, можно использовать в этом разделе.  
  
Этот сценарий полезен в ситуациях, где вы хотите направить трафик из одного часового пояса для альтернативного таких серверов приложений, веб-серверы, которые находятся в другом часовом поясе. Это дает возможность балансировки нагрузки трафика между экземплярами приложения во время пиковой временные периоды, когда серверы-источники являются перегруженными с трафиком.   
  
### <a name="bkmk_example1"></a>Пример интеллектуальных ответов DNS на основе времени дня  
Ниже приведен пример того, как можно использовать политики DNS для балансировки трафика приложения на основе времени суток.  
  
В этом примере используется один вымышленной компании Contoso подарок Services, которая предоставляет Интернет-решений, дарения по всему миру через его веб-узел, contosogiftservices.com.   
  
Contosogiftservices.com веб-сайт размещается в двух центрах обработки данных и в Сиэтле (Северная Америка), а в Дублине (Европа). DNS-серверы настраиваются для отправки географическое расположение знать ответы, с помощью политики DNS. С помощью последних рост бизнеса contosogiftservices.com имеет большее количество посетителей каждый день, и некоторые пользователи сообщали о проблемах доступности службы.  
  
Службы Contoso подарок выполняет анализ сайта и обнаруживает, что каждый вечер между 18: 00 до 21: 00 по местному времени, скачков трафика на веб-серверы. Веб-серверов нельзя масштабировать для обработки большего объема трафика в эти часы максимальной нагрузки, приводит к отказу в обслуживании клиентов. Же перегрузка трафика час пик происходит в Европе и США центрах данных. В другое время суток серверы обработки объема трафика, которые являются намного меньшее их максимальные возможности.  
  
Чтобы убедиться, что contosogiftservices.com клиенты получают более высокую скорость работы с веб-сайта, службы подарок Contoso хочет перенаправления Dublin трафик на серверы приложений Сиэтл между 18: 00 до 21: 00 в Дублине; и они должны перенаправляться часть трафика Сиэтл на серверах приложений Dublin между 18: 00 до 21: 00 в Сиэтле.  
  
Этот сценарий показан на следующем рисунке.  
  
![Время дня DNS политику](../../media/DNS-Policy-Tod1/dns_policy_tod1.jpg)  
  
### <a name="bkmk_works1"></a>Как интеллектуальные ответы DNS, на основе времени дня Works  
  
Если DNS-сервер настроен с временем дня политики DNS, между 18: 00 до 21: 00 в каждом географическом расположении, DNS-сервер выполняет следующие задачи.  
  
- Отвечает на первые четыре запросы, которые оно получает IP-адрес веб-сервера в локальном центре обработки данных.  
- Отвечает на запрос пятый, которые оно получает IP-адрес веб-сервера в удаленном центре обработки данных.   
  
Это поведение на основе политик разгружает двадцать процентов нагрузки трафика локальных веб сервера для удаленного веб-сервера, облегчая нагрузку на локальном сервере приложений и повышения производительности сайта для клиентов.  
  
Часы с наименьшей загрузкой DNS-серверы, осуществлять управление обычный географических расположений, на основе трафика. Кроме того, DNS-клиенты, отправляющие запросы из расположения, отличные от Северная Америка или Европа, нагрузку на DNS-сервер распределяет трафик в Сиэтле и Dublin центрах обработки данных.  
  
При настройке нескольких политик DNS в службе DNS, они представляют собой упорядоченный набор правил, и они обрабатываются DNS от наиболее важных к наименее важным. DNS использует первая политика, соответствующий обстоятельства, включая время суток. По этой причине более конкретные политики должны иметь более высокий приоритет. Если вы создаете времени дня политик и предоставить их с высоким приоритетом в списке политик, DNS обрабатывает и использует эти политики сначала в том случае, если они соответствовали параметрам запроса клиента DNS и критериям, определенным в политике. Если они не совпадают, DNS передвигается далее по списку политик для обработки политик по умолчанию, пока не найдет совпадение.  
  
Дополнительные сведения о типах политики и условия см. в разделе [Обзор политик DNS](../../dns/deploy/DNS-Policies-Overview.md).  
  
### <a name="bkmk_how1"></a>Настройка политики DNS для интеллектуальных ответов DNS на основе времени дня  
Чтобы настроить политики времени балансировки нагрузки приложений, день, в основе ответы на запросы DNS, необходимо выполнить следующие действия.  
  
- [Создание подсетей клиента DNS](#bkmk_subnets)  
- [Создание области зоны](#bkmk_zscopes)  
- [Добавление записей в области зоны](#bkmk_records)  
- [Создайте политики DNS](#bkmk_policies)  
  
>[!NOTE]
>Эти действия необходимо выполнить на DNS-сервере, который заслуживает доверия для зоны, которую требуется настроить. Членство в группе **DnsAdmins**, или наличие эквивалентных прав, необходимых для выполнения следующих процедур.  
  
Следующие разделы содержат подробных инструкций по настройке.  
  
>[!IMPORTANT]
>В следующих разделах приведены примеры команд Windows PowerShell, которые содержат примеры значений для многих параметров. Убедитесь, что примеры значений в этих командах замените значения, которые подходят для развертывания, прежде чем вы выполните следующие команды.  
  
#### <a name="bkmk_subnets"></a>Создание подсетей клиента DNS  
Первым шагом является определение подсети и пространства IP-адресов из регионов, для которых вы хотите перенаправить трафик. Например если вы хотите перенаправить трафик для США и Европе, необходимо определить подсети и пространства IP-адресов из этих регионов.  
  
Эти сведения можно получить из maps Geo-IP. На основе этих Geo-IP версий, необходимо создать «Подсетей клиента DNS». Подсеть клиента DNS — это логическая группа подсети IPv4 или IPv6, из которых запросы отправляются на DNS-сервер.  
  
Можно использовать следующие команды Windows PowerShell для создания подсетей клиента DNS.  
  
```  
Add-DnsServerClientSubnet -Name "AmericaSubnet" -IPv4Subnet "192.0.0.0/24, 182.0.0.0/24"  
  
Add-DnsServerClientSubnet -Name "EuropeSubnet" -IPv4Subnet "141.1.0.0/24, 151.1.0.0/24"  
  
```  
Дополнительные сведения см. в разделе [DnsServerClientSubnet добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverclientsubnet?view=win10-ps).  
  
#### <a name="bkmk_zscopes"></a>Создание области зоны  
После того как настроены подсети клиента, необходимо секционировать зоны, трафик которых вы хотите перенаправить на две области для другой зоны, одну область для каждой из подсетей клиента DNS, который вы настроили.  
  
Например если вы хотите перенаправить трафик для www.contosogiftservices.com имя DNS, необходимо создать две области другую зону в зоне contosogiftservices.com: для США и Европы.  
  
Область зоны — это уникальный экземпляр зоны. Зоны DNS может иметь несколько областей зоны, с каждой из областей зоны, содержащий собственный набор записей DNS. Та же запись могут присутствовать в нескольких областях, различные IP-адреса или же IP-адреса.  
  
>[!NOTE]
>По умолчанию области зоны существует для зон DNS. Эта область зоны имеет то же имя, что зона и устаревших работы DNS работать в этой области.  
  
Следующие команды Windows PowerShell можно использовать для создания области зоны.  
  
```  
Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "SeattleZoneScope"  
  
Add-DnsServerZoneScope -ZoneName "contosogiftservices.com" -Name "DublinZoneScope"  
  
```  
Дополнительные сведения см. в разделе [DnsServerZoneScope добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverzonescope?view=win10-ps).  
  
#### <a name="bkmk_records"></a>Добавление записей в области зоны  
Теперь необходимо добавить записи, представляющий узел веб-сервера в области две зоны.  
  
Например, в **SeattleZoneScope**, запись **www.contosogiftservices.com** добавляется с IP-адресом 192.0.0.1, который находится в Сиэтле центре обработки данных. Аналогично, в **DublinZoneScope**, запись **www.contosogiftservices.com** добавляется с IP-адресом 141.1.0.3 в центре обработки данных Дублин  
  
Следующие команды Windows PowerShell можно использовать для добавления записей в области зоны.  
  
```  
Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "192.0.0.1" -ZoneScope "SeattleZoneScope  
  
Add-DnsServerResourceRecord -ZoneName "contosogiftservices.com" -A -Name "www" -IPv4Address "141.1.0.3" -ZoneScope "DublinZoneScope"  
  
```  
Параметр зонаобласть не включена, при добавлении записи в области по умолчанию. Это то же самое, что при добавлении записей стандартной зоны DNS.  
  
Дополнительные сведения см. в разделе [Add-DnsServerResourceRecord](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverresourcerecord?view=win10-ps).  
  
#### <a name="bkmk_policies"></a>Создайте политики DNS  
После создания подсети секций (области зоны) и добавления записей, необходимо создать политики, которые соединяют подсетей и секций, таким образом, когда запрос поступает из источника в одной из подсетей клиента DNS, ответ на запрос возвращается из области зоны. Политики не являются обязательными для сопоставления области зоны по умолчанию.  
  
После настройки этих политик DNS, поведение сервера DNS выглядит следующим образом:  
  
1. Европейская DNS-клиенты получают IP-адрес веб-сервера в центре обработки данных Dublin в их ответа на запрос DNS.  
2. American DNS-клиенты получают IP-адрес веб-сервера в центре обработки данных Сиэтл в их ответа на запрос DNS.  
3. Между 18: 00 до 21: 00 в Дублине 20% запросов из Европы клиенты получают IP-адрес веб-сервера в центре обработки данных Сиэтл в их ответа на запрос DNS.  
4. От 18: 00 до 21: 00 в Сиэтле 20% запросов от клиентов American получать IP-адрес веб-сервера в центре обработки данных Dublin в их ответа на запрос DNS.  
5. Половина запросов от остальной части мира получают IP-адрес в центре обработки данных в Сиэтле, а вторая половина получают IP-адрес центра обработки данных Dublin.  
  
  
Следующие команды Windows PowerShell можно использовать для создания политики DNS, каналам подсетей клиента DNS и области зоны.  
  
>[!NOTE]
>В этом примере DNS-сервер находится в часовом поясе GMT, поэтому час пиковые периоды времени должно быть выражено в эквивалентное время по Гринвичу.  
  
```  
Add-DnsServerQueryResolutionPolicy -Name "America6To9Policy" -Action ALLOW -ClientSubnet "eq,AmericaSubnet" -ZoneScope "SeattleZoneScope,4;DublinZoneScope,1" -TimeOfDay "EQ,01:00-04:00" -ZoneName "contosogiftservices.com" -ProcessingOrder 1  
  
Add-DnsServerQueryResolutionPolicy -Name "Europe6To9Policy" -Action ALLOW -ClientSubnet "eq,EuropeSubnet" -ZoneScope "SeattleZoneScope,1;DublinZoneScope,4" -TimeOfDay "EQ,17:00-20:00" -ZoneName "contosogiftservices.com" -ProcessingOrder 2  
  
Add-DnsServerQueryResolutionPolicy -Name "AmericaPolicy" -Action ALLOW -ClientSubnet "eq,AmericaSubnet" -ZoneScope "SeattleZoneScope,1" -ZoneName "contosogiftservices.com" -ProcessingOrder 3  
  
Add-DnsServerQueryResolutionPolicy -Name "EuropePolicy" -Action ALLOW -ClientSubnet "eq,EuropeSubnet" -ZoneScope "DublinZoneScope,1" -ZoneName "contosogiftservices.com" -ProcessingOrder 4  
  
Add-DnsServerQueryResolutionPolicy -Name "RestOfWorldPolicy" -Action ALLOW --ZoneScope "DublinZoneScope,1;SeattleZoneScope,1" -ZoneName "contosogiftservices.com" -ProcessingOrder 5  
  
```  
Дополнительные сведения см. в разделе [DnsServerQueryResolutionPolicy добавить](https://docs.microsoft.com/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy?view=win10-ps).  
  
Теперь DNS-сервера с помощью необходимых политик DNS для перенаправления трафика на основе географического расположения и время суток.  
  
Когда DNS-сервер получает запросы разрешения имен, DNS-сервер оценивает поля в запрос DNS к настроенных политик DNS. Если исходный IP-адрес в запрос на разрешение имени соответствует какой-либо политики, области связанных зоны, используются для ответа на запрос, и пользователь перенаправляется к ресурсу, которая географически ближе к ним.  
  
Можно создать тысячи политик DNS в соответствии с трафиком требований к управлению, а все новые политики применяются динамически — без перезапуска DNS-сервер — на входящих запросов.

