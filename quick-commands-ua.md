## Швидка робота з чужим репозиторієм

### клонуємо і привласнюємо собі репозиторій

``` bash
# для початку відкриваємо папку де буде працювати
git clone https://github.com/goitacademy/vanilla-app-template.git folder-name # клонувати репозиторій в папку , де folder-name назва папки
# відкриваємо папку folder-name у редакторі VSCode
git remote -v # дивимося url репозиторія в якому працюємо
git remote remove origin # видаляємо прив'язку до репозиторію
# Створюємо свій репозиторій просто через браузер, наприклад з назвою test
git remote add origin https://github.com/Tigriceo/test.git #додати віддалений репозиторій що ми створили
````
### робимо зміни
``` bash
git add. # зберігаємо всі зміни
git commit -m "Test commit" # робимо коміт
git push origin main # пухаємо все в гілку (main)

git checkout -b feature-test # створюємо гілку, комміт робимо також (git add. і git commit-m "Test commit")
git push origin feature-test # пушим у свою гілку
git checkout main # перемикається на main
git checkout feature-test # перемикається на feature-test
````
### забираємо зміни з гілки
``` bash
git pull origin main # беремо останні зміни для гілки main
````
