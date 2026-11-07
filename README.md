# Лабораторная работа №6
## Выполнил: Галимов И.Р.

## Лог команд
```
git config --global user.name "Группа 4515 Галимов И.Р."
git config --global user.email "iskander.6alimov@gmail.com"
git config --global --list
git clone https://github.com/dexhexRU/LR6.git
git pull
git checkout -b feature-branch
git log --oneline
git log --all --oneline --graph --decorate
git show
git branch
git add File11
git commit -m "Изменил File11 в feature-branch"
git checkout master
git add File11
git commit -m "Изменил File11 в master"
git merge feature-branch
git add File11
git commit -m "Разрешен конфликт слияния"
git branch -d feature-branch
echo "Текст 1" > test1.txt
git add .
git commit -m "Добавил первый тестовый файл"
echo "Текст 2" > test2.txt
git add .
git commit -m "Добавил второй тестовый файл"
git revert HEAD
git checkout -b report-branch
git add README.md
git commit -m "Начал оформление отчета"
git log --pretty=format:"%h - %ad - %an - %s" --date=short
git add README.md
git commit -m "Добавил историю коммитов в отчет"
git push -u origin report-branch
git pull origin report-branch
git add File11
git commit -m "Убрал остатки маркеров конфликта из File11"
git branch -a
git log master --oneline
git log report-branch --oneline
git log --oneline --graph --all
mkdir img
git add img
git commit -m "Добавил скриншоты в папку img"
git push origin report-branch
git show e2b0fd9
git show d1604e0
git add img
git commit -m "Добавил скриншоты git show для слияния и отката"
git push origin report-branch
git add README.md
git commit -m "Добавил скриншоты и лог команд в отчет"
git push origin report-branch
git checkout master
git pull origin master
git merge report-branch
git push origin master
git checkout report-branch
```

## Ход работы

1. Создал аккаунт на GitHub (`dexhexRU`).
2. Сделал Fork репозитория `Kurtyanik/LR6` в личное хранилище.
3. Установил Git с сайта git-scm.com.
4. Настроил Git: указал имя пользователя (`Группа 4515 Галимов И.Р.`) и email командами `git config --global`.
5. Клонировал свой репозиторий на компьютер командой `git clone`.
6. Добавил файл `File11` через интерфейс GitHub и подтянул его в локальный репозиторий командой `git pull`.
7. Создал ветку `feature-branch` и изменил в ней файл `File11`, затем сделал коммит.
8. Просмотрел историю операций и последние изменения (`git log`, `git log --graph`, `git show`).
9. Вернулся в `master`, изменил тот же файл по-другому и сделал коммит.
10. Выполнил слияние `feature-branch` в `master`. Возник конфликт, я исправил файл вручную и зафиксировал результат коммитом «Разрешен конфликт слияния».
11. Удалил побочную ветку `feature-branch` командой `git branch -d`.
12. Создал и закоммитил два тестовых файла (`test1.txt`, `test2.txt`) с комментариями.
13. Откатил последний коммит командой `git revert HEAD`: файл `test2.txt` был удалён, история сохранилась.
14. Создал ветку `report-branch` для отчёта.
15. Начал оформлять отчёт в `README.md` в формате Markdown, периодически делая коммиты.
16. Получил историю коммитов в формате `хэш - дата - автор - комментарий` (`git log --pretty=format`) и добавил её в отчёт.
17. Отправил ветку отчёта на GitHub командой `git push`.
18. Убрал из `File11` остатки маркеров конфликта и закоммитил исправление.
19. Добавил в отчёт скриншоты (папка `img`) и лог команд.
20. Влил `report-branch` в `master` и отправил изменения на GitHub, чтобы отчёт отображался на главной странице репозитория.

## Скриншоты

### Настройка git
![git config](img/screen2.png)

### Ветки и история
![ветки](img/screen1.png)

### История ветки master
![log master](img/screen3.png)

### История ветки report-branch
![log report-branch](img/screen4.png)

### Слияние с разрешённым конфликтом
![merge](img/screen5.png)

### Откат коммита
![revert](img/screen6.png)

## История коммитов
```
$ git log --pretty=format:"%h - %ad - %an - %s" --date=short
4a9f8bc - 2026-11-07 - Группа 4515 Галимов И.Р. - Дополнил лог команд
e9c4c23 - 2026-11-07 - Группа 4515 Галимов И.Р. - Обновил историю коммитов в отчет
0941c4a - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил лог команд в отчет
a3be94c - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил скриншоты и лог команд в отчет
815fdc6 - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил скриншоты git show для слияния и отката
2ae6293 - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил скриншоты в папку img
6f2f6e8 - 2026-11-07 - Группа 4515 Галимов И.Р. - Убрал остатки маркеров конфликта из File11
01b1bbb - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил историю коммитов в отчет
c05be17 - 2026-11-07 - Группа 4515 Галимов И.Р. - Начал оформление отчета
d1604e0 - 2026-11-07 - Группа 4515 Галимов И.Р. - Revert "Добавил второй тестовый файл"
6df21c2 - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил второй тестовый файл
0eefb0d - 2026-11-07 - Группа 4515 Галимов И.Р. - Добавил первый тестовый файл
e2b0fd9 - 2026-11-07 - Группа 4515 Галимов И.Р. - Разрешен конфликт слияния
0ae0a85 - 2026-11-07 - Группа 4515 Галимов И.Р. - Изменил File11 в master
86f6ae2 - 2026-11-07 - Группа 4515 Галимов И.Р. - Изменил File11 в feature-branch
3071277 - 2026-11-07 - Iskander - Create File11
921f53b - 2020-11-21 - Kurtyanik - Обновление информации
c08a654 - 2020-11-21 - Kurtyanik - Файл создан пустым
3c6e913 - 2020-11-21 - Kurtyanik - Initial commit
```