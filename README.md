# Лабораторная работа №6
## Выполнил: Галимов И.Р.

**Тема:** Система контроля версий Git

**Цель:** изучение базовых возможностей системы управления версиями, получение опыта работы с Git, с локальным и удалённым репозиторием.

## Ход работы

### 1. Аккаунт на GitHub и форк репозитория
Зарегистрировался на сайте GitHub (аккаунт `dexhexRU`). Открыл исходный репозиторий https://github.com/Kurtyanik/LR6/ и нажал кнопку **Fork**. На GitHub появилась моя личная копия `dexhexRU/LR6`, а исходный репозиторий остался без изменений.

### 2. Установка и настройка Git
Установил Git с сайта https://git-scm.com/. После установки в Git Bash указал имя пользователя в формате «Группа Фамилия И.О.» и email. Эти данные Git записывает в каждый коммит как данные автора:
```
git config --global user.name "Группа 4515 Галимов И.Р."
git config --global user.email "iskander.6alimov@gmail.com"
```
Проверил настройки командой `git config --global --list`. В выводе видны строки `user.name` и `user.email` (рисунок 1).

<p align="center">
  <img src="img/screen2.png" alt="git config"><br>
  Рисунок 1 — Проверка настроек Git командой git config --list
</p>

### 3. Клонирование репозитория
Склонировал свой форк с GitHub на компьютер и перешёл в папку репозитория. Команда `git clone` скачала все файлы вместе с полной историей коммитов и сохранила адрес удалённого репозитория под именем `origin`:
```
git clone https://github.com/dexhexRU/LR6.git
cd LR6
```

### 4. Добавление файла через интерфейс GitHub
На сайте GitHub в своём репозитории создал файл `File11` (Add file, Create new file) и сохранил его в ветку `master` с комментарием `Create File11`. Автором этого коммита (`3071277`) указан Iskander: коммиты через сайт подписываются именем из профиля GitHub, а не данными из `git config`.

Затем подтянул изменение в локальный репозиторий:
```
git pull
```
Дальше работу вёл локально.

### 5. Создание ветки feature-branch и первое изменение
Создал новую ветку и сразу переключился на неё. Командой `git checkout -b` ветка создаётся и открывается за один шаг:
```
git checkout -b feature-branch
```
В Блокноте изменил файл `File11`: добавил текст ветки feature. Добавил файл в индекс и зафиксировал изменение с комментарием:
```
git add File11
git commit -m "Изменил File11 в feature-branch"
```

### 6. История операций и последние изменения
Просмотрел историю операций и состояние веток. Команда `git log --oneline` показывает историю кратко, `git log --all --oneline --graph --decorate` показывает все ветки в виде графа, `git show` показывает последний коммит с изменениями, `git branch` выводит список веток:
```
git log --oneline
git log --all --oneline --graph --decorate
git show
git branch
```
Получил историю операций для каждой из веток (рисунки 2 и 3) и общий граф (рисунок 4). Снимки сделаны в конце работы, поэтому в них видны и более поздние коммиты:
```
git log master
git log report-branch
git log --oneline --graph --all
```

<p align="center">
  <img src="img/screen3.png" alt="log master"><br>
  Рисунок 2 — История коммитов ветки master (git log master)
</p>

<p align="center">
  <img src="img/screen4.png" alt="log report-branch"><br>
  Рисунок 3 — История коммитов ветки report-branch (git log report-branch)
</p>

<p align="center">
  <img src="img/screen1.png" alt="граф веток"><br>
  Рисунок 4 — Граф всех веток (git log --oneline --graph --all)
</p>

### 7. Изменение в master и слияние с конфликтом
Вернулся в ветку `master` и изменил тот же файл `File11` в той же части, что и в `feature-branch`. Зафиксировал изменение:
```
git checkout master
git add File11
git commit -m "Изменил File11 в master"
```
Выполнил слияние ветки `feature-branch` в `master`:
```
git merge feature-branch
```
Git сообщил о конфликте слияния: одни и те же строки файла изменены по-разному в двух ветках, и автоматически объединить их Git не смог. В файле `File11` он расставил маркеры `<<<<<<< HEAD`, `=======` и `>>>>>>> feature-branch`.

Открыл файл в Блокноте, оставил нужный текст (из обеих веток) и удалил маркеры. После этого добавил файл и зафиксировал результат слияния:
```
git add File11
git commit -m "Разрешен конфликт слияния"
```
Получился коммит слияния `e2b0fd9` с двумя родителями (`0ae0a85` из `master` и `86f6ae2` из `feature-branch`). Посмотрел его командой `git show e2b0fd9` (рисунок 5).

