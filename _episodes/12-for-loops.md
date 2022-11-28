---
title: "Цикли for"
teaching: 10
exercises: 15
questions:
- "Як змусити програму робити багато речей?"
objectives:
- "Поясніть, для чого зазвичай використовуються цикли for."
- "Відстежуйте виконання простого (невкладеного) циклу та правильно вказуйте значення змінних у кожній ітерації."
- "Пишить цикли for, які використовують паттерн накопичувача для агрегування значень."  
keypoints:
- "Цикл *for* виконує команди один раз для кожного значення в колекції."
- "Цикл `for` складається з колекції, змінної циклу та тіла."
- "Перший рядок циклу `for` має закінчуватися двокрапкою, а тіло має бути з відступом."
- "Відступи завжди важливі в Python."
- "Змінні циклу можна називати як завгодно (але настійно рекомендується мати значущу назву для змінної циклу)."
- "Тіло циклу може містити багато операторів."
- "Використовуйте `range` для перебору послідовності чисел."
- "Патерн накопичувача перетворює багато значень в одне."
---
## *Цикл for* виконує команди один раз для кожного значення в колекції.

*   Виконувати обчислення для значень у списку одне за іншим
    так само неприємно, як працювати з `pressure_001`, `pressure_002` і так далі.
*  *Цикл for* повідомляє Python виконати деякі оператори один раз для кожного значення в списку,
    рядку символів,
    або якісь іншій колекції.
*   "для кожного елемента в цій групі виконайте ці операції"

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

*   Цей цикл `for` є еквівалентним:

~~~
print(2)
print(3)
print(5)
~~~
{: .language-python}

*   І результат циклу `for` є таким:

~~~
2
3
5
~~~
{: .output}

## Цикл `for` складається з колекції, змінної циклу та тіла.

~~~
for number in [2, 3, 5]:
    print(number)
~~~
{: .language-python}

*   Колекція `[2, 3, 5]` є тим, на чому виконується цикл.
*   Тіло, `print(number)`, визначає, що робити для кожного значення в колекції.
*   Змінна циклу, `number`, змінюється для кожної *ітерації* циклу.
    *   "Актуальне".

## Перший рядок циклу `for` має закінчуватися двокрапкою, а тіло має бути з відступом.

*   Двокрапка в кінці першого рядка вказує на початок *блоку* операторів.
*   Python використовує відступ, а не `{}` або `begin`/`end`, щоб показати *вкладеність*.
    *   Будь-який послідовний відступ допустимий, але майже кожен використовує чотири пробіли.

~~~
for number in [2, 3, 5]:
print(number)
~~~
{: .language-python}
~~~
IndentationError: expected an indented block
~~~
{: .error}

*   Відступи завжди важливі в Python.

~~~
firstName = "Jon"
  lastName = "Smith"
~~~
{: .language-python}
~~~
  File "<ipython-input-7-f65f2962bf9c>", line 2
    lastName = "Smith"
    ^
IndentationError: unexpected indent
~~~
{: .error}

*   Цю помилку можна виправити, видаливши зайві пробіли
    на початку другого рядка.

## Змінні циклу можна називати як завгодно 

*   Як і всі інші змінні, змінні циклу:
    *   Створені на замовлення.
    *   Безглуздо: їхні імена можуть бути будь-якими.

~~~
for kitten in [2, 3, 5]:
    print(kitten)
~~~
{: .language-python}

## Тіло циклу може містити багато операторів.

*   Але жоден цикл не повинен мати довжину більше кількох рядків.
*   Людям важко запам’ятати великі фрагменти коду.

~~~
primes = [2, 3, 5]
for p in primes:
    squared = p ** 2
    cubed = p ** 3
    print(p, squared, cubed)
~~~
{: .language-python}
~~~
2 4 8
3 9 27
5 25 125
~~~
{: .output}

## Використовуйте `range` для перебору послідовності чисел.

