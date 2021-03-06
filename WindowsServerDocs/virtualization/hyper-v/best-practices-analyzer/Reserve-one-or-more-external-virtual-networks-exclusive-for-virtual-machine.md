---
title: Резервирование одной или нескольких внешних виртуальных сетей для монопольного использования виртуальными машинами
description: Содержит инструкции по устранению проблемы, о которой сообщило это правило анализатор соответствия рекомендациям.
ms.prod: windows-server
ms.service: na
manager: dongill
ms.technology: compute-hyper-v
ms.author: kathydav
ms.topic: article
ms.assetid: f7732258-93f1-44e8-835b-5ad2d1c45cd9
author: KBDAzure
ms.date: 8/16/2016
ms.openlocfilehash: a72f3d616bb0c520e49c27f90686196463f25953
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71364781"
---
# <a name="reserve-one-or-more-external-virtual-networks-for-exclusive-use-by-virtual-machines"></a>Резервирование одной или нескольких внешних виртуальных сетей для монопольного использования виртуальными машинами

>Область применения. Windows Server 2016

Дополнительные сведения о рекомендациях и сканировании см. в разделе [Анализатор соответствия рекомендациям](https://go.microsoft.com/fwlink/?LinkId=122786).  
  
|Свойство|Подробности|  
|-|-|  
|**Операционная система**|Windows Server 2016|  
|**Продукт или функция**|Hyper-V|  
|**Серьезности**|Ошибка|  
|**Категория**|Конфигурация|  
  
В следующих разделах курсив указывает текст пользовательского Интерфейса, который отображается в анализатор соответствия рекомендациям для этой проблемы.  
  
## <a name="issue"></a>Проблемы  
  
*Все внешние виртуальные сети настроены для использования как операционной системой управления, так и виртуальными машинами.*  
  
## <a name="impact"></a>Влияние  
  
*Производительность сети может снижаться в операционной системе управления.*  
  
## <a name="resolution"></a>Разрешение  
  
*Используйте диспетчер виртуальных коммутаторов, чтобы запретить общий доступ к внешней виртуальной сети с помощью операционной системы управления.*  
  
#### <a name="to-stop-sharing-the-external-virtual-network-with-the-management-operating-system"></a>Отмена общего доступа к внешней виртуальной сети с помощью операционной системы управления  
  
1.  Откройте диспетчер Hyper-V. Нажмите кнопку **запустить**, пункты **Администрирование**, а затем нажмите кнопку **диспетчера Hyper-V**.  
  
2.  В меню **Действия** выберите пункт **Диспетчер виртуальных коммутаторов**.  
  
3.  В разделе **виртуальные коммутаторы**щелкните имя внешнего виртуального коммутатора.  
  
4.  В области **тип подключения** в поле Имя физического сетевого адаптера снимите флажок **разрешить операционной системе предоставлять общий доступ к этому сетевому адаптеру** .  
  
5.  Нажмите кнопку **ОК**.  
  