<p align="center">
  <img src="img/screen5.png" alt="слияние"><br>
  Рисунок 5 — Коммит слияния с разрешённым конфликтом (git show e2b0fd9)
</p>

### 8. Удаление побочной ветки
После успешного слияния побочная ветка стала не нужна: все её изменения уже есть в `master`. Удалил её. При этом удаляется только имя ветки, а коммиты остаются в истории:
```
git branch -d feature-branch
```
Проверил список веток командой `git branch -a`: ветки `feature-branch` больше нет.

### 9. Несколько коммитов с комментариями
Создал два тестовых файла и зафиксировал каждый отдельным коммитом с комментарием. Команда `git add .` добавляет в индекс все изменённые файлы:
```
echo "Текст 1" > test1.txt
git add .
git commit -m "Добавил первый тестовый файл"
echo "Текст 2" > test2.txt
git add .
git commit -m "Добавил второй тестовый файл"
```

### 10. Откат коммита
Откатил последний коммит («Добавил второй тестовый файл»). Команда `git revert` не стирает историю, а создаёт новый коммит, который отменяет изменения выбранного. Файл `test2.txt` при этом удалился:
```
git revert HEAD
```
Получился коммит `d1604e0` с комментарием `Revert "Добавил второй тестовый файл"`. Посмотрел его командой `git show d1604e0`. В выводе видно, что файл `test2.txt` удалён (`deleted file`), рисунок 6.

<p align="center">
  <img src="img/screen6.png" alt="откат"><br>
  Рисунок 6 — Откат коммита (git show d1604e0)
</p>

### 11. Ветка для отчёта
Создал отдельную ветку для отчёта, чтобы не менять `master` во время работы над документом:
```
git checkout -b report-branch
```

### 12. Оформление отчёта в README.md
В Блокноте оформлял отчёт в файле `README.md` в формате Markdown. Периодически фиксировал изменения с комментариями:
```
git add README.md
git commit -m "Начал оформление отчета"
```
Получил историю операций в нужном формате (сокращённый хэш, дата, имя автора, комментарий), добавил её в отчёт и зафиксировал:
```
git log --pretty=format:"%h - %ad - %an - %s" --date=short
git add README.md
git commit -m "Добавил историю коммитов в отчет"
```
Отправил ветку отчёта в сетевое хранилище. Параметр `-u` связывает локальную ветку с веткой на GitHub:
```
git push -u origin report-branch
```

### 13. Исправление файла File11
При проверке в файле `File11` нашёл остатки маркеров конфликта (слова `HEAD` и `feature-branch`). Удалил их и зафиксировал исправление. Перед этим подтянул актуальное состояние ветки:
```
git pull origin report-branch
git add File11
git commit -m "Убрал остатки маркеров конфликта из File11"
```

### 14. Скриншоты в отчёте
Создал папку `img` для скриншотов и сохранял в неё снимки консоли (клавиши Win + Shift + S). Закоммитил и отправил:
```
mkdir img
git add img
git commit -m "Добавил скриншоты в папку img"
git push origin report-branch
```
Затем выполнил `git show e2b0fd9` и `git show d1604e0`, снял результат и добавил скриншоты в ту же папку и в отчёт.

### 15. Лог команд и финальная фиксация
Из истории консоли (команда `history`) собрал лог выполненных команд без результатов и добавил его в отчёт (раздел «Лог команд»). Обновил историю коммитов и сделал финальную фиксацию:
```
git add README.md
git commit -m "Добавил скриншоты и лог команд в отчет"
git push origin report-branch
```

### 16. Слияние отчёта в master и отправка на GitHub
Чтобы отчёт отображался на главной странице репозитория, влил ветку `report-branch` в `master` и отправил на GitHub:
```
git checkout master
git pull origin master
git merge report-branch
git push origin master
git checkout report-branch
```
Проверил на GitHub, что все коммиты на месте.

## Вывод
В ходе лабораторной работы изучил базовые возможности системы контроля версий Git: настройку клиента, клонирование репозитория, создание и слияние веток, разрешение конфликтов, откат коммитов (`git revert`) и просмотр истории. Получил опыт работы с локальным и удалённым репозиторием на GitHub (`fork`, `clone`, `pull`, `push`) и оформления отчёта в формате Markdown.

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