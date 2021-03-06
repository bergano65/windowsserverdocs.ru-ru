---
title: Настройка контроллеров SCSI только при поддержке операционной системой на виртуальной машине
description: Интернет-версия текста для этого правила анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: 861f194f-467e-4b07-a1c5-55b35f6327c4
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: da8d929a8f06f58610913d28d2f1e90299efb235
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71366421"
---
# <a name="configure-scsi-controllers-only-when-supported-by-the-guest-operating-system"></a>Настройка контроллеров SCSI только при поддержке операционной системой на виртуальной машине

>Область применения: Windows Server 2016


  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Тревожное|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблема  
  
*Для виртуальной машины настроен контроллер SCSI, который нельзя использовать, так как операционная система на виртуальной машине не поддерживает контроллеры SCSI.*  
  
## <a name="impact"></a>Влияние  
  
*Виртуальные машины не могут использовать хранилище, подключенное к контроллеру SCSI. Это влияет на следующие виртуальные машины:*  
  
\<список виртуальных машин >  
  
## <a name="resolution"></a>Разрешение  
  
*Завершите работу виртуальной машины и с помощью диспетчера Hyper-V удалите контроллер SCSI с виртуальной машины. Затем перезапустите виртуальную машину.*  
  


