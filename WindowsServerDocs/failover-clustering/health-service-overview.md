---
title: Служба работоспособности в Windows Server
ms.prod: windows-server-threshold
manager: eldenc
ms.author: cosdar
ms.technology: storage-health-service
ms.topic: article
ms.assetid: 5bc71e71-920e-454f-8195-afebd2a23725
author: cosmosdarwin
ms.date: 02/09/2018
ms.openlocfilehash: 5afb64dcf0c59697ed55d7cf51ef1bc36e7e0e36
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59863815"
---
# <a name="health-service-in-windows-server"></a>Служба работоспособности в Windows Server

> Область применения: Windows Server 2016

Служба работоспособности — это новая функция в Windows Server 2016, которая улучшает ежедневного мониторинга и опыт эксплуатации кластеров дисковыми пространствами.

## <a name="prerequisites"></a>Предварительные требования  

Служба работоспособности включена по умолчанию для локальных дисковых пространств. Не требуется никаких дополнительных действий для ее настройки и запуска. Дополнительные сведения о дисковых пространств, см. в разделе [дисковых пространств в Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md).  

## <a name="reports"></a>Отчеты

См. в разделе [отчеты о работоспособности службы](health-service-reports.md).

## <a name="faults"></a>Ошибки

См. в разделе [ошибки службы работоспособности](health-service-faults.md).

## <a name="actions"></a>Действия

См. в разделе [действия служба работоспособности](health-service-actions.md).

## <a name="automation"></a>Автоматизация  

В следующем разделе описываются рабочие процессы жизненного цикла диска, которые автоматизирует служба работоспособности.  

### <a name="disk-lifecycle"></a>Жизненный цикл диска   

Служба работоспособности автоматизирует практически все этапы жизненного цикла физического диска. Предположим, что изначально развертывание находится в идеальном состоянии, то есть все физические диски работают должным образом.  

#### <a name="retirement"></a>Снятие диска с учета  

Физические диски автоматически снимаются с учета, если их невозможно использовать. При этом создается соответствующее сообщение об ошибке. Причины этого могут быть разные:  

-   Сбой носителя: несомненный сбой или поломка физического диска, требуется замена диска.  

-   Потеря связи: физический диск теряет подключение более чем на 15 минут подряд.  

-   Отсутствие ответа: ответ от физического диска задерживался более чем на 5 секунд как минимум 3 раза за час.  

>[!NOTE]
> Если утрачено соединение одновременно с несколькими физическими дисками, со всем узлом или дисковой полкой, служба работоспособности *не* снимает диски с учета, так как, скорее всего, они не являются главной проблемой.  

Если снятый с учета диск выполнял функции кэша для нескольких других физических дисков, то для них автоматически назначается новый диск кэша (если он доступен). Никаких действий со стороны пользователя не требуется.  

#### <a name="restoring-resiliency"></a>Восстановление устойчивости  

После снятия с учета физического диска служба работоспособности немедленно начинает копировать данные на оставшиеся физические диски, чтобы восстановить полную устойчивость. После завершения этой операции данные снова полностью защищены и отказоустойчивы.  

>[!NOTE]
> Для такого немедленного восстановления требуется наличие достаточной емкости на оставшихся физических дисках.  

#### <a name="blinking-the-indicator-light"></a>Мигающий световой индикатор  

Если возможно, служба работоспособности активирует мигание светового индикатора на снятом с учета физическом диске или на его слоте. Мигание продолжается неограниченно долго, вплоть до замены снятого с учета диска.  

>[!NOTE]
> При некоторых сбоях, например при полной потере питания, становится невозможным даже мигание индикатора.  

#### <a name="physical-replacement"></a>Физическая замена  

Снятый с учета физический диск следует заменить как можно быстрее. Чаще всего он состоит из горячей замены, — т. е. выключение узла или дисковой полки не является обязательным. В описании ошибки представлена полезная информация о проблемной детали и ее расположении.  

#### <a name="verification"></a>Проверка

При вставке заменяющий диск, он проверяется на соответствие документ поддерживаемых компонентов (см. следующий раздел).

#### <a name="pooling"></a>Включение в пул  

Если новый диск признается допустимым, он автоматически занимает место своего предшественника в пуле и берет на себя его функции. На этом этапе система возвращается в исходное состояние идеальной работоспособности и ошибка исчезает.  

## <a name="supported-components-document"></a>Поддерживаемые компоненты документа  

