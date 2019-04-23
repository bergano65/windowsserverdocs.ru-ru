---
title: Требования к оборудованию для локальных дисковых пространств
ms.prod: windows-server-threshold
description: Минимальные требования к оборудованию для тестирования локальных дисковых пространств.
ms.author: eldenc
ms.manager: eldenc
ms.technology: storage-spaces
ms.topic: article
author: eldenchristensen
ms.date: 04/12/2018
ms.localizationpriority: medium
ms.openlocfilehash: 84d10ab3e25500720dd13e2ba057dc3c5bf05a6f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59849325"
---
# <a name="storage-spaces-direct-hardware-requirements"></a>Требования к оборудованию для локальных дисковых пространств

> Относится к: Windows Server 2016, Windows Server Insider Preview

В этом разделе описываются минимальные требования к оборудованию для дисковых пространств.

Для рабочей среды, корпорация Майкрософт рекомендует эти [определяемые серверное программное обеспечение Windows](https://microsoft.com/wssd) предлагает оборудование и программное обеспечение от наших партнеров, которые включают средства и процедуры развертывания. Они разработаны, собраны и проверены в нашей эталонной архитектуры для обеспечения совместимости и надежности, чтобы оперативно настраивайте и быстрый запуск. Подробнее см. на [ https://microsoft.com/wssd ](https://microsoft.com/wssd).

![Логотипы партнерах определенные программное обеспечение Windows Server](media/hardware-requirements/wssd-partners.png)

   > [!TIP]
   > Чтобы оценить дисковыми пространствами, но нет оборудования? Использование виртуальных машин Hyper-V или Azure, как описано в разделе [с помощью дисковых пространств в кластеров гостевых виртуальных машин](storage-spaces-direct-in-vm.md).

## <a name="base-requirements"></a>Основные требования

Систем, компонентов, устройств и драйверы должны быть **Windows Server 2016 Certified** на [каталоге Windows Server](https://www.windowsservercatalog.com). Кроме того, мы рекомендуем, что серверы, дисков, адаптеров шины и сетевые адаптеры имеют **Standard Center программно определяемого данных (SDDC)** и/или **Center программно определяемого данных (SDDC) уровня "премиум"** Дополнительные квалификации (AQs), как на рисунке ниже. Существует более чем 1000 компонентов с SDDC AQs.

![Снимок экрана, показывающий SDDC AQs каталога Windows Server](media/hardware-requirements/sddc-aqs.png)

Полностью настроенный кластера (серверы, сеть и хранилище) должна пройти все [тестах для проверки кластеров](https://technet.microsoft.com/library/cc732035(v=ws.10).aspx) каждого мастера в диспетчере отказоустойчивости кластеров или с `Test-Cluster` [командлет](https://docs.microsoft.com/powershell/module/failoverclusters/test-cluster?view=win10-ps) в PowerShell.

Кроме того применяются следующие требования:

## <a name="servers"></a>Серверы

- Минимум два сервера, максимум 16 серверов.
- Рекомендуемый того же изготовителя и модели все серверы

## <a name="cpu"></a>ЦП

- Intel Nehalem или более поздней версии совместимым процессором; или
- AMD EPYC или более поздней версии совместимым процессором

## <a name="memory"></a>Память

- Память для Windows Server, виртуальные машины и другие приложения или рабочие нагрузки; плюс
- 4 ГБ ОЗУ на емкость диска кэша на каждом сервере для дисковых метаданных терабайт (ТБ)

## <a name="boot"></a>Загрузки

- Любое устройство загрузки, поддерживаемые сервером Windows, который [теперь включает SATADOM](https://cloudblogs.microsoft.com/windowsserver/2017/08/30/announcing-support-for-satadom-boot-drives-in-windows-server-2016/)
- Уровень RAID 1 зеркала **не** требуются, но поддерживает для загрузки
- Рекомендуемое: Минимальный размер 200 ГБ

## <a name="networking"></a>Сеть

Минимальное значение (для небольших 2 – 3 узла)
- 10 Гбит/с сетевой интерфейс
- Для прямого соединения (switchless) поддерживается с 2 узлами

Рекомендуется (для высокой производительности, масштабирования или развертываний 4 + узлов)
- Сетевые адаптеры, удаленный прямой доступ к памяти (RDMA), поддержка (рекомендуется) iWARP или RoCE
- Два или несколько сетевых карт для обеспечения избыточности и производительности
- 25 Гбит/с сетевой интерфейс или более поздней версии

## <a name="drives"></a>Накопители

Storage Spaces Direct работает с прямым подключением SATA, SAS или NVMe накопители, физически подключенные к только один сервер. Дополнительную информацию о выборе дисков см. в статье [Выбор дисков](choosing-drives.md).

- Диски SATA, SAS и NVMe (M.2 U.2 и добавить в карту) поддерживаются
- поддерживаются 512n, 512e и дисков с 4K
- Необходимо указать твердотельные накопители [защиты отключения питания](https://blogs.technet.microsoft.com/filecab/2016/11/18/dont-do-it-consumer-ssd/)
- Же количество и типы дисков в каждом сервере — см. в разделе [диска симметрии вопросы](drive-symmetry-considerations.md)
- Драйвер NVMe корпорации Майкрософт в поле или обновленный драйвер NVMe.
- Рекомендуемое: Емкость дисков не кратна количества накопителей, кэш
- Рекомендуемое: Кэш-дисках должен иметь высокий уровень записи нагрузочное тестирование: по крайней мере 3 диска операций записи — в день (DWPD) или по крайней мере 4 терабайта, написанные (TBW) в день — см. в разделе [записывает основные сведения о диске в день (DWPD), написанные терабайт (TBW) и минимальной рекомендуется использовать для хранения Пространствами](https://blogs.technet.microsoft.com/filecab/2017/08/11/understanding-dwpd-tbw/)

Вот, как можно подключить диски для дисковых пространств:

1. Непосредственно подключенных дисков SATA
2. Непосредственно подключенных дисков NVMe
3. SAS адаптер шины (HBA) с дисками SAS
4. SAS адаптер шины (HBA) с дисками SATA
5. **НЕ ПОДДЕРЖИВАЕТСЯ:** RAID-контроллеры или SAN (Fibre Channel, iSCSI, FCoE) хранилища. Карты адаптера шины необходимо реализовать простой сквозной режим.

![Схема поддерживаемых дисков соединения](media/hardware-requirements/drive-interconnect-support-1.png)

Диски можно внутри сервера, или в корпусе при внешней подключенного одного единственного сервера. SCSI корпуса Services (SES) является обязательным для идентификации и сопоставление слотов. Каждый внешний корпус должен предоставить уникальный идентификатор (уникальный идентификатор).

1. Диски, внутри сервера
2. Диски в внешних корпусе («JBOD»), подключаться к одному серверу
3. **НЕ ПОДДЕРЖИВАЕТСЯ:** Общих корпусах SAS подключен к нескольким серверам или какого-либо из многопутевого ввода-ВЫВОДА (MPIO) где диски доступны несколько путей.

![Схема поддерживаемых дисков соединения](media/hardware-requirements/drive-interconnect-support-2.png)

### <a name="minimum-number-of-drives-excludes-boot-drive"></a>Минимальное количество дисков (за исключением загрузочного диска)

- При использовании кэш-накопителей их должно быть не меньше двух на сервер.
- Должно быть по крайней мере 4 диска хранения (не кэш-диска) на сервер.

| Имеющиеся типы накопителей   | Необходимое минимальное количество |
|-----------------------|-------------------------|
| Только накопители NVMe (одной и той же модели) | 4 накопителя NVMe                  |
| Только твердотельные накопители (SSD) (одной и той же модели)  | 4 накопителя SSD                   |
| NVMe + SSD            | 2 NVMe + 4 SSD          |
| NVMe + жесткий диск            | 2 NVMe + 4 жестких диска          |
| SSD + жесткий диск             | 2 SSD + 4 жестких диска           |
| NVMe + SSD + жесткий диск      | 2 NVMe + 4 других       |

   >[!NOTE]
   > Эта таблица содержит минимальное развертываниям оборудования. Если вы являетесь, развертывание с помощью виртуальных машин и виртуальных хранилища, например Microsoft Azure, см. в разделе [с помощью дисковых пространств в кластеров гостевых виртуальных машин](storage-spaces-direct-in-vm.md).

### <a name="maximum-capacity"></a>Максимальная емкость

- Рекомендуемое: Максимальная емкость хранилища 100 терабайт (ТБ) для сервера
- Максимальное 1 до нескольких петабайт (1000 ТБ) номинальной емкости в пуле носителей