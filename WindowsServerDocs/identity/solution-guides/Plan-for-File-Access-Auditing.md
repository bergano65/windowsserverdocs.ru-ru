---
ms.assetid: 3ea48a72-20a2-4da4-84e4-26b5728513ce
title: План аудита доступа к файлам
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adds
ms.openlocfilehash: 65e941f6741298da54186be10bd9c0add115ea14
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59820905"
---
# <a name="plan-for-file-access-auditing"></a>План аудита доступа к файлам

>Область применения. Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

Информация в этой статье объясняется, безопасности, аудита усовершенствования, появившиеся в Windows Server 2012 и нового аудита параметры, которые следует учитывать, разворачивая динамический контроль доступа на предприятии. Фактические параметры политики аудита будут зависеть от поставленных целей, которые могут включать проверку соответствия нормативным требованиям, наблюдение, криминалистический анализ и устранение неисправностей.  
  
> [!NOTE]  
> Подробные сведения о планировании и развертывании общей стратегии аудита для вашей организации объясняется в безопасности [планирование и развертывание расширенных политик аудита безопасности](https://go.microsoft.com/fwlink/?LinkID=191139). Дополнительные сведения о настройке и развертывании политики аудита безопасности см. в разделе [безопасности аудита Пошаговое руководство по расширенной политике](https://go.microsoft.com/fwlink/?LinkID=191141).  
  
Следующие возможности аудита безопасности в Windows Server 2012 можно использовать динамический контроль доступа для расширения общей стратегии аудита безопасности.  
  
-   **Политики аудита на основе выражений**. Динамический контроль доступа позволяет создавать адресные политики аудита, используя выражения на основе требований пользователя, компьютера и ресурсов. Например, можно создать политику аудита для отслеживания всех операций чтения и записи в файлах, которые классифицируются как "оказывающие сильное влияние на бизнес", для сотрудников, не обладающих высокой категорией доступа. Политики аудита на основе выражений могут быть созданы непосредственно для файла или папки либо централизованно через групповую политику. Дополнительные сведения см. в разделе [групповой политики с помощью глобального аудита доступа к объектам](https://go.microsoft.com/fwlink/?LinkId=241498).  
  
-   **Дополнительная информация от аудита доступа к объектам**. Аудит доступа к файлам не знакомы с Windows Server 2012. Если применяется правильная политика аудита, операционные системы Windows и Windows Server будут создавать событие аудита при каждой попытке пользователя получить доступ к файлу. События доступа к существующим файлам (4656, 4663) содержат сведения об атрибутах файла, к которому был получен доступ. Эту информацию могут использовать средства фильтрации журнала событий, чтобы помочь в определении наиболее значимых событий аудита. Дополнительные сведения см. в разделе [аудита работы с дескрипторами](https://technet.microsoft.com//library/dd772626(WS.10).aspx) и [диспетчера учетных записей безопасности аудита](https://go.microsoft.com/fwlink/?LinkId=241501).  
  
-   **Дополнительные сведения о событиях входа пользователя**. Если применяется правильная политика аудита, операционные системы Windows создают событие аудита при каждом локальном или удаленном входе пользователя в систему. В Windows Server 2012 или Windows 8 вы также можете отслеживать утверждения пользователей и устройств, связанные с токеном безопасности пользователя. Например, это могут быть такие категории доступа, как "Отдел", "Организация", "Проект" и "Безопасность". Событие 4626 содержит информацию об этих заявках пользователей и устройств на доступ, что может использоваться в средствах управления журналом аудита, чтобы связать события входа пользователя с событиями доступа к объектам и разрешить фильтрацию событий на основе атрибутов файлов и атрибутов пользователей. Дополнительные сведения об аудите входа пользователей см. в разделе [аудит входа в систему](https://go.microsoft.com/fwlink/?LinkId=241502).  
  
-   **Отслеживание изменений в новых типах защищаемых объектов**. В следующих сценариях важно отслеживать изменения в защищаемых объектах.  
  
    -   **Отслеживание изменений в централизованных политиках и правилах доступа**. Централизованные политики доступа и централизованные правила доступа определяют централизованную политику, которая может использоваться для управления доступом к важным ресурсам. Любые их изменения могут непосредственно влиять на права доступа к файлам, которые предоставлены пользователям на нескольких компьютерах. Поэтому отслеживание изменений в централизованных политиках и правилах доступа может быть важно для организации. Так как централизованные политики доступа и правила доступа хранятся в доменных службах Active Directory (AD DS), можно проводить аудит попыток их изменения, как проводить аудит изменений любых других защищаемых объектов в AD DS. Дополнительные сведения см. в разделе [доступ к службе каталогов аудита](https://technet.microsoft.com/library/dd941618(WS.10).aspx).  
  
    -   **Отслеживание изменений в определениях словаря утверждений**. Определения утверждений включают имя утверждения, описание и возможные значения. Любые изменения в определении утверждения могут влиять на права доступа к критическим ресурсам. Поэтому отслеживание изменений в определениях утверждений может быть важно для организации. Подобно централизованных политик доступа и централизованные правила доступа определения утверждений хранятся в Доменных службах Active Directory; Таким образом они доступны для аудита как и любой другой защищаемый объект в AD DS. Дополнительные сведения см. в разделе [доступ к службе каталогов аудита](https://technet.microsoft.com/library/dd941618(WS.10).aspx).  
  
    -   **Отслеживание изменений в атрибутах файла**. Атрибуты файла определяют, какое централизованное правило доступа применяется к этому файлу. Изменение атрибутов файла потенциально может влиять на ограничения доступа к файлу. Поэтому важно отслеживать изменения атрибутов файла. Можно отслеживать изменения атрибутов файла на любом компьютере, настроив политику аудита для изменения политики авторизации. Дополнительные сведения см. в разделе [аудит изменений политики авторизации](https://go.microsoft.com/fwlink/?LinkId=241504) и [аудита доступа к объектам для файловых систем](https://go.microsoft.com/fwlink/?LinkId=241505). В Windows Server 2012 событие 4911 отличает изменения политики атрибутов файла от других событий изменения политики авторизации.  
  
    -   **Отслеживание изменений в централизованной политике доступа, связанной с файлом.** Событие 4913 отображает идентификаторы безопасности (SID) для старой и новой централизованных политик доступа. Каждая централизованная политика доступа также имеет имя, понятное для пользователя, которое может быть найдено с помощью этого идентификатора безопасности. Дополнительные сведения см. в разделе [аудит изменений политики авторизации](https://go.microsoft.com/fwlink/?LinkId=241504).  
  
    -   **Отслеживание изменений атрибутов пользователя и компьютера**. Подобно файлам объекты пользователей и компьютеров может иметь атрибуты и изменения этих атрибутов может повлиять на возможность доступа к файлам. Таким образом, важно отслеживать изменения атрибутов пользователя или компьютера. Объекты пользователей и компьютеров хранятся в Доменных службах Active Directory; Таким образом изменения их атрибутов может быть проверено. Дополнительные сведения см. в разделе [доступ к службе Каталогов](https://go.microsoft.com/fwlink/?LinkId=241508).  
  
-   **Промежуточное сохранение изменений политики**. Изменения в централизованных политиках доступа могут влиять на решения о предоставлении доступа на всех компьютерах, на которых применяются политики. Нестрогая политика может предоставить больше доступа, чем предполагается, в то время как чрезмерно строгая политика может вызвать огромное количество обращений в службу поддержки. Поэтому очень важно проверить изменения централизованной политики доступа до того, как они будут применены. Для этой цели Windows Server 2012 введено понятие «промежуточное сохранение». Промежуточное сохранение позволяет пользователям проверить предложенные изменения политики до того, как применить их. Для использования промежуточного сохранения предложенные политики разворачиваются вместе с принятыми политиками, но промежуточные политики фактически не предоставляют доступ и не запрещают его. Вместо этого Windows Server 2012 регистрирует событие аудита (4818) каждый раз, когда результат проверки доступа, в которой используется промежуточная политика, отличается от результата проверки доступа, который используется применяемая политика.  
  

