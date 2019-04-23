---
title: "Четность с зеркальным ускорением"
ms.prod: windows-server-threshold
ms.author: gawatu
ms.manager: masriniv
ms.technology: storage-file-systems
ms.topic: article
author: gawatu
ms.date: 8/9/2017
ms.assetid: 
ms.openlocfilehash: a94bc4f8251d0f1fb18c3dad95c2915d3346c69a
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="mirror-accelerated-parity"></a>Четность с зеркальным ускорением
>Область применения: Windows Server2016

В дисковых пространствах отказоустойчивость данных могут использоваться две фундаментальные технологии: зеркалирование и контроль четности. С [локальными дисковыми пространствами](../storage-spaces/storage-spaces-direct-overview.md) в ReFS появилась новая технология— четность с зеркальным ускорением. С ее помощью можно создавать тома, устойчивость которых будет обеспечиваться одновременно зеркалированием и контролем четности. Четность с зеркальным ускорением позволяет организовать недорогое хранение данных с экономичным использованием пространства без ущерба для производительности. 

![Том с четностью с зеркальным ускорением](media/mirror-accelerated-parity/Mirror-Accelerated-Parity-Volume.png)


## <a name="background"></a>Общая информация
С точки зрения производительности и экономии пространства характеристики зеркалирования и контроля четности как схем обеспечения устойчивости отличаются в корне:
- Зеркалирование обеспечивает пользователям высокую скорость записи, однако репликацию данных для каждой копии нельзя назвать эффективным использованием пространства. 
- Контроль четности, с другой стороны, подразумевает необходимость пересчитывать четность для каждой операции записи, что снижает скорость произвольной записи. Однако контроль четности позволяет пользователям более эффективно использовать пространство для хранения своих данных. (Подробнее об эффективном использовании пространства можно прочитать ![здесь](../storage-spaces/Storage-Spaces-Fault-Tolerance.md)). 

Таким образом, зеркалирование лучше подходит для хранения данных с высокими требованиями к производительности, тогда как контроль четности обеспечивает более экономное использование пространства. Четность с зеркальным ускорением в ReFS дает возможность использовать преимущества обеих этих схем, чтобы обеспечить одновременно экономичное и высокопроизводительное хранение данных за счет объединения зеркалирования и контроля четности в одном томе.


## <a name="data-rotation-on-mirror-accelerated-parity"></a>Ротация данных при четности с зеркальным ускорением

ReFS обеспечивает активную ротацию данных между зеркалированием и контролем четности в реальном времени. Это позволяет быстро записывать входящие операции записи на уровень с зеркалированием, а затем переводить их на уровень с контролем четности для экономичного хранения. Соответственно, входящий ввод-вывод быстро обслуживается на уровне с зеркалированием, тогда как "холодные" данные эффективно хранятся на уровне с контролем четности, обеспечивая и оптимальную производительность, и малозатратное хранение в пределах одного и того же тома. 

Для ротации данных между зеркалированием и контролем четности ReFS логически делит том на области размером 64МиБ, которые представляют собой единицу ротации. На рисунке ниже показан том с четностью с зеркальным ускорением, разделенный на области. 

![Том с четностью с зеркальным ускорением с контейнерами хранения](media/mirror-accelerated-parity/Mirror-Accelerated-Parity-Volume-with-Storage-Containers.png)

ReFS начинает ротацию целых областей с уровня с зеркалированием на уровень с контролем четности, как только уровень с зеркалированием достигнет заданного уровня по емкости. Вместо того чтобы немедленно перемещать данные с уровня с зеркалированием на уровень с контролем четности, ReFS ожидает и оставляет данные на уровне с зеркалированием как можно дольше, что позволяет продолжить обеспечивать для этих данных оптимальную производительность (см. "Производительность ввода-вывода" ниже). 

