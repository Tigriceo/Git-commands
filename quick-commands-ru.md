## Быстрая работа с чужим репозиторием

### клонируем и присваеваем себе репозиторий

``` bash
# для начала открываем папку где будет работать
git clone https://github.com/user/user_rep_name.git folder-name # клонировать репозиторий в папку , где folder-name название папки
# открываем папку folder-name в редакторе VSCode
git remote -v # смотрим url репозитория в котором работаем
git remote remove origin # удаляем привязку к репозиторию
# создаем свой репозиторий просто через браузер , например с названием test
git remote add origin https://github.com/Tigriceo/test.git #добавить удалённый репозиторий что мы создали
```
### делаем изменения
``` bash
git add .  # сохраняем все изменения
git commit -m "Test commit" # делаем коммит
git push origin main # пушим все в ветку (main)

git checkout -b feature-test # создаем ветку , коммит делаем также (git add . и git commit -m "Test commit")
git push origin feature-test # пушим в свою ветку
git checkout main # переключаеся на main
git checkout feature-test # переключаеся на feature-test
```
### забираем изменения с ветки
``` bash
git pull origin main # берем последние изменения для ветки main
```
