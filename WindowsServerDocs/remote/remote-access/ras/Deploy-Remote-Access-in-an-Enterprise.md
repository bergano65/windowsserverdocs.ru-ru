---
title: Развертывание удаленного доступа на предприятии
description: В этом разделе приводятся общие сведения о сценарии DirectAccess в Windows Server 2016 для предприятия.
manager: brianlic
ms.custom: na
ms.prod: windows-server
ms.reviewer: na
ms.suite: na
ms.technology: networking-ras
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4781df0a-158b-4562-b8f5-32b27615a4f8
ms.author: pashort
author: shortpatti
ms.openlocfilehash: 1ab337da85387be8c7d960315bb28644fa3a8a93
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71367499"
---
# <a name="deploy-remote-access-in-an-enterprise"></a>Развертывание удаленного доступа на предприятии

>Область применения. Windows Server (Semi-Annual Channel), Windows Server 2016

В этом разделе содержатся вводные сведения о реализации сценария DirectAccess на предприятии.  
  
  
> [!IMPORTANT]  
> Для развертывания DirectAccess с помощью этого руководством необходимо использовать сервер DirectAccess под Windows Server 2016, Windows Server 2012 R2 или Windows Server 2012.  
  
## <a name="before-you-begin-deploying-see-the-list-of-unsupported-configurations-known-issues-and-prerequisites"></a>Перед началом развертывания ознакомьтесь со списком неподдерживаемых конфигураций, известных проблем и предварительных условий.  
  
-   [Неподдерживаемые конфигурации DirectAccess](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/directaccess-unsupported-configurations)  
  
-   [DirectAccess — известные проблемы](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/directaccess-known-issues)  
  
