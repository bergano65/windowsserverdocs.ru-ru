---
ms.assetid: f0d4cecc-5a03-448c-bef9-86c4730b4eb0
title: "Обзор балансировки нагрузки виртуальной машины"
ms.prod: windows-server-threshold
ms.technology: storage-failover-clustering
ms.topic: article
author: bhattacharyaz
manager: eldenc
ms.author: subhatt
ms.date: 09/19/2016
ms.openlocfilehash: 0a106db25d476088898b914481e6041f20ce2e9e
ms.sourcegitcommit: 583355400f6b0d880dc0ac6bc06f0efb50d674f7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2017
---
# <a name="virtual-machine-load-balancing-overview"></a>Обзор балансировки нагрузки виртуальной машины

> Применяется к: Windows Server (канал точками годовой), Windows Server 2016

Ключа следует учитывать для развертывания частного облака находится капитальных расходов (<abbr title="капитальных расходов">Капитальные</abbr>) необходимо перейти в рабочую среду. Очень часто, чтобы добавить избыточность развертывания частного облака, во избежание находящиеся на стадии емкости во время пиковой в рабочей среде, но это увеличивает <abbr title="капитальных расходов">Капитальные</abbr>. Требуется для обеспечения избыточности управляется балансировки частных облаков, где некоторые узлы размещены другие виртуальные машины (<abbr title="виртуальных машин">Виртуальные машины</abbr>) и другие — недостаточно (например, только что после перезагрузки сервера).

## <a id="what-is-vm-load-balancing"></a>Что такое балансировки нагрузки виртуальной машины?
<abbr title="Виртуальная машина">Виртуальная машина</abbr> балансировки нагрузки — это новая функция в поле, в Windows Server 2016, которая позволяет оптимизировать использование узлов в отказоустойчивом кластере. Идентифицирует перегруженное узлов, а также повторно распространяет <abbr title="виртуальных машин">Виртуальные машины</abbr> из этих узлов в группе выделенной узлам. Некоторые ключевые аспекты эта функция таковы:

* *Это решение, время простоя ноль*: <abbr title="виртуальных машин">Виртуальные машины</abbr> являются live перенесенные простоя узлам.
* *Интеграция с существующей среды кластера*: сбой политики, такие как запрет близости, доменах сбоя и возможные владельцы учитываются.
* *Эвристические методы для балансировки*: <abbr title="виртуальной машины">Виртуальная машина</abbr> нехватку памяти и загрузка Процессора узла.
* *Тонкая настройка*: включена по умолчанию. Можно активировать по требованию или периодические интервалом.
* *Пороговые значения интенсивности*: доступны три пороговые значения на основе характеристик развертывания.

## <a id="feature-in-action"></a>Функции в действии
### <a id="new-node-added"></a>Новый узел будет добавлен в отказоустойчивом кластере
![Рисунок нового узла, добавляемого в отказоустойчивом кластере](media/vm-load-balancing/overview-VM-load-balancing-1.png)

При добавлении нового емкости в отказоустойчивом кластере, <abbr title="виртуальной машины">Виртуальная машина</abbr> функции балансировки нагрузки автоматически регулирует производительности из существующих узлах, добавленный узел в следующем порядке:

1. Загрузка оценивается на существующих узлах отказоустойчивого кластера.
2. Определяются все узлы в случае превышения порогового значения.
3. Узлы с наибольшим давления определяются для определения приоритета балансировки нагрузки.
4. <abbr title="Виртуальные машины">Виртуальные машины</abbr> будут динамической миграции (нет время простоя) с узла, превышение добавленный узел в отказоустойчивом кластере.

### <a id="recurring-load-balancing"></a>Повторяющиеся балансировки нагрузки
![Балансировка нагрузки рисунок повторяющихся виртуальной машины](media/vm-load-balancing/overview-VM-load-balancing-2.png)

При настройке для периодического балансировки давления на узлах кластера оценивается для балансировки каждые 30 минут. Кроме того загрузка может быть вычисляется по требованию. Здесь представлена последовательность шагов:

1. Загрузка оценивается на всех узлах в частном облаке.
2. Определяются все узлы, превышение порогового значения и тем ниже порогового значения.
3. Узлы с наибольшим давления определяются для определения приоритета балансировки нагрузки.
4. <abbr title="Виртуальные машины">Виртуальные машины</abbr> будут динамической миграции (нет время простоя) из узла превышения порогового значения в узле минимального порогового значения.

## <a name="see-also"></a>См. также:
* [Подробное описание балансировки нагрузки виртуальной машины](vm-load-balancing-deep-dive.md)
* [Отказоустойчивый кластер](failover-clustering-overview.md)
* [Обзор Hyper-V](../virtualization/hyper-v/Hyper-V-on-Windows-Server.md)