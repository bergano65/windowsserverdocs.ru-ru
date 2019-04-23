<properties pageTitle="Команды Git для создания новой статьи или обновления существующей статьи" description="Шаги для создания и обновления статьи в WindowsServerDocs-pr." metaKeywords="" services="" solutions="" documentationCenter="" authors="Kathy Davies" videoId="" scriptId="" manager="dongill" />

<tags ms.service="contributor-guide" ms.devlang="" ms.topic="article" ms.tgt_pltfrm="" ms.workload="" ms.date="08/24/16" ms.author="kathydav" />

# <a name="git-commands-to-create-or-update-an-article"></a>Команды Git, чтобы создать или обновить статью

>! ПРИМЕЧАНИЕ. Эти команды предполагают вы настроили Github, чтобы указать, где извлекать файлы из репозитория по умолчанию. В Github — терминология, где вы извлечь файлы из вашего *вышестоящего*. Где вы отправляете файлы — ваш *origin*. На основании как наш репозиторий и рабочий процесс разработаны, ваш вышестоящего должно быть присвоено наш репозиторий, которая находится в стадии корпорации Майкрософт - https://github.com/Microsoft/WindowsServerDocs-pr и своем сервере-источнике должно быть в вилку этого репозитория, в свою учетную запись Github. Например в Kathy — https://github.com/KBDAzure/WindowsServerDocs-pr 

>Чтобы проверить параметры, введите ```git config -l```. Взгляните на URL-адреса, чтобы убедиться в том, что они ссылаются на расположение, предназначенные.

## <a name="add-or-update-an-article"></a>Добавить или обновить статью

Вот как можно создать локальную ветвь, сохраните изменения и затем отправьте их в удаленной вилке.

1. Запустите Git Bash (или средство командной строки, используемой для Git).

2. Измените WindowsServerDocs-pr.

        cd WindowsServerDocs-pr

3. Лучше всего оставить локальной главной ветви и удаленной главной ветви в вилке синхронизирован с главного репозитория. Это может помочь вам сэкономить массу разочарование и потери времени--вы скорее выявление проблем на ранней стадии и хранить все данные в рабочем состоянии использовать хорошие и известные. Выполните:

        git checkout master
        git pull upstream master
        git push origin master

4. Теперь вы готовы создать ветвь для выполнения вашей ежедневной или конечный результат на основе работать. Чтобы создать локальную рабочую ветвь из ветви выпуска рекомендуется использовать для выполнения:

        git checkout upstream/upstream-branch-name -b your-local-branch-name

   Это создает локальную ветвь непосредственно из вышестоящей ветви и помогает избежать слияния неправильных файлов в новой локальной ветви. Например для создание рабочей ветви ветви пороговое значение общедоступной версии, можно выполнить следующую команду:
      
        git checkout upstream/master -b working-11-18

   Если вы работаете на содержимое, которое должен быть объединен в ветвь, которая не является         

5. Добавьте локальную рабочую ветвь в вилку:

        git push origin <working branch>

6. Создайте статью или внесите изменения в существующую статью. Откройте файлы markdown и markdown editor для создания и редактирования файлов с помощью проводника Windows. Основную информацию форматирования, см. в этом [статье](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/) в Github.

7. Добавьте необходимые метаданные и сведения о версии, согласно [управление версиями метаданных и продукта](metadata-OSversioning-and-trademarks.md).

8. Проверка состояния, а затем добавьте и зафиксируйте изменения:

        git status

   Просмотрите результаты, чтобы убедиться в том, список файлов, которые были изменены. Если правильные файлы, выполните следующую команду, чтобы добавить все файлы:

        git add .
        git commit –m "<comment>"

   Чтобы добавить только определенные файлы (например, в том случае, если ```git status``` перечислены файлы, которые вы не хотите отправить), вместо этого необходимо запустить:

        git add <file path>
        git commit –m "<comment>"

   >[!IMPORTANT]
   >Команда ```git add .``` добавляет все ожидающие изменения, о которых сообщает ```git status```. Это означает, что если ```git status``` Нетрассируемые обновления, которые вы не хотите добавить, используйте ```git add <file path>``` вместо этого.  

9. Обновление локальной рабочей ветви с изменениями из восходящего источника:

        git pull upstream master

10. Отправьте изменения в разветвление на GitHub:

        git push origin <working branch>

## <a name="submit-your-changes"></a>Отправить изменения

Когда вы будете готовы отправить содержимое для промежуточного хранения, проверки и/или публикации, используйте пользовательский Интерфейс GitHub для создания запроса на включение внесенных изменений. 

При открытии запроса на Вытягивание (PR), это инициирует тестового прохода, выполняет сборку проекта и публикует нашей внутренней промежуточный сайт. Допустимо открыть запрос на включение внесенных изменений, который вы еще не готовы слияние, так как это, как получить тестовый проход и проверьте изменения на промежуточном сайте. Подробные сведения о построении и такими ссылками учитываются как комментарии для PR. 

Это необходимо выполнить следующие **перед требуется объединить изменения**:
  - Просмотрите сборки подробно, чтобы убедиться в том, что он не содержит ошибок. 
  - Просмотрите изменения на промежуточном сайте.

После этого, что означает, что с помощью:
- Добавление метки «все готово к слиянию» PR. \(Нажмите кнопку **метки** или значок шестеренки справа от потока комментариев в PR.)
- Добавление все готово к слиянию как комментарий и отправлять по электронной почте на включение внесенных изменений рецензенты WSSC псевдоним: адреса pra wssc

Проверяет изменения рецензентом запросов на Вытягивание и принимает запрос на Вытягивание, если есть вопросы или проблемы. Отзывы и запросы для устранения проблем, добавляются как комментарии. Просмотрите [критерии качества для по запросу запросить проверку](contributor-guide-pr-criteria.md) дополнительные поведения, ожидаемого.

## <a name="publishing"></a>Publishing (Выполняется публикация)

- Статьях, опубликованных в около 10:00 до 15:00 по тихоокеанскому времени, с понедельника по пятницу. Имейте в виду, что рецензент запросов на Вытягивание требуется время, чтобы просмотреть и принять изменения, прежде чем они могут объединять. Чтобы быть учтены в следующем запланированном цикле публикации необходимо выполнить слияние изменений. Если вам нужна статьи, опубликованной для конкретной публикации цикла, позвольте знать заранее, проверяющий запрос на включение внесенных изменений. Когда принимается запрос на Вытягивание, изменения объединяются в репозиторий и будут включены в следующей публикации времени выполнения. Может занять до 30 минут для отображение статьей в Интернете после публикации. 