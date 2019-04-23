---
title: Общие сведения о Windows Admin Center
description: Сведения об управлении Windows Server с помощью Windows Admin Center (Project Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.localizationpriority: high
ms.prod: windows-server-threshold
ms.openlocfilehash: e23d02fd8da96392f44874ad6ea4d6c40e2be940
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59828205"
---
# <a name="windows-admin-center"></a>Windows Admin Center

>Область применения. Windows Admin Center, предварительная версия Windows Admin Center

Добро пожаловать в Windows Admin Center!

**Windows Admin Center** (под кодовым названием **Гонолулу проекта**) является результатом эволюционного развития средств управления, входящие в комплект Windows Server; он является единой панели, объединяющий все аспекты управления локальным и удаленным сервером. Так как платформа развертывается локально, а в качестве интерфейса управления используется браузер, подключение к Интернету и Azure не требуются. Windows Admin Center предоставляет полный контроль над всеми аспектами вашего развертывания, включая частные сети, не подключенные к Интернету.

## <a name="introduction"></a>Введение

>[!VIDEO https://www.youtube.com/embed/PcQj6ZklmK0]

![Информационная схема по Windows Admin Center](media/WAC1809Poster_thumb.PNG)

[Скачать PDF-ФАЙЛ](https://github.com/MicrosoftDocs/windowsserverdocs/raw/master/WindowsServerDocs/manage/windows-admin-center/media/WindowsAdminCenter1809Poster.pdf)

## <a name="quick-start"></a>Быстрый запуск

Windows Admin Center можно подготовить к работе и запустить в вашей среде за считаные минуты.

1. [Скачать](https://aka.ms/windowsadmincenter)
2. [Установить](deploy/install.md)
3. [Начало работы](use/get-started.md)

## <a name="contents-at-a-glance"></a>Содержимое с одного взгляда

<table>
    <tr></tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Общие сведения</h3>
            <ul>
            <li><a href="understand/what-is.md">Что такое Windows Admin Center?</a>
            <li><a href="understand/faq.md">ВОПРОСЫ И ОТВЕТЫ</a>
            <li><a href="understand/case-studies.md">Примеры внедрения</a>
            <li><a href="understand/related-management.md">Продукты управления</a>
            <li><a href="understand/videos.md">Видео</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Планирование</h3>
            <ul>
            <li><a href="plan/installation-options.md">Какой тип установки подходит для вас?</a>
            <li><a href="plan/user-access-options.md">Параметры доступа пользователей</a>
            <li><a href="plan/azure-integration-options.md">Существуют ли какие варианты интеграции Azure?</a>
            <br>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Развертывание</h3>
            <ul>
            <li><a href="deploy/prepare-environment.md">Подготовка среды</a>
            <li><a href="deploy/install.md">Установка Windows Admin Center</a>
            <li><a href="deploy/high-availability.md">Включить высокую доступность</a>
         </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Настройка</h3>
            <ul>
            <li><a href="configure/settings.md">Параметры Windows Admin Center</a>
            <li><a href="configure/user-access-control.md">Управление доступом пользователей и разрешения</a>
            <li><a href="configure/using-extensions.md">Расширения</a>
            <li><a href="configure/azure-integration.md">Интеграция с Azure</a>
            <li><a href="configure/manage-azure-vms.md">Управление виртуальными машинами Azure с помощью Windows Admin Center</a>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: top;">
            <h3>Используйте</h3>
            <ul>
            <li><a href="use/get-started.md">& Запустить добавление подключений</a>
            <li><a href="use/manage-servers.md">Управление серверами</a>
            <li><a href="use/manage-hyper-converged.md">Управление гиперконвергентная инфраструктура</a>
            <li><a href="use/manage-failover-clusters.md">Управления отказоустойчивыми кластерами</a>
            <li><a href="use/manage-virtual-machines.md">Управление виртуальными машинами</a>
            <li><a href="use/azure-services.md">Использовать службы Azure</a>
            <li><a href="use/troubleshooting.md">Общие действия по устранению неполадок</a>
            <li><a href="use/logging.md">Ведение журнала</a>
            <li><a href="use/known-issues.md">Известные проблемы</a>
            </ul>
        </td>
        <td style="vertical-align: top;">
            <h3>Расширение</h3>
            <ul>
            <li><a href="extend/extensibility-overview.md">Общие сведения о модулях</a>
            <li><a href="extend/understand-extensions.md">Основные сведения о расширения</a>
            <li><a href="extend/developing-extensions.md">Разработка расширения</a>
            <li><a href="extend/publish-extensions.md">Направляющие</a>
            <li><a href="extend/publish-extensions.md">Публикация расширений</a>
            </ul>
        </td>
    </tr>

</table>

## <a name="release-history"></a>История выпусков

Узнайте о наших последних выпущенных функциях:

- Версии [1902] (https://aka.ms/wac1902) добавлен в список общих соединений и улучшения управления программно-определяемой сети (SDN), включая новые средства SDN для управления списки управления доступом, подключений шлюза и логических сетей.
- В версию [1812](https://aka.ms/wac1812) добавлена темная тема (бета-версия), параметры настройки питания, сведения о BMC, а также поддержка PowerShell для управления [расширениями](./configure/using-extensions.md#manage-extensions-with-powershell) и [подключениями](./use/get-started.md#use-powershell-to-import-or-export-your-connections-with-tags).
- Версия [1809.5](https://aka.ms/wac1809.5) представляет собой официальное накопительное обновление, в состав которого входят различные улучшения качества и компонентов, в том числе исправления ошибок в работе платформы, а также несколько новых функций в решении по управлению гиперконвергентной инфраструктурой.
- Версия [1809](https://cloudblogs.microsoft.com/windowsserver/2018/09/20/windows-admin-center-1809-and-sdk-now-generally-available/) представляла собой официальный выпуск с функциями, которые ранее были доступны только в ознакомительной версии.
- В версию [1808](https://aka.ms/WACPreview1808-InsiderBlog) были добавлены средство "Установленные приложения", множество улучшений системного уровня, а также основные обновления ознакомительной версии пакета SDK.
- В версию [1807](https://aka.ms/WACPreview1807-InsiderBlog) были добавлены оптимизация подключения к Azure, улучшена страница инвентаризации виртуальных машин, добавлена функция обмена данными, интеграция управления обновлениями Azure и др. 
- В версию [1806](https://aka.ms/WACPreview1806-InsiderBlog) были добавлены сценарий "Отобразить PowerShell", управление SDN, подключения 2008 R2, SDN, возможность планирования заданий и множество других улучшений.
- Версия 1804.25 — пакет обновления для реализации поддержки пользователей, устанавливающих Windows Admin Center в полностью автономных средах.
- Версия [1804](https://cloudblogs.microsoft.com/windowsserver/2018/04/12/announcing-windows-admin-center-our-reimagined-management-experience/) — Project Honolulu меняет название на Windows Admin Center. Вместе с этим добавлены функции обеспечения безопасности и управления доступом на основе ролей. Наш первый официальный выпуск.
- Версия [1803](https://blogs.windows.com/windowsexperience/2018/03/13/announcing-project-honolulu-technical-preview-1803-and-rsat-insider-preview-for-windows-10) — добавлена поддержка управления доступом Azure AD, подробного ведения журнала, изменения размера содержимого и ряд улучшений средств.
- Версия [1802](https://blogs.windows.com/windowsexperience/2018/02/13/announcing-windows-server-insider-preview-build-17093-project-honolulu-technical-preview-1802) — добавлена поддержка специальных возможностей, локализации, развертываний с высокой степенью доступности, тегов, параметров узла Hyper-V и проверки подлинности шлюза.
- Версия [1712](https://blogs.windows.com/windowsexperience/2017/12/19/announcing-project-honolulu-technical-preview-1712-build-05002) —добавлены дополнительные функции виртуальных машин и улучшена производительность всех средств.
- Версия [1711](https://cloudblogs.microsoft.com/windowsserver/2017/12/01/1711-update-to-project-honolulu-technical-preview-is-now-available/) — добавлены долгожданные средства ("Удаленный рабочий стол" и PowerShell) наряду с другими улучшениями.
- Версия [1709](https://cloudblogs.microsoft.com/windowsserver/2017/09/22/project-honolulu-technical-preview-is-now-available-for-download/) — была выпущена в качестве нашего первого общедоступного предварительного выпуска.

## <a name="stay-updated"></a>Обновлять

<a target="_blank" class="mscom-link twitter-follow-link" title="Следите за нашими новостями в Twitter" aria-label="Follow us on Twitter" data-info="Twitter" href="https://twitter.com/servermgmt"><picture><source srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR" media="(min-width:0)"><img srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR" alt="Follow us on Twitter" src="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOolR"></picture></a>
 | 
<a target="_blank" class="mscom-link blogs-follow-link" title="Читайте наши блоги" aria-label="Visit our Blogs" data-info="Blogs" href="https://blogs.technet.microsoft.com/servermanagement/"><picture><source srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw" media="(min-width:0)"><img srcset="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw" alt="Follow us on Blogs" src="//img-prod-cms-rt-microsoft-com.akamaized.net/cms/api/am/imageFileData/REOtyw"></picture></a>