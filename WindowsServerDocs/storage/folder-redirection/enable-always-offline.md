---
title: Включение постоянного автономного режима для ускорения доступа к файлам
description: Использование постоянного автономного режима компонента "Автономные файлы" для более быстрого доступа к кэшированным файлам и перенаправленным папкам.
ms.prod: windows-server
ms.topic: article
author: JasonGerend
ms.author: jgerend
ms.technology: storage
ms.date: 09/10/2018
ms.localizationpriority: medium
ms.openlocfilehash: 389fdd26a7e1d9824f1eaf0136a544547f08eb05
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71401960"
---
# <a name="enable-always-offline-mode-for-faster-access-to-files"></a>Включение постоянного автономного режима для ускорения доступа к файлам

>Применяется к: Windows 10, Windows 8, Windows 8.1, Windows Server 2019, Windows Server 2016, Windows Server 2012, Windows Server 2012 R2 и Windows (Semi-Annual Channel)

В этом документе объясняется, как ускорить доступ к кэшированным файлам и перенаправленным папкам с помощью постоянного автономного режима компонента "Автономные файлы". Постоянный автономный режим также снижает уровень использования пропускной способности, так как пользователи всегда работают с автономными данными, даже при высокоскоростном сетевом подключении.

## <a name="prerequisites"></a>Предварительные условия

Чтобы включить постоянный автономный режим, убедитесь, что ваша среда соответствует следующим требованиям:

- Наличие домена AD DS (доменных служб Active Directory), к которому присоединены клиентские компьютеры. К функциональному уровню леса или домена, а также к схеме домена требований нет.
- Клиентские компьютеры должны работать под управлением: Windows 10, Windows 8.1, Windows 8, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 (клиентские компьютеры под управлением более ранних версий Windows могут по-прежнему переходить в сетевой режим при наличии сетевого подключения с очень высокой скоростью).
- Компьютер с установленным компонентом управления групповой политикой.

## <a name="enable-always-offline-mode"></a>Включение постоянного автономного режима

Чтобы активировать постоянный автономный режим, включите для групповой политики параметр **Настроить режим медленного подключения** и установите значение задержки **1** (в миллисекундах). После этих изменений клиентские компьютеры под управлением Windows 8 или Windows Server 2012 автоматически используют постоянный автономный режим.

>[!NOTE]
>Компьютеры под управлением Windows 7, Windows Vista, Windows Server 2008 R2 или Windows Server 2008 могут по-прежнему переходить в сетевой режим, если задержка сетевого подключения будет ниже одной миллисекунды.

1. Откройте раздел **Управление групповой политикой**.
2. Чтобы создать новый объект групповой политики для настройки параметров автономных файлов, щелкните правой кнопкой мыши соответствующий домен или подразделение предприятия, а затем выберите элемент **Создать объект групповой политики в этом домене и связать его**.
3. В дереве консоли щелкните правой кнопкой мыши объект GPO, для которого вам нужно изменить настройки автономных файлов, и выберите команду **Изменить**. Откроется **редактор управления групповыми политиками**.
4. В дереве консоли в разделе **Конфигурация компьютера** последовательно разверните элементы **Политики**, **Административные шаблоны**, **Сеть**, **Автономные файлы**.
5. Щелкните правой кнопкой мыши **Настроить режим медленного подключения** и выберите пункт **Изменить**. Откроется окно **Настроить режим медленного подключения**.
6. Выберите **Включено**.
7. В поле **Параметры** выберите пункт **Показывать**. Откроется **окно отображения содержимого**.
8. В поле **Имя значения** укажите общую сетевую папку, для которой нужно включить постоянный автономный режим.
9. Чтобы включить постоянный автономный режим для всех общих папок, введите **\*** .
10. В поле **Значение** введите **Latency=1**, чтобы установить для задержки порог в одну миллисекунду, и нажмите кнопку **ОК**.

>[!NOTE]
>По умолчанию в постоянном автономном режиме Windows синхронизирует автономные файлы в кэше по расписанию фоновой синхронизации, то есть каждые два часа. Чтобы изменить это значение, используйте параметр политики **Настройка фоновой синхронизации**.

## <a name="more-information"></a>Дополнительные сведения

* [Общие сведения о перенаправлении папок, автономных файлах и перемещаемых профилях пользователей](folder-redirection-rup-overview.md)
* [Развертывание перенаправления папок с помощью автономных файлов](deploy-folder-redirection.md)