При перемещении данных с уровня с зеркалированием на уровень с контролем четности данные считываются, вычисляются кодировки четности, после чего эти данные записываются на уровень с контролем четности. Приведенная ниже анимация иллюстрирует этот процесс на примере трехсторонней зеркалируемой области, которая во время ротации преобразуется в область, кодированную под стирание:

![Ротация при четности с зеркальным ускорением](media/mirror-accelerated-parity/Container-Rotation.gif)

## <a name="io-on-mirror-accelerated-parity"></a>Ввод-вывод при четности с зеркальным ускорением
### <a name="io-behavior"></a>Поведение ввода-вывода
**Операции записи:** ReFS обслуживает входящие операции записи тремя различными способами:
1.  **Операции записи на уровень с зеркалированием:** 
     - **а.** Если входящая операция записи изменяет существующие данные на уровне с зеркалированием, ReFS внесет изменения в данные на месте. 
     - **б.** Если входящая операция записи представляет собой запись новых данных и ReFS удается найти достаточно свободного пространства на уровне с зеркалированием для обслуживания этой операции записи, ReFS запишет данные на уровень с зеркалированием. 

![Запись на уровень с зеркалированием](media/mirror-accelerated-parity/Write-to-Mirror.png)

2. **Операции записи на уровень с зеркалированием, перенаправляемые с уровня с контролем четности:**
    - **а.** Если входящая операция записи изменяет данные, которые находятся на уровне с контролем четности, и ReFS удается найти достаточно свободного пространства на уровне с зеркалированием для обслуживания этой входящей операции записи, ReFS сначала сделает недействительными ранее сохраненные данные на уровне с контролем четности, а затем выполнит запись на уровень с зеркалированием. Такое аннулирование данных представляет собой быструю и малозатратную операцию с метаданными, которая помогает существенно повысить производительность записи на уровень с контролем четности.

![Перенаправленная запись](media/mirror-accelerated-parity/Reallocated-Write.png)

3. **Операции записи на уровень с контролем четности:**
    - **а.** Если ReFS не удается найти достаточно свободного пространства на уровне с зеркалированием, ReFS запишет новые данные на уровень с контролем четности или изменит существующие данные непосредственно на уровне с контролем четности. В разделе "Оптимизация производительности" ниже приведены рекомендации, которые помогут свести к минимуму запись на уровень с контролем четности.

![Запись на уровень с контролем четности](media/mirror-accelerated-parity/Write-to-Parity.png)

**Операции чтения:** ReFS выполняет считывание непосредственно с уровня, содержащего соответствующие данные. Если уровень с контролем четности составлен из жестких дисков, кэш в локальных дисковых пространствах будет кэшировать эти данные для ускорения будущих операций чтения. 

> [!NOTE]
> Операции чтения никогда не приводят к переносу данных обратно на уровень с зеркалированием. 

### <a name="io-performance"></a>Производительность ввода-вывода

**Операции записи:** каждому типу записи, приведенному выше, свойственны собственные характеристики по производительности. Грубо говоря, операции записи на уровень с зеркалированием происходят намного быстрее, чем перенаправленные операции записи, а перенаправленные операции записи значительно быстрее, чем запись непосредственно на уровень с контролем четности. Это соотношение можно проиллюстрировать неравенством ниже: 


- **Уровень с зеркалированием > Перенаправленная запись >> Уровень с контролем четности**


**Операции чтения:** считывание с уровня с контролем четности не оказывает существенного отрицательного влияния на производительность:
- Если уровень с зеркалированием и уровень с контролем четности составлены из носителей одинакового типа, производительность чтения будет эквивалентной. 
- Если же уровень с зеркалированием и уровень с контролем четности составлены из носителей разных типов — например, уровень с зеркалированием из твердотельных дисков, а уровень с контролем четности из жестких дисков — [кэш в локальных дисковых пространствах](../storage-spaces/understand-the-cache.md) будет кэшировать "горячие" данные для ускорения операций считывания с уровня с контролем четности.