*   Вбудована функція [`range`](https://docs.python.org/3/library/stdtypes.html#range) створює послідовність чисел.
    *   *Не* список: номери виготовляються на замовлення
        щоб зробити цикл у великих діапазонах більш ефективним.
*   `range(N)`  - це числа 0..N-1
    *   Точно допустимі індекси списку або рядка символів довжиною N

~~~
print('a range is not a list: range(0, 3)')
for number in range(0, 3):
    print(number)
~~~
{: .language-python}
~~~
a range is not a list: range(0, 3)
0
1
2
~~~
{: .output}

## Патерн накопичувача перетворює багато значень в одне.

*   Загальний паттерн у програмах:
    1.  Ініціалізуйте *накопичувальну* змінну нулем, порожнім рядком або порожнім списком.
    2.  Оновіть змінну значеннями з колекції.

~~~
# Знайдіть суму перших 10 цілих чисел.
total = 0
for number in range(10):
   total = total + (number + 1)
print(total)
~~~
{: .language-python}
~~~
55
~~~
{: .output}

*   Прочитайте `total = total + (number + 1)` наступним чином:
    *   Додати 1 до поточного значення  змінної циклу `number`.
    *   Додати це до поточного значення накопичувальної змінної `total`.
    *   Призначити це `total`, замінивши поточне значення.
*   Ми маємо додавати `number + 1`, тому що `range` продукує 0..9, а не  1..10.

> ## Класифікація помилок
>
> Помилка відступу є синтаксичною чи помилкою виконання?
> > ## Рішення
> > IndentationError є синтаксичною помилкою. Неможливо запустити програми з синтаксичними помилками.
> > Програма з помилкою виконання запускається, але за певних умов видається помилка.
> {: .solution}
{: .challenge}

> ## Відстеження виконання
>
> Створіть таблицю з номерами рядків, які виконуються під час виконання цієї програми,
> і значення змінних після виконання кожного рядка.
>
> ~~~
> total = 0
> for char in "tin":
>     total = total + 1
> ~~~
> {: .language-python}
> > ## Solution
> >
> > | Line no | Variables            |
> > |---------|----------------------|
> > | 1       | total = 0            |
> > | 2       | total = 0 char = 't' |
> > | 3       | total = 1 char = 't' |
> > | 2       | total = 1 char = 'i' |
> > | 3       | total = 2 char = 'i' |
> > | 2       | total = 2 char = 'n' |
> > | 3       | total = 3 char = 'n' |
> {: .solution}
{: .challenge}

> ## Перевертання рядка
>
> Заповніть порожні місця в програмі нижче, щоб вона друкувала "nit"
> (зворотний вихідний рядок символів "tin").
>
> ~~~
> original = "tin"
> result = ____
> for char in original:
>     result = ____
> print(result)
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > original = "tin"
> > result = ""
> > for char in original:
> >     result = char + result
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Практика накопичення.
>
> Заповніть пропуски в кожній із наведених нижче програм,
> щоб отримати вказаний результат
>
> ~~~
> # Загальна довжина рядків у списку: ["red", "green", "blue"] => 12
> total = 0
> for word in ["red", "green", "blue"]:
>     ____ = ____ + len(word)
> print(total)
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > total = 0
> > for word in ["red", "green", "blue"]:
> >     total = total + len(word)
> > print(total)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Список довжин слів: ["red", "green", "blue"] => [3, 5, 4]
> lengths = ____
> for word in ["red", "green", "blue"]:
>     lengths.____(____)
> print(lengths)
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > lengths = []
> > for word in ["red", "green", "blue"]:
> >     lengths.append(len(word))
> > print(lengths)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Concatenate all words: ["red", "green", "blue"] => "redgreenblue"
> words = ["red", "green", "blue"]
> result = ____
> for ____ in ____:
>     ____
> print(result)
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > words = ["red", "green", "blue"]
> > result = ""
> > for word in words:
> >     result = result + word
> > print(result)
> > ~~~
> > {: .language-python}
> {: .solution}
>
> ~~~
> # Створіть акронім: ["red", "green", "blue"] => "RGB"
> # Напишіть всю прграму
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > acronym = ""
> > for word in ["red", "green", "blue"]:
> >     acronym = acronym + word[0].upper()
> > print(acronym)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Кумулятивна сума
>
> Змініть порядок і належним чином розставте рядки коду нижче
> щоб в результаті отримати список із сукупною сумою даних.
> Результатом має бути `[1, 3, 5, 10]`.
>
> ~~~
> cumulative.append(sum)
> for number in data:
> cumulative = []
> sum += number
> sum = 0
> print(cumulative)
> data = [1,2,2,5]
> ~~~
> {: .language-python}
> > ## Рішення
> > ~~~
> > sum = 0
> > data = [1,2,2,5]
> > cumulative = []
> > for number in data:
> >     sum += number
> >     cumulative.append(sum)
> > print(cumulative)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Виявлення помилок імен змінних
>
> 1. Прочитайте наведений нижче код і спробуйте визначити, у чому полягають помилки
>    *без* запуску програми.
> 2. Запустіть код і прочитайте повідомлення про помилку.
>   Як ви думаєте, який це тип `NameError`?
>   Це рядок без лапок, змінна з орфографічною помилкою чи 
>    змінна, яка мала бути визначена, але не була визначена?
> 3. Виправте помилку.
> 4. Повторюйте кроки 2 і 3, доки не виправите всі помилки.
>
> ~~~
> for number in range(10):
>     # use a if the number is a multiple of 3, otherwise use b
>     if (Number % 3) == 0:
>         message = message + a
>     else:
>         message = message + "b"
> print(message)
> ~~~
> {: .language-python}
> > ## Рішення
> > TЗмінну `message` потрібно ініціалізувати, а назви змінних Python чутливі до регістру: `number` і `Number`
> > посилаються на різні змінні.
> > ~~~
> > message = ""
> > for number in range(10):
> >     # use a if the number is a multiple of 3, otherwise use b
> >     if (number % 3) == 0:
> >         message = message + "a"
> >     else:
> >         message = message + "b"
> > print(message)
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Виявлення помилок програми
>
> 1. Прочитайте наведений нижче код і спробуйте визначити, у чому полягають помилки
>    *без* запуску програми.
> 2. Запустіть код і прочитайте повідомлення про помилку. Який тип помилки?
> 3. Виправте помилку.
>
> ~~~
> seasons = ['Spring', 'Summer', 'Fall', 'Winter']
> print('My favorite season is ', seasons[4])
> ~~~
> {: .language-python}
> > ## Рішення
> > Цей список складається з 4 елементів, а індекс для доступу до останнього елемента в списку – «3».
> > ~~~
> > seasons = ['Spring', 'Summer', 'Fall', 'Winter']
> > print('My favorite season is ', seasons[3])
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

