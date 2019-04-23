---
ms.assetid: 8f994e2e-6c07-43f0-aef4-75f8b2c9a144
title: Повышение уровня безопасности среды
description: ''
author: MicrosoftGuyJFlo
ms.author: joflore
manager: mtillman
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 554f841473d79edbac19ce4c53e99f5a43fa2b23
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59821705"
---
# <a name="maintaining-a-more-secure-environment"></a>Повышение уровня безопасности среды

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

*Закон десять чисел: Технологии — не панацея.* - [10 непреложных законов безопасности администрирования](https://technet.microsoft.com/library/cc722488.aspx)  
  
При создании управляемой, безопасной среды для важных ресурсов, следует сместить фокус ввода на гарантирует, что он сохранится безопасно. Несмотря на то, что вам предоставлен конкретных технических средств для повышения безопасности пакетов установки AD DS, одни лишь технологии не сможет защитить среду, в котором она не работает в сотрудничестве с бизнеса и поддержания инфраструктуры безопасности, можно использовать. Высокого уровня рекомендации, приведенные в этом разделе предназначены для использования в качестве рекомендации, которые можно использовать для разработки не только эффективную защиту, но эффективный жизненный цикл управления.  
  
В некоторых случаях ИТ может сталкиваться ваша организация уже тесное сотрудничество с бизнес-подразделения, которые помогут в реализации этих рекомендаций. В организациях, в котором она и бизнес-подразделения не связаны тесно, может потребоваться сначала получить одобрения руководства для внедрения инициатив по налаживанию тесное между ИТ и бизнес-единицы. [Пояснительная записка](../../../ad-ds/manage/component-updates/Executive-Summary.md) должен быть полезен, так как в результате одиночного документа на рассмотрение executive и его для ответственных за принятие решений в вашей организации.  
  
## <a name="creating-business-centric-security-practices-for-active-directory"></a>Создание по деловых безопасности для Active Directory  
В прошлом информационных технологий, многие организации рассматривали как структура поддержки и центра затрат. ИТ-отделы часто во многом были отделенной от бизнес-пользователей и взаимодействий, ограничена модель запрос ответ, в котором бизнеса запрошенных ресурсов и ответил ИТ.  
  
Так как технология прошла путь от и ростом обработки данных, концепции «компьютер, на каждом настольном компьютере» эффективно скидок передать большую часть мира и даже было число, широкий спектр легко доступные технологии, доступные сегодня. Информационные технологии больше не является функцией поддержки, а основные бизнес-функции. Если ваша организация не продолжать работать, если все ИТ-служб были недоступны, в организации является, по крайней мере в части информационных технологий.  
  
Чтобы создать эффективный компромисс планы восстановления, ИТ-служб необходимо проконсультироваться с бизнес-подразделениям организации для определения не только самые важные компоненты ИТ-ландшафте. Однако важные функции, необходимые для компании. Определив, что важно для вашей организации в целом, можно сосредоточиться на обеспечение безопасности компоненты, имеющие максимальную пользу. Это не является рекомендацией для шерк безопасности низкое значение систем и данных. Вместо этого, как определить уровни обслуживания для время работы системы, следует определение уровни безопасности контроля и мониторинга на основе важности средства.  
  
Когда вы вложили средства в создание текущего, безопасные, управляемые среды, можно переместить фокус эффективно управлять им и обеспечить эффективный жизненный цикл управления процессы, которые не определены только в ИТ, но для компании. Для этого необходимо не только позволяет сотрудничать с бизнеса, но вкладывать бизнеса в «владельцем» данных и систем в Active Directory.  
  
При добавлении данных и систем в Active Directory без назначенного, владельцы предприятий и ИТ-владельцев, нет не очистить цепи ответственностей в любое время для подготовки, управления, мониторинга, обновления и со временем ее из эксплуатации системы. Это приводит к инфраструктур, в которых системы подвергнуть организацию риску, но не удается из эксплуатации, так как остается неясным, владение. Для эффективного управления жизненным циклом пользователей, данных, приложений и систем под управлением служб Active Directory, должно соответствовать принципам, описанные в этом разделе.  
  
### <a name="assign-a-business-owner-to-active-directory-data"></a>Назначить владельцем компании данные Active Directory  
Данные в Active Directory должны иметь определенный бизнеса владельца, то есть указанное подразделение или пользователь, являющийся точку контакта для принятия решений о жизненном цикле средства. В некоторых случаях владелец компании долей Active Directory будет для ИТ-отдел или пользователя. Компоненты инфраструктуры, таких как контроллеры домена, серверы DHCP и DNS и Active Directory будет скорее «владельцем» ИТ. Для данных, добавляется в AD DS для поддержки бизнеса (например, новые сотрудники, новые приложения и новые сведения о репозитории), назначенный бизнеса единица или пользователя должна быть связана с данными.  
  
Независимо от используемого для записи владение данными в каталоге Active Directory или ли вы реализуете отдельную базу данных для отслеживания ИТ-активами, учетная запись пользователя отсутствует должен будет создан, нет сервера или рабочей станции должен быть установлен и приложение не должны развертываться без назначенного владельца записи. При попытке установления прав владения систем после их развертывания в рабочей среде может быть сложной задачей, в лучшем и в некоторых случаях невозможно. Таким образом владельца, нужно установить во время данных впервые появился в Active Directory.  
  
### <a name="implement-business-driven-lifecycle-management"></a>Реализовать управление жизненным циклом, управляемых деловой активностью  
Управление жизненным циклом должны быть реализованы в все данные в Active Directory. Например наличие нового приложения в домене Active Directory, владелец приложения компании следует с регулярными интервалами, ожидать подтвердить Продолжение использования приложения. При выпуске новой версии приложения владельцу бизнеса приложения нужны и необходимо определить, когда будет реализована новая версия.  
  
Если владелец предприятия решил не утверждать развертывание новой версии приложения, что владелец компании также должны быть уведомлены об дату, когда текущая версия больше не будет поддерживаться и должно быть ответственность за определение, будет ли приложение быть списан или замены. Поддержка предыдущих версий приложения под управлением и не поддерживается не должно быть параметр.  
  
При создании учетных записей пользователей в Active Directory свои диспетчеры записи следует уведомления во время создания объекта и требуется подтвердить действительность указанной учетной записи с регулярными интервалами. Путем реализации бизнеса driven жизненный цикл и регулярного аттестации допустимости данных, пользователям предоставляется возможность выявлять отклонения в данных лучше всего это люди, которые просмотрите данные.  
  
Например злоумышленники создать учетные записи пользователей, которые могут быть действительными учетными записями, следующие соглашения об именовании и размещение объекта в вашей организации. Чтобы обнаружить при создании этих учетных записей, может реализовать ежедневной задачи, возвращает все объекты пользователей, не имеющих владельца указанного бизнеса, таким образом, вы можете изучить учетные записи. Если злоумышленники создавать учетные записи и назначить владельцу бизнеса, путем реализации задачу, сообщающую создания новых объектов владельцу указанного предприятия, владелец компании может быстро определить ли учетная запись является законным.  
  
Следует реализовать подобные подходы для групп безопасности и распространения. Несмотря на то, что некоторые группы может быть функциональной группы, создаваемые ИТ, путем создания каждой группы с назначенного владельца, вы сможете получить все группы, принадлежащие указанного пользователя и пользователь должен подтвердить допустимость их членства. Как и подход для использования с создания учетной записи пользователя, вы можете активировать отчетов изменения групп владельцу указанного предприятия. Дополнительные процедуры становится для бизнес-владельцу подтвердить допустимость или недействительность данных в Active Directory, более широкие возможности, идентифицировать аномалии, которые можно указывать сбоев процесса или фактический компрометации.  
  
### <a name="classify-all-active-directory-data"></a>Классифицировать все данные Active Directory  
Помимо записи владелец предприятия для всех данных Active Directory во время он добавляется в каталог, необходимо также требовать компаниях для предоставления классификации данных. Например если приложение сохраняет критически важных бизнес-данных, владелец компании должны метки приложения таким образом, в соответствии с инфраструктурой классификации вашей организации.  
  
В некоторых организациях реализации политик классификации данных, метки данных, в соответствии с потенциальный ущерб от раскрытия данных придется при его были украдены или предоставляются. Другим организациям реализации классификации данных метки данных, уровень важности, требования к доступу и хранения. Независимо от модели классификации данных, используемых в вашей организации следует убедиться, что есть возможность применить классификацию, чтобы данные Active Directory, не только к данным «file». Если учетная запись пользователя учетной записи виртуального IP-адреса, это должно обнаружиться в базе данных классификации активов (ли это можно реализовать с помощью атрибутов для объектов в Доменных службах Active Directory или при развертывании баз данных классификации отдельный ресурс).  
  
В рамках модели классификации данных следует включить классификацию для данных AD DS, например следующие.  
  
### <a name="systems"></a>системы  
Вы должны не только классифицировать данные, но и их население сервера. Для каждого сервера, следует знать, какая операционная система установлена, какие основные роли, предоставляемые сервером, какие приложения работают на сервере, владельцем ИТ записи и владелец компании записи, где это возможно. Для всех данных или приложений, работающих на сервере должна требовать классификации и сервер должны быть защищены в соответствии с требованиями для рабочих нагрузок, которые она поддерживает и классификации, применительно к системе и данных. Можно также сгруппировать серверы по классификации рабочих нагрузок, которая позволяет быстро определить серверы, которые должны быть наиболее близко отслеживаемых и наиболее компиляторам настроен.  
  
### <a name="applications"></a>Приложения  
Следует классифицировать приложения по функциональности (что они делают), базу пользователей (который использует приложения) и операционной системы, в которой они выполняются. Необходимо поддерживать записи, содержащие сведения о версии, состояния обновлений и другие необходимые сведения. Следует также классифицировать приложений, типы данных, которые они обрабатывают, как описано выше.  
  
### <a name="users"></a>Пользователи  
Вызывать их пользователей «Виртуальный IP-адрес», ключевых учебных записей, или используйте другую метку, учетные записи в вашей установке службы Active Directory, которые, скорее всего, стали целью злоумышленников следует с тегами и отслеживается. В большинстве организаций нецелесообразно просто для отслеживания всех действий всех пользователей. Тем не менее если есть возможность определить критические учетные записи в установке Active Directory, вы можете отслеживать эти учетные записи для изменения, как описано ранее в этом документе.  
  
Кроме того, вы сможете построить базу данных «поведение» для этих учетных записей при проверке учетных записей. Например, если выяснится, что данный Руководитель использует его защищенной рабочей станции для доступа к важным данным из своего офиса и из него дома, но редко из других расположений, если вы видите пытается получить доступ к данным с помощью своей учетной записи, от неавторизованного компьютера или расположение на равном расстоянии по всей планете где известно руководителя находится не в настоящее время, можно более быстро обнаруживать и исследовать этот Аномальное поведение.  
  
Благодаря интеграции бизнес-информации с инфраструктурой, можно использовать бизнес-информации для идентификации ложных положительных результатов. Например если executive travel записывается в календаре, доступном для ИТ-специалистов, ответственность за наблюдение за среду, вы можете сопоставлять попыток соединения с руководители определенное место.  
  
Предположим, исполнительный объект обычно находится в Чикаго и использует защищенной рабочей станции для доступа к критически важных бизнес-данных с биноклем в руках, и событие инициируется Неудачная попытка доступа к данным из незащищенных рабочей станции, расположенный в Атланте. Если есть возможность убедитесь, что руководитель в настоящее время в Атланте, может разрешить событие, обратившись в службу руководителя или помощник руководителя, чтобы определить, было ли сбой доступа к результат руководителя, указан на защищенной рабочей станции доступ к данным. С помощью программы, использующей подходов, описанных в [планирование при компрометации](../../../ad-ds/plan/security-best-practices/Planning-for-Compromise.md), вы сможете создать базу данных ожидаемого поведения, наиболее «important» учетных записей в установке Active Directory, можно потенциально помогает более быстро обнаружить и реагирование на атаки.  
  

