# Лабораторная работа №6
## Выполнил: Галимов И.Р.
## Лог команд
```
git branch -a
git log HEAD
git log master
git log report-branch
git status
git commit -m "Добавил скриншоты в отчет"
git push origin report-branch
git checkout master
git pull origin master
git merge report-branch
git push origin master
git checkout report-branch
git --no-pager log --oneline --graph --all
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