## <a name="refs-compaction"></a>Сжатие в ReFS
В этом осеннем выпуске в ReFS появилась технология сжатия, которая существенно повышает производительность томов с зеркальным ускорением четности, которые заполнены на 90процентов и более. 

**Общие сведения:** ранее по мере заполнения томов с зеркальным ускорением четности производительность этих томов могла ухудшаться. Ухудшение производительности связано с тем, что "горячие" и "холодные" данные перемешиваются при слишком большой активности тома. Это означает, что на уровне с зеркалированием удается хранить меньше "горячих" данных — "холодные" данные занимают на нем место, которое в противном случае могло бы использоваться под "горячие" данные. Хранение "горячих" данных на уровне с зеркалированием — важнейшее условие поддержания высокой производительности, потому что запись непосредственно на уровень с зеркалированием гораздо быстрее перенаправленной записи и на несколько порядков быстрее записи непосредственно на уровень с контролем четности. Таким образом, наличие "холодных" данных на уровне с зеркалированием отрицательно сказывается на производительности, поскольку уменьшает вероятность того, что ReFS сможет выполнять запись непосредственно на уровень с зеркалированием. 

Технология сжатия в ReFS направлена на устранение этих проблем с производительностью путем освобождения на уровне с зеркалированием места под "горячие" данные. При сжатии все данные — и с уровня с зеркалированием, и с уровня с контролем четности — сначала консолидируются на уровне с контролем четности. Это снижает фрагментацию в томе и увеличивает объем доступного для адресации пространства на уровне с зеркалированием. Что более важно, этот процесс позволяет ReFS консолидировать "горячие" данные обратно на уровень с зеркалированием:
-   При поступлении новых операций записи эти операции будут обслуживаться на уровне с зеркалированием. Таким образом, вновь записанные, "горячие" данные находятся на уровне с зеркалированием. 
-   В случае записи, изменяющей данные на уровне с контролем четности, выполняет перенаправленную запись, поэтому такая операция записи также обслуживается уровне с зеркалированием. Следовательно, "горячие" данные, которые были перемещены на уровень с контролем четности при сжатии, будут перенесены обратно на уровень с зеркалированием. 

## <a name="performance-optimizations"></a>Оптимизация производительности

>[!IMPORTANT]
>Для рабочих нагрузок Hyper-V на томах с четностью с зеркальным ускорением ReFS обеспечивает наилучшую производительность тогда, когда виртуальные жесткие диски с интенсивной записью распределены по нескольким каталогам. Таким образом, для достижения оптимальной производительности рекомендуется не помещать много виртуальных жестких дисков с интенсивной записью в один и тот же подкаталог.   

### <a name="performance-counters"></a>Счетчики производительности 

В ReFS предусмотрены счетчики производительности, которые помогают оценить производительность томов с четностью с зеркальным ускорением. 
-   Как было сказано выше в разделе "Запись на уровень четности", ReFS выполняет запись непосредственно на уровень с контролем четности, когда не удается найти свободное место на уровне с зеркалированием. Как правило, это происходит, когда уровень с зеркалированием заполняется быстрее, чем ReFS переводит данные на уровень с контролем четности. Иными словами, скорость ротации в ReFS не соответствует скорости приема данных. Приведенные ниже счетчики производительности позволяют определить, когда ReFS выполняет запись непосредственно на уровень с контролем четности:
```
ReFS\Data allocations slow tier/sec
ReFS\Metadata allocations slow tier/sec
```
-   Если эти счетчики не равны нулю, это указывает на то, что ReFS при ротации не удается достаточно быстро переводить данные с уровня с зеркалированием. Чтобы решить эту проблему, можно либо изменить интенсивность ротации, либо увеличить размер уровня с зеркалированием.

