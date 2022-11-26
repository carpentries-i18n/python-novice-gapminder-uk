## Список зберігає багато значень в одній структурі.

*   Виконання обчислень із сотнею змінних під назвою `pressure_001`, `pressure_002` тощо,
    було б принаймні так само повільно, як робити їх вручну.
*   Використовуйте *список* для зберігання багатьох значень разом.
    *   Список позначається квадратними дужками `[...]`.
    *   Значення розділені комами `,`.
*   Використовуйте `len`, щоб дізнатися, скільки значень у списку.

~~~
pressures = [0.273, 0.275, 0.277, 0.275, 0.276]
print('pressures:', pressures)
print('length:', len(pressures))
~~~
{: .language-python}
~~~
pressures: [0.273, 0.275, 0.277, 0.275, 0.276]
length: 5
~~~
{: .output}

## Використовуйте індекс елемента, щоб отримати його зі списку.

*   Так само, як при опрацюванні рядків.

~~~
print('zeroth item of pressures:', pressures[0])
print('fourth item of pressures:', pressures[4])
~~~
{: .language-python}
~~~
zeroth item of pressures: 0.273
fourth item of pressures: 0.276
~~~
{: .output}

## Значення елементів списків можна замінити шляхом присвоєння.

*   Використовуйте вираз індексу ліворуч від знаку присвоєння, щоб замінити значення.

~~~
pressures[0] = 0.265
print('нові значення pressures:', pressures)
~~~
{: .language-python}
~~~
Нові значення pressures: [0.265, 0.275, 0.277, 0.275, 0.276]
~~~
{: .output}

## Додавання елементів до списку подовжує його.

*   Використовуйте `list_name.append`, щоб додати елементи в кінець списку.

~~~
primes = [2, 3, 5]
print('початкові значення списку primes:', primes)
primes.append(7)
primes.append(9)
print('список primes змінився:', primes)
~~~
{: .language-python}
~~~
початкові значення primes: [2, 3, 5]
список primes змінився: [2, 3, 5, 7, 9]
~~~
{: .output}

*   `append` є *методом* списку.
    *   Як функція, але прив’язаний до певного об’єкта.
*   Використовуйте `object_name.method_name` для виклику методів.
    *   Спеціально  нагадує те, як ми називаємо складові бібліотеки.
*   По ходу роботи ми познайомимося з іншими методами списків.
    *  Використовуйте `help(list)` для попереднього перегляду.
*  метод `extend` схожий на `append`, але він дозволяє об’єднувати два списки. Наприклад:

~~~
teen_primes = [11, 13, 17, 19]
middle_aged_primes = [37, 41, 43, 47]
print('поточний список primes:', primes)
primes.extend(teen_primes)
print('розширений список primes:', primes)
primes.append(middle_aged_primes)
print('фінальний список primes:', primes)
~~~
{: .language-python}
~~~
поточний список primes: [2, 3, 5, 7, 9]
розширений список primes: [2, 3, 5, 7, 9, 11, 13, 17, 19]
фінальний список primes: [2, 3, 5, 7, 9, 11, 13, 17, 19, [37, 41, 43, 47]]
~~~
{: .output}

Зауважимо, що хоча `extend` підтримує "плоску" структуру списку, додавання списку до списку дає результат
двовимірний - останній елемент у `primes` є списком, а не цілим числом.

## Використовуйте `del`, щоб повністю видалити елементи зі списку.

*   `del list_name[index]` видаляє елемент зі списку та скорочує список.
*   Це оператор мови, а не функція і не метод.

~~~
primes = [2, 3, 5, 7, 9]
print('список primes перед видаленням останнього елемента:', primes)
del primes[4]
print('список primes після видалення останнього елемента:', primes)
~~~
{: .language-python}
~~~
список primes перед видаленням останнього елемента: [2, 3, 5, 7, 9]
список primes після видалення останнього елемента: [2, 3, 5, 7]
~~~
{: .output}

## Порожній список не містить значень.

*   Використовуйте `[]`, щоб представити список, який не містить жодних значень.
    *   "Нуль списків."
