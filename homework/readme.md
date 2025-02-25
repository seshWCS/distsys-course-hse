# Домашние задания

Здесь находятся домашние задания по курсу. Если вы будете сдавать решения, прочитайте внимательно текст ниже.

## Настройка личного репозитория

Для решения и сдачи заданий вам надо будет создать (один раз) **приватный** fork репозитория курса. Сделать это по кнопке Fork в интерфейсе GitHub не получится - будет создан публичный репозиторий, и сделать его приватным вы уже не сможете. Поэтому следуйте инструкции ниже:

1. Создайте свой личный **приватный** репозиторий на GitHub (далее будем считать, что его имя `distsys-course-work`), репозиторий должен быть пустой.

2. Сделайте bare clone репозитория курса (в любой папке, после этого шага ее можно удалить) и скопируйте полученный клон в ваш личный репозиторий:

```
git clone --bare git@github.com:osukhoroslov/distsys-course-hse.git
cd distsys-course-hse.git
git push --mirror git@github.com:<your_username>/distsys-course-work.git
```

3. Откройте личный репозиторий в веб-интерфейсе GitHub, убедитесь что в нем появилось содержимое репозитория курса. Перейдите в настройки и установите ветку `2023` веткой по умолчанию (Settings / Default branch). Также выдайте доступ к репозиторию системному пользователю `hse-dist` ([инструкция](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-personal-account-on-github/managing-access-to-your-personal-repositories/inviting-collaborators-to-a-personal-repository)).

4. Скачайте к себе личный репозиторий и настройте синхронизацию с репозиторием курса:

```
git clone git@github.com:<your_username>/distsys-course-work.git
cd distsys-course-work
git remote add upstream git@github.com:osukhoroslov/distsys-course-hse.git
```

Ваш личный репозиторий готов к работе.

## Синхронизация личного репозитория

По ходу курса вам надо будет регулярно синхронизовать содержимое вашего личного репозитория с репозиторием курса. Например, при публикации и обновлении домашних заданий или других материалов. Делается это с помощью команд:

```
git fetch upstream
git checkout 2023
git rebase upstream/2023
```

Старайтесь не изменять без необходимости файлы из родительского репозитория. Обычно вам будет достаточно создавать или редактировать файлы с решением задания. Это позволит избежать конфликтов при синхронизации.

## Решение и сдача задания

1. Создайте ветку, в который вы будете работать над решением задания, например:

```
git checkout -b 01-guarantees
```

2. Напишите код решения и протестируйте его локально по инструкции в задании.

3. Запушите код решения в ветку:

```
git push origin
```

4. Создайте pull request (PR) из ветки задания в ветку `2023` вашего репозитория. 

5. Внутри PR должен будет запуститься CI с тестами задания. Если они не проходят, то доработайте решение (шаги 2-3) так, чтобы статус CI стал зеленым.

6. **До дедлайна** сдайте ссылку на PR в соответствующее задание в Canvas.

7. В ходе проверки задания проверяющий может оставлять замечания в вашем PR. По завершению проверки вмержите PR.
