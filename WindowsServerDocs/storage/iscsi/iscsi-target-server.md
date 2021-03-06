---
title: iSCSI Target Server Overview
TOCTitle: iSCSI Target Server
ms.prod: windows-server
ms.technology: storage-iscsi
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 09/11/2018
ms.openlocfilehash: 638343abf782983020a3301898920470ffcd5952
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403053"
---
# <a name="iscsi-target-server-overview"></a>Обзор сервера цели iSCSI

Область применения: Windows Server 2016, Windows Server 2012 R2, Windows Server 2012

В этом разделе содержится краткий обзор сервера цели iSCSI, службы роли в Windows Server, которая позволяет сделать хранилище доступным через протокол iSCSI. Это полезно для предоставления доступа к хранилищу на сервере Windows Server для клиентов, которые не могут взаимодействовать через собственный протокол общего доступа к файлам Windows, SMB.

Сервер цели iSCSI оптимально подходит для следующих целей:

* **Сетевая и бесдисковая загрузка**   с помощью сетевых адаптеров с поддержкой загрузки или программного загрузчика позволяет развертывать сотни бесдисковых серверов. Благодаря серверу цели iSCSI развертывание проходит быстро. В рамках внутреннего тестирования в корпорации Майкрософт 256 компьютеров были развернуты за 34 минуты. Используя разностные виртуальные жесткие диски, можно сэкономить до 90 % дискового пространства, которое использовалось для образов операционной системы. Этот способ идеален для крупных развертываний идентичных образов операционных систем, например, в виртуальных машинах под управлением Hyper-V или в кластерах высокопроизводительной вычислительной системы (HPC).

* **Хранилище серверных приложений**   некоторым приложениям требуется хранилище блоков. Конечный iSCSI-сервер может предоставить таким приложениям блочное хранилище постоянной доступности. Так как хранилище доступно в удаленном режиме, оно может также консолидировать блочное хранилище для расположений в центре или в филиалах.

* **Разнородное хранилище**   iSCSI Target Server поддерживает инициаторы iSCSI сторонних производителей, что упрощает совместное использование хранилища на серверах в смешанной программной среде.

* **Разработка, тестирование, демонстрация и лабораторные среды**   при включенном сервере iSCSI Target Server компьютер под управлением операционной системы Windows Server становится доступным для использования в сети блочным устройством хранения. Это полезно при тестировании приложений перед их развертыванием в сети хранения данных (SAN).

## <a name="block-storage-requirements"></a>Требования к блочному хранилищу

Чтобы предоставить блочное хранилище, для включения конечного iSCSI-сервера используется существующая сеть Ethernet. Дополнительное оборудование не требуется. Если важен высокий уровень доступности, рассмотрите возможность настройки кластера высокой доступности. Для кластера с высоким уровнем доступности потребуется общее хранилище — аппаратное хранилище Fibre Channel или последовательный присоединенный массив хранения SCSI (SAS).

Если разрешена гостевая кластеризация, необходимо обеспечить блочное хранилище. Блочное хранилище могут предоставить любые серверы, на которых выполняется программное обеспечение Windows Server с сервером цели iSCSI.

## <a name="see-also"></a>См. также

[Целевое хранилище блоков iSCSI, как](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh848268(v%3dws.11))  
[Новые возможности iSCSI Target Server в Windows Server](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn305893(v%3dws.11))