*   Є корисним як початкова точка для збору значень
        (ми це побачимо в [наступному_параграфі]({% link _episodes/12-for-loops.md %}).

## Списки можуть містити значення різних типів.

*   Один список може містити числа, рядки та будь-що інше.

~~~
goals = [1, 'Створити списки.', 2, 'Вилучити елементи із списків.', 3, 'Змінити списки.']
~~~
{: .language-python}

## Рядки символів можна індексувати як списки.

*   Отримати окремі символи з рядка символів  можна за допомогою індексів у квадратних дужках.

~~~
element = 'carbon'
print('нульовий символ:', element[0])
print('третій символ:', element[3])
~~~
{: .language-python}
~~~
нульовий символ: c
третій символ: b
~~~
{: .output}

## Рядки символів незмінні.

*   Неможливо змінити символи в рядку після його створення.
    *   *Незмінний*: не можна змінити після створення.
    *   На відміну від рядків, списки є *змінними*: їх можна змінювати на місці.
*   Python розглядає рядок як одне значення з частинами,
  а не як сукупність значень.

~~~
element[0] = 'C'
~~~
{: .language-python}
~~~
TypeError: об'єкт 'str' не підтримує призначення елементів
~~~
{: .error}

*   Списки та рядки символів є *колекціями*.

## Індексація після кінця колекції є помилкою.

*   Python повідомляє про помилку IndexError, якщо ми намагаємося отримати доступ до значення, якого не існує.
    *   Це свого роду [помилка виконання]({{ page.root }}/04-built-in/#runtime-error).
* Цю помилку неможливо виявити під час аналізу коду,
        оскільки індекс може бути розрахований на основі даних.

~~~
print('99м елементом елемента є:', element[99])
~~~
{: .language-python}
~~~
IndexError: string index out of range
~~~
{: .output}

> ## Заповнити пропущені місця
>
> Заповніть порожні поля, щоб програма, наведена нижче, видала показаний результат.
>
> ~~~
> values = ____
> values.____(1)
> values.____(3)
> values.____(5)
> print('перший раз:', values)
> values = values[____]
> print('другий раз:', values)> ~~~
> {: .language-python}
>
> ~~~
> перший раз: [1, 3, 5]
> другий раз: [3, 5]
> ~~~
> {: .output}
>
> > ## Рішення
> > ~~~
> > values = []
> > values.append(1)
> > values.append(3)
> > values.append(5)
> > print('перший раз:', values)
> > values = values[1:]
> > print('другий раз:', values)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Наскільки є великим зріз?
>
> Якщо «low» і «high» є невід’ємними цілими числами,
> яка довжина списку `values[low:high]`?>
> > ## Рішення
> > Список `values[low:high]` має `high - low` elements.  Наприклад,
> > `values[1:4]` має 3 елементи `values[1]`, `values[2]`, and `values[3]`.
> >Зауважимо, що зріз працюватиме, лише якщо `high` менше загальної
> > довжини списку `значень`.
> {: .solution}
{: .challenge}

> ## Від рядків до списків і назад.
>
> Дано:
>
> ~~~
> print('рядок у список:', list('tin'))
> print('список у рядок:', ''.join(['g', 'o', 'l', 'd']))
> ~~~
> {: .language-python}
> ~~~
> ['t', 'i', 'n']
> 'gold'
> ~~~
> {: .output}
>
> 1.  Що робить `list('якийсь рядок')`?
> 2.  Що генерує `'-'.join(['x', 'y', 'z'])`?>
> > ## Рішення
> > 1. [`list('якийсь рядок')`](https://docs.python.org/3/library/stdtypes.html#list) перетворює рядок на список, що містить усі його символи.
> > 2. [`join`](https://docs.python.org/3/library/stdtypes.html#str.join) повертає рядок, який є _конкатенацією_
> >    кожного елемента рядка у списку та додає роздільник між кожним елементом у списку. Це призводить до
> >    `x-y-z`. Роздільником між елементами є рядок, який забезпечує цей метод.
> {: .solution}
{: .challenge}

> ## Почати з кінця
>
> Що друкує наступна програма?
>
> ~~~
> element = 'helium'
> print(element[-1])
> ~~~
> {: .language-python}
>
> 1.  Як Python інтерпретує від'ємний  індекс?
> 2.  Якщо список або рядок містить N елементів,
>    який найбільший за модулем від'ємний індекс можна безпечно використовувати,
>     і яку локацію визначає цей індекс?
> 3.  Якщо `values` є списком, що робить `del values[-1]`
> 4.  Як ви можете відобразити всі елементи, крім останнього, не змінюючи `values`?
>     (Підказка: вам потрібно буде поєднати зрізи та від'ємну індексацію.)
>
> > ## Рішення
> > Програма надрукує `m`.
> > 1. Python інтерпретує від'ємний індекс як початок з кінця (на відміну від
> >    початку).  Останній елемент – `-1`.
> > 2. Останнім індексом, який можна безпечно використовувати зі списком із N елементів, є елемент
> >    `-N`, який представляє перший елемент.
> > 3. `del values[-1]` видаляє останній елемент зі списку.
> > 4. `values[:-1]`
> {: .solution}
{: .challenge}

> ## Перехід по списку
>
> Що друкує наступна програма?
>
> ~~~
> element = 'fluorine'
> print(element[::2])
> print(element[::-1])
> ~~~
> {: .language-python}
>
> 1.  Якщо ми пишемо фрагмент як `low:high:stride`, що робить `stride`
> 2. Яка команда дозволить вибрати всі елементи з парними номерами з колекції?
>
> > ## Рішення
> > Програма надрукує
> > ~~~
> > furn
> > eniroulf
> > ~~~
> > {: .language-python}
> > 1. `stride` є розміром кроку зріза
> > 2. Зріз `1::2` вибирає всі елементи з парними номерами з колекції: він починається
> >    з елементу `1` (який є другим елементом, оскільки індексація починається з `0`),
> >    продовжується до кінця (оскільки `end` не задано) і використовує розмір кроку `2`
> >    (таким чином обираючи кожний другий елемент).
> {: .solution}
{: .challenge}

> ## Границі зрізу
>
> Що друкує наступна програма?
>
> ~~~
> element = 'lithium'
> print(element[0:20])
> print(element[-1:3])
> ~~~
> {: .language-python}
>
> > ## Рішення
> > ~~~
> > lithium
> > 
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Сортувати і бути відсортованим
>
> Що друкують ці дві програми?
> Простими словами поясніть різницю між `sorted(letters)` and `letters.sort()`.
>
> ~~~
> # Програма A
> letters = list('gold')
> result = sorted(letters)
> print('letters is', letters, 'and result is', result)
> ~~~
> {: .language-python}
>
> ~~~
> # Програма B
> letters = list('gold')
> result = letters.sort()
> print('letters is', letters, 'and result is', result)
> ~~~
> {: .language-python}
>
> > ## Рішення
> > Програма A друкує
> > ~~~
> > літери  ['g', 'o', 'l', 'd'] і результат є таким: ['d', 'g', 'l', 'o']
> > ~~~
> > {: .language-python}
> > Програма В друкує
> > ~~~
> > літери ['d', 'g', 'l', 'o'] і результат є None
> > ~~~
> > {: .language-python}
> > `sorted(letters)` повертає відсортовану копію списку `letters` (оригінал
> > списку `letters` залишається без змін), тоді як `letters.sort()` сортує список
> > `letters` на місці та нічого не повертає.
> {: .solution}
{: .challenge}

> ## Копіювання (чи Ні)
>
> Що друкують ці дві програми?
> Простими словами поясніть різницю між `new = old` and `new = old[:]`.
>
> ~~~
> # Програма A
> old = list('gold')
> new = old      # просте присвоювання
> new[0] = 'D'
> print('новим є', new, 'і старим є', old)
> ~~~
> {: .language-python}
>
> ~~~Програма B
> old = list('gold')
> new = old[:]   # присвоювання зріза
> new[0] = 'D'
> print('новим є', new, 'і старим є', old)
> ~~~
> {: .language-python}
>
> > ## Рішення
> > Програма А друкує
> > ~~~
> > новим є ['D', 'o', 'l', 'd'] і старим є ['D', 'o', 'l', 'd']
> > ~~~
> > Програма В друкує
> > ~~~
> > новим є ['D', 'o', 'l', 'd'] і старим є ['g', 'o', 'l', 'd']
> > ~~~
> > {: .language-python}
> > `new = old` робить `new` посиланням на список `old`; `new` and `old` вказують
> >  на той самий об'єкт.
> > 
> > `new = old[:]` однак створює новий об’єкт списку `new`, який містить усі елементи
> > зі списку `old`; `new` та `old` є різними об'єктами. Front Matte: python-novice-gapminder/_episodes/12-for-loops.md:sgid "---
title: "For Loops"
teaching: 10
exercises: 15
questions:
- "How can I make a program do many things?"
objectives:
- "Explain what for loops are normally used for."
- "Trace the execution of a simple (unnested) loop and correctly state the values of variables in each iteration."
- "Write for loops that use the Accumulator pattern to aggregate values."
keypoints:
- "A *for loop* executes commands once for each value in a collection."
- "A `for` loop is made up of a collection, a loop variable, and a body."
- "The first line of the `for` loop must end with a colon, and the body must be indented."
- "Indentation is always meaningful in Python."
- "Loop variables can be called anything (but it is strongly advised to have a meaningful name to the looping variable)."
- "The body of a loop can contain many statements."
- "Use `range` to iterate over a sequence of numbers."
- "The Accumulator pattern turns many values into one."
---sgstr "---
title: "Для циклів"
навчання: 10
вправи: 15
питання:
- "Як змусити програму робити багато речей?"
цілі:
- "Поясніть, для чого зазвичай використовуються цикли for."
- "Відстежуйте виконання простого (невкладеного) циклу та правильно вказуйте значення змінних у кожній ітерації."
- "Пишить цикли for, які використовують паттерн накопичувача для агрегування значень."  
ключові моменти:
- "Цикл *for* виконує команди один раз для кожного значення в колекції."
- "Цикл `for` складається з колекції, змінної циклу та тіла."
- "Перший рядок циклу `for` має закінчуватися двокрапкою, а тіло має бути з відступом."
- "Відступи завжди важливі в Python."
- "Змінні циклу можна називати як завгодно (але настійно рекомендується мати значущу назву для змінної циклу)."
- "Тіло циклу може містити багато операторів."
- "Використовуйте `range` для перебору послідовності чисел."
- "Патерн накопичувача перетворює багато значень в одне."
---
> {: .solution}
{: .challenge}
