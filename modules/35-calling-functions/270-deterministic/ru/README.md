Независимо от того, какой язык программирования используется, функции внутри него обладают некоторыми фундаментальными свойствами. Если знать эти свойства, легче прогнозировать поведение функций, способы их тестирования и место их использования. В этом уроке мы изучим такие свойства функций и особенности их работы.

## Что такое детерминированность

**Детерминированность** — это одно из фундаментальных свойств функций. Функция будет детерминированной, когда для одних и тех же входных аргументов она возвращает один и тот же результат. Например, функция, которая переворачивает строку, — детерминированная:

```php
<?php

strrev('cat'); // tac
strrev('cat'); // tac
```

Сколько бы раз мы ее не вызывали и не передавали туда значение `'cat'`, она всегда вернет `'tac'`.

При этом функция, которая возвращает случайное число, не является детерминированной. В этом случае у одного и того же входа мы всегда получим разный результат.

Даже если хотя бы один из миллиона вызовов вернет что-то другое, эта функция автоматически считается недетерминированной:

```php
<?php

rand(); // 827606195
rand(); // 635369726
```

Детерминированность серьезно влияет на многие аспекты. Детерминированные функции удобны в работе, их легко оптимизировать и тестировать. Если есть возможность сделать функцию детерминированной, это стоит сделать.

## Что такое побочные эффекты

`print_r()` — это тоже функция. Она принимает на вход данные любого типа и выводит их на экран. При этом что бы она не возвращала, это значение не используется.

`print_r()` выводит что-то на экран, но это не возврат значения. Это действие, которое выполняет функция. Вывод на экран и возврат значения из функции — разные и независимые операции.

Технически вывод на экран равносилен записи в файл. Чтобы понять это, необходимо разобраться в устройстве операционных систем, что крайне важно для программистов.

С точки зрения программы вывод на экран — это **побочный эффект**. Побочным эффектом называют операции, при которых происходит взаимодействие с внешним окружением (средой выполнения). К таким операциям относятся любые сетевые взаимодействия, вывод информации на экран, печать на принтере, взаимодействие с файловой системой — чтение и запись файлов.

Побочные эффекты — один из основных источников проблем и ошибок в программных системах. Код с побочными эффектами сложен в тестировании и ненадежен. При этом без побочных эффектов программирование не имеет смысла. Без них было бы невозможно получить результат работы программы, например, записать в базу, вывести на экран, отправить по сети и так далее.

Важно понимать принципы работы с побочными эффектами. Это влияет на стиль программирования и способность строить качественные программы. Эта тема полностью раскроется в курсе о функциях.

## Что такое чистые функции

Когда функция детерминированная и не имеет побочных эффектов, ее называют **чистой** функцией. Такие функции:

* Проще читать, отлаживать и тестировать
* Не зависят от порядка, в котором они вызываются
* Просто запустить параллельно

Чистые функции независимы от времени. Недетерминизм и побочные эффекты добавляют понятие времени. Если функция зависит от чего-то, что может случиться или нет, и меняет что-то за пределами своих границ, то она неожиданно становится зависимой от времени.

Вопрос для самопроверки. Можно ли определить наличие побочных эффектов внутри функции, опираясь только на ее возврат?