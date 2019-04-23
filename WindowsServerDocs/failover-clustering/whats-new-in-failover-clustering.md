---
ms.assetid: 350aa5a3-5938-4921-93dc-289660f26bad
title: "Новые возможности отказоустойчивой кластеризации в Windows Server"
ms.prod: windows-server-threshold
ms.technology: storage-failover-clustering
ms.topic: get-started-article
manager: dongill
author: JasonGerend
ms.author: jgerend
ms.date: 10/11/2016
ms.openlocfilehash: a4330f62095e13f2f4736f15924ed31fb4893e7a
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="whats-new-in-failover-clustering-in-windows-server-2016"></a>Новые возможности отказоустойчивой кластеризации в Windows Server 2016
> Применяется к: Windows Server (канал точками годовой), Windows Server 2016

В этом разделе приводятся сведения о новых и измененных функциях отказоустойчивой кластеризации в Windows Server 2016.  

## <a name="BKMK_RollingUpgrade"></a>Последовательное обновление ОС кластера  
Это новая функция в отказоустойчивой кластеризации последовательного обновления кластерной ОС, позволяет администратору обновлять ОС узлов кластера с Windows Server 2012 R2 до Windows Server 2016 не останавливая рабочие нагрузки Scale-Out File Server или Hyper-V. С помощью этой функции, можно избежать простоя потерь от службы соглашений об УРОВНЕ обслуживания.  

**Какой эффект дает это изменение?**  

Обновление кластера Hyper-V или масштабируемого файлового сервера с Windows Server 2012 R2 до Windows Server 2016 больше не требуется простой. Кластер будет продолжать работать на уровне Windows Server 2012 R2, пока все узлы в кластере под управлением Windows Server 2016. Режим работы кластера обновляется до Windows Server 2016 с помощью командлет Windows PowerShell `Update-ClusterFunctionalLevel`.  

> [!WARNING]  
> -   После обновления режим работы кластера, вы не сможете перейти на режим работы кластера Windows Server 2012 R2.  
> -   Пока `Update-ClusterFunctionalLevel`выполняется командлет, процесс обратимое и можно добавить узлы Windows Server 2012 R2 и узлы Windows Server 2016, можно удалить.  

**Что работает иначе?**  

Теперь можно без труда обновлять без простоев отказоустойчивого кластера Hyper-V или масштабируемого файлового сервера, или требуется создать новый кластер с узлами под управлением операционной системы Windows Server 2016. Миграция кластеров в Windows Server 2012 R2 участвует отключая существующего кластера и повторной установки новой операционной системе для каждого узлов, а затем перенос кластера в оперативный режим. Старый процесс был громоздкой задачей, требуется время простоя. Тем не менее в Windows Server 2016 кластера не требуется перейти в автономный режим в любой момент.  

Операционные системы кластера к обновлению поэтапно таковы для каждого узла в кластере:  
-   Узел приостановлен и разрядилась всех виртуальных машин, запущенных на нем.  
-   Виртуальные машины (или другие рабочей нагрузки кластера) переносятся на другой узел в кластере cluster.The переносятся на другой узел в кластере.  
-   Существующая операционная система удаляется и выполнена чистая установка операционной системы Windows Server 2016 на узле.  
-   Узел, под управлением операционной системы Windows Server 2016 будет добавлен к кластеру.  
-   На этом этапе кластера считается работает в смешанном режиме, так как узлы кластера под управлением Windows Server 2012 R2 или Windows Server 2016.  
-   Режим работы кластера остается в Windows Server 2012 R2. В этот режим работы новых функций в Windows Server 2016, влияющие на совместимость с предыдущими версиями операционной системы не будет доступен.  
-   В конце концов все узлы будут обновлены до Windows Server 2016.  
-   Режим работы кластера, то изменить на Windows Server 2016 с помощью командлета Windows PowerShell `Update-ClusterFunctionalLevel`. На этом этапе можно воспользоваться преимуществами функций Windows Server 2016.  

Дополнительные сведения см. в разделе [последовательного обновления кластерной ОС ](cluster-operating-system-rolling-upgrade.md).  

## <a name="BKMK_SR"></a>Реплика хранилища  
Реплика хранилища — новая функция, которая реализует независимую от хранилища, блочного синхронную репликацию между серверами или кластерами в целях аварийного восстановления, а также расширяющая преимущества отказоустойчивого кластера между сайтами. Синхронная репликация позволяет зеркально отображать данные в физических расположениях с отказоустойчивыми томами, что полностью предотвращает потерю данных на уровне файловой системы. Асинхронная репликация позволяет сайта за пределами города, при этом вероятна потеря данных.  

**Какой эффект дает это изменение?**  

Реплика хранилища позволяет выполнить следующие действия.  

-   Предоставляет один поставщика решения для аварийного восстановления запланированных и незапланированных сбоях критически важных приложений.  

-   Использование транспортного протокола SMB3 с доказанной надежностью, масштабируемостью и производительностью.  

