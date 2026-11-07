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

## Скриншоты

### Настройка git
![git config](img/screen1.png)

### Ветки и история
![ветки](img/screen2.png)

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