---
title: Использование групповая политика для настройки клиентских компьютеров членов домена
description: Эта статья является частью руководства по развертыванию BranchCache для Windows Server 2016, в котором показано, как развернуть BranchCache в распределенном и размещенном режимах кэша для оптимизации использования пропускной способности глобальной сети в филиалах.
manager: dougkim
ms.prod: windows-server
ms.technology: networking-bc
ms.topic: get-started-article
ms.assetid: 911c1538-f79d-42e9-ba38-f4618f87b008
ms.author: pashort
author: shortpatti
ms.date: 06/02/2018
ms.openlocfilehash: 6f093e605ce735d8f86f7f4d479a646d144e8829
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71356519"
---
# <a name="use-group-policy-to-configure-domain-member-client-computers"></a>Использование групповая политика для настройки клиентских компьютеров членов домена

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе вы создадите объект групповая политика для всех компьютеров в Организации, настроили клиентские компьютеры-члены домена с режимом распределенного кэша или режимом размещенного кэша, а также настроим брандмауэр Windows в режиме повышенной безопасности, чтобы разрешить BranchCache. трафика.  
  
Этот раздел содержит следующие процедуры.  
  
1.  [Создание объекта групповая политика и настройка режимов BranchCache](#bkmk_gp)  
  
2.  [Настройка брандмауэра Windows в правилах входящего трафика с повышенной безопасностью](#bkmk_inbound)  
  
3.  [Настройка брандмауэра Windows в правилах исходящего трафика с повышенной безопасностью](#bkmk_outbound)  
  
> [!TIP]  
> В следующей процедуре показано, как создать объект групповая политика в политике домена по умолчанию. Однако можно создать объект в подразделении (OU) или другом контейнере, подходящем для вашего развертывания.  
  
Для выполнения этих процедур необходимо быть членом **группы "Администраторы домена"** или эквивалентными.  
  
## <a name="bkmk_gp"></a>Создание объекта групповая политика и настройка режимов BranchCache  
  
1.  На компьютере, на котором установлена роль сервера домен Active Directory Services, в диспетчер сервера выберите **Сервис**, а затем щелкните **Управление Групповая политика**. Откроется консоль управления групповая политика.  
  
2.  В консоли управления групповая политика разверните следующий путь: **лес:** *example.com*, **домены**, *example.com*, **Групповая политика объекты**, где *example.com* — это имя домена, в котором находятся учетные записи клиентского компьютера BranchCache, которые требуется настроить.  
  
3.  Щелкните правой кнопкой мыши **Групповая политика объекты**и выберите команду **создать**. Откроется диалоговое окно **Создание объекта групповой политики** . В поле **имя**введите имя нового объекта Групповая политика (GPO). Например, если вы хотите присвоить имя объекту клиентские компьютеры BranchCache, введите " **клиентские компьютеры BranchCache**". Нажмите кнопку **ОК**.  
  
4.  В консоли управления групповая политика убедитесь, что выбран параметр **Групповая политика объекты** , и в области сведений щелкните правой кнопкой мыши только что созданный объект групповой политики. Например, если вы наназвали клиентские компьютеры BranchCache объекта групповой политики, щелкните правой кнопкой мыши **клиентские компьютеры BranchCache**. Щелкните **Изменить**. Откроется консоль редактор "Управление групповыми политиками".  
  
5.  В консоли редактор "Управление групповыми политиками" разверните следующий путь: **Конфигурация компьютера**, **политики**, **Административные шаблоны: определения политик (ADMX-файлы), полученные с локального компьютера**, **сети**, **BranchCache**.  
  
6.  Щелкните **BranchCache**, а затем в области сведений дважды щелкните **включить BranchCache**. Откроется диалоговое окно "параметр политики".  
  
7.  В диалоговом окне **Включение BranchCache** щелкните **включено**, а затем нажмите кнопку **ОК**.  
  
8.  Чтобы включить режим распределенного кэша BranchCache, в области сведений дважды щелкните **установить режим распределенного кэша BranchCache**. Откроется диалоговое окно "параметр политики".  
  
9. В диалоговом окне **Установка режима распределенного кэша BranchCache** установите флажок **включено**и нажмите кнопку **ОК**.  
  
10. При наличии одного или нескольких филиалов, где вы развертываете BranchCache в режиме размещенного кэша и развернули серверы размещенного кэша в этих офисах, дважды щелкните **включить автоматическое обнаружение размещенного кэша по точке подключения службы**. Откроется диалоговое окно "параметр политики".  
  
11. В диалоговом окне **Включение автоматического обнаружения размещенного кэша по точке подключения службы** щелкните **включено**, а затем нажмите кнопку **ОК**.  
  
    > [!NOTE]  
    > Если включить **режим распределенного кэша BranchCache** и **включить автоматическое обнаружение размещенного кэша по параметрам политики точки подключения службы** , клиентские компьютеры работают в режиме распределенного кэша BranchCache, если только они не находят сервер размещенного кэша в офисе филиала, и на этом этапе они работают в режиме размещенного кэша.  
  
12. Используйте приведенные ниже процедуры для настройки параметров брандмауэра на клиентских компьютерах с помощью групповая политика.  
  
## <a name="bkmk_inbound"></a>Настройка брандмауэра Windows в правилах входящего трафика с повышенной безопасностью  
  
1.  В консоли управления групповая политика разверните следующий путь: **лес:** *example.com*, **домены**, *example.com*, **Групповая политика объекты**, где *example.com* — это имя домена, в котором находятся учетные записи клиентского компьютера BranchCache, которые требуется настроить.  
  
2.  В консоли управления групповая политика убедитесь, что выбран параметр **Групповая политика объекты** , и в области сведений щелкните правой кнопкой мыши объект групповой политики "клиентские компьютеры BranchCache", созданный ранее. Например, если вы наназвали клиентские компьютеры BranchCache объекта групповой политики, щелкните правой кнопкой мыши **клиентские компьютеры BranchCache**. Щелкните **Изменить**. Откроется консоль редактор "Управление групповыми политиками".  
  
3.  В консоли редактор "Управление групповыми политиками" разверните следующий путь: **Конфигурация компьютера**, **политики**, **Параметры Windows**, **Параметры безопасности**, **Брандмауэр Windows в расширенной безопасности**, **Брандмауэр Windows в Advanced Security-LDAP**, правила для **входящих подключений**.  
  
4.  Правой кнопкой мыши щелкните **Правила для входящих подключений**, а затем щелкните **Создать правило**. Откроется мастер создания правила для нового входящего подключения.  
  
5.  В поле **тип правила**щелкните **предопределенный**, разверните список вариантов, а затем щелкните **BranchCache — получение содержимого (используется HTTP)** . Нажмите кнопку **Далее**.  
  
6.  В окне **предопределенные правила**нажмите кнопку **Далее**.  
  
7.  В поле **действие**убедитесь, что выбран **параметр Разрешить подключение** , а затем нажмите кнопку **Готово**.  
  
    > [!IMPORTANT]  
    > Необходимо выбрать параметр **Разрешить** клиенту BranchCache подключение к этому порту получать трафик.  
  
8.  Чтобы создать исключение брандмауэра WS-Discovery, снова щелкните правой кнопкой мыши **правила для входящих подключений**и выберите команду **создать правило**. Откроется мастер создания правила для нового входящего подключения.  
  
9. В поле **тип правила**щелкните **предопределенный**, разверните список вариантов, а затем щелкните **BranchCache — обнаружение кэширующих узлов (использует WSD)** . Нажмите кнопку **Далее**.  
  
10. В окне **предопределенные правила**нажмите кнопку **Далее**.  
  
11. В поле **действие**убедитесь, что выбран **параметр Разрешить подключение** , а затем нажмите кнопку **Готово**.  
  
    > [!IMPORTANT]  
    > Необходимо выбрать параметр **Разрешить** клиенту BranchCache подключение к этому порту получать трафик.  
  
## <a name="bkmk_outbound"></a>Настройка брандмауэра Windows в правилах исходящего трафика с повышенной безопасностью  
  
1.  В консоли редактор "Управление групповыми политиками" щелкните правой кнопкой мыши **правила исходящих подключений**и выберите команду **создать правило**. Откроется мастер создания правила для исходящего трафика.  
  
2.  В поле **тип правила**щелкните **предопределенный**, разверните список вариантов, а затем щелкните **BranchCache — получение содержимого (используется HTTP)** . Нажмите кнопку **Далее**.  
  
3.  В окне **предопределенные правила**нажмите кнопку **Далее**.  
  
4.  В поле **действие**убедитесь, что выбран **параметр Разрешить подключение** , а затем нажмите кнопку **Готово**.  
  
    > [!IMPORTANT]  
    > Необходимо выбрать параметр **Разрешить** клиенту BranchCache подключение для отправки трафика через этот порт.  
  
5.  Чтобы создать исключение брандмауэра WS-Discovery, щелкните правой кнопкой мыши **правила исходящих подключений**и выберите команду **создать правило**. Откроется мастер создания правила для исходящего трафика.  
  
6.  В поле **тип правила**щелкните **предопределенный**, разверните список вариантов, а затем щелкните **BranchCache — обнаружение кэширующих узлов (использует WSD)** . Нажмите кнопку **Далее**.  
  
7.  В окне **предопределенные правила**нажмите кнопку **Далее**.  
  
8.  В поле **действие**убедитесь, что выбран **параметр Разрешить подключение** , а затем нажмите кнопку **Готово**.  
  
    > [!IMPORTANT]  
    > Необходимо выбрать параметр **Разрешить** клиенту BranchCache подключение для отправки трафика через этот порт.  
  


