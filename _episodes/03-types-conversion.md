## Кожне значення має тип.

*   Кожне значення, яке використовує програма, має деякий тип.
*   Ціле число (`int`): зображує додатні або від’ємні цілі числа, наприклад 3 або -512.
*   Число з плаваючою крапкою (`float`): зображує дійсні числа, наприклад 3.14159 або -2.5.
*   Рядки символів (звичайно просто "рядки", `str`): текст.
    *   Укладені в одинарні або подвійні лапки (тип лапок має співпадати).
    *   Під час відображення рядку лапки не друкуються.

## Вбудована функція `type` повертає тип значення.

*   Використовуйте вбудовану функцію `type` щоб з'ясувати який тип має значення.
*   Це також працює із змінними.
    *   Але запамʼятайте: *значення* має свій тип, а *змінна* тільки вказує на будь-яке значення.

~~~
print(type(52))
~~~
{: .language-python}
~~~
<class 'int'>
~~~
{: .output}

~~~
fitness = 'average'
print(type(fitness))
~~~
{: .language-python}
~~~
<class 'str'>
~~~
{: .output}

## Тип визначає які операції (або методи) можна виконувати із даним значенням.

*   Тип значення визначає, що може робити з ним програма.

~~~
print(5 - 3)
~~~
{: .language-python}
~~~
2
~~~
{: .output}

~~~
print('hello' - 'h')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-2-67f5626a1e07> in <module>()
----> 1 print('hello' - 'h')

TypeError: unsupported operand type(s) for -: 'str' and 'str'
~~~
{: .error}

## Ви можете використовивати оператори "+" та "*" для дій над рядками.

*   "Додавання" рядків виконує їх конкатенацію.

~~~
full_name = 'Ahmed' + ' ' + 'Walsh'
print(full_name)
~~~
{: .language-python}
~~~
Ahmed Walsh
~~~
{: .output}

*   Якщо рядок помножити на ціле число _N_, то це створить новий рядок який буде містити цей рядок повторений  _N_ разів.
    *   Оскільки множення - це повторюване додавання.

~~~
separator = '=' * 10
print(separator)
~~~
{: .language-python}
~~~
==========
~~~
{: .output}

## Рядки мають довжину (але числа її не мають).

*   Вбудована функція `len` повертає кількість символів у рядку.

~~~
print(len(full_name))
~~~
{: .language-python}
~~~
11
~~~
{: .output}

*   Але числа не мають довжини (навіть нуль).

~~~
print(len(52))
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-3-f769e8e8097d> in <module>()
----> 1 print(len(52))

TypeError: object of type 'int' has no len()
~~~
{: .error}

## <a name='convert-numbers-and-strings'></a> Для деяких операцій може бути необхідно спочатку перетворити число у строку, або навпаки.

*   Додавання чисел та рядків неможливе.

~~~
print(1 + '2')
~~~
{: .language-python}
~~~
---------------------------------------------------------------------------
TypeError                                 Traceback (most recent call last)
<ipython-input-4-fe4f54a023c6> in <module>()
----> 1 print(1 + '2')

TypeError: unsupported operand type(s) for +: 'int' and 'str'
~~~
{: .error}

*   Таке додавання не дозволено, тому що воно не визначене: чи має `1 + '2'` повертати `3` чи `'12'`?
*   Деякі типи можуть бути перетворені на інші типи за допомогою функції, яка має те ж саме імʼя, що і потрібний тип.

~~~
print(1 + int('2'))
print(str(1) + '2')
~~~
{: .language-python}
~~~
3
12
~~~
{: .output}

## Цілі та дійсні числа можна використовувати разом.

*   Цілі та дійсні числа можна використовувати разом для аріфметичних дій.
    *   Python 3 автоматично перетворить цілі числа у дійсні, якщо це потрібно. (У Python 2 ділення цілих чисел поверне ціле число, яке буде цілою частиною відповідного дійсного числа.)

