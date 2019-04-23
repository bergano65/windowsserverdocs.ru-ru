---
ms.assetid: 38eb3726-e97b-484e-9926-67e8a046b0c5
title: Создание правила для отправки утверждений с помощью настраиваемого правила
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f0eef89e651585d48ba87d14bc782efa49087669
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59824835"
---
# <a name="create-a-rule-to-send-claims-using-a-custom-rule"></a>Создание правила для отправки утверждений с помощью настраиваемого правила

>Область применения. Windows Server 2016, Windows Server 2012 R2

С помощью **Отправка утверждений с помощью настраиваемого правила** шаблона в службах федерации Active Directory (AD FS), можно создать пользовательские правила для утверждений для ситуации, в котором со стандартным шаблоном правила не удовлетворяет требованиям вашего организация. Настраиваемые правила для утверждений, написаны на языке правил утверждений и необходимо скопировать в **настраиваемого правила** текстового поля, прежде чем они могут использоваться в набор правил. Сведения о построении синтаксис расширенное правило, см. в разделе [роль языка правил утверждений](../../ad-fs/technical-reference/The-Role-of-the-Claim-Rule-Language.md).  
  
Можно использовать следующую процедуру для создания правила утверждения с помощью оснастки управления AD FS\-в.  
  
Членство в группе **Администраторы**, или наличие эквивалентных прав на локальном компьютере, является минимальным требованием для выполнения этой процедуры.  Просмотрите сведения об использовании соответствующих учетных записей и членства в группах в [локальные и доменные группы по умолчанию](https://go.microsoft.com/fwlink/?LinkId=83477).



## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-relying-party-trust-in-windows-server-2016"></a>Чтобы создать правило, чтобы пропуск или Фильтрация входящего утверждения на доверия с проверяющей стороной в Windows Server 2016 

1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  
  
2.  В дереве консоли в разделе **AD FS**, нажмите кнопку **доверия проверяющей стороны**. 
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)  
  
3.  Справа\-выберите выбранного отношения доверия и нажмите кнопку **изменить политику выдачи утверждений**.
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)   
  
4.  В **изменить политику выдачи утверждений** диалогового **правила преобразования выдачи** щелкните **добавить правило** для запуска мастера создания правила. 
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)    

5.  На **Выбор шаблона правила** раздела **шаблон правила утверждения**выберите **Отправка утверждений с помощью настраиваемого правила** в списке и нажмите кнопку **Далее**.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG)   
  
6.  На **Настройка правила** раздела **имя правила утверждения**, введите отображаемое имя для этого правила. В разделе **настраиваемого правила**введите или вставьте синтаксиса языка правил утверждений для этого правила.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG)     

7.  Нажмите кнопку **Готово**.  
  
8.  В **изменение правил для утверждений** диалоговом окне щелкните **ОК** сохранить правило.   
  
## <a name="to-create-a-rule-to-pass-through-or-filter-an-incoming-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>Чтобы создать правило, чтобы пропуск или Фильтрация входящего утверждения на отношением доверия поставщика утверждений в Windows Server 2016 
  
1.  В диспетчере серверов щелкните **средства**, а затем выберите **управления AD FS**.  
  
2.  В дереве консоли в разделе **AD FS**, нажмите кнопку **отношения доверия поставщиков утверждений**. 
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)  
  
3.  Справа\-выберите выбранного отношения доверия и нажмите кнопку **изменение правил для утверждений**.
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)   
  
4.  В **изменение правил для утверждений** диалогового **правила преобразования принятия** щелкните **добавить правило** для запуска мастера создания правила.
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)    

5.  На **Выбор шаблона правила** раздела **шаблон правила утверждения**выберите **Отправка утверждений с помощью настраиваемого правила** в списке и нажмите кнопку **Далее**.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom3.PNG)   
  
6.  На **Настройка правила** раздела **имя правила утверждения**, введите отображаемое имя для этого правила. В разделе **настраиваемого правила**введите или вставьте синтаксиса языка правил утверждений для этого правила.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom4.PNG)     

7.  Нажмите кнопку **Готово**.  
  
8.  В **изменение правил для утверждений** диалоговом окне щелкните **ОК** сохранить правило.   

















   
  
## <a name="to-create-a-rule-to-send-claims-by-using-a-custom-claim-in-windows-server-2012-r2"></a>Чтобы создать правило для отправки утверждений с помощью пользовательского утверждения в Windows Server 2012 R2 
  
1.  В диспетчере серверов щелкните **средства**, а затем нажмите кнопку **управления AD FS**.  
  
2.  В дереве консоли в разделе **AD FS\\отношения доверия**, нажать **отношения доверия поставщиков утверждений** или **доверия проверяющей стороны**и нажмите кнопку конкретного доверие в списке, где вы хотите создать это правило.  
  
3.  Справа\-выберите выбранного отношения доверия и нажмите кнопку **изменение правил для утверждений**.  
![Создание правила](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG) 
  
4.  В **изменение правил для утверждений** диалоговое окно, выберите один следующие вкладки, которое зависит от для отношения доверия, редактирования и в какие наборе правил вы хотите создать это правило и нажмите кнопку **добавить правило** для запуска правила Задайте мастер, который связан с этим правилом.  
  
    -   **Правила преобразования принятия**  
  
    -   **Правила преобразования выдачи**  
  
    -   **Правила авторизации выдачи**  
  
    -   **Правила авторизации делегирования**  
![Создание правила](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)
  
5.  На **Выбор шаблона правила** раздела **шаблон правила утверждения**выберите **Отправка утверждений с помощью настраиваемого правила** в списке и нажмите кнопку **Далее**.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom1.PNG)   
  
6.  На **Настройка правила** раздела **имя правила утверждения**, введите отображаемое имя для этого правила. В разделе **настраиваемого правила**введите или вставьте синтаксиса языка правил утверждений для этого правила.  
![Создание правила](media/Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule/custom2.PNG)     

7.  Нажмите кнопку **Готово**.  
  
8.  В **изменение правил для утверждений** диалоговом окне щелкните **ОК** сохранить правило.  

## <a name="additional-references"></a>Дополнительная справка 
[Настройка правил утверждений](Configure-Claim-Rules.md)  
 
[Контрольный список: Создание правил для утверждений для доверия проверяющей стороны](https://technet.microsoft.com/library/ee913578.aspx)  

[Контрольный список: Создание правил для утверждений для поставщика утверждений доверия](https://technet.microsoft.com/library/ee913564.aspx)  
  
[Когда следует использовать Authorization Claim Rule](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)  

[Роль утверждений](../../ad-fs/technical-reference/The-Role-of-Claims.md)  
  
[Роль правил утверждений](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md) 