Служба работоспособности есть механизм контроля, чтобы ограничить компонентах, используемых локальными дисковыми пространствами с элементами на поддерживаемые документа компоненты, предоставляемые администратора или поставщика решений. Благодаря этому можно предотвратить случайное использование неподдерживаемого оборудования, что помогает соблюсти условия гарантии или договора. Эта функция действует в настоящее время только для физических дисковых устройств, включая SSDs, жесткие диски, и диски NVMe. Поддерживаемые компоненты документа можно ограничить на модель, производителям (необязательно) и версии встроенного по (необязательно).

### <a name="usage"></a>Использование  

Поддерживаемые компоненты документа использует синтаксиса на основе XML. Мы рекомендуем использовать текстовый редактор, например [Visual Studio Code](http://code.visualstudio.com/) или Блокнот, чтобы создать документ XML, который можно сохранить и повторно использовать.

#### <a name="sections"></a>Разделы

Документ состоит из двух независимых разделов: `Disks` и `Cache`.

Если `Disks` раздел не указан, перечислены только те диски (как `Disk`) получат право присоединять пулов. Все отсутствующие в списке диски не могут присоединяться к пулам, что фактически исключает их использование в рабочей среде. Если в этом разделе оставлено пустым, любой диск будет разрешено присоединение пулов.

Если `Cache` раздел не указан, перечислены только те диски (как `CacheDisk`) используются для кэширования. Если в этом разделе оставлено пустым, дисковыми пространствами пытается [прогноз на основе типа носителя и тип шины](../storage/storage-spaces/understand-the-cache.md#cache-drives-are-selected-automatically). Перечисленные здесь должен быть указан в `Disks`.

>[!IMPORTANT]
> Документ компонентов поддерживается не применяется к дискам, которые уже включенных в пул и используется задним числом.  

#### <a name="example"></a>Пример

```XML
<Components>

  <Disks>
    <Disk>
      <Manufacturer>Contoso</Manufacturer>
      <Model>XYZ9000</Model>
      <AllowedFirmware>
        <Version>2.0</Version>
        <Version>2.1</Version>
        <Version>2.2</Version>
      </AllowedFirmware>
      <TargetFirmware>
        <Version>2.1</Version>
        <BinaryPath>C:\ClusterStorage\path\to\image.bin</BinaryPath>
      </TargetFirmware>
    </Disk>
    <Disk>
      <Manufacturer>Fabrikam</Manufacturer>
      <Model>QRSTUV</Model>
    </Disk>
  </Disks>

  <Cache>
    <CacheDisk>
      <Manufacturer>Fabrikam</Manufacturer>
      <Model>QRSTUV</Model>
    </CacheDisk>
  </Cache>

</Components>

```

Чтобы получить список несколько дисков, просто добавьте дополнительные `<Disk>` или `<CacheDisk>` теги.

Чтобы внедрить этот XML-код при развертывании дисковых пространств, используйте `-XML` параметр:

```PowerShell
$MyXML = Get-Content <Filepath> | Out-String  
Enable-ClusterS2D -XML $MyXML
```

Чтобы задать или изменить документ поддерживаемых компонентов, после развертывания дисковых пространств:

```PowerShell
$MyXML = Get-Content <Filepath> | Out-String  
Get-StorageSubSystem Cluster* | Set-StorageHealthSetting -Name "System.Storage.SupportedComponents.Document" -Value $MyXML  
```

>[!NOTE]
>Модель, изготовитель и версия встроенного ПО должны полностью совпадать с теми значениями, которые возвращает командлет **Get-PhysicalDisk**. В некоторых случаях эти значения отличаются от того, что подсказывает здравый смысл. Например, производитель может быть обозначен как "CONTOSO-LTD" вместо "Contoso", или это поле остается пустым, зато для модели указывается значение "Contoso-XZY9000".  

Эти данные можно проверить с помощью командлета PowerShell:  

```PowerShell
Get-PhysicalDisk | Select Model, Manufacturer, FirmwareVersion  
```

## <a name="settings"></a>Параметры

См. в разделе [параметры службы работоспособности](health-service-settings.md).

## <a name="see-also"></a>См. также

- [Отчеты о работоспособности службы](health-service-reports.md)
- [Ошибки службы работоспособности](health-service-faults.md)
- [Действия службы работоспособности](health-service-actions.md)
- [Параметры службы работоспособности](health-service-settings.md)
- [Дисковые пространства в Windows Server 2016](../storage/storage-spaces/storage-spaces-direct-overview.md)