-   Растягивание отказоустойчивых кластеров Windows до Городской сети.  

-   Использование программного обеспечения корпорации Майкрософт в сквозном режиме для хранения и кластеризации, в частности Hyper-V, реплика хранилища, дисковых пространств, кластера, масштабируемого файлового сервера, SMB3, дедупликации данных и ReFS/NTFS.  

-   Сокращение затрат и Уменьшение сложности следующим образом:  

    -   Не зависит от оборудования, отсутствуют строгие требования к конфигурации хранилища, DAS или SAN.  

    -   Разрешается использовать стандартные технологии хранения и сетевых подключений.  

    -   В удобной графической управление отдельными узлами и кластерами с помощью диспетчера отказоустойчивости кластеров.  

    -   Включает в себя полноценного и крупномасштабных скриптов с помощью Windows PowerShell.  

-   Помогают сократить простои и повысить надежность и производительность, встроенные в Windows.  

-   Обеспечивают поддержку, диагностику и Определение метрик производительности.  

Дополнительные сведения см. в разделе [реплики хранилища в Windows Server 2016](../storage/storage-replica/storage-replica-overview.md).  


## <a name="BKMK_CloudWitness"></a>Облако-свидетель  
Облако-свидетель — это новый тип свидетеля кворума отказоустойчивого кластера в Windows Server 2016, которая использует Microsoft Azure в качестве точки арбитража. Облако-свидетель, как любой другой свидетель кворума, получает голос и может участвовать в подсчете кворума. Можно настроить облако-свидетель, как свидетеля кворума с помощью мастера настройки кластера кворума.  

**Какой эффект дает это изменение?**  

С помощью облако-свидетель в качестве отказоустойчивого кластера свидетеля кворума предоставляет следующие преимущества:  

-   Использует Microsoft Azure и исключает необходимость в третий отдельный центра обработки данных.  

-   Использует стандартные общедоступными Microsoft Azure хранилище BLOB-объектов тем самым устраняет дополнительную поддержку виртуальных машин, размещенных в общедоступном облаке.  

-   Учетную запись хранения Azure Майкрософт можно использовать для нескольких кластеров (один большой двоичный объект файла на кластер; уникальный идентификатор кластера используется в качестве имени файла большой двоичный объект).  

-   Предоставляет очень низкой стоимости на переход к учетной записи хранилища (очень малой данные, записанные на большой двоичный объект файл, файл большой двоичный объект обновляется только в том случае, когда при изменении состояния узлов кластера).  

Дополнительные сведения см. в разделе [развертывание облака свидетеля для отказоустойчивого кластера ](deploy-cloud-witness.md).  

**Что работает иначе?**  

Эта возможность появилась в Windows Server 2016.  

## <a name="BKMK_VMs"></a>Устойчивость виртуальных машин  
**Вычисления устойчивости** Windows Server 2016 включает устойчивости вычислительных Повышенная виртуальных машин для снижения проблемы взаимодействия внутри кластера вычислительных кластеров, следующим образом: 

-   **Параметры устойчивости, доступные для виртуальных машин:** теперь можно настроить параметры устойчивости виртуальной машины, определяющих поведение виртуальных машин во время временные ошибки:  

    -   **Уровень устойчивости:** поможет определить, как обрабатываются временные ошибки.  

    -   **Период устойчивости:** поможет определить, как долго все виртуальные машины могут выполняться изолированной.  

-   **Карантин неработоспособное узлов:** неработоспособное узлы, находящиеся в карантине и больше не могут присоединяться к кластеру. Это предотвращает отрицательно влияют на другие узлы и кластеру flapping узлов.  

