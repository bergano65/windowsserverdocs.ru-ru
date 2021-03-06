---
title: Новые возможности SDN для Windows Server
description: В этом разделе содержатся сведения о новых сетевых функциях, определяемых программным обеспечением для Windows Server 1709.
manager: dougkim
ms.prod: windows-server
ms.technology: networking-hv-switch
ms.topic: get-started-article
ms.assetid: efad919b-e9e7-4a0c-b373-e68a092f93b5
ms.author: pashort
author: shortpatti
ms.date: 10/02/2018
ms.openlocfilehash: 09fcf8e3faf8d8b7f943255599dd3b273314db23
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405997"
---
# <a name="whats-new-in-sdn-for-windows-server-2019"></a>Что нового в программно-конфигурируемой сети (SDN) для Windows Server 2019?

>Относится к: Windows Server (Semi-Annual Channel)


|                         **Возможность**                          |                                                                                                                                                                                         **Описание**                                                                                                                                                                                         | **Новые или обновленные** |
|--------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|
| [Зашифрованные сети](vnet-encryption/sdn-vnet-encryption.md) | Шифрование виртуальной сети позволяет выполнять шифрование трафика виртуальной сети между виртуальными машинами, взаимодействующими друг с другом в подсетях, помеченных как "шифрование включено". Для шифрования пакетов с помощью этой возможности также используется протокол DTLS в виртуальной подсети. Протокол DTLS обеспечивает защиту от перехвата, несанкционированных изменений и подделки со стороны любых лиц, имеющих доступ к физической сети. |       Оператор new       |
|    [Аудит брандмауэра](security/sdn-firewall-auditing.md)    |                                                                                            Аудит брандмауэра — это новая возможность для брандмауэра SDN в Windows Server 2019. При включении брандмауэра SDN все потоки, обрабатываемые правилами брандмауэра SDN (ACL), для которых включено ведение журнала, записываются.                                                                                            |       Оператор new       |
| [Пиринг виртуальной сети](vnet-peering/sdn-vnet-peering.md)  |                                                                                                                      Пиринг виртуальных сетей позволяет легко подключать две виртуальные сети. После пиринга для подключения виртуальные сети отображаются в виде одной.                                                                                                                      |       Оператор new       |
|           [Измерение исходящего трафика](manage/sdn-egress.md)            |                  Эта новая функция в Windows Server 2019 обеспечивает использование SDN для предоставления показателей использования для передачи исходящих данных. После добавления этой функции сетевой контроллер сохраняет список разрешений на виртуальную сеть всех диапазонов IP-адресов, используемых в SDN, и рассматривайте все связанные с пакетами данные, которые не включены в один из этих диапазонов, для выставления счетов за передачу исходящих данных.                   |       Оператор new       |

---



