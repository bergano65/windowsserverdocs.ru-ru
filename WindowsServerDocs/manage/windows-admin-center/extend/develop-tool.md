---
title: Разработка расширения средства
description: Разработка расширения средства Windows Admin Center SDK (проект Honolulu)
ms.technology: manage
ms.topic: article
author: nwashburn-ms
ms.author: niwashbu
ms.date: 09/18/2018
ms.localizationpriority: medium
ms.prod: windows-server-threshold
ms.openlocfilehash: 7dd213f7032ab77021bbfcbdc966c9c2307b86eb
ms.sourcegitcommit: be0144eb59daf3269bebea93cb1c467d67e2d2f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/20/2018
ms.locfileid: "4081061"
---
# Разработка расширения средства

>Относится к: Windows Admin Center, ознакомительная версия Windows Admin Center

Расширение средства — это основной способ, которым пользователи взаимодействуют с помощью Windows Admin Center для управления подключением, такие как серверу или кластеру. При нажатии на подключение на главной странице Windows Admin Center и подключении, затем появится список средств в левой области навигации. При нажатии на средство расширения средства загрузится и появится в правой области.

При загрузке расширения средства, его можно выполнять вызовы WMI и скрипты PowerShell на целевом сервере или кластере и отображать информацию в пользовательском Интерфейсе или выполнять команды на основании введенных пользователем данных. Средство расширения определяют, какие решения, оно должно отображаться, что приводит к другой набор средств для каждого решения.

> [!NOTE]
> Не знакомы с типами другое расширение? Дополнительные сведения о [расширяемости типы архитектуры и расширение](understand-extensions.md).

## Подготовка среды

Если вы еще не сделали этого, [Подготовьте свою среду](prepare-development-environment.md) , установив зависимостей и глобального компонентов, необходимых для всех проектов.

## Создание нового расширения средства с помощью Windows Admin Center CLI ##

Получив все зависимости, которые устанавливаются, вы готовы создать новое расширение средства.  Создание или перейдите к папке, содержащей файлы проекта, откройте командную строку и задать эту папку в качестве рабочий каталог.  С помощью CLI центра администрирования Windows, который ранее был установлен, создайте новое расширение с помощью следующего синтаксиса:

```
wac create --company "{!Company Name}" --tool "{!Tool Name}"
```

| Значение | Объяснение | Пример. |
| ----- | ----------- | ------- |
| ```{!Company Name}``` | Название компании (с пробелами) | ```Contoso Inc``` |
| ```{!Tool Name}``` | Ваше средство имя (пробелы) | ```Manage Foo Works``` |

Вот пример использования:

```
wac create --company "Contoso Inc" --tool "Manage Foo Works"
```

В результате создается новая папка в текущий рабочий каталог, используя имя для вашего средства, копирует все необходимые шаблона файлы в свой проект и настраивает файлы с именем вашей компании и средства.  

Затем измените каталог в папке только что создали, а затем установите необходимые локальные зависимости, выполнив следующую команду:

```
npm install
```

По завершении этого настройки все необходимые для загрузки нового расширения в Windows Admin Center. 

## Добавление содержимого в расширении

Теперь, когда вы создали расширения с помощью Windows Admin Center CLI, все готово для настройки содержимого.  См. следующие руководства по примеры того, вы можете:

- Добавление [пустой модуль](guides\add-module.md)
- Добавьте [Интернет-кадра](guides\add-iframe.md)
 
Даже Дополнительные примеры можно найти нашем [сайте GitHub SDK](https://aka.ms/wacsdk):
-  [Средства разработчика](https://github.com/Microsoft/windows-admin-center-sdk/tree/master/windows-admin-center-developer-tools) — это полнофункциональное расширение, которое может быть неопубликованным в Windows Admin Center и содержит широкий набор пример функциональных возможностей и примеры средства, которые можно просматривать и использовать в собственном расширении.

## Создание и загрузка расширения

Затем создание и загрузка расширения в Windows Admin Center.  Откройте окно командной строки, измените каталог на каталог источника, а затем все готово для построения.

* Создание и обслуживание с помощью Gulp:

    ```
    gulp build
    gulp serve -p 4201
    ```

Обратите внимание, что необходимо выбрать порт, который в данный момент будет не занят. Убедитесь, что вы не используете порт, на котором работает Windows Admin Center.

Проект можно загрузить в локальный экземпляр Windows Admin Center для тестирования, присоединив локально обслуживаемый проект к Windows Admin Center.

* Запустите Windows Admin Center в веб-браузере
* Откройте отладчик (F12)
* Откройте консоль и введите следующую команду:

    ```
    MsftSme.sideLoad("http://localhost:4201")
    ```

*   Обновите веб-браузер

Теперь проект будет отображаться в списке "Средства" (неопубликованный) рядом с соответствующим именем.

## Выбрать другую версию пакета SDK Windows Admin Center

Поддержание в актуальном состоянии с помощью пакета SDK изменений и платформы расширения очень просто.  Прочитать о том, как [другая версия целевого](target-sdk-version.md) пакета SDK Windows Admin Center.