Дополнительные сведения о виртуальной машины вычислений рабочего процесса и узел карантина параметры устойчивости, управляющие размещение узлу в изоляции или поместить в карантин, в разделе [вычисления устойчивость виртуальных машин в Windows Server 2016](http://blogs.msdn.com/b/clustering/archive/2015/06/03/10619308.aspx).  

**Устойчивость хранилища** в Windows Server 2016, являются более устойчивы к сбоям временные хранилища виртуальных машин. Улучшенные устойчивость виртуальных машин помогает сохранять состояния сеанса клиента виртуальных машин в случае прерывания хранилища. Это достигается виртуальной машины интеллектуальной и быстрый ответ на проблем инфраструктуры хранения.  

При отключении виртуальной машины от базового хранилища, она приостанавливает и ожидает хранения для восстановления. Во время приостановки, виртуальная машина сохраняет контекст приложений, которые выполняются в нем. При восстановлении подключения к виртуальной машине хранилище виртуальной машины возвращает рабочее состояние. В результате машина клиента состояние сеанса сохраняется на восстановление.  

В Windows Server 2016 устойчивость хранилища виртуальных машин тоже извещены об этом и оптимизированный для гостевых кластеров.  

## <a name="BKMK_Diagnostics"></a>Усовершенствования диагностики: в отказоустойчивой кластеризации  
Для диагностики проблем с отказоустойчивыми кластерами Windows Server 2016 включает следующее:  

-   Несколько улучшений в файлы журналов кластера (например, сведения о часовых поясах и DiagnosticVerbose журнала), позволяет проще, можно устранить неполадки отказоустойчивой кластеризации. Дополнительные сведения см. в разделе [Windows Server 2016 отказоустойчивого кластера улучшенное Устранение неполадок — журнал кластера](http://blogs.msdn.com/b/clustering/archive/2015/05/15/10614930.aspx).  

-   Новый дампа тип **дампа памяти Active**, который отфильтровывает большинство страниц памяти, выделенной виртуальным машинам и таким образом делает memory.dmp гораздо меньше и проще для сохранения или копирования.  Дополнительные сведения см. в разделе [Windows Server 2016 кластера улучшенное Устранение неполадок отказоустойчивого - Active дамп](http://blogs.msdn.com/b/clustering/archive/2015/05/18/10615526.aspx).  

## <a name="BKMK_SiteAware"></a>Поддержкой отказоустойчивых кластеров  
Windows Server 2016 включает учитывать отказоустойчивых кластеров на узел -, позволяющие группы узлы в растянутых кластерах, в зависимости от их физического расположения (сайт). Сайтах кластера оптимизирует ключевые операции, во время жизненного цикла кластера, включая отработку отказа, применение политик размещения, подтверждения соединения между узлами и поведение кворума. Дополнительные сведения см. в разделе [поддержкой отказоустойчивых кластеров в Windows Server 2016](http://blogs.msdn.com/b/clustering/archive/2015/08/19/10636304.aspx).  

## <a name="BKMK_multidomainclusters"></a>Кластеры рабочей группы и несколькими доменами  
В Windows Server 2012 R2 и предыдущих версиях кластер могут создаваться только между узлов-участников, присоединен к тому же домену.   Windows Server 2016 эти снято, а также добавлена возможность создавать отказоустойчивый кластер без зависимостей от Active Directory. Теперь вы можете создавать отказоустойчивые кластеры в следующих конфигурациях:  

-   **Кластеры с одним доменом.** Кластеры с всех узлов, присоединенных к домену.  

-   **Кластеры с несколькими доменами.** Кластеры с узлами, которые входят в разных доменах.  

-   **Кластеры рабочей группы.** В кластерах с узлами, которые являются рядовыми серверами или рабочей группы (не к домену).  

Дополнительные сведения см. в разделе [кластеры рабочей группы и несколькими доменами в Windows Server 2016](http://blogs.msdn.com/b/clustering/archive/2015/08/17/10635825.aspx)  
## <a name="BKMK_VMLoadBalancing"></a>Балансировка нагрузки виртуальной машины  
Балансировка нагрузки виртуальной машины — это новая функция в отказоустойчивой кластеризации, упрощающая эффективной балансировки нагрузки виртуальных машин между узлами в кластере. Узлы перегруженного определяются на основе виртуальной машины памяти и ЦП на узле. Виртуальные машины перемещаются (динамическую миграцию) из узла перегруженное узлы доступной пропускной способности (если применимо). Интенсивности балансировки может быть настроена для обеспечения оптимальной кластера производительности и использования в.  По умолчанию в Windows Sever 2016 Technical Preview включена балансировки нагрузки. Однако Балансировка нагрузки отключен при включении SCVMM динамической оптимизации.  

## <a name="BKMK_VMStartOrder"></a>Порядок запуска виртуальных машин  
Порядок запуска виртуальных машин — это новая функция в отказоустойчивой кластеризации с начала оркестрации заказа для виртуальных машин (и всех групп) в кластере. Виртуальные машины, теперь могут быть объединены в уровней и зависимостей порядка start могут создаваться между различными уровнями. Это гарантирует, что наиболее важных виртуальных машин (например, контроллеры домена или служебной программы виртуальных машин), запущены первый. Пока виртуальные машины, которые они зависят от также запущены виртуальные машины не запускаются.  

## <a name="BKMK_SMBMultiChannel"></a>Упрощенные SMB Multichannel и сети кластера Multi-NIC  
Отказоустойчивый кластер сети больше не являются только один сетевой Адаптер на подсеть / сеть. С упрощенная многоканальным SMB и сети кластера Multi-NIC автоматической конфигурации сети и для трафика кластера и рабочая нагрузка может использоваться каждый сетевой Адаптер подсети. Это улучшение позволяет клиентам для повышения пропускной способности сети для Hyper-V, экземпляра отказоустойчивого кластера SQL Server и других рабочих нагрузок SMB.  

Дополнительные сведения см. в разделе [упрощенная SMB Multichannel и сети кластера Multi-NIC](smb-multichannel.md).

## <a name="see-also"></a>См. также:  
* [Хранилища](../storage/storage.md)  
* [Новые возможности хранилища в Windows Server 2016](../storage/whats-new-in-storage.md)  