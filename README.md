# Шпаргалка по консольним командам Git

### Додайте свої команди та інші корисності через `Pull request`.
### [Книга з команд гітхабу та онлайн документація](https://git-scm.com/book/uk/v2).

## Загальне

Git – система контролю версій (файлів). Щось на зразок можливості зберігатися в комп'ютерних іграх (у Git еквівалент ігрового збереження - коміт). **Важливо**: додавання файлів до "збереження" двоступінчасте: спочатку додаємо файл в індекс (`git add`), потім "зберігаємо" (`git commit`).

Будь-який файл у директорії існуючого репозиторію може перебувати або перебувати під версійним контролем (відслідковуються і неотслеживаемые).

Файли, що відстежуються, можуть бути в 3-х станах: незмінені, змінені, проіндексовані (готові до комміту).

### Ключ до розуміння

Ключ до розуміння концепції git — знання про «три дерева»:

- Робоча директорія – файлова система проекту (ті файли, з якими ви працюєте).
- Індекс — список файлів і директорій, що відстежуються git-ом, проміжне сховище змін (редагування, видалення файлів, що відстежуються).
- Директорія `.git/` - всі дані контролю версій цього проекту (вся історія розробки: комміти, гілки, теги та ін.).

Коміт — «збереження» (зберігає набір змін, зроблений робочої директорії з попереднього коммита). Коміт незмінний, його не можна відредагувати.

У всіх комітів (крім найпершого) є один або більше батьківських комітів, оскільки коміти зберігають зміни від попередніх станів.

### Найпростіший цикл робіт

- Редагування, додавання, видалення файлів (власне робота).
- Індексація/додавання файлів до індексу (вказівка для git які зміни потрібно буде закоммітити).
- Коміт (фіксація змін).
- Повернення до кроку 1 або відхід до сну.

### Вказівники

- `HEAD` - покажчик на поточний коміт або поточну гілку (тобто, у разі, на комміт). Вказує на батька комміта, який буде створено наступним.
- `ORIG_HEAD` - покажчик на комміт, з якого ви щойно перемістили `HEAD` (командою `git reset...`, наприклад).
- Гілка (`master`, `develop` etc.) – покажчик на коміт. При додаванні комміта вказівник гілки переміщається з батьківського комміту на новий.
- Теги – прості покажчики на комміти. Не рухаються.



### Налаштування

Перед початком роботи потрібно виконати деякі налаштування:

````
git config --global user.name "Your Name" # вказати ім'я, яким будуть підписані коміти
git config --global user.email "e@w.com" # вказати електропошту, яка буде в описі комітера
````

Якщо ви у Windows:

````
git config --global core.autocrlf true # включити перетворення закінчених рядків з CRLF на LF
````


### Вказування файлів, що не відстежуються.

