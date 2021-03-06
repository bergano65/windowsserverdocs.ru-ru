---
title: Использование регулярных выражений в NPS
description: В этом разделе объясняется использование регулярных выражений для сопоставления шаблонов в NPS в Windows Server. Этот синтаксис можно использовать для указания условий атрибутов сетевой политики и сфер RADIUS.
manager: brianlic
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: bc22d29c-678c-462d-88b3-1c737dceca75
ms.author: jgerend
author: jasongerend
msdate: 08/16/2019
ms.openlocfilehash: 94bb9b54dba046c57c6f82e6a52a71adbcf4ce75
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396375"
---
# <a name="use-regular-expressions-in-nps"></a>Использование регулярных выражений в NPS

> Область применения: Windows Server 2019, Windows Server 2016, Windows Server (половина ежегодного канала)

В этом разделе объясняется использование регулярных выражений для сопоставления шаблонов в NPS в Windows Server. Этот синтаксис можно использовать для указания условий атрибутов сетевой политики и сфер RADIUS.

## <a name="pattern-matching-reference"></a>Справочник по соответствию шаблону

Приведенную ниже таблицу можно использовать в качестве эталонного источника при создании регулярных выражений с синтаксисом сопоставления шаблонов. Обратите внимание, что шаблоны регулярных выражений часто заключены в прямые косые черты (/).

|  Символов  |  Описание  |   Пример                                                                 |
| ----------- | ------------- | ------------------------------------------------------------------------  |
|     `\ `     | Указывает, что символ, следующий за, является специальным символом или должен интерпретироваться буквально.  | `/n/ matches the character "n" while the sequence /\n/ matches a line feed or newline character.`  |
|     `^`     |                                                                 Соответствует началу ввода или строки.                                                                  |                                                                 &nbsp;                                                                  |
|     `$`     |                                                                    Соответствует концу ввода или строки.                                                                     |                                                                 &nbsp;                                                                  |
|     `*`     |                                                             Соответствует предыдущему символу ноль или более раз.                                                              |                                                  `/zo*/ matches either "z" or "zoo."`                                                   |
|     `+`     |                                                              Соответствует предыдущему символу один или более раз.                                                              |                                                   `/zo+/ matches "zoo" but not "z."`                                                    |
|     `?`     |                                                              Соответствует предыдущему символу ноль или один раз.                                                              |                                                 `/a?ve?/ matches the "ve" in "never."`                                                  |
|     `.`     |                                                           Соответствует любому отдельному символу, кроме символа новой строки.                                                           |                                                                 &nbsp;                                                                  |
| `(pattern)` |                         Соответствует "шаблону" и запоминает совпадение.<br />Чтобы сопоставить литеральные символы `(` и `)` (круглые скобки), используйте `\(` или `\)`.                         |                                                                 &nbsp;                                                                  |
|   `x | y `  |                                                                               Соответствует либо x, либо y.                                                          |
|   `{n} `    |                                                          Соответствует ровно n раз \(n — не\-отрицательное целое число\).                                                           |               `/o{2}/ does not match the "o" in "Bob," but matches the first two instances of the letter o in "foooood."`               |
|   `{n,}`    |                                                          Соответствует как минимум n раз \(n — не\-отрицательное целое число\).                                                          | `/o{2,}/ does not match the "o" in "Bob" but matches all of the instances of the letter o in "foooood." /o{1,}/ is equivalent to /o+/.` |
|   `{n,m}`   |                                                Соответствует как минимум n и не более m раз \(m и n являются не\-отрицательными целыми числами\).                                                |                               `/o{1,3}/ matches the first three instances of the letter o in "fooooood."`                               |
|   `[xyz]`   |                                                       Соответствует любому из вложенных символов \(кодировке\).                                                        |                                                  `/[abc]/ matches the "a" in "plain."`                                                  |
|  `[^xyz]`   |                                                  Соответствует всем символам, не заключенным \(\)ной кодировке.                                                  |                                                 `/[^abc]/ matches the "p" in "plain."`                                                  |
|    `\b`     |                                                              Соответствует границе слова \(например, пробел\).                                                               |                                              `/ea*r\b/ matches the "er" in "never early."`                                              |
|    `\B`     |                                                                         Соответствует несловной границе.                                                                          |                                             `/ea*r\B/ matches the "ear" in "never early."`                                              |
|    `\d`     |                                                       Соответствует цифровому символу \(эквивалентно цифрам от 0 до 9\).                                                        |                                                                 &nbsp;                                                                  |
|    `\D`     |                                                           Соответствует нецифровому символу \(эквивалент `[^0-9]`\).                                                           |                                                                 &nbsp;                                                                  |
|    `\f`     |                                                                        Соответствует символу перевода формы.                                                                        |                                                                 &nbsp;                                                                  |
|    `\n`     |                                                                        Соответствует символу перевода строки.                                                                        |                                                                 &nbsp;                                                                  |
|    `\r`     |                                                                     Соответствует символу возврата каретки.                                                                     |                                                                 &nbsp;                                                                  |
|    `\s`     |                                   Соответствует любому символу пробела, включая пробел, табуляцию и веб-канал формы \(эквивалентом `[ \f\n\r\t\v]`\).                                   |                                                                 &nbsp;                                                                  |
|    `\S`     |                                                  Соответствует любому символу, отличному от пробела, \(эквиваленте `[^ \f\n\r\t\v]`\).                                                   |                                                                 &nbsp;                                                                  |
|    `\t`     |                                                                           Соответствует символу табуляции.                                                                           |                                                                 &nbsp;                                                                  |
|    `\v`     |                                                                      Соответствует символу вертикальной табуляции.                                                                       |                                                                 &nbsp;                                                                  |
|    `\w`     |                                              Соответствует любому символу слова, включая знак подчеркивания \(эквивалент `[A-Za-z0-9_]`\).                                              |                                                                 &nbsp;                                                                  |
|    `\W`     |                                           Соответствует любому символу, не\-слову, без знака подчеркивания \(эквивалента `[^A-Za-z0-9_]`\).                                           |                                                                 &nbsp;                                                                  |
|   `\num`    | Ссылается на сохраненные соответствия \(`?num`, где num — положительное целое число\).  Этот параметр можно использовать только в текстовом поле **заменить** при настройке манипуляций с атрибутами. |                                       `\1` заменяет то, что хранится в первом сохраненном совпадении.                                       |
|   `/n/ `    |                      Позволяет вставлять ASCII-коды в регулярные выражения \(`?n`, где n — восьмеричное, шестнадцатеричное или десятичное значение escape\).                       |                                                                 &nbsp;                                                                  |

