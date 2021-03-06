---
title: Сообщения об ошибках и событиях политики качества обслуживания
description: В этом разделе содержится список сообщений об ошибках и событиях для политики качества обслуживания (QoS) в Windows Server 2016.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 76974e10-6a57-4533-83be-cfd5a0d364a3
manager: brianlic
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 935bda5ab47f3e9a362c81a8aeb99ebf22095725
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405330"
---
# <a name="qos-policy-error-and-event-messages"></a>Сообщения об ошибках и событиях политики качества обслуживания

>Область применения: Windows Server (Semi-Annual Channel), Windows Server 2016

Ниже приведены сообщения об ошибках и событиях, связанные с политикой QoS.  
  
## <a name="informational-messages"></a>Информационные сообщения  

Ниже приведен список информационных сообщений политики качества обслуживания.

|||  
|-|-|  
|**MessageId**|16500|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_MACHINE_POLICY_REFRESH_NO_CHANGE|  
|**Язык**|Английский|  
|**Сообщение**|Политики QoS на компьютере успешно обновлены. Изменения не обнаружены.|  
  
|||  
|-|-|  
|**MessageId**|16501|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_MACHINE_POLICY_REFRESH_WITH_CHANGE|  
|**Язык**|Английский|  
|**Сообщение**|Политики QoS на компьютере успешно обновлены. Обнаружены изменения политик.|  
  
|||  
|-|-|  
|**MessageId**|16502|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_USER_POLICY_REFRESH_NO_CHANGE|  
|**Язык**|Английский|  
|**Сообщение**|Политики QoS на пользователя успешно обновлены. Изменения не обнаружены.|  
  
|||  
|-|-|  
|**MessageId**|16503|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_USER_POLICY_REFRESH_WITH_CHANGE|  
|**Язык**|Английский|  
|**Сообщение**|Политики QoS на пользователя успешно обновлены. Обнаружены изменения политик.|  
  
|||  
|-|-|  
|**MessageId**|16504|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_TCP_AUTOTUNING_NOT_CONFIGURED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенная настройка качества обслуживания для входящего уровня пропускной способности TCP успешно обновлена. Значение параметра не указано ни одной политикой качества обслуживания. Будет применено значение по умолчанию локального компьютера.|  
  
|||  
|-|-|  
|**MessageId**|16505|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_TCP_AUTOTUNING_OFF|  
|**Язык**|Английский|  
|**Сообщение**|Расширенная настройка качества обслуживания для входящего уровня пропускной способности TCP успешно обновлена. Значение параметра — уровень 0 (Минимальная пропускная способность).|  
  
|||  
|-|-|  
|**MessageId**|16506|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_TCP_AUTOTUNING_HIGHLY_RESTRICTED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенная настройка качества обслуживания для входящего уровня пропускной способности TCP успешно обновлена. Значение параметра — Level 1.|  
  
|||  
|-|-|  
|**MessageId**|16507|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_TCP_AUTOTUNING_RESTRICTED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенная настройка качества обслуживания для входящего уровня пропускной способности TCP успешно обновлена. Значение параметра — уровень 2.|  
  
|||  
|-|-|  
|**MessageId**|16508|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_TCP_AUTOTUNING_NORMAL|  
|**Язык**|Английский|  
|**Сообщение**|Расширенная настройка качества обслуживания для входящего уровня пропускной способности TCP успешно обновлена. Значение параметра — уровень 3 (максимальная пропускная способность).|  
  
|||  
|-|-|  
|**MessageId**|16509|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_APP_MARKING_NOT_CONFIGURED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенный параметр качества обслуживания для переопределения разметки DSCP успешно обновлен. Значение параметра не указано. Приложения могут устанавливать значения DSCP независимо от политик качества обслуживания.|  
  
|||  
|-|-|  
|**MessageId**|16510|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_APP_MARKING_IGNORED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенный параметр качества обслуживания для переопределения разметки DSCP успешно обновлен. Запросы на пометку DSCP для приложения будут игнорироваться. Только политики качества обслуживания могут устанавливать значения DSCP.|  
  
|||  
|-|-|  
|**MessageId**|16511|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_APP_MARKING_ALLOWED|  
|**Язык**|Английский|  
|**Сообщение**|Расширенный параметр качества обслуживания для переопределения разметки DSCP успешно обновлен. Приложения могут устанавливать значения DSCP независимо от политик качества обслуживания.|  
  