Файли та директорії, які не потрібно включати до репозиторій, вказуються у файлі `.gitignore`. Зазвичай це встановлювані залежності (`node_modules/`, `bower_components/`), готове складання `build/` або `dist/` і подібні, створювані під час встановлення або запуску. Кожен файл або директорія вказуються з нового рядка, [можливе використання шаблонів](http://git-scm.com/book/ru/v2/%D0%9E%D1%81%D0%BD%D0%BE%D0%B2%D1%8B-Git-%D0%97%D0%B0%D0%BF%D0%B8%D1%81%D1%8C-%D0%B8%D0%B7%D0%BC%D0%B5%D0%BD%D0%B5%D0%BD%D0%B8%D0%B9-%D0%B2-%D1%80%D0%B5%D0%BF%D0%BE%D0%B7%D0%B8%D1%82%D0%BE%D1%80%D0%B8%D0%B9#Игнорирование-файлов)


### Консоль

[Як використовувати консоль Bash у Windows, основні команди](https://github.com/Tigriceo/Git-commands/blob/main/GIT-BASH-ua.md).


### Довгий висновок у консолі: Vim

Виклик деяких консольних команд призводить до необхідності дуже довгого виведення консоль (приклад: виведення історії всіх змін у файлі командою `git log -p fileName.txt`). При цьому прямо в консолі запускається редактор [Vim] (https://ua.wikipedia.org/wiki/Vim). Він працює у кількох режимах, з яких Вас зацікавлять режим вставки (редагування тексту) та нормальний (командний) режим. Щоб потрапити з Vim назад до консолі, потрібно в командному режимі ввести <kbd>:q</kbd>. Перехід до командного режиму з іншого: <kbd>Esc</kbd>.

Якщо потрібно щось написати, натисніть <kbd>i</kbd>, щоб перейти до режиму вставки тексту. Якщо потрібно зберегти зміни, перейдіть до командного режиму та наберіть <kbd>:w</kbd>.

# Vim (деякі команди)

``` bash
# Натискання кнопок
ESC – перехід у командний режим
i — перехід до режиму редагування тексту
ZQ (затиснутий Shift, почергове натискання) - вихід без збереження
ZZ (затиснутий Shift, почергове натискання) — зберегти та вийти
``` bash
# Натискання кнопок
ESC – перехід у командний режим
i — перехід до режиму редагування тексту
ZQ (затиснутий Shift, почергове натискання) - вихід без збереження
ZZ (затиснутий Shift, почергове натискання) — зберегти та вийти

# Введення у командному режимі
:q! - Вийти без збереження
:wq - зберегти файл і вийти
:w filename.txt — зберегти файл як filename.txt

````
  

## Консольні команди

### Створити новий репозиторій

``` bash
git init # створити новий проект у поточній директорії
git init folder-name # створити новий проект у вказаній директорії
````


### Клонування репозиторію

``` bash
# клонувати віддалений репозиторій до однойменної директорії
git clone https://github.com/Tigriceo/Git-commands.git

# клонувати віддалений репозиторій до директорії «FolderName»
git clone https://github.com/Tigriceo/Git-commands.git FolderName
````


### Перегляд змін

``` bash
git status # показати стан репозиторію (відстежувані, змінені, нові файли та ін.)
git diff # порівняти робочу директорію та індекс (невідстежувані файли ІГНОРУЮТЬСЯ)
git diff --color-words # порівняти робочу директорію та індекс, показати відмінності в словах (невідстежувані файли ІГНОРУЮТЬСЯ)
git diff index.html # порівняти файл з робочої директорії та індекс
git diff HEAD # порівняти робочу директорію та коміт, на який вказує HEAD (невідстежувані файли ІГНОРУЮТЬСЯ)
git diff --staged # порівняти індекс та коміт з HEAD
git diff master feature # подивитися що зроблено у гілці feature в порівнянні з гілкою master
git diff --name-only master feature # подивитися що зроблено у гілці feature в порівнянні з гілкою master, показати тільки імена файлів
git diff master...feature # подивитися що зроблено у гілці feature з моменту (комміту) розбіжності з master
````


### Додавання змін до індексу

``` bash
git add. # додати до індексу все нові, змінені, видалені файли з поточної директорії та її піддиректорій
git add text.txt # додати в індекс вказаний файл (було змінено, було видалено або це новий файл)
git add -i # запустити інтерактивну оболонку для додавання до індексу тільки вибраних файлів
git add -p # показати нові/змінені файли по черзі із зазначенням їх змін та питанням про відстеження/індексування
````


### Видалення змін з індексу

``` bash
git reset # прибрати з індексу всі додані до нього зміни (в робочій директорії всі зміни збережуться), антипод git add
git reset readme.txt # прибрати з індексу зміни вказаного файлу (у робочій директорії зміни збережуться)
````


### Скасування змін

``` bash
git checkout text.txt # НЕБЕЗПЕКА: скасувати зміни у файлі, повернути стан файлу, що є в індексі
git reset --hard # НЕБЕЗПЕЧНО: скасувати зміни; повернути те, що в коміті, на який вказує HEAD (незакомічні зміни видалені з індексу та з робочої директорії, файли, що не відслідковуються, залишаться на місці)
git clean -df # видалити файли та директорії, що не відслідковуються.
````


### Комміти

``` bash
git commit -m "Name of commit" # зафіксувати в коміті проіндексовані зміни (закомітити), додати повідомлення
git commit -a -m "Name of commit" # проіндексувати файли, що відстежуються (ТІЛЬКИ відстежувані, але НЕ нові файли) і закомітувати, додати повідомлення
````


### Скасування коммітів та переміщення по історії

Всі коміти, які вже були відправлені у віддалений репозиторій, повинні скасовуватися новими комітами (git revert), щоб уникнути проблем з історією розробки в інших учасників проекту.

``` bash
git revert HEAD --no-edit # створити новий коміт, який скасовує зміни останнього комміту без запуску редактора повідомлення
git revert b9533bb --no-edit # те ж, але скасовуються зміни, внесені комітом із зазначеним хешем (b9533bb)
````

**Всі команди, наведені нижче, можна виконувати ТІЛЬКИ якщо комміти ще не були відправлені у віддалений репозиторій.**

``` bash
# УВАГА! Небезпечні команди, можна втратити незакоммічені зміни
git commit --amend -m "Назва" # «перекоммітити» зміни останнього комміта, замінити його новим коммітом з іншим повідомленням (зрушити поточну гілку на один коміт назад, зберігши робочу директорію та індекс «як є», створити новий коміт з даними з «відмінюваного» комміту, але новим повідомленням)
git reset --hard @~ # пересунути HEAD (і гілку) на попередній комміт, робочу директорію та індекс зробити такими, якими вони були в момент попереднього комміту
git reset --hard 75e2d51 # пересунути HEAD (і гілку) на коміт із зазначеним хешем, робочу директорію та індекс зробити такими, якими вони були в момент зазначеного комміту
git reset --soft @~ # пересунути HEAD (і гілку) на попередній коміт, але в робочій директорії та індексі залишити всі зміни
git reset --soft @~2 # те ж, але пересунути HEAD (і гілку) на 2 коміти назад
git reset @~ # пересунути HEAD (і гілку) на попередній коміт, робочу директорію залишити як є, індекс зробити таким, яким він був у момент попереднього комміту (зручніше, ніж git reset --soft @~, якщо індекс потрібно задати заново)
# Майже як git reset --hard, але безпечніше: не вдасться втратити зміни в робочій директорії
git reset --keep @~ # пересунути HEAD (і гілку) на попередній коміт, скинути індекс, але в робочій директорії залишити зміни, якщо можливо (якщо файл зі змінами між коммітами змінювався, буде видана помилка і перемикання не відбудеться)
````


### Тимчасово перейти на інший коміт

``` bash
git checkout b9533bb # перейти на коміт із зазначеним хешем (перемістити HEAD на вказаний комміт, робочу директорію повернути до стану, на момент цього комміту)
git checkout master # перейти на комміт, на який вказує master (перемістити HEAD на комміт, на який вказує master, робочу директорію повернути до стану на момент цього комміту)
````


### Перейти на інший коміт і продовжити роботу з нього

Потрібно створення нової гілки, що починається із зазначеного комміту.

``` bash
git checkout -b new-branch 5589877 # створити гілку new-branch, що починається з коміту c хешем 5589877 (перемістити HEAD на вказаний комміт, робочу директорію повернути до стану, на момент цього комміту, створити вказівник на цей коміт) )
````


### Відновлення змін

``` bash
git checkout 5589877 index.html # відновити в робочій директорії вказаний файл на момент вказаного комміту (і додати цю зміну в індекс) (git reset index.html для видалення з індексу, але збереження змін у файлі)
````


### Копіювання комміту (перенесення коммітів)

``` bash
git cherry-pick 5589877 # скопіювати на активну гілку зміни із зазначеного комміту, закомитити ці зміни
git cherry-pick master~2..master # скопіювати на активну гілку зміни з master (2 останніх коміти)
git cherry-pick -n 5589877 # скопіювати на активну гілку зміни із зазначеного комміту, але НЕ КОМІТИТИ (маю на увазі, що ми самі потім закоммітуємо)
git cherry-pick master..feature # скопіювати на активну гілку зміни з усіх коммітів гілки feature з моменту її розбіжності з master (схоже на злиття гілок, але це копіювання змін, а не злиття), закоммітити ці зміни; це може викликати конфлікт
git cherry-pick --abort # перервати конфліктне перенесення коммітів
git cherry-pick --continue # продовжити конфліктне перенесення коммітів (спрацює тільки після вирішення конфлікту)
````


### Видалення файлу

``` bash
git rm text.txt # видалити незмінений файл, що відстежується, і проіндексувати цю зміну
git rm -f text.txt # видалити відстежуваний змінений файл і проіндексувати цю зміну
git rm -r log/ # видалити весь вміст директорії log/, що відстежується, і проіндексувати цю зміну
git rm ind* # видалити всі відстежувані файли з ім'ям, що починається на «ind» у поточній директорії і проіндексувати цю зміну
git rm --cached readme.txt # видалити з відстежуваних індексований файл (ФАЙЛ ЗАЛИШЕТЬСЯ НА МІСЦІ) (часто використовується для ненавмисно доданих у відстежувані файли)
````


### Переміщення/перейменування файлів

Для git немає перейменування. Перейменування сприймається як видалення старого файлу та створення нового. Факт перейменування можна визначити лише після індексації зміни.

``` bash
git mv text.txt test_new.txt # перейменувати файл «text.txt» на «test_new.txt» і проіндексувати цю зміну
git mv readme_new.md folder/ # перемістити файл readme_new.md в директорію folder/ (має існувати) і проіндексувати цю зміну
````


### Історія коммітів

Вихід із довгого лога виведення: `q`.

``` bash
git log master # показати комміти у вказаній гілці
git log -2 # показати останні 2 коміти в активній гілці
git log -2 --stat # показати останні 2 коміти та статистику внесених ними змін
git log -p -22 # показати останні 22 коміти та внесену ними різницю на рівні рядків
git log --graph -10 # показати останні 10 коммітів з ASCII-поданням розгалуження
git log --since=2.weeks # показати коміти за останні 2 тижні
git log --after '2018-06-30' # показати коміти, зроблені після вказаної дати
git log index.html # показати історію змін файлу index.html (тільки комміти)
git log -5 index.html # показати історію змін файлу index.html, останні 5 комітів (тільки комміти)
git log -p index.html # показати історію змін файлу index.html (комміти та зміни)
git log -G'myFunction' -p # показати всі комміти, в яких змінювалися рядки з myFunction (у лапках регулярний вираз)
git log -L '/<head>/','/<\/head>/':index.html # показати зміни від вказаного до вказаного регулярних виразів у вказаному файлі
git log --grep fix # показати комміти, в описі яких є буквосполучення fix (реєстрозалежно, тільки коміти поточної гілки)
git log --grep fix -i # показати коміти, в описі яких є буквосполучення fix (реєстронезалежно, тільки коміти поточної гілки)
git log --grep 'fix(ing|me)' -P # показати комміти, в описі яких є збіги для регулярного вираження (тільки коміти поточної гілки)
git log --pretty=format:"%h - %an, %ar : %s" -4 # показати останні 4 коміти з форматуванням даних, що виводяться
git log --pretty=format:"%h %ad |
git log master..branch_99 # показати комміти з гілки branch_99, які не влиті в master
git log branch_99..master # показати комміти з гілки master, які не влиті в branch_99
git log master...branch_99 --boundary -- graph # показати коміти із зазначених гілок, починаючи з їхнього розходження (комміт розбіжності буде показаний)
````

``` bash
git show 60d6582 # показати зміни з комміта із зазначеним хешем
git show HEAD~ # показати дані про попередній коментар в активній гілці
git show @~ # аналогічно попередньому
git show HEAD~3 # показати дані про комітет, який був 3 коміти тому
git show my_branch~2 # показати дані про коміт, який був 2 коміти тому у зазначеній гілці
git show @~:index.html # показати контент зазначеного файлу на момент попереднього (від HEAD) комміту
git show :/"підвал" # показати найновіший коміт, в описі якого є вказане слово (з будь-якої гілки)
````


### Хто написав рядок

``` bash
git blame README.md --date=short -L 5,8 # показати рядки 5-8 вказаного файлу та коміти, в яких рядки були додані
````


### Історія змін покажчиків (гілок, HEAD)

````
git reflog -20 # показати останні 20 змін положення покажчика HEAD
git reflog --format='%C(auto)%h %<|(20)%gd %C(blue)%cr%C(reset) %gs (%s)' -20 # те ж, але із зазначенням давності дій
````

### Гілки

``` bash
git branch # показати список гілок
git branch -v # показати список гілок та останній коміт у кожній
git branch new_branch # створити нову гілку із вказаним ім'ям на поточному коміті
git branch new_branch 5589877 # створити нову гілку з вказаним ім'ям на вказаному коментарі
git branch -f master 5589877 # перемістити гілку master на вказаний коміт
git branch -f master master~2 # перемістити гілку master на 2 коміти назад
git checkout new_branch # перейти у вказану гілку
git checkout -b new_branch # створити нову гілку із зазначеним ім'ям та перейти в неї
git checkout -B master 5589877 # перемістити гілку із зазначеним ім'ям на вказаний коміт та перейти до неї
git merge hotfix # влити у гілку, в якій знаходимося, дані з гілки hotfix
git merge hotfix -m "Гаряча правка" # влити у гілку, в якій знаходимося, дані з гілки hotfix (вказано повідомлення комміту злиття)
git merge hotfix --log # влити у гілку, в якій знаходимося, дані з гілки hotfix, показати редактор опису комміту, додати до нього повідомлення коммітів, що вливаються.
git merge hotfix --no-ff # влити у гілку, в якій знаходимося, дані з гілки hotfix, заборонити простий зсув покажчика, зміни з hotfix «залишаться» в ній, а в активній гілці з'явиться тільки коміт злиття
git branch -d hotfix # видалити гілку hotfix (використовується, якщо її зміни вже влиті в головну гілку)
git branch --merged # показати гілки, вже злиті з активної
git branch --no-merged # показати гілки, не злиті з активної
git branch -a # показати всі гілки (в т.ч. на віддалених репозиторіях)
git branch -m old_branch_name new_branch_name # локально перейменувати гілку old_branch_name в new_branch_name
git branch -m new_branch_name # перейменувати локально ПОТОЧНУ гілку в new_branch_name
git push origin :old_branch_name new_branch_name # застосувати перейменування у віддаленому репозиторії
git branch --unset-upstream # завершити процес перейменування
````


### Теги

``` bash
git tag v1.0.0 # створити тег із вказаним ім'ям на коміті, на який вказує HEAD
git tag -a -m 'У продакшені!' v1.0.1 master # створити тег з описом на тому коміті, на який дивиться гілка master
git tag -d v1.0.0 # видалити тег із зазначеним ім'ям(ами)
git tag -n # показати всі теги і по 1 рядку повідомлення коммітів, на які вони вказують
git tag -n -l 'v1.*' # показати всі теги, які починаються з 'v1.*'
````


### Тимчасове збереження змін без комміту

``` bash
git stash # тимчасово зберегти незакоммічені зміни та прибрати їх з робочої директорії
git stash pop # повернути збережені командою git stash зміни до робочої директорії
````


### Віддалені репозиторії

Є два поширені способи прив'язати віддалений репозиторій до локального: HTTPS і SSH. Якщо SSH у вас не налаштований (або ви не знаєте що це), прив'язуйте віддалений репозиторій за HTTPS (адреса репозиторію, що прив'язується, повинен починатися з https://).

``` bash
git remote -v # показати список віддалених репозиторіїв, пов'язаних з локальним
git branch -r # показати видалені гілки
git branch -a # показати всі гілки (локальні та віддалені)
git remote remove origin # прибрати прив'язку віддаленого репозиторію з скор. ім'ям origin
git remote add origin https://github.com:nicothin/test.git # додати віддалений репозиторій (з скор. ім'ям origin) із зазначеним URL
git remote rm origin # видалити прив'язку видаленого репозиторію
git remote show origin # отримати дані про віддалену репозиторію зі скороченим ім'ям origin
git fetch origin # скачати всі гілки з віддаленого репозиторію (з скор. ім'ям origin), але не зливати зі своїми гілками
git fetch origin master # те ж, але скачується тільки вказана гілка
git checkout --track origin/github_branch # створити локальну гілку github_branch (дані взяти з віддаленого репозиторію з скор. ім'ям origin, гілка github_branch) і переключитися на неї
git push origin master # відправити у віддалений репозиторій (з скор. ім'ям origin) дані своєї гілки master
git pull origin # влити зміни з віддаленого репозиторію (всі гілки)
git pull origin master # влити зміни з віддаленого репозиторію (тільки вказана гілка)
````


### Конфлікт злиття

Передбачається ситуація: є гілка `master` та є гілка `feature`. В обох гілках є комміти, зроблені після розбіжності гілок. У гілку `master` намагаємось влити гілку `feature` (`git merge feature`), отримуємо конфлікт, т.к. в обох гілках є зміни одного і того ж рядка у файлі `index.html`.

У разі конфлікту, репозиторій перебуває у стані перерваного злиття. Потрібно залишити у конфліктуючих місцях файлів лише потрібний код, проіндексувати зміни та закоммітувати.

``` bash
git merge feature # влити в активну гілку зміни з гілки feature
git merge-base master feature # показати хеш останнього спільного комміту для двох зазначених гілок
git checkout --ours index.html # залишити в конфліктному файлі (index.html) стан гілки, В ЯКУ ми вливаємо (у прикладі — з гілки master)
git checkout --theirs index.html # залишити в конфліктному файлі (index.html) стан гілки, З ЯКОЇ ми вливаємо (у прикладі - з гілки feature)
git checkout --merge index.html # показати в конфліктному файлі (index.html) порівняння вмісту гілок, що зливаються (для ручного редагування)
git checkout --conflict=diff3 --merge index.html # показати в конфліктному файлі (index.html) порівняння вмісту гілок, що зливаються плюс те, що було в місці конфлікту в коміті, на якому розійшлися гілки, що зливаються
````

``` bash
git reset --hard # припинити це перерване злиття, повернути робочу директорію та індекс як було в момент комміту, на який вказує HEAD, а я піду трохи поплачу
git reset --merge # припинити це перерване злиття, але залишити зміни, не закоммічені до злиття (для випадку, коли злиття робиться не на чистому статусі)
git reset --abort # те ж, що і рядком вище
````


### «Перенесення» гілки

Можна «перемістити» відгалуження будь-якої гілки від основної на довільний коміт. Це потрібно для того, щоб в «гілці, що переноситься» з'явилися які-небудь зміни, внесені в основній гілці (вже після відгалуження переносимої).

Не можна «переносити» гілку, якщо її вже відправлено на віддалений репозиторій.

``` bash
git rebase master # перенести всі комміти (створити їх копії) активної гілки так, ніби активна гілка відгалужилася від master на нинішній вершині master (часто викликає конфлікти)
git rebase --onto master feature # перенести комміти активної гілки на master, починаючи з того місця, в якому активна гілка відокремилася від гілки feature
git rebase --abort # перервати конфліктний rebase, повернути робочу директорію та індекс до стану до початку rebase
git rebase --continue # продовжити конфліктний rebase (спрацює тільки після вирішення конфлікту та індексації такого вирішення)
````

#### Як скасувати rebase

``` bash
git reflog feature -2 # дивимося лог переміщень гілки, якою робили rebase (у цьому прикладі — feature), бачимо останній коміт ПЕРЕД rebase, на нього і потрібно перенести покажчик гілки
git reset --hard feature@{1} # перемістити покажчик гілки feature на один коміт назад, оновити робочу директорію та індекс
````


### Різне

``` bash
git archive -o ./project.zip HEAD # створити архів з файловою структурою проекту за вказаним шляхом (стан репозиторію, що відповідає покажчику HEAD)
````





## Приклади

Збираємо колекцію простих та складних прикладів роботи.


### Початок роботи

Створення нового репозиторію, перший коміт, прив'язка віддаленого репозиторію з gthub.com, відправка змін до віддаленого репозиторію.

``` bash
# вказана послідовність дій:
# створено директорію проекту, ми в ній
git init # створюємо репозиторій у цій директорії
touch readme.md # створюємо файл readme.md
git add readme.md # додаємо файл в індекс
git commit -m "Старт" # створюємо коміт
git remote add origin https://github.com:nicothin/test.git # додаємо попередньо створений порожній віддалений репозиторій
git push -u origin master # відправляємо дані з локального репозиторію у віддалений (у гілку master)
````


### «Внесення змін» до комітету

Тільки якщо коміт ще не був відправлений до віддалених репозиторій.

``` bash
# вказано послідовність дій:
subl inc/header.html # редагуємо та зберігаємо розмітку «шапки»
git add inc/header.html # індексуємо змінений файл
git commit -m "Прибрав телефон із шапки" # робимо комміт
# УВАГА: коміт поки не був відправлений у віддалений репозиторій
# Усвідомлюємо, що потрібно було ще щось зробити в цьому коментарі.
subl inc/header.html # вносимо зміни
git add inc/header.html # індексуємо змінений файл (можна git add .)
git commit --amend -m "Шапка": виконано завдання №34" # заново робимо коміт
````


### Робота з гілками

Є master (публічна версія сайту), виконуємо масштабне завдання (переверстати «шапку»), але в процесі роботи виникає необхідність підправити критичний баг (неправильно вказаний контакт у «підвалі»).

``` bash
# вказано послідовність дій:
git checkout -b new-page-header # створимо нову гілку для завдання зміни «шапки» і перейдемо до неї
subl inc/header.html # редагуємо розмітку «шапки»
git commit -a -m "Нова шапка: зміна логотипу" # робимо комміт (робота ще не завершена)
тут з'ясовується, що є баг з контактом у «підвалі»
git checkout master # повертаємося до гілки master
subl inc/footer.html # усуваємо баг і зберігаємо розмітку «підвалу»
git commit -a -m "Виправлення контакту в підвалі" # робимо коміт
git push # відправляємо комміт зі швидкою критичною зміною в master у віддаленому репозиторії
git checkout new-page-header # перемикаємося назад у гілку new-page-header для продовження робіт над «шапкою»
subl inc/header.html # редагуємо та зберігаємо розмітку «шапки»
git commit -a -m "Нова шапка: зміна навігації" # робимо комміт (робота над «шапкою» завершена)
git checkout master # перемикаємось у гілку master
git merge new-page-header # вливаємо в master зміни з гілки new-page-header
git branch -d new-page-header # видаляємо гілку new_page_header
````


### Робота з гілками, злиття та відкат до стану до злиття

Була гілка `fix`, у якій виправляли баг. Виправили, влили `fix` у `master`. Але тут з'ясувалося, що це виправлення ламає якусь функціональність, Потрібно відкотити `master` до стану без злиття (наявність бага менш критична, ніж псування функціональності).

``` bash
# перебуваємо у гілці fix, баг вже «виправлений»
git checkout master # перемикаємося на master
git merge fix # вливаємо зміни з fix в master
бачимо проблему: частина функціональності зламалася
git checkout fix # перемикаємося на fix (поки ми в master, git не дасть її рухати)
git branch -f master ORIG_HEAD # пересуваємо гілку master на комміт, вказаний у ORIG_HEAD (той, на який вказувала master до вливання fix)
````



### Робота з гілками, конфлікт злиття

Є гілка `master` (публічна версія сайту), у двох паралельних гілках (`branch-1` та `branch-2`) було відредаговано одне й те саме місце одного і того ж файлу, першу гілку (`branch-1`) влили в master, спроба влити другу викликає конфлікт.

``` bash
# вказано послідовність дій:
git checkout master # перемикаємося на гілку master
git checkout -b branch-1 # створюємо гілку branch-1, засновану на гілці master
subl. # редагуємо та зберігаємо файли
git commit -a -m "Правка 1" # комітім
git checkout master # повертаємося до гілки master
git checkout -b branch-2 # створюємо гілку branch-2, засновану на гілці master
subl. # редагуємо та зберігаємо файли
git commit -a -m "Правка 2" # комітім
git checkout master # повертаємося до гілки master
git merge branch-1 # вливаємо зміни з гілки branch-1 в поточну гілку (master), удача (автозлиття)
git merge branch-2 # вливаємо зміни з гілки branch-2 в поточну гілку (master), КОНФЛІКТ автозлиття
# Automatic merge failed; fix conflicts and then commit the result.
subl. # вибираємо у конфліктних файлах ті ділянки, які потрібно залишити, зберігаємо
git commit -a -m "Усунення конфлікту" # комітім результат усунення конфлікту
````



### Синхронізація репозиторію-форку з майстер-репозиторієм

Є якийсь репозиторій на github.com, він нами був зроблений форк, додані якісь зміни. Оригінальний (майстер-)репозиторій якось оновлено. Завдання: зняти з майстер-репозиторія зміни (які там внесені вже після того, як ми його форкнули).

``` bash
# вказано послідовність дій:
git remote add upstream https://github.com:address.git # додаємо віддалений репозиторій: скор. ім'я - upstream, URL майстер-репозиторія
git fetch upstream # стягуємо всі гілки майстер-репозиторію, але поки не зливаємо зі своїми
git checkout master # перемикаємося на гілку master свого репозиторію
git merge upstream/master # вливаємо стягнуту гілку master віддаленого репозиторію upstream у свою гілку master
````



### Помилка в роботі: закомітили в майстер, але зрозуміли, що треба було комити в нову гілку

**ВАЖЛИВО: це спрацює тільки якщо коміт ще не відправлений у віддалений репозиторій.**

``` bash
# вказано послідовність дій:
# зробили зміни, проіндексували їх, закоммітували в master, але ЩЕ НЕ ВІДПРАВИЛИ (не робили git push)
git checkout -b new-branch # створюємо нову гілку з master
git checkout master # перемикаємося на master
git reset HEAD~ --hard # зсуваємо покажчик (гілку) master на 1 коміт назад
git checkout new-branch # перемикаємося назад на нову гілку для продовження роботи
````



### Потрібно повернути вміст файлу до стану, що був у якомусь коміті (відомий хеш комміта)

``` bash
# вказано послідовність дій:
git checkout f26ed88 -- index.html # відновити в робочій директорії стан зазначеного файлу на момент вказаного комміту, додати цю зміну до індексу
git commit -am "Navigation fixs" # зробити коміт
````



### При будь-якій дії з github (або іншим віддаленим сервісом) запитується логін та пароль

Мова саме про запит пари логін + пароль, а не ключової фрази. Відбувається це тому, що git за умовчанням не збереже пароль для доступу до репозиторію HTTPS.

Просте рішення: [вказати git кешувати ваш пароль](https://help.github.com/articles/caching-your-github-password-in-git/).



## `.gitattributes`

````
* text=auto

*.html diff=html
*.css diff=css
*.scss diff=css
````
