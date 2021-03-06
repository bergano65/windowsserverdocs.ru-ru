---
title: netstat
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 60e2718f-93cc-4ceb-bf0e-58a6a6e4fc8b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 54bd21b7e96275d329e45e825971d9236488c793
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373265"
---
# <a name="netstat"></a>netstat

>Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Отображаются активные TCP-подключения, порты, на которых компьютер прослушивается, статистика Ethernet, таблица маршрутизации IP-адресов, статистика IPv4 (для протоколов IP, ICMP, TCP и UDP) и Статистика IPv6 (для протоколов IPv6, ICMPv6, TCP по IPv6 и UDP через IPv6). Используется без параметров, команда **netstat** ОТОБРАЖАЕТ активные TCP-подключения. 

## <a name="syntax"></a>Синтаксис
```
netstat [-a] [-e] [-n] [-o] [-p <Protocol>] [-r] [-s] [<Interval>]
```

### <a name="parameters"></a>Параметры

|   Параметр   |                                                                                                                                              Описание                                                                                                                                              |
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      -a       |                                                                                                   Отображает все активные TCP-подключения и порты TCP и UDP, прослушиваемые компьютером.                                                                                                   |
|      -e       |                                                                                 Отображает статистику Ethernet, например число отправленных и полученных байтов и пакетов. Этот параметр можно сочетать с **-s**.                                                                                  |
|      -n       |                                                                               Отображает активные TCP-подключения, однако адреса и номера портов выражаются в числовом виде, и для определения имен не выполняется никаких попыток.                                                                               |
|      -o       |                          Отображает активные TCP-подключения и включает идентификатор процесса (PID) для каждого подключения. Приложение, основанное на PID, можно найти на вкладке процессы в диспетчере задач Windows. Этот параметр можно сочетать с параметрами **-a**, **-n**и **-p**.                           |
| -p <Protocol> |               Показывает соединения для протокола, заданного *протоколом*. В этом случае *протоколом* может быть TCP, UDP, TCPv6 или UDPv6. Если этот параметр используется вместе с **-s** для вывода статистики по протоколу, *протокол* может принимать значение TCP, UDP, ICMP, IP, tcpv6, udpv6, ICMPv6 или IPv6.                |
|      -s       | Отображает статистику по протоколу. По умолчанию для протоколов TCP, UDP, ICMP и IP отображается статистика. Если установлен протокол IPv6, для протоколов TCP через IPv6, UDP через IPv6, ICMPv6 и IPv6 отображаются статистические данные. Параметр **-p** можно использовать для указания набора протоколов. |
|      -r       |                                                                                                     Отображает содержимое таблицы IP-маршрутизации. Это эквивалентно команде Route Print.                                                                                                     |
|  <Interval>   |                                                        Повторно отображает выбранную информацию каждый *интервал* в секундах. Нажмите клавиши CTRL + C, чтобы прерывать повторное отображение. Если этот параметр не указан, команда **netstat** выводит выбранные данные только один раз.                                                         |
|      /?       |                                                                                                                                 Отображение справки в командной строке.                                                                                                                                  |

## <a name="remarks"></a>Примечания
-   Параметры, используемые с этой командой, должны начинаться с дефиса ( **-** ), а не с косой черты ( **/** ).
-   **netstat** предоставляет статистические данные для следующих действий:
    -   Имя протокол (TCP или UDP).
    -   Локальный адрес IP-адрес локального компьютера и используемый номер порта. Имя локального компьютера, соответствующее IP-адресу и имя порта, отображается, если не указан параметр **-n** . Если порт еще не установлен, номер порта отображается в виде звездочки (*).
    -   инородный адрес IP-адрес и номер порта удаленного компьютера, к которому подключен сокет. Имена, соответствующие IP-адресу и порту, отображаются, если не указан параметр **-n** . Если порт еще не установлен, номер порта отображается в виде звездочки (*).
    -   с Указывает состояние TCP-соединения. Возможны следующие состояния. CLOSE_WAIT закрытый FIN_WAIT_1 FIN_WAIT_2 LAST_ACK listEN SYN_RECEIVED SYN_SEND timeD_WAIT дополнительные сведения о состояниях TCP-подключения см. в документе RFC 793.
-   Эта команда доступна, только если протокол Internet Protocol (TCP/IP) установлен в качестве компонента в свойствах сетевого адаптера в окне Сетевые подключения.

## <a name="BKMK_Examples"></a>Примеров
Чтобы отобразить статистику Ethernet и статистику для всех протоколов, введите:
```
netstat -e -s
```
Чтобы отобразить статистику только для протоколов TCP и UDP, введите:
```
netstat -s -p tcp udp
```
Чтобы отобразить активные TCP-подключения и идентификаторы процессов каждые 5 секунд, введите:
```
netstat -o 5
```
Чтобы отобразить активные TCP-подключения и идентификаторы процессов в числовом формате, введите:
```
netstat -n -o
```

## <a name="additional-references"></a>Дополнительные ссылки
-   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