## <a name="examples-for-network-policy-attributes"></a>Примеры атрибутов сетевой политики

В следующих примерах описывается использование синтаксиса сопоставления шаблонов для указания атрибутов сетевой политики.

- Для указания всех номеров телефонов в коде области 899 используется следующий синтаксис:

     `899.*`

- Чтобы указать диапазон IP-адресов, начинающихся с 192.168.1, используется следующий синтаксис:

    `192\.168\.1\..+`

## <a name="examples-for-manipulation-of-the-realm-name-in-the-user-name-attribute"></a>Примеры манипуляций с именем области в атрибуте имени пользователя

В следующих примерах описывается использование синтаксиса сопоставления шаблонов для управления именами областей для атрибута имени пользователя, который находится на вкладке **атрибут** в свойствах политики запросов на подключение.

**Удаление области в атрибуте имени пользователя**

В сценарии удаленного коммутируемого доступа, в котором поставщик услуг Интернета \(\) направляет запросы на подключение к NPS Организации, прокси-серверу поставщика услуг Интернета может потребоваться имя области для маршрутизации запроса на проверку подлинности. Однако сервер политики сети может не распознать имя области, часть имени пользователя. Таким образом, имя области должно быть удалено прокси-сервером RADIUS поставщика услуг Интернета до его перенаправления в NPS Организации.

- Поиск: @microsoft\.com

- Замена:

**Для замены <em>user@example.microsoft.com</em> на _example.microsoft.com\user_**

- Поиск:`(.*)@(.*)`

- Заменить:`$2\$1`



**Замена _домен \ пользователь_ на _specific_domain_**

- Поиск:`(.*)\\(.*)`

- Заменить: *specific_domain*`\$2`



<strong>Замена *пользователя* *user@specific_domain</strong>*

- Поиск:`$`

- Заменить: @*specific_domain*

## <a name="example-for-radius-message-forwarding-by-a-proxy-server"></a>Пример перенаправления сообщений RADIUS прокси-сервером

Вы можете создать правила маршрутизации, которые перенаправляют сообщения RADIUS с указанным именем области в набор серверов RADIUS, когда NPS используется в качестве прокси-сервера RADIUS. Ниже приведен рекомендуемый синтаксис для маршрутизации запросов на основе имени области.

- **NetBIOS-имя**: `WCOAST`
- **Шаблон**: `^wcoast\\`

В следующем примере wcoast.microsoft.com — это уникальный суффикс имени участника-пользователя (UPN) для DNS или доменного wcoast.microsoft.com Active Directory. Используя указанный шаблон, прокси-сервер NPS может маршрутизировать сообщения на основе имени NetBIOS домена или суффикса UPN.

- **NetBIOS-имя**: `WCOAST`
- **Суффикс имени участника-пользователя**: `wcoast.microsoft.com`
- **Шаблон**: `^wcoast\\|@wcoast\.microsoft\.com$`


Дополнительные сведения об управлении NPS см. в разделе [Управление сервером политики сети](nps-manage-top.md).

Дополнительные сведения о NPS см. в разделе [сервер политики сети (NPS)](nps-top.md).
