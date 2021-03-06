---
title: Расширения для Windows Admin Center
description: Расширения для пакета SDK Windows Admin Center (Project Honolulu)
ms.technology: extend
ms.topic: article
author: daniellee-msft
ms.author: jol
ms.date: 09/17/2018
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: ee8c0203be25b30f173b1887de506844d5b58738
ms.sourcegitcommit: 6aff3d88ff22ea141a6ea6572a5ad8dd6321f199
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/27/2019
ms.locfileid: "71406917"
---
# <a name="extensions-for-windows-admin-center"></a>Расширения для Windows Admin Center

>Область применения. Windows Admin Center, ознакомительная версия Windows Admin Center

Windows Admin Center — это расширяемая платформа, предоставляющая партнерам и разработчикам возможность использовать имеющиеся средства Windows Admin Center. Ее удобно интегрировать с другими продуктами и решениями для ИТ-администрирования, получая за счет этого дополнительные преимущества. Каждое решение и средство в Windows Admin Center разработано в виде расширения с помощью тех же возможностей расширяемости, которые доступны партнерам и разработчикам, поэтому вы можете создавать мощные инструменты, аналогичные тем, которые доступны в настоящий момент в Windows Admin Center.

Расширения Windows Admin Center созданы с использованием современных веб-технологий, включая HTML5, CSS, Angular, TypeScript и jQuery, и платформа может осуществлять управление целевыми серверами через PowerShell или инструментарий WMI. Также управлять целевыми серверами, службами или устройствами можно через различные протоколы, например REST, путем создания подключаемого модуля шлюза для Windows Admin Center.

## <a name="why-you-should-consider-developing-an-extension-for-windows-admin-center"></a>Преимущества разработки расширений для Windows Admin Center

Ниже приведено значение, которое можно перенести в продукт и клиентов путем разработки расширений для центра администрирования Windows.

- **Интеграция с инструментами центра администрирования Windows:** Интегрируйте свои продукты и службы с помощью средств управления сервером и кластером в центре администрирования Windows, а также единым и простым в управлении, комплексным средствам мониторинга, устранением неполадок для клиентов.
- **Используйте средства обеспечения безопасности платформы, идентификации и управления:** Включите поддержку Azure Active Directory (AAD), многофакторную идентификацию, управление доступом на основе ролей (RBAC), ведение журнала, аудит для вашего продукта и служб, используя возможности платформы центра администрирования Windows для удовлетворения сложных требований современных ИТ – организации.
- **Разработка с использованием новейших веб-технологий:** Быстро создавайте привлекательные пользовательские интерфейсы с помощью современных веб-технологий, включая HTML5, CSS, угловые, TypeScript и jQuery, а также широкие мощные элементы управления пользовательского интерфейса, включенные в пакет SDK для Windows Admin Center.
- **Увеличение доступности продуктов:** Станьте участником новой экосистемы центра администрирования Windows, чтобы получить доступ к нашему быстро растущему клиентской базе и использовать время запуска Windows Server 2019 позднее в этом году.

## <a name="start-developing-with-the-windows-admin-center-sdk"></a>Начало разработки с помощью пакета SDK центра администрирования Windows

Начать работу с разработкой в центре администрирования Windows очень просто!  Пример кода можно найти для типов расширений [подключаемого модуля](develop-gateway-plugin.md) [средства](develop-tool.md), [решения](develop-solution.md)и шлюза в документации по пакету SDK. Вы будете использовать интерфейс командной строки центра администрирования Windows для создания нового проекта расширения, а затем следуйте индивидуальным руководствам по настройке проекта в соответствии с вашими потребностями.

