---
title: Управление vRSS
description: В этом разделе вы используете команды Windows PowerShell для управления vRSS на виртуальных машинах (ВМ) и на узлах Hyper-V.
ms.prod: windows-server
ms.technology: networking
ms.topic: article
ms.assetid: 0fe5bfc3-591f-4a19-b98a-0668d4c9f93a
ms.localizationpriority: medium
manager: dougkim
ms.date: 09/05/2018
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 9d528f7e658d61f613eedc635fb81d8f18fd59aa
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71405165"
---
# <a name="manage-vrss"></a>Управление vRSS

В этом разделе вы используете команды Windows PowerShell для управления vRSS на виртуальных машинах \(ВМ\) и на узлах Hyper\-V.

>[!NOTE]
>Дополнительные сведения о командах, упомянутых в этом разделе, см. в разделе [команды Windows PowerShell для RSS и vRSS](vrss-wps.md).

## <a name="vmq-on-hyper-v-hosts"></a>VMQ на узлах Hyper-V

На узле Hyper-V необходимо использовать ключевые слова, управляющие процессорами VMQ.

**Просмотр текущих параметров:** 

```PowerShell
Get-NetAdapterVmq
```

**Настройте параметры VMQ:** 

```PowerShell
Set-NetAdapterVmq
```


## <a name="vrss-on-hyper-v-switch-ports"></a>vRSS на портах коммутатора Hyper-V

На узле Hyper-V необходимо также включить vRSS на порте виртуального коммутатора Hyper\-V.

**Просмотр текущих параметров:**

```PowerShell
Get-VMNetworkAdapter <vm-name> | fl

Get-VMNetworkAdapter -ManagementOS | fl
```
    
Оба следующих параметра должны иметь **значение true**. 

- Врссенабледрекуестед: true
- Врссенаблед: true
    
>[!IMPORTANT]
>В некоторых условиях ограничения ресурсов для порта виртуального коммутатора Hyper\-V может быть невозможно включить эту функцию. Это временное условие, и эта функция может стать доступной в следующий раз.
>
>Если **врссенаблед** имеет **значение true**, эта функция включена для этого порта виртуального коммутатора Hyper\-V, т. е. для этой виртуальной машины или vNIC.

**Настройте параметры vRSS для портов коммутатора:**

```PowerShell
Set-VMNetworkAdapter <vm-name> -VrssEnabled $TRUE
    
Set-VMNetworkAdapter -ManagementOS -VrssEnabled $TRUE
```

## <a name="vrss-in-vms-and-host-vnics"></a>vRSS в виртуальных машинах и узле vNIC

Вы можете использовать те же команды, которые используются для собственного RSS-канала, чтобы настроить параметры vRSS на виртуальных машинах и узле vNIC, что также является способом включения RSS на узле vNIC.  

**Просмотр текущих параметров:**

```PowerShell
Get-NetAdapterRSS
```

**Настройка параметров vRSS:**

```PowerShell
Set-NetAdapterRss
```

>[!NOTE]
> Настройка профиля в виртуальной машине не влияет на планирование работы. Hyper\-V принимает все решения по планированию и игнорирует профиль внутри виртуальной машины.

## <a name="disable-vrss"></a>Отключение vRSS

Можно отключить vRSS, чтобы отключить любые из упомянутых выше параметров.

- Отключите VMQ для физического сетевого адаптера или виртуальной машины.

  >[!CAUTION]
  >Отключение VMQ на физическом сетевом адаптере серьезно влияет на способность узла Hyper\-V обрабатывать входящие пакеты.

- Отключите vRSS для виртуальной машины на порте виртуального коммутатора Hyper\-V на узле Hyper\-V.

   ```PowerShell
   Set-VMNetworkAdapter <vm-name> -VrssEnabled $FALSE
   ```

- Отключите vRSS для узла vNIC на порте виртуального коммутатора Hyper\-V на узле Hyper\-V.

   ```PowerShell
   Set-VMNetworkAdapter -ManagementOS -VrssEnabled $FALSE
   ```

- Отключите RSS в виртуальной машине \(или узле vNIC\) внутри \(виртуальной машины или на узле\)

   ```PowerShell
   Disable-NetAdapterRSS *
   ```
