---
title: Управление — TPM BDE
description: 'Раздел Windows команды для ****- '
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 11a8530d-edd7-4fe3-ae81-b943766760fe
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 577f5f2ecb85ac8c0c28fef2ca343635796454d2
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71373827"
---
# <a name="manage-bde-tpm"></a>Manage-bde: TPM

> Область применения. Windows Server (половина ежегодного канала), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012
> 
> [!IMPORTANT]
> Эта команда не поддерживается для использования на компьютерах под управлением Windows 8, Windows Server 2012 или более поздних операционных систем. Для этих компьютеров можно использовать [командлеты управления TPM для Windows PowerShell](https://docs.microsoft.com/powershell/module/trustedplatformmodule/).
> Если эта команда используется на компьютере под Windows 7 или Windows Server 2008, можно по-прежнему настроить доверенный платформенный модуль (TPM) компьютера (TPM) с помощью этой команды. Примеры использования этой команды см. в разделе [примеры](#BKMK_Examples).
> ## <a name="syntax"></a>Синтаксис
> ```
> manage-bde -tpm [-turnon] [-takeownership <OwnerPassword>] [-computername <Name>] [{-?|/?}] [{-help|-h}]
> ```
> ### <a name="parameters"></a>Параметры
> 
> |    Параметр    |                                                                              Описание                                                                               |
> |-----------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
> |     -Турнон     |              Включает и активирует доверенный платформенный модуль, позволяя задать пароль владельца доверенного платформенного модуля. Можно также использовать **-t** в качестве сокращенной версии этой команды.              |
> | -такеовнершип  |                      Получает владение доверенным платформенным модулем, задавая пароль владельца. Можно также использовать параметр **-o** в качестве сокращенной версии этой команды.                       |
> | <OwnerPassword> |                                                      Представляет пароль владельца, указанный для доверенного платформенного модуля.                                                       |
> |  -ComputerName  | Указывает, что Manage-bde. exe будет использоваться для изменения защиты BitLocker на другом компьютере. Можно также использовать параметр **-CN** в качестве сокращенной версии этой команды. |
> |     <Name>      |    Представляет имя компьютера, на котором необходимо изменить защиту BitLocker. Допустимые значения включают имя NetBIOS компьютера и IP-адрес компьютера.     |
> |    -? или/?     |                                                               Отображает краткую справку в командной строке.                                                               |
> |   -Help или-h   |                                                             Отображает полную справку в командной строке.                                                              |
> 
> ## <a name="BKMK_Examples"></a>Примеров
> В следующем примере показано использование команды **-TPM** для включения доверенного платформенного модуля.
> ```
> manage-bde  tpm -turnon
> ```
> В следующем примере показано, как использовать команду **TPM** , чтобы стать владельцем TPM и установить пароль владельца 0wnerP@ss.
> ```
> manage-bde  tpm  takeownership 0wnerP@ss
> ```
> ## <a name="additional-references"></a>Дополнительные ссылки
> -   [Условные обозначения синтаксиса команд командной строки](command-line-syntax-key.md)
> -   [manage-bde](manage-bde.md)