Мы предоставили [набор SDK](https://github.com/Microsoft/windows-admin-center-sdk/blob/master/WindowsAdminCenterDesignToolkit.zip) для Windows Admin Center, который поможет быстро проектировать расширения в PowerPoint с помощью стилей, элементов управления и шаблонов страниц в центре администрирования Windows. Прежде чем приступить к написанию кода, посмотрите, как ваше расширение будет выглядеть в центре администрирования Windows!

Мы также добавили пример кода, размещенного на GitHub: [Средства для разработчиков](https://aka.ms/wacsdk) — это пример расширения решения, содержащего обширную коллекцию элементов управления, которые можно просматривать и использовать в собственном расширении. Средства разработчика — это полнофункциональное расширение, которое можно без публикации загрузить в Windows Admin Center в режиме разработчика.

См. разделы ниже, чтобы узнать больше о пакете SDK и о том, как приступить к работе.

- [Узнайте, как работают расширения](understand-extensions.md)
- [Разработка расширения](developing-extensions.md)
- [Рекомендации](guides.md)
- [Публикация расширения](publish-extensions.md)

## <a name="partner-spotlight"></a>Интересное из опыта партнеров

Ознакомьтесь с проектами наших партнеров из экосистемы Windows Admin Center и оцените их возможности. Узнайте, [как устанавливать расширения](../configure/using-extensions.md) из Windows Admin Center.

### <a name="biitops"></a>биитопс
Расширение Биитопс Changes обеспечивает отслеживание изменений оборудования, программного обеспечения и параметров конфигурации на физических и виртуальных машинах Windows Server. Расширение Биитопс changes будет точно показывать новые возможности, что изменилось и что было удалено в одной панели, чтобы помочь в отслеживании проблем, связанных с соответствием, надежностью и безопасностью. Дополнительные [сведения о расширении Биитопс Changes](case-studies/biitops.md).

![Расширение Биитопс](../media/extensibility-overview/biitops-1.png)

### <a name="dataon"></a>DataON

Расширение Датаон должно переносит мониторинг, управление и полное представление о инфраструктуре и системах хранения с технологией Датаон, основанной на Windows Server. Расширение должно добавлять уникальные значения, такие как отчеты с предысторией данных, сопоставление дисков, системные оповещения и служба домашнего вызова по сети SAN, дополняющие сервер центра администрирования Windows и возможности управления инфраструктурой, реализованные с помощью технологии Hyper-конвергенции, посредством простого единый интерфейс. [Узнайте больше о расширении MUST от DataON и их опыте разработки](case-studies/dataon.md).

![Расширение DataON MUST](../media/extensibility-overview/dataon-must-extension.png)

### <a name="fujitsu"></a>Fujitsu

Расширения работоспособности Сервервиев и работоспособности RAID для центра администрирования Windows компании Fujitsu предоставляют подробные сведения о мониторинге и управлении критически важными компонентами оборудования, такими как процессоры, память, подсистемы питания и хранилища для серверов Fujitsu ПРИМЕРГИ. Используя шаблоны дизайна пользовательского интерфейса Windows Admin Center и элементы управления пользовательского интерфейса компания Fujitsu сделала огромный шаг вперед на пути к формированию концепции комплексного мониторинга серверных ролей и служб, а также управления операционной системой и оборудованием с помощью платформы Windows Admin Center. [Узнайте больше о расширениях компании Fujitsu и их опыте разработки](case-studies/fujitsu.md).

![Расширение Fujitsu ServerView](../media/extensibility-overview/fujitsu-serverview-extension.png)

### <a name="lenovo"></a>Lenovo

Расширение Lenovo Кскларити Integrator обеспечивает управление оборудованием на следующий уровень благодаря тесной интеграции с различными возможностями в центре администрирования Windows. Решение Кскларити Integrator обеспечивает общее представление всех серверов Lenovo, а различные расширения инструментов предоставляют сведения об оборудовании при подключении к одному серверу, отказоустойчивому кластеру или кластеру с поддержкой Hyper-in. Дополнительные [сведения о расширении Lenovo Кскларити Integrator](case-studies/lenovo.md).

![Расширение Lenovo](../media/extensibility-overview/lenovo-extension.png)

### <a name="pure-storage"></a>Pure Storage

В чистом хранилище реализованы все решения для хранения данных на основе флэш-памяти, обеспечивающие архитектуру, ориентированную на данные, для ускорения бизнеса с учетом конкурентного преимущества. Расширение чистого хранилища для центра администрирования Windows предоставляет одностраничное представление для чистого Флашаррай продуктов и дает пользователям возможность выполнять задачи мониторинга, просматривать метрики производительности в режиме реального времени, а также управлять томами и инициаторами хранилища с помощью одного пользовательского интерфейса. удобной. [Дополнительные сведения о расширениях чистого модуля и их опыте разработки](case-studies/purestorage.md).

![Расширение чистого хранилища](../media/extensibility-overview/purestorage-extension.png)

### <a name="qct"></a>ККТ

Расширение ККТ Management Suite дополняет центр администрирования Windows, обеспечивая мониторинг физического сервера и управление для сертифицированных систем ККТ Azure Stack ХЦИ. Расширение ККТ Management Suite отображает сведения об оборудовании сервера и предоставляет интуитивно понятный пользовательский интерфейс мастера для эффективного замены физических дисков, средств журнала событий оборудования и S.M.A.R.T. Управление прогнозируемыми дисками на основе. Дополнительные [сведения о расширении ККТ Management Suite](case-studies/qct.md).

![Расширение ККТ](../media/extensibility-overview/qct-extension.png)

### <a name="squared-up"></a>Squared Up

Squared Up предоставляет лучшие в своем классе возможности мониторинга на основе продукта System Center Operations Manager и интеграции со службы Log Analytics в Azure, Application Insights и другими решениями для мониторинга. [Расширение Squared Up](https://squaredup.com/product/honolulu/windows-admin-center-extension/?utm_source=microsoft-docs&utm_medium=public-relations&utm_campaign=honolulu) согласует исторические данные о производительности и активные топологии приложений и их зависимости с контекстом администрирования сервера и кластера, предоставляемым Windows Admin Center, и первые пользователи уже оценили по достоинству возможность работать с огромными объемами данных из большого количества разных источников в одном интерфейсе. [Узнайте больше о расширении Squared Up и их опыте разработки](case-studies/squared-up.md).

![Расширение Squared Up](../media/extensibility-overview/squaredup-extension.png)