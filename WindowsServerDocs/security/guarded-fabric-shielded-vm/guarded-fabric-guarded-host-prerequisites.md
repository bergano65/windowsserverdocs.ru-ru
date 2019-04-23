---
title: Предварительные требования для защищенных узлов
ms.custom: na
ms.prod: windows-server-threshold
ms.topic: article
manager: dongill
author: rpsqrd
ms.technology: security-guarded-fabric
ms.date: 08/29/2018
ms.openlocfilehash: 5f2c3ec4b2c434ea945d86c4b1593e2e416a5123
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59819235"
---
# <a name="prerequisites-for-guarded-hosts"></a>Предварительные требования для защищенных узлов

>Относится к: Windows Server 2019 г., Windows Server (полугодовой канал), Windows Server 2016

Ознакомьтесь с необходимыми условиями узла для режима аттестации, что вы выбрали, а затем нажмите кнопку Далее, чтобы добавить защищенные узлы.

## <a name="tpm-trusted-attestation"></a>Аттестация доверенного платформенного МОДУЛЯ

Защищенные узлы, с помощью режима доверенного платформенного МОДУЛЯ необходимо выполнить следующие условия:

-   **Оборудование**: Одного из узлов является обязательным для первоначального развертывания. Чтобы протестировать динамической миграции Hyper-V для экранированных виртуальных машин, необходимо иметь по крайней мере два узла.

    Узлы должны иметь:
    
    - IOMMU и преобразование адресов второго уровня (SLAT)
    - TPM 2.0
    - UEFI 2.3.1 или более поздней версии
    - Настроить загрузку с помощью UEFI (не BIOS или «устаревший» режим)
    - Безопасная загрузка включена
        
-   **Операционная система**: Windows Server 2016 Datacenter edition или более поздней версии

    > [!IMPORTANT]
    > Убедитесь, что установкой [последнее накопительное обновление](https://support.microsoft.com/help/4000825/windows-10-and-windows-server-2016-update-history).  

-   **Роли и компоненты**: Роль Hyper-V и функция поддержку защиты узла Hyper-V. Функция поддержку защиты узла Hyper-V доступна только в выпусках Windows Server Datacenter. 

> [!WARNING]
> Поддержку защиты узла Hyper-V позволяет на базе технологии виртуализации защиты целостности кода, который может быть несовместим с некоторыми устройствами. Мы настоятельно рекомендуем, протестировать эту конфигурацию в лабораторных условиях перед включением этой функции. В противном случае могут возникать непредвиденные ошибки, в том числе потеря данных или системная ошибки (STOP-ошибка). Дополнительные сведения см. в разделе [совместимое оборудование с помощью защиты целостности кода на основе Windows Server Virtualization](guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity.md).

**Следующий шаг.** 
>[!div class="nextstepaction"]
[Записать сведения доверенного платформенного МОДУЛЯ](guarded-fabric-tpm-trusted-attestation-capturing-hardware.md)

## <a name="host-key-attestation"></a>Аттестация ключей узла

Защищенные узлы, с помощью аттестации ключей узла необходимо выполнить следующие условия:

- **Оборудование**: Любой сервер, поддерживающий работу Hyper-V, появившийся с Windows Server 2019
- **Операционная система**: Выпуск Windows Server Datacenter 2019 г.
- **Роли и компоненты**: Роль Hyper-V и компонент поддержку защиты узла Hyper-V 

Узел можно присоединить к домену или рабочей группе. 

Для аттестации ключей узла необходимо быть под управлением Windows Server 2019 и с v2 аттестации HGS. Дополнительные сведения см. в разделе [предварительные требования HGS](guarded-fabric-prepare-for-hgs.md#prerequisites). 

**Следующий шаг.** 
>[!div class="nextstepaction"]
[Создание пары ключей](guarded-fabric-create-host-key.md)

## <a name="admin-trusted-attestation"></a>Аттестация по группе доверенного администратора

>[!IMPORTANT]
>Аттестацию с доверием администратора (режим AD) является устаревшим, начиная с Windows Server 2019. Для сред, где аттестацию доверенного платформенного МОДУЛЯ не поддерживается, Настройка [размещения Аттестация ключей](#host-key-attestation). Аттестация ключей узла обеспечивает аналогичный уверенность в режим AD и проще в настройке. 

Узлы Hyper-V необходимо выполнить следующие условия для режима AD:

-   **Оборудование**: Любой сервер, поддерживающий работу Hyper-V, появившийся с Windows Server 2016. Одного из узлов является обязательным для первоначального развертывания. Для тестирования динамической миграции Hyper-V для экранированных виртуальных машин, необходимо по крайней мере два узла.

-   **Операционная система**: Windows Server 2016 Datacenter edition

    > [!IMPORTANT]
    > Установка [последнее накопительное обновление](https://support.microsoft.com/help/4000825/windows-10-and-windows-server-2016-update-history).

-   **Роли и компоненты**: Роль Hyper-V и функция поддержку защиты узла Hyper-V, которая доступна только в Windows Server 2016 Datacenter edition. 

> [!WARNING]
> Поддержку защиты узла Hyper-V позволяет на базе технологии виртуализации защиты целостности кода, который может быть несовместим с некоторыми устройствами. Мы настоятельно рекомендуем, протестировать эту конфигурацию в лабораторных условиях перед включением этой функции. В противном случае могут возникать непредвиденные ошибки, в том числе потеря данных или системная ошибки (STOP-ошибка). Дополнительные сведения см. в разделе [совместимое оборудование с помощью защиты целостности кода на основе виртуализации Windows Server 2016](guarded-fabric-compatible-hardware-with-virtualization-based-protection-of-code-integrity.md).

**Следующий шаг.** 
>[!div class="nextstepaction"]
[Установите защищенных узлов в группу безопасности](guarded-fabric-admin-trusted-attestation-creating-a-security-group.md)