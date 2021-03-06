Добре, тепер ми знаємо як писати Bash скрипти. Але це не легко. Часом ми маємо проблеми і Bash надає нам інструменти для відладки.
Якщо ми захочемо виконувати скрипт у режимі відладки, то ми повинні використовувати спеціальні опції:

```bash
#!/bin/bash options
```
Ці опції є налаштуваннями, що міняють поведінку. Таблиця опцій які можуть бути корисними для застосування:

| Опція | Назва       | Опис                                                      |
| :---: | :---------- | :-------------------------------------------------------- |
| `-f`  | noglob      | Вимикає генерацію імені файлу метасимволів (підстановка). |
| `-i`  | interactive | Скрипт виконується в інтерактивному режимі.               |
| `-n`  | noexec      | Читає команди, але не виконує їх (перевірка синтаксису).  |
| `-t`  | —           | Вихід після першої команди                                |
| `-v`  | verbose     | Показує вхідні рядки оболонки в міру їх зчитування.       |
| `-x`  | xtrace      | Показує команду перед виконанням команди.                 |

Наприклад, ми виконаємо скрипт з опцією `-x:

```bash
#!/bin/bash -x

for (( i = 0; i < 3; i++ )); do
  echo $i
done
```

Буде поміщатися значення змінної в `stdout` разом з іншою корисною інформацією:

```
$ ./my_script
+ (( i = 0 ))
+ (( i < 3 ))
+ echo 0
0
+ (( i++  ))
+ (( i < 3 ))
+ echo 1
1
+ (( i++  ))
+ (( i < 3 ))
+ echo 2
2
+ (( i++  ))
+ (( i < 3 ))
```

    Часом нам необхідно відладити тільки частину скрипта. Використання `set` буде зручним. Ця команда дозволяє активувати і деактивовувати опцію. Опції активуються `-` , а деактивовуються `+`:

```bash
#!/bin/bash

echo "xtrace is turned off"
set -x
echo "xtrace is enabled"
set +x
echo "xtrace is turned off again"
```

## Завдання

Створіть файл `debugging.bash`.

Ви будете отримувати позиційні аргументи, вони будуть назвами файлів. Ваш скрипт повинен відповідати таким вимогам:

1. Увімкнення **verbose** і **noexec** опцій через використання `set`
2. Вивід усіх отриманих аргументів через `echo`
3. Створити всі ці файли
4. Створити директорію з ім'ям `folder` в поточному директорії
5. Перемістити усі ці файли до `folder`
6. Змінити директорію на `folder`
7. Показати усі файли в `folder`
8. Відімкнути **verbose** і **noexec** опції через `set`

Будь ласка, пишіть одну команду на рядок без пустих рядків.

Ви маєте знати як переміщати один або декілька файлів в інше місце. Коли необхідно перемістити файли ми використовуєм команду `mv`. Ця команда отримує два аргументи: джерело і призначення. Якщо обидва імена файлів знаходяться в одній файловой системі, то виконується просте перейменування файлу. Якщо файл переміщується і існує файл з таким же ім'я в точці призначння, існуючий файл буде замінений.

Для прикладу:

    mv old new           # перейменування 'old' в 'new'.
    mv file subdir/file  # перемішення 'file' в 'subdir/file'
    mv name* subdir/     # переміщення усіх файлів які відповідають 'name*' в 'subdir'

Крім того, існує `cp` команда, яка копіює один або кілька файлів або директорій. Використання `cp` є таким же, як і команди `mv`.

---
