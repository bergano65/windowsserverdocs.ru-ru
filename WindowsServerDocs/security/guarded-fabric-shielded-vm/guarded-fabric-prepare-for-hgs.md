---
title: Проверка предварительных требований для HGS
ms.custom: na
ms.prod: windows-server
ms.topic: article
ms.assetid: f4b4d1a8-bf6d-4881-9150-ddeca8b48038
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 9024557dd42ede27144bf10aa5873b6bb12d585c
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71403491"
---
# <a name="review-prerequisites-for-the-host-guardian-service"></a>Проверка предварительных требований для службы защиты узла

>Относится к: Windows Server 2019, Windows Server (половина ежегодного канала), Windows Server 2016


В этом разделе рассматриваются предварительные требования для HGS и начальные шаги для подготовки к развертыванию HGS.

## <a name="prerequisites"></a>Предварительные требования 

-   **Оборудование**: HGS можно запустить на физических компьютерах или виртуальных машинах, но рекомендуется использовать физические компьютеры.

    Если вы хотите запустить HGS как физический кластер из трех узлов (для обеспечения доступности), необходимо иметь три физических сервера. (Для кластеризации рекомендуется, чтобы на трех серверах было очень похожее оборудование.)
  
-   **Операционная система**: Для аттестации ключа узла требуется ОС Windows Server 2019 Standard или Datacenter Edition с [аттестацией v2](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md#versioned-attestation-policies). Для аттестации на основе доверенного платформенного модуля HGS может работать под управлением Windows Server 2019 или Windows Server 2016, Standard или Datacenter Edition.

-   **Роли сервера**: Служба защиты узла и вспомогательные роли сервера.

-   **Разрешения и привилегии конфигурации для домена структуры (узла)** : Необходимо настроить перенаправление DNS между доменом (узлом) и доменом HGS. 
    
## <a name="upgrading-hgs"></a>Обновление HGS

Если вы уже развернули HGS и хотите обновить свою операционную систему, следуйте инструкциям [по обновлению, чтобы обновить](guarded-fabric-upgrade-to-2019.md) серверы HGS и Hyper-V до последней ОС.

## <a name="next-step"></a>Дальнейшие действия

> [!div class="nextstepaction"]
> [Получение сертификатов для HGS](guarded-fabric-obtain-certs.md)