### <a name="rotation-aggressiveness"></a>Интенсивность ротации
ReFS начинает ротацию данных после того, как уровень с зеркалированием достигнет заданного порога заполнения.
-   Чем выше значения этого порога ротации, тем дольше ReFS держит данные на уровне с зеркалированием. Оставлять "горячие" данные на уровне оптимально с точки зрения производительности, однако ReFS не сможет эффективно обслуживать большие объемы входящего ввода-вывода. 
-   Более низкие значения позволяют ReFS заблаговременно переносить данные и лучше принимать входящий ввод-вывод. Это имеет смысл при рабочих нагрузках, связанных с интенсивным приемом данных, — например, в случае архивного хранилища. В то же время более низкие пороговые значения могут привести к ухудшению производительности при рабочих нагрузках общего назначения. Излишняя ротация данных, т.е. их перенос с уровня с зеркалированием, влечет за собой снижение производительности. 

В ReFS предусмотрен новый параметр для корректировки этого порога, настраиваемый с помощью раздела реестра. Этот раздел реестра необходимо настроить на **каждом узле в развертывании локальных дисковых пространств**. Чтобы изменения вступили в силу, требуется перезапуск. 
-   **Раздел:** HKEY_LOCAL_MACHINE\System\CurrentControlSet\Policies
-   **Имя значения (DWORD):** DataDestageSsdFillRatioThreshold
-   **Тип значения:** процент

Если этот раздел реестра не задан, ReFS будет использовать значение по умолчанию, равное 85%.  Это значение по умолчанию рекомендуется для большинства развертываний; использовать значения меньше 50% не рекомендуется. Приведенная ниже команда PowerShell демонстрирует, как установить для этого раздела реестра значение 75%. 
```
Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Policies -Name DataDestageSsdFillRatioThreshold -Value 75
 ```
 Для настройки этого раздела реестра на каждом узле в среде локальных дисковых пространств можно использовать указанную ниже команду PowerShell.
 ```
 $Nodes = 'S2D-01', 'S2D-02', 'S2D-03', 'S2D-04'
 Invoke-Command $Nodes {Set-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Policies -Name DataDestageSsdFillRatioThreshold -Value 75}
 ```

### <a name="increasing-the-size-of-the-mirrored-tier"></a>Увеличение размера уровня с зеркалированием. 
Увеличение размера уровня с зеркалированием позволяет ReFS держать большую часть рабочего набора на этом уровне. Это повышает вероятность того, что ReFS сможет записывать данные непосредственно на уровень с зеркалированием, что помогает добиться более высокой производительности. Приведенные ниже командлеты PowerShell демонстрируют, как увеличить размер уровня с зеркалированием.
```
Resize-StorageTier -FriendlyName “Performance” -Size 20GB
Resize-StorageTier -InputObject (Get-StorageTier -FriendlyName “Performance”) -Size 20GB
```
>[!TIP]
>Обязательно измените размер **Partition** и **Volume** после изменения размера **StorageTier**. Дополнительные сведения и примеры см. в разделе [Resize-Volumes](../storage-spaces/resize-volumes.md).

## <a name="creating-a-mirror-accelerated-parity-volume"></a>Создание тома с четностью с зеркальным ускорением
Приведенный ниже командлет PowerShell создает том с четностью с зеркальным ускорением с соотношением "зеркалирование : четность" 20:80 (рекомендуемая конфигурация для большинства рабочих нагрузок). Дополнительные сведения и примеры см. в разделе [Создание томов в локальных дисковых пространствах](../storage-spaces/Create-volumes.md).

```
New-Volume – FriendlyName “TestVolume” -FileSystem CSVFS_ReFS -StoragePoolFriendlyName “StoragePoolName” -StorageTierFriendlyNames Performance, Capacity -StorageTierSizes 200GB, 800GB
```

## <a name="see-also"></a>См. также

-   [Обзор ReFS](refs-overview.md)
-   [Клонирование блоков ReFS](block-cloning.md)
-   [Потоки целостности ReFS](integrity-streams.md)
-   [Обзор локальных дисковых пространств](../storage-spaces/storage-spaces-direct-overview.md)