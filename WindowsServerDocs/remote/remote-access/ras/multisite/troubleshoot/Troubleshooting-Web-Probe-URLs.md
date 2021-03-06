---
title: Диагностическая информация об URL-адресах веб-пробы
description: Эта статья является частью руководств по развертыванию нескольких серверов удаленного доступа в многосайтовом развертывании в Windows Server 2016.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6dfffd1e-f4f4-43b6-9e3c-49015ce34338
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 132db4811ee135d2ebff99efed6f53b5db1356ad
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71404432"
---
# <a name="troubleshooting-web-probe-urls"></a>Диагностическая информация об URL-адресах веб-пробы

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Этот раздел содержит информацию по устранению проблем, связанных с командой `Set-DAEntryPointDC`. Чтобы убедиться, что полученное сообщение об ошибке относится к заданию контроллера домена для точки входа, проверьте наличие события с идентификатором 10065 в журнале событий Windows.  
  
## <a name="SaveGPOSettings"></a>Сохранение параметров объекта групповой политики сервера  
**Произошла ошибка**. Произошла ошибка при сохранении параметров удаленного доступа в GPO < GPO_name >.  
  
Сведения об устранении этой ошибки см. в разделе Сохранение параметров объекта групповой политики сервера.  
  
## <a name="remote-access-is-not-configured"></a>Удаленный доступ не настроен  
**Произошла ошибка**. Удаленный доступ не настроен на < server_name >. Укажите имя сервера, включенного в многосайтовое развертывание.  
  
или  
  
Удаленный доступ не настроен на сервере < server_name >. Укажите компьютер с включенным DirectAccess.  
  
**Причина**  
  
На компьютере, который задан параметром *ComputerName*, не настроен удаленный доступ.  
  
Командлет `Set-DaEntryPointDC` доступен только на серверах, входящих в состав настроенного многосайтового развертывания.  
  
**Решение**  
  
Выполните эту команду, указав в параметре *ComputerName* имя сервера, который уже настроен как часть многосайтового развертывания.  
  
## <a name="multisite-is-not-enabled"></a>Многосайтовое развертывание не включено  
**Произошла ошибка**. Перед выполнением этой операции необходимо включить многосайтовое развертывание. Для этого используйте командлет `Enable-DAMultiSite`.  
  
**Причина**  
  
На сервере не включено многосайтовое развертывание, указанное параметром *ComputerName*.  
  
Командлет `Set-DaEntryPointDC` доступен только на серверах, входящих в состав настроенного многосайтового развертывания.  
  
**Решение**  
  
Выполните эту команду, указав в параметре *ComputerName* имя сервера, который уже настроен как часть многосайтового развертывания.  
  
## <a name="entry-point-and-domain-controller-not-provided-in-cmdlet"></a>В командлете не указаны точка входа и контроллер домена  
Командлет `Set-DaEntryPointDC` позволяет менять контроллеры домена, связанные с различными точками входа — например, если тот или иной контроллер оказался недоступным. При этом можно задать другой контроллер домена для конкретной точки входа или для всех точек входа, использовавших определенный контроллер. В первом случае следует указать точку входа, свойства которой требуется обновить, с помощью параметра *EntryPointName*. Во втором случае следует указать контроллер домена, который требуется заменить, с помощью параметра *ExistingDC*. Задать можно только один из этих параметров.  
  
**Произошла ошибка**. Обязательные параметры не указаны. Введите имя точки входа или имя существующего контроллера домена.  
  
или  
  
Для командлета `Set-DaEntryPointDC` указаны не все необходимые параметры.  
  
**Причина**  
  
Не указаны параметры *ентрипоинтнаме* или *ексистингдк* , или для командлета `Set-DaEntryPointDC` указаны оба параметра.  
  
**Решение**  
  
Выполните команду, указав в ней параметр *EntryPointName* или *ExistingDC*, но не оба параметра сразу.  
  
## <a name="could-not-locate-domain-controller"></a>Контроллер домена не найден  
**Произошла ошибка**. Не удается автоматически выбрать новый контроллер домена. Повторите попытку позже или проверьте параметры контроллера домена.  
  
**Причина**  
  
Компьютер, указанный в параметре *ComputerName*, недоступен через RPC или в домене отсутствуют доступные для записи контроллеры домена.  
  
**Решение**  
  
Обеспечьте доступ к удаленному компьютеру через RPC и наличие в этом домене доступного для записи контроллера домена. Если в домене имеется доступный для записи контроллер, можно указать его имя явно, используя параметр *NewDC*.  
  
## <a name="could-not-connect-to-domain-controller"></a>Не удалось подключиться к контроллеру домена  
  