~~~
print('half is', 1 / 2.0)
print('three squared is', 3.0 ** 2)
~~~
{: .language-python}
~~~
half is 0.5
three squared is 9.0
~~~
{: .output}

## Змінні можуть змінити своє значення тільки через присвоювання.

*   У електроних таблицях, якщо одна комірка залежить від іншої,
    то у разі зміни у останній,
    залежна комірка оновиться автоматично.
*   Це **не** трапляється у мовах програмування.

~~~
first = 1
second = 5 * first
first = 2
print('first is', first, 'and second is', second)
~~~
{: .language-python}
~~~
first is 2 and second is 5
~~~
{: .output}

*   Компʼютер використовує значення змінної `first` коли виконує множення,
    сворює нове значення, та присвоює його змінній `second`.
*   Після цього, `second` не памʼятає, звідки це значення було отримане.

> ## Дроби
>
> Який тип має 3.4?
> Як це можна встановити?
>
> > ## Рішення
> >
> > Це - дійсне число (або число з плаваючою крапкою).
> >
> > ~~~
> > print(type(3.4))
> > ~~~
> > {: .language-python}
> > ~~~
> > <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Автоматичне перетворення типів
>
> Який тип має 3.25 + 4?
>
> > ## Рішення
> >
> > Це - дійсне число:
> > Цілі числа автоматично перетворюються у дійсні, коли це необхідно.
> >
> > ~~~
> > result = 3.25 + 4
> > print(result, 'is', type(result))
> > ~~~
> > {: .language-python}
> > ~~~
> > 7.25 is <class 'float'>
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Як вибрати тип
>
> Який тип (ціле число, дійсне число, рядок символів) Ви будете використовувати для зберігання наступних значень? Спробуйте надати більш ніж одну підхожу відповідь у кожному випадку. Наприклад, в питанні # 1, коли для рахування дней дійсні числа можуть бути більш придатними ніж цілі?  
>
> 1. Кількість дней з початку року.
> 2. Час, який пройшов з початку року до цього моменту, у днях.
> 3. Серійний номер лабораторного обладнання.
> 4. Вік лабораторного зразку.
> 5. Поточне населення міста.
> 6. Середня чисельність населення міста за певний час.
>
> > ## Відповіді
> >
> > Ці питання мають наступні відповіді:
> > 1. Ціле число, оскільки кількість дней буде від 1 до 365. 
> > 2. Дійсне число, оскільки треба використовувати частини дня.
> > 3. Рядок символів, якщо серійний номер містить букви та цифри; ціле число, якщо він містить тільки цифри.
> > 4. Це залежить від багатьох факторів! Як вимірюється вік зразку? Кількість дней з моменту коли його було знайдено (ціле число)? дата і час (рядок)?
> > 5. Виберіть дійсне число, щоб представити велику кількість населення за допомогою округлення (наприклад, до мільйонів), або ціле число, щоб представити точну кількість населення.
> > 6. Дійсне число, оскільки результат усереднення скоріш за все буде мати дрібну частину.
> > {: .output}
> {: .solution}
{: .challenge}