|||  
|-|-|  
|**MessageId**|16512|  
|**Серьезности**|Сведения|  
|**SymbolicName**|EVENT_EQOS_INFO_LOCAL_SETTING_DONT_USE_NLA|  
|**Язык**|Английский|  
|**Сообщение**|Выборочное применение политик QoS на основе категории "сеть домена" отключено. Политики QoS будут применены ко всем сетевым интерфейсам.|  
  
## <a name="warning-messages"></a>Предупреждающие сообщения

Ниже приведен список предупреждающих сообщений политики QoS.

|||  
|-|-|  
|**MessageId**|16600|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_TEST_1|  
|**Язык**|Английский|  
|**Сообщение**|ЕКОС: * * * тестирование\*\*\*[, с одной строкой] "%2".|  
  
|||  
|-|-|  
|**MessageId**|16601|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_TEST_2|  
|**Язык**|Английский|  
|**Сообщение**|ЕКОС: * * * тестирование\*\*\*[, с двумя строками, строка1 —] "%2" [, строка2 —] "%3".|  
  
|||  
|-|-|  
|**MessageId**|16602|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_MACHINE_POLICY_VERSION|  
|**Язык**|Английский|  
|**Сообщение**|Политика качества обслуживания компьютера "%2" имеет недопустимый номер версии. Эта политика не будет применена.|  
  
|||  
|-|-|  
|**MessageId**|16603|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_USER_POLICY_VERSION|  
|**Язык**|Английский|  
|**Сообщение**|В политике качества обслуживания пользователя "%2" указан недопустимый номер версии. Эта политика не будет применена.|  
  
|||  
|-|-|  
|**MessageId**|16604|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_MACHINE_POLICY_PROFILE_NOT_SPECIFIED|  
|**Язык**|Английский|  
|**Сообщение**|В политике QoS на компьютере "%2" не указано значение DSCP или частота регулирования. Эта политика не будет применена.|  
  
|||  
|-|-|  
|**MessageId**|16605|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_USER_POLICY_PROFILE_NOT_SPECIFIED|  
|**Язык**|Английский|  
|**Сообщение**|В политике качества обслуживания пользователя "%2" не указано значение DSCP или частота регулирования. Эта политика не будет применена.|  
  
|||  
|-|-|  
|**MessageId**|16606|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_MACHINE_POLICY_QUOTA_EXCEEDED|  
|**Язык**|Английский|  
|**Сообщение**|Превышено максимальное число политик качества обслуживания компьютера. Политика качества обслуживания "%2" и последующие политики QoS на компьютере не будут применены.|  
  
|||  
|-|-|  
|**MessageId**|16607|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_USER_POLICY_QUOTA_EXCEEDED|  
|**Язык**|Английский|  
|**Сообщение**|Превышено максимальное число политик QoS на пользователя. Политика качества обслуживания "%2" и последующие политики качества обслуживания пользователя не будут применены.|  
  
|||  
|-|-|  
|**MessageId**|16608|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_MACHINE_POLICY_CONFLICT|  
|**Язык**|Английский|  
|**Сообщение**|Политика QoS на компьютере "%2" может конфликтовать с другими политиками качества обслуживания. См. документацию по правилам, к которым будет применена политика.|  
  
|||  
|-|-|  
|**MessageId**|16609|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_USER_POLICY_CONFLICT|  
|**Язык**|Английский|  
|**Сообщение**|Политика QoS на пользователя "%2" может конфликтовать с другими политиками качества обслуживания. См. документацию по правилам, к которым будет применена политика.|  
  
|||  
|-|-|  
|**MessageId**|16610|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_MACHINE_POLICY_NO_FULLPATH_APPNAME|  
|**Язык**|Английский|  
|**Сообщение**|Политика QoS на компьютере "%2" была пропущена, так как не удается обработать путь приложения. Путь к приложению может быть недопустимым, содержать недопустимую букву диска или состоять из сетевого диска.|  
  