-   [Предварительные требования для развертывания DirectAccess)](https://technet.microsoft.com/windows-server-docs/networking/remote-access/directaccess/prerequisites-for-deploying-directaccess)  
  
## <a name="BKMK_OVER"></a>Описание сценария  
Компонент удаленного доступа включает несколько функций для предприятий, в том числе: развертывание нескольких серверов удаленного доступа в кластере с балансировкой нагрузки при помощи компонента балансировки сетевой нагрузки Windows (NLB) или внешней подсистемы балансировки нагрузки; настройка мультисайтовых развертываний с серверами удаленного доступа, которые находятся в различных географических расположениях; развертывание DirectAccess с двухфакторной аутентификацией клиента с использованием одноразовых паролей (OTP).  
  
## <a name="in-this-scenario"></a>Содержание сценария  
Каждый корпоративный сценарий описывается в документе, который содержит инструкции по планированию и развертыванию. Дополнительные сведения см. в следующих разделах:  
  
-   [Развертывание удаленного доступа в кластере](cluster/Deploy-Remote-Access-In-Cluster.md)  
  
-   [Развертывание нескольких серверов удаленного доступа в многосайтовом развертывании](multisite/Deploy-Multiple-Remote-Access-Servers-in-a-Multisite-Deployment.md)  
  
-   [Развертывание удаленного доступа с проверкой подлинности методом OTP](otp/Deploy-RA-OTP.md)  
  
-   [Развертывание удаленного доступа в среде с несколькими лесами](multi-forest/Deploy-Remote-Access-in-a-Multi-Forest-Environment.md)  
  
## <a name="BKMK_APP"></a>Практические приложения  
Корпоративные сценарии удаленного доступа предоставляют следующие преимущества.  
  
-   **Повышенная доступность**. Развертывание нескольких серверов удаленного доступа в кластере обеспечивает масштабируемость и увеличивает емкость для пропускной способности и количества пользователей. Балансировка нагрузки кластера обеспечивает высокую доступность. Если происходит отказ одного из серверов в кластере, то удаленные пользователи могут сохранить доступ к внутренней корпоративной сети через другой сервер в кластере. Обработка отказа происходит прозрачно для пользователей, поскольку клиенты подключаются к кластеру при помощи виртуальных IP-адресов.  
  
-   **Простота управления**. Развертывание кластера или многосайтового развертывания можно настроить и управлять как единым объектом с помощью консоли управления удаленным доступом, работающей на одном из серверов кластера. Кроме того, мультисайтовое развертывание позволяет администраторам согласовать конфигурацию развертывания удаленного доступа и узлы Active Directory для создания упрощенной архитектуры. На всех серверах кластера или мультисайтовой точки входа можно легко установить общие параметры. Управление параметрами удаленного доступа можно осуществлять только с использованием одного из серверов в кластере или развертывании либо удаленно при помощи средств удаленного администрирования сервера. Кроме того, наблюдение за всем кластером или мультисайтовым развертыванием можно осуществлять с одной консоли управления удаленным доступом.  
  
-   **Экономичность**. Многосайтовое развертывание с удаленным доступом позволяет предприятиям развертывать серверы удаленного доступа на нескольких сайтах, соответствующих расположениям клиентов. Благодаря этому удаленным клиентам предоставляется предсказуемый механизм взаимодействия независимо от их расположения, снижаются затраты и степень использования пропускной способности интрасети за счет маршрутизации трафика клиента через Интернет на ближайший сервер удаленного доступа.  
  
-   **Безопасность.** Развертывание надежной проверки подлинности клиента с одноразовым паролем (OTP) вместо стандартного Active Directory пароля повышает безопасность.  
  
## <a name="BKMK_NEW"></a>Роли и компоненты, входящие в этот сценарий  
В следующей таблице перечислены роли и компоненты, необходимые для корпоративного сценария.  
  
|Роль/компонент|Способ поддержки сценария|  
|---------|-----------------|  
|Роль сервера удаленного доступа|Эта роль устанавливается и удаляется с помощью консоли Диспетчера серверов. Эта роль включает как DirectAccess, который раньше был компонентом Windows Server 2008 R2, так и службы маршрутизации и удаленного доступа, которые были службой роли в рамках роли сервера служб политики сети и доступа (NPAS). Роль удаленного доступа включает два компонента.<br /><br />1.  VPN-подключения DirectAccess и службы маршрутизации и удаленного доступа (RRAS) управляются вместе в консоли управления удаленным доступом.<br />2.  Маршрутизация RRAS. Управление функциями маршрутизации RRAS осуществляется с помощью устаревшей консоли маршрутизации и удаленного доступа.<br /><br />Роль сервера удаленного доступа зависит от следующих компонентов сервера.<br /><br />-Службы IIS (IIS). Эта функция необходима для настройки сервера сетевых расположений и веб-проверки по умолчанию.<br />-Функция консоль управления групповыми политиками требуется компоненту DirectAccess для создания объектов GPO и управления групповая политика ими в Active Directory и должен быть установлен в качестве обязательной функции для роли сервера.|  
|Средства управления удаленным доступом|Этот компонент устанавливается описанным ниже образом.<br /><br />— Он устанавливается по умолчанию на сервере удаленного доступа при установке роли удаленного доступа и поддерживает пользовательский интерфейс консоли удаленного управления.<br />— Его можно дополнительно установить на сервере, на котором не запущена роль сервера удаленного доступа. В этом случае компонент используется для удаленного управления компьютером с возможностью удаленного доступа, на котором установлены DirectAccess и VPN.<br /><br />Средства управления удаленным доступом включают следующие элементы:<br /><br />1.  графический интерфейс пользователя удаленного доступа и программы командной строки;<br />2.  модуль удаленного доступа для Windows PowerShell.<br /><br />Зависимости включают следующее:<br /><br />1.  Консоль управления групповыми политиками<br />2.  пакет администрирования диспетчера RAS-подключений (CMAK);<br />3.  Windows PowerShell 3.0<br />4.  графические средства управления и инфраструктура.|  
|Компонент балансировки нагрузки Windows (NLB)|Данный компонент позволяет сбалансировать нагрузку между несколькими серверами удаленного доступа.|  
  

  