> ## Типи операцій ділення 
>
> У Python 3, оператор `//` виконує ціле ділення (повертаючи цілу частину результату), оператор `/` виконує ділення з плаваючою крапкою,
> та оператор '%' (або *модуль*) повертає залишок від цілого ділення:
>
> ~~~
> print('5 // 3:', 5//3)
> print('5 / 3:', 5/3)
> print('5 % 3:', 5%3)
> ~~~
> {: .language-python}
>
> ~~~
> 5 // 3: 1
> 5 / 3: 1.6666666666666667
> 5 % 3: 2
> ~~~
> {: .output}
>
> Але у Python 2 (та інших мовах), оператор `/` для двох цілих чисел буде виконувати ціле (`//`) ділення. Щоб виконати ділення з плаваючою крапкою, треба перетворити одне з цілих чисел на дійсне.
>
> ~~~
> print('5 // 3:', 1)
> print('5 / 3:', 1 )
> print('5 / float(3):', 1.6666667 )
> print('float(5) / 3:', 1.6666667 )
> print('float(5 / 3):', 1.0 )
> print('5 % 3:', 2)
> ~~~
>
> Нехай `num_subjects` - це загальне число людей які беруть участь у дослідженні,
> а `num_per_survey` - це число людей які можуть взяти участь у одному опитуванні.
> Як обчислити кількість досліджень, необхідну
> щоб опитати кожного один раз?
>
> > ## Рішення
> > Нам треба знайти мінимальну кількість опитувань необхідну щоб опитати кожного один раз, тобто
> > округлити до більшого цілого числа `num_subjects / num_per_survey`. Це
> > еківалентно виконанню цілого ділення за допомогою `//` з додаванням  1.
> > ~~~
> > num_subjects = 600
> > num_per_survey = 42
> > num_surveys = num_subjects // num_per_survey + 1
> >
> > print(num_subjects, 'subjects,', num_per_survey, 'per survey:', num_surveys)
> > ~~~
> > {: .language-python}
> > ~~~
> > 600 subjects, 42 per survey: 15
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Перетворення рядків у числа
>
> Коли доцільно, `float()` перетворить рядок на число з плаваючою крапкою,
> а `int()` перетворить число з плаваючою крапкою на ціле:
>
> ~~~
> print("string to float:", float("3.4"))
> print("float to int:", int(3.4))
> ~~~
> {: .language-python}
>
> ~~~
> string to float: 3.4
> float to int: 3
> ~~~
> {: .output}
>
> Однак якщо перетворення не має сенсу, то зʼявиться повідомлення про помилку
>
> ~~~
> print("string to float:", float("Hello world!"))
> ~~~
> {: .language-python}
>
> ~~~
> ---------------------------------------------------------------------------
> ValueError                                Traceback (most recent call last)
> <ipython-input-5-df3b790bf0a2> in <module>()
> ----> 1 print("string to float:", float("Hello world!"))
>
> ValueError: could not convert string to float: 'Hello world!'
> ~~~
> {: .error}
>
> Виходячи з цього, що Ви чекаєте від наступної програми?
>
> Що вона робить насправді?
>
> Як це пояснити?
>
> ~~~
> print("fractional string to int:", int("3.4"))
> ~~~
> {: .language-python}
> 
> > ## Рішення
> > Що можна чекати від цієї програми? Чому б не очікувати, що у Python 3 команда `int` 
> > перетворить рядок "3.4" на 3.4 та виконає додаткове перетворення у ціле число 3. Зрештою, Python 3 виконує багато іншої
> > магії - хіба це не частина його чарівності?
> > 
> > Однак Python 3 видає помилку. Чому? Можливо, щоб бути послідовним. Якщо ви прохаєте Python виконати два послідовні
> > перетворення типу, ви маєте явним образом вказати це у коді програми.
> >
> > ~~~
> > int("3.4")
> > int(float("3.4"))
> > ~~~
> > {: .language-python}
> > ~~~
> > In [2]: int("3.4")
> > ---------------------------------------------------------------------------
> > ValueError                                Traceback (most recent call last)
> > <ipython-input-2-ec6729dfccdc> in <module>()
> > ----> 1 int("3.4")
> > ValueError: invalid literal for int() with base 10: '3.4'
> > 3
> > ~~~
> > {: .output}
> {: .solution}
{: .challenge}

> ## Аріфметичні дії з різними типами
>
> Яка з наступних команд поверне дійсне число `2.0`?
> Примітка: це питання може мати декілька коректних відповідей.
>
> ~~~
> first = 1.0
> second = "1"
> third = "1.1"
> ~~~
> {: .language-python}
>
> 1. `first + float(second)`
> 2. `float(second) + float(third)`
> 3. `first + int(third)`
> 4. `first + int(float(third))`
> 5. `int(first) + int(float(third))`
> 6. `2.0 * second`
>
> > ## Рішення
> >
> > Відповідь: 1 та 4
> {: .solution}
{: .challenge}

> ## Комплексні числа
>
> Python підтримує комплексні числа,
> які записуються як `1.0+2.0j`.
> Якщо `val` - комплексне число,
> то до його дійсної та уявної частин можна отримати доступ за допомогою *крапкової нотації*
> як `val.real` та `val.imag`.
>
> ~~~
> complex = 6 + 2j
> print(complex.real)
> print(complex.imag)
> ~~~
> {: .language-python}
>
> ~~~
> 6.0
> 2.0
> ~~~
> {: .output}
>
>
> 1.  Чому, на Вашу думку, Python використовує `j` замість `i` для уявної частини?
> 2.  Що Ви очікуєте отримати від `1+2j + 3`?
> 3.  Що Ви очікуєте від `4j`?  А що від `4 j` або `4 + j`?
> 
> > ## Рішення
> >
> > 1. Стандартні математичні позначення зазвичай використовують `i` для позначення комплексного числа. Однак, судячи з різних джерел, це
> > було раннє позначення, яке використовувалось у електротехніці, та зараз було б дуже дорого його
> > змінити. [Stack Overflow містить додаткові пояснення та
> > обговорення.](http://stackoverflow.com/questions/24812444/why-are-complex-numbers-in-python-denoted-with-j-instead-of-i)
> > 2. `(4+2j)`
> > 3. `4j`, `Syntax Error: invalid syntax`, у цьому випадку _j_ вважається змінною, і це залежить від того, чи визначене _j_, і якщо так, то його присвоєне значення Front Matte: python-novice-gapminder/_episodes/04-built-in.md:sgid "---
title: "Built-in Functions and Help"
teaching: 15
exercises: 10
questions:
- "How can I use built-in functions?"
- "How can I find out what they do?"
- "What kind of errors can occur in programs?"
objectives:
- "Explain the purpose of functions."
- "Correctly call built-in Python functions."
- "Correctly nest calls to built-in functions."
- "Use help to display documentation for built-in functions."
- "Correctly describe situations in which SyntaxError and NameError occur."
keypoints:
- "Use comments to add documentation to programs."
- "A function may take zero or more arguments."
- "Commonly-used built-in functions include `max`, `min`, and `round`."
- "Functions may only work for certain (combinations of) arguments."
- "Functions may have default values for some arguments."
- "Use the built-in function `help` to get help for a function."
- "The Jupyter Notebook has two ways to get help."
- "Every function returns something."
- "Python reports a syntax error when it can't understand the source of a program."
- "Python reports a runtime error when something goes wrong while a program is executing."
- "Fix syntax errors by reading the source code, and runtime errors by tracing the program's execution."
---sgstr "---
title: "Вбудовані функції та довідка"
час вивчення: 15
практичні завдання: 10
питання:
- "Як я можу використовувати вбудовані функції?"
- "Як я можу дізнатися, що вони роблять?"
- "Які помилки можуть виникати в програмах?"
цілі:
- "Пояснення призначення функцій."
- "Коректний виклик вбудованих функцій Python."
- "Коректний виклик вкладених вбудованих функцій."
- "Використання довідки для перегляду документації про вбудовані функції."
- "Правильний опис ситуації, в яких виникають SyntaxError і NameError"
ключові моменти:
- "Використання коментарів при створенні документації програм."
- "Функція без аргументів та функція з довільною кількістю аргументів."
- "Поширені вбудовані функції `max`, `min` та `round`."
- "Функції можуть працювати лише з певними аргументами (комбінаціями аргументів)."
- "Функції можуть мати значення за замовчуванням для певних аргументів."
- "Використання вбудованої функції `help` для отримання довідки про функції".
- "Два шляхи отримання допомоги у Jupyter Notebook."
- "Кожна функція щось повертає."
- "Python повідомляє про синтаксичну помилку, коли джерело програми не зрозуміле."
- "Python повідомляє про помилку виконання, коли щось йде не так під час компілювання програми."
- "Виправлення синтаксичних помилок у процесі читання вихідного коду, а помилок виконання - у процесі компіляції програми."
> {: .solution}
{: .challenge}
