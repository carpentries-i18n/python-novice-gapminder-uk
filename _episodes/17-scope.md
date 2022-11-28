## Область змінної - це частина програми, яка може "бачити" цю зміну.

*   Є дуже багато розумних імен для змінних.
*  Людям, які використовують функції, не варто хвилюватися,
    яке ім'я змінної використав автор функції.
* Людям, які пишуть функції, не варто хвилюватися,
які імена змінних використовує виклик функції.
* Частина програми, в якій змінна є видимою, називається її *областю*.

~~~
pressure = 103.9

def adjust(t):
    temperature = t * 1.43 / pressure
    return temperature
~~~
{: .language-python}

*   `pressure` є *глобальною змінною*.
    *   Визначається поза будь-якою конкретною функцією.
    *   Є видимою у будь-якому місці програми.
*   `t` та `temperature` є *локальними змінними* в `adjust`.
    *   Визначені у функції.
    *   Не є видимими у головній програмі.
    *   Пам'ятайте: параметр функції є змінною,
        якій автоматично присвоюється значення під час виклику функції.

~~~
print('adjusted:', adjust(0.9))
print('температура після виклику функції:', temperature)
~~~
{: .language-python}
~~~
adjusted: 0.01238691049085659
~~~
{: .output}
~~~
Traceback (most recent call last):
  File "/Users/swcarpentry/foo.py", line 8, in <module>
    print('temperature after call:', temperature)
NameError: name 'temperature' is not defined
~~~
{: .error}

> ## Використання локальних і глобальних змінних
>
> Відстежте значення всіх змінних у цій програмі під час її виконання.
> (Використовуйте '---' як значення змінних до і після їх існування.)
>
> ~~~
> limit = 100
>
> def clip(value):
>     return min(max(0.0, value), limit)
>
> value = -22.5
> print(clip(value))
> ~~~
> {: .language-python}
{: .challenge}

> ## Читання повідомлень про помилки
>
> Прочитайте системну діагностику нижче та визначте наступне:
>
> 1. Скільки рівнів має трасування помилок?
> 2. Як називається файл, у якому сталася помилка?
> 3. Як називається функція, у якій сталася помилка?
> 4. Який номер рядка цієї функції, де виникла помилка?
> 5. Який тип помилки?
> 6. Яке повідомлення про помилку?
>
> ~~~
> ---------------------------------------------------------------------------
> KeyError                                  Traceback (most recent call last)
> <ipython-input-2-e4c4cbafeeb5> in <module>()
>       1 import errors_02
> ----> 2 errors_02.print_friday_message()
>
> /Users/ghopper/thesis/code/errors_02.py in print_friday_message()
>      13
>      14 def print_friday_message():
> ---> 15     print_message("Friday")
>
> /Users/ghopper/thesis/code/errors_02.py in print_message(day)
>       9         "sunday": "Aw, the weekend is almost over."
>      10     }
> ---> 11     print(messages[day])
>      12
>      13
>
> KeyError: 'Friday'
> ~~~ Front Matte: python-novice-gapminder/_episodes/18-style.md:sgid "---
title: "Programming Style"
teaching: 15
exercises: 15
questions:
- "How can I make my programs more readable?"
- "How do most programmers format their code?"
- "How can programs check their own operation?"
objectives:
- "Provide sound justifications for basic rules of coding style."
- "Refactor one-page programs to make them more readable and justify the changes."
- "Use Python community coding standards (PEP-8)."
keypoints:
- "Follow standard Python style in your code."
- "Use docstrings to provide builtin help."
---sgstr "---
title: "Стиль програмування"
teaching: 15
exercises: 15
questions:
- "Як я можу зробити мої програми більш читабельними?"
- "Як більшість програмістів форматують свій код?"
- "Як програми можуть перевірити свою роботу?"
objectives:
- "Визначення основних правил стилю кодування"
- "Рефакторинг односторінкових програм, щоб зробити їх більш читабельними та обґрунтувати зміни"
- "Використовання стандартів кодування спільноти Python (PEP-8)."
keypoints:
- "Дотримуйтеся стандартного стилю Python у своєму коді."
- "Використовуйте рядки документів для надання вбудованої довідки"
---
> {: .error}
{: .challenge}

