Допустим, нам нужно напечатать на экран слово «Father!» два раза или даже пять раз. Эту задачу можно решить так:

```php
<?php

print_r('Father!');
print_r('Father!');
```

В простом случае так и стоит поступить, но если слово «Father!» начнет использоваться чаще и в разных частях программы, то придется его везде повторять. Если нам понадобится изменить слово, то придется найти все места, где оно использовалось и выполнить необходимую замену. А можно поступить по-другому. Вместо копирования выражения достаточно создать переменную с этой фразой:

```php
<?php

// greeting - переводится как приветствие
$greeting = 'Father!';
print_r($greeting);
print_r("\n");
print_r($greeting);
// => Father!
// => Father!
```

В строчке `$greeting = 'Father!'` значение `'Father!'` присваивается переменной с именем `$greeting`. В PHP имена переменных начинаются со знака *$*. В итоге переменная указывает на данные, которые были в нее записаны.

Когда переменная создана, можно начать ее использовать.

## Использование переменной

Переменная подставляется в те места, где раньше стояло наше слово. Во время выполнения интерпретатор доходит до строчки `print_r($greeting);` и подставляет вместо переменной ее содержимое, а затем выполняет код.

Для имени переменной используется любой набор допустимых символов, к которым относятся буквы английского алфавита, цифры, знак `_`. При этом цифру нельзя ставить в начале. Имена переменных регистрозависимы, то есть имя `hello` и имя `heLLo` — это два разных имени, значит, это две переменные. Регистр в PHP имеет важное значение, не стоит забывать про него.

Количество создаваемых переменных не ограничено, большие программы содержат десятки и сотни тысяч имен переменных. Для удобства анализа программы переменные принято создавать как можно ближе к тому месту, где они используются.