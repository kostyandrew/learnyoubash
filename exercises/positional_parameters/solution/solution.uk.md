# Вітаю!

Позиційні параметри є дуже корисні для створення власних додатків командного рядка.

Наприклад, у нас є скрипт:

```bash
#!/usr/bin/env bash

echo "Arguments:"
echo $*
```

Запустимо його з деякими параметрами:

    ./script.bash --test -t -a -b -c

Воно виведе:

    --test -t -a -b -c

Це означає, що ми можемо оброблять ці параметри і змінити результа, що скрипт буде повертати.
очно так же, як з `--help` параметром, які виводять довідку замість запуску програми.

У наступній вправі ми вивчемо масиви в Bash.