|||  
|-|-|  
|**MessageId**|16611|  
|**Серьезности**|Warning|  
|**SymbolicName**|EVENT_EQOS_WARNING_USER_POLICY_NO_FULLPATH_APPNAME|  
|**Язык**|Английский|  
|**Сообщение**|Политика качества обслуживания пользователя "%2" была пропущена, так как не удается обработать путь приложения. Путь к приложению может быть недопустимым, содержать недопустимую букву диска или состоять из сетевого диска.|  
  
## <a name="error-messages"></a>Сообщения об ошибке  

Ниже приведен список сообщений об ошибках политики QoS.

|||  
|-|-|  
|**MessageId**|16700|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_MACHINE_POLICY_REFERESH|  
|**Язык**|Английский|  
|**Сообщение**|Не удалось обновить политики качества обслуживания компьютера. Код ошибки: "%2".|  
  
|||  
|-|-|  
|**MessageId**|16701|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_USER_POLICY_REFERESH|  
|**Язык**|Английский|  
|**Сообщение**|Не удалось обновить политики качества обслуживания пользователя. Код ошибки: "%2".|  
  
|||  
|-|-|  
|**MessageId**|16702|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_OPENING_MACHINE_POLICY_ROOT_KEY|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось открыть корневой ключ уровня компьютера для политик QoS. Код ошибки: "%2".|  
  
|||  
|-|-|  
|**MessageId**|16703|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_OPENING_USER_POLICY_ROOT_KEY|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось открыть корневой ключ уровня пользователя для политик QoS. Код ошибки: "%2".|  
  
|||  
|-|-|  
|**MessageId**|16704|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_MACHINE_POLICY_KEYNAME_TOO_LONG|  
|**Язык**|Английский|  
|**Сообщение**|Политика QoS на компьютере превышает максимально допустимую длину имени. Политика, вызывающая ошибку, указана в корневом ключе политики качества обслуживания на уровне компьютера с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16705|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_USER_POLICY_KEYNAME_TOO_LONG|  
|**Язык**|Английский|  
|**Сообщение**|Длина имени политики QoS для пользователя превышает максимально допустимую. Политика, вызывающая ошибку, указана в корневом ключе политики QoS на уровне пользователя с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16706|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_MACHINE_POLICY_KEYNAME_SIZE_ZERO|  
|**Язык**|Английский|  
|**Сообщение**|Имя политики QoS на компьютере имеет нулевую длину. Политика, вызывающая ошибку, указана в корневом ключе политики качества обслуживания на уровне компьютера с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16707|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_USER_POLICY_KEYNAME_SIZE_ZERO|  
|**Язык**|Английский|  
|**Сообщение**|Имя политики QoS на пользователя имеет нулевую длину. Политика, вызывающая ошибку, указана в корневом ключе политики QoS на уровне пользователя с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16708|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_OPENING_MACHINE_POLICY_SUBKEY|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось открыть подраздел реестра для политики QoS на компьютере. Политика указана в корневом ключе политики качества обслуживания на уровне компьютера с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16709|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_OPENING_USER_POLICY_SUBKEY|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось открыть подраздел реестра для политики качества обслуживания пользователя. Политика отображается в корневом ключе политики QoS на уровне пользователя с индексом "%2".|  
  
|||  
|-|-|  
|**MessageId**|16710|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_PROCESSING_MACHINE_POLICY_FIELD|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось прочитать или проверить поле "%2" для политики QoS на компьютере "%3".|  
  
|||  
|-|-|  
|**MessageId**|16711|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_PROCESSING_USER_POLICY_FIELD|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось прочитать или проверить поле "%2" для политики качества обслуживания пользователя "%3".|  
  
|||  
|-|-|  
|**MessageId**|16712|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_SETTING_TCP_AUTOTUNING|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось прочитать или задать уровень входящей пропускной способности TCP, код ошибки: "%2".|  
  
|||  
|-|-|  
|**MessageId**|16713|  
|**Серьезности**|Ошибка|  
|**SymbolicName**|EVENT_EQOS_ERROR_SETTING_APP_MARKING|  
|**Язык**|Английский|  
|**Сообщение**|QoS не удалось прочитать или задать параметр переопределения разметки DSCP, код ошибки: "%2".|  

В следующем разделе этого руководстве приведены [часто задаваемые вопросы о политике качества обслуживания](qos-policy-faq.md).

Для первого раздела в этом руководстве см. раздел [Политика качества обслуживания (QoS)](qos-policy-top.md).
