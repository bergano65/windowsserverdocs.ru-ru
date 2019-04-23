---
ms.assetid: 69ec592a-5499-4249-8ba0-afa356a8ff75
title: Технический справочник по регистрации устройств
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: fac6437e9b6c3893064769a8279c2cf96cbc47d6
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59833785"
---
>Область применения. Windows Server 2016, Windows Server 2012 R2

# <a name="device-registration-technical-reference"></a>Технический справочник по регистрации устройств
Служба регистрации устройств \(DRS\) — это новая служба Windows, который входит в состав роли службы федерации Active Directory в Windows Server 2012 R2.  Службы DRS должны быть установлены и настроены на всех серверах федерации в ферме AD FS.  Сведения о развертывании DRS см. в разделе [Настройка сервера федерации с помощью службы регистрации устройств](https://technet.microsoft.com/library/dn486831.aspx).  
  
## <a name="active-directory-objects-created-when-a-device-is-registered"></a>Объекты Active Directory, создаваемые при регистрации устройства  
Служба регистрации устройств создает указанные ниже объекты Active Directory.  
  
### <a name="device-registration-configuration"></a>Конфигурация регистрации устройств  
Конфигурация регистрации устройств хранится в контексте именования конфигурации леса Active Directory. \(Например **CN\=Device Registration Configuration, CN\=служб, < конфигурации\-именования\-контекст >**\). Этот объект создается, когда лес Active Directory инициируется для регистрации устройств.  
  
Конфигурация регистрации устройств включает перечисленные ниже элементы.  
  
-   **Ключи издателя**  
  
    Открытый и закрытый ключи, используемые для выдачи сертификата X.509, связанного с зарегистрированным устройством.  Закрытые ключи защищены с помощью DKM.  
  
-   **Конфигурация службы регистрации устройств**  
  
    Политики, относящиеся к службе регистрации устройств.  
  
### <a name="registered-devices-container"></a>Контейнер зарегистрированных устройств  
Контейнер объектов устройств создается в одном из доменов леса Active Directory.  Этот контейнер будет содержать все объекты устройств для леса Active Directory.  
  
По умолчанию контейнер создается в том же домене, что и службы AD FS.  \(Например **CN\=RegisteredDevices, DC\=< по умолчанию\-именования\-контекст >**\). Этот объект создается в том случае, когда лес Active Directory инициируется для регистрации устройств.  
  
### <a name="registered-devices"></a>Зарегистрированные устройства  
Объекты устройств — это новые компактные объекты в доменных службах Active Directory.  Они служат для представления отношения между пользователем, устройством и организацией.  Объекты устройств используют сертификат, подписанный службами AD FS, для привязки физического устройства к логическому объекту устройства в Active Directory.  
  
Зарегистрированные устройства включают следующие элементы:  
  
-   **Отображаемое имя**  
  
    Понятное имя устройства.  Для устройств Windows это имя узла компьютера.  
  
-   **Идентификатор устройства**  
  
    Идентификатор GUID, созданный сервером регистрации устройств.  
  
-   **Отпечаток сертификата**  
  
    Отпечаток сертификата X.509, который используется с зарегистрированным устройством.  
  
-   **Тип ОС**  
  
    Тип операционной системы устройства.  
  
-   **Версия ОС**  
  
    Версия операционной системы устройства.  
  
-   **Включен**  
  
    Логическое значение, указывающее, включено ли устройство в Active Directory.  Только включенным устройствам разрешен доступ к службам.  
  
-   **Приблизительное время последнего использования**  
  
    Приблизительное время, когда устройство использовалось для доступа к ресурсу.  Чтобы ограничить объем трафика репликации, это значение обновляется один раз каждые 14 дней.  
  
-   **Зарегистрированный владелец**  
  
    Идентификатор безопасности \(SID\) пользователя, который присоединил это устройство к рабочему месту.  
  
## <a name="ad-fsdrs-server-ssl-certificate-revocation-checking"></a>AD FS\/проверку отзыва сертификатов SSL сервера DRS  
Клиент присоединения к рабочему месту проверяет действительность SSL-сертификата сервера AD FS.  Если сертификат SSL сервера AD FS включает список отзыва сертификатов \(CRL\) конечной точки, клиент должен иметь возможность связаться с конечной точкой, заданной для проверки сертификата.  
  
Если вы используете тестовая среда и тестовый центр сертификации \(ЦС\) для выдачи SSL-сертификаты сервера, то можно не включать конечную точку CRL в сертификаты серверов, выдаваемые ЦС.  Это позволит клиенту присоединения к рабочему месту пропустить проверку списка CRL.  
  
> [!CAUTION]  
> Для рабочих систем делать это не рекомендуется.  
  