-   **Выпуск 1**  
  
    **Произошла ошибка**. Не удается подключиться к >у domain_controller < контроллера домена. Проверьте подключение к сети и доступность сервера.  
  
    **Причина**  
  
    Не удается связаться с контроллером домена. Это происходит, только если администратор указал контроллер домена в параметрах *NewDC* или *ExistingDC*.  
  
    **Решение**  
  
    Убедитесь, что имя контроллера домена написано правильно. Если использовалось короткое имя, укажите вместо него полное доменное имя и повторите попытку.  
  
-   **Выпуск 2**  
  
    **Произошла ошибка**. Не удается связаться с > domain_controller контроллера домена <.  
  
    **Причина**  
  
    Это сообщение может указывать на неполадки в сети, не позволяющие связаться с контроллером домена, указанным в параметре *NewDC*, или с каким-либо другим существующим контроллером домена в данной конфигурации.  
  
    **Решение**  
  
    Убедитесь, что имя контроллера домена написано правильно, что такой контроллер существует, работает и доступен для записи, а также в том, что между этим контроллером и соответствующим доменом имеется отношение доверия.  
  
-   **Выпуск 3**  
  
    **Произошла ошибка**. Не удается подключиться к < > domain_controller контроллера домена для %2! s!.  
  
    **Причина**  
  
    Для поддержания согласованности конфигурации в многосайтовом развертывании важно, чтобы каждым объектом групповой политики управлял один контроллер домена. Если контроллер домена, управляющий объектом групповой политики сервера точки входа, недоступен, параметры конфигурации удаленного доступа не могут быть прочитаны или изменены.  
  
    **Решение**  
  
    Выполните процедуру "Изменение контроллера домена, который управляет объектами групповой политики сервера", описанным в [2,4. Настройка объектов групповой политики](assetId:///b1960686-a81e-4f48-83f1-cc4ea484df43#ConfigGPOs).  
  
-   **Выпуск 4**  
  
    **Произошла ошибка**. Не удается подключиться к основному контроллеру домена в домене < domain_name >.  
  
    **Причина**  
  
    Для поддержания согласованности конфигурации в многосайтовом развертывании важно, чтобы каждым объектом групповой политики управлял один контроллер домена. Управление клиентскими объектами групповой политики осуществляется на основном контроллере домена. Если основной контроллер домена недоступен, чтение или изменение параметров конфигурации удаленного доступа невозможно.  
  
    **Решение**  
  
    Выполните процедуру "перенесите роль эмулятора PDC", описанную в [2,4. Настройка объектов групповой политики](assetId:///b1960686-a81e-4f48-83f1-cc4ea484df43#ConfigGPOs).  
  
## <a name="read-only-domain-controller"></a>Контроллер домена только для чтения.  
**Произошла ошибка**. Контроллер домена < domain_controller > доступен только для чтения. Укажите контроллер домена, доступный не только для чтения.  
  
**Причина**  
  
Контроллер домена, указанный в параметре *NewDC*, доступен только для чтения.  
  
**Решение**  
  
При использовании командлета `Set-DAEntryPointDC` с помощью параметра *NewDC* задается новый контроллер домена для конкретной точки входа или всех точек входа, связанных с определенным контроллером домена. Поэтому новый контроллер домена должен быть доступен для записи. Укажите доступный для записи контроллер домена в параметре *NewDC* и повторите попытку.  
  
## <a name="cannot-retrieve-gpo"></a>Не удается получить объект групповой политики  
  
-   **Выпуск 1**  
  
    **Произошла ошибка**. < Объектов групповой политики GPO_name > на контроллере домена < previous_domain_controller > не может быть получен из контроллера домена < replacement_domain_controller >, так как они находятся в разных доменах.  
  
    **Причина**  
  
    Сервер удаленного доступа и контроллер домена находятся в разных доменах, поэтому получить объект групповой политики не удается.  
  
    **Решение**  
  
    Если вы пытались обновить параметры конкретной точки входа, убедитесь, что новый контроллер домена находится в том же домене, что и сервер точки входа. Если вы пытались заменить конкретный контроллер домена, убедитесь, что новый контроллер домена находится в том же домене, что и подлежащий замене контроллер.  
  
-   **Выпуск 2**  
  
    **Произошла ошибка**. < Объектов групповой политики GPO_name > на контроллере домена < previous_domain_controller > не может быть получен из контроллера домена < replacement_domain_controller >. Дождитесь завершения репликации домена и повторите попытку.  
  
    **Причина**  
  
    В процессе назначения точке входа нового контроллера домена командлет предпринимает попытку прочесть объект групповой политики сервера с данного контроллера, но найти этот объект не удается, поскольку он еще не реплицирован.  
  
    **Решение**  
  
    Объект групповой политики сервера отсутствует на новом контроллере домена. Убедитесь, что все объекты групповой политики успешно реплицированы на новом контроллере домена, а затем повторите попытку.  
  
-   **Выпуск 3**  
  
    **Произошла ошибка**. У вас нет разрешений на доступ к < объектов групповой политики GPO_name >.  
  
    **Причина**  
  
    В процессе назначения нового контроллера домена точке входа командлет предпринимает попытку прочесть объект групповой политики сервера с данного контроллера, но сделать это не удается, поскольку у пользователя нет соответствующих разрешений.  
  
    **Решение**  
  
    Объект групповой политики существует на контроллере домена, но не может быть считан. Заручитесь необходимыми разрешениями и повторите попытку.  
  
## <a name="entry-point-not-part-of-multisite-deployment"></a>Точка входа не входит в многосайтовое развертывание  
**Произошла ошибка**. Точка входа < entry_point_name > не является частью многосайтового развертывания. Укажите другое значение.  
  
**Причина**  
  
Указанное вами имя точки входа не найдено.  
  
**Решение**  
  
Убедитесь в том, что имя точки входа написано правильно и что объекты групповой политики реплицированы на соответствующие контроллеры домена, после чего повторите попытку. Чтобы увидеть, какой контроллер домена назначен каждой из точек входа, воспользуйтесь командлетом `Get-DAEntryPointDC`.  
  
## <a name="remote-access-server-settings"></a>Параметры сервера удаленного доступа  
  
-   **Выпуск 1**  
  
    **Произошла ошибка**. Сервер < server_name > в точке входа < entry_point_name > недоступен.  
  
    **Причина**  
  
    В процессе назначения точке входа нового контроллера домена командлет предпринимает попытку прочесть и записать данные об этом контроллере домена на всех соответствующих серверах удаленного доступа. Командлету не удалось прочесть данные с одного или нескольких серверов удаленного доступа.  
  
    **Решение**  
  
    Убедитесь в том, что все соответствующие серверы удаленного доступа работают и на каждом из них у вас имеются разрешения локального администратора, после чего повторите попытку.  
  
-   **Выпуск 2**  
  
    **Произошла ошибка**. Не удается сохранить параметры в реестре на сервере < server_name > в точке входа < entry_point_name >.  
  
    **Причина**  
  
    В процессе назначения точке входа нового контроллера домена командлет предпринимает попытку прочесть и записать данные об этом контроллере домена на всех соответствующих серверах удаленного доступа. Командлету не удалось записать данные на один или несколько серверов удаленного доступа.  
  
    **Решение**  
  
    Убедитесь в том, что все соответствующие серверы удаленного доступа работают и на каждом из них у вас имеются разрешения локального администратора, после чего повторите попытку.  
  
-   **Выпуск 3**  
  
    **Произошла ошибка**. Обновления объектов групповой политики не могут применяться к < server_name >. Изменения вступят в силу только при следующем обновлении политики.  
  
    **Причина**  
  
    При использовании командлета `Set-DAEntryPointDC` в параметре *ComputerName* указан сервер удаленного доступа не в той точке входа, которая была последней добавлена в многосайтовое развертывание.  
  
    **Решение**  
  
    Увидеть, какие серверы не были обновлены, можно в разделе **Состояние конфигурации** на **панели мониторинга** консоли управления удаленным доступом. Это не влечет никаких функциональных нарушений; чтобы немедленно обновить состояние конфигурации, можно запустить командлет `gpupdate /force` на серверах, которые не были обновлены.  
  
## <a name="problem-resolving-fqdn"></a>Проблема с разрешением полного доменного имени  
**Произошла ошибка**. Сервер < server_name > в точке входа < entry_point_name > недоступен.  
  
**Причина**  
  
При получении списка серверов DirectAccess, которые требуется изменить, командлету не удалось разрешить полное доменное имя одного из серверов по идентификатору безопасности его компьютера.  
  
**Решение**  
  
Точка входа, указанная в сообщении об ошибке, связана с контроллером домена. Убедитесь в доступности контроллера домена для этой точки входа. Если компьютер, которому принадлежит данный идентификатор безопасности, был исключен из домена, не обращайте внимания на это сообщение и удалите соответствующий сервер из многосайтового развертывания.  
  
## <a name="no-entry-points-to-update"></a>Нет точек входа, подлежащих обновлению  
**Получено предупреждение**. Параметры контроллера домена не были изменены. Если вы считаете, что изменения необходимы, убедитесь, что параметры командлета заданы правильно и что объекты групповой политики реплицированы на требуемые контроллеры домена.  
  
**Причина**  
  
При вызове командлета `Set-DaEntryPointDC` с параметром *ExistingDC* служба DirectAccess проверяет все точки входа и обновляет параметры точек входа, связанных с указанным контроллером домена. Однако ни одна точка входа не использует контроллер домена, указанный в параметре *ExistingDC*.  
  
**Решение**  
  
Чтобы просмотреть список точек входа и связанных с ними контроллеров домена, воспользуйтесь командлетом `Get-DAEntryPointDC`. Если изменения должны были произойти, убедитесь в том, что параметры командлета написаны правильно и что объекты групповой политики реплицированы на соответствующие контроллеры домена, после чего повторите попытку.  
  


