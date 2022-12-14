---
layout: reference
permalink: /reference/
root: ..
---

## Довідник

## [Запуск та завершення роботи]({{ page.root }}/01-run-quit/)
- Python файли мають розширення `.py`.
- Можуть бути створені у текстовому редакторі або у [Jupyter Notebook][jupyter].
  - Файли, створені в середовищі Jupyter notebook, мають розширення `.ipynb`
  - Файли, створені в середовищі Jupyter notebook,  можуть бути відкриті в [Anaconda](https://docs.continuum.io/anaconda/install) or through the command line by entering `$ jupyter notebook`
    - В комірках markdown для документування коду можна використовувати як Markdown так і HTML.

## [Змінні та присвоєння]({{ page.root }}/02-variables/)
- Значення змінних зберігаються за допомогою  `=`.
  - Рядки визначаються в лапках `'...'`.
  - Цілі числа та числа з плаваючою комою визначаються без лапок.
- Змінні можуть містити літери, цифри та символ підкреслення "_".
  - Не можуть починатися з цифри.
  - Слід уникати змінних, які починаються з підкреслення.
- Використовуйте `print(...)`, щоб відобразити значення як текст.
- Можна використовувати індексацію рядків.
  - Індексація починається з 0.
  - Позиція вказується в квадратних дужках `[position]` після імені змінної.
  - Зріз створюється за допомогою `[start:stop]`. Це робить копію частини вихідного рядка) 
    - `start` є індексом першого елемента.
    - `stop` є індексом елемента після останнього потрібного елемента.
- Використовуйте `len(...)` для визначення довжини змінної або рядка. 

## [Типи даних та їх перетворення]({{ page.root }}/03-types-conversion/)
- Кожна величина має тип. Це контролює дії, які можна з нею робити.
  - `int` є цілим числом
  - `float` представляє число з плаваючою комою.
  - `str` є рядком.
Щоб визначити тип змінної, скористайтеся вбудованою функцією `type(...)`, вказавши назву змінної в дужках.
- Модифікація рядків:
  - Використовуйте `+` для об'єднання (конкатенації) рядків.
  - Використовуйте `*`, щоб повторити рядок.
  - Числа та рядки не можна додавати один до іншого.
    - Перетворити рядок на ціле: `int(...)`.
    - Перетворити ціле на рядок : `str(...)`.

## [Вбудовані функції та довідка]({{ page.root }}/04-built-in/)
- Щоб додати коментар, поставте `#` перед тим, що ви не хочете виконувати.
- Вбудовані функції, які часто використовуються: 
  - `min()` визначає найменшу величину.
  - `max()` визначає найбільшу величину.
  - `round()` округлює число з плаваючою комою.
  - `help()` відображає документацію для функції в дужках.
    - Інші способи отримати допомогу включають одночасне натискання `shift` і `tab` у Jupyter Notebooks.

## [Бібліотеки]({{ page.root }}/06-libraries/)
- Імпорт бібліотеки:
  - Використовуйте `import ...` для підключення бібліотеки.
  - Звертайтеся до цієї бібліотеки у форматі `module_name.thing_name`.
    - `.` вказує на 'частину'.
- Щоб імпортувати певний елемент із бібліотеки, використовуйте команду `from ... import ...`
- Щоб імпортувати бібліотеку та створити її псевдонім, використовуйте команду `import ... as ...`
- Імпорт математичної бібліотеки: `import math`
  - Приклад посилання на елемент із назвою модуля: `math.cos(math.pi)`.
- Імпорт графічної бібліотеки та позначення її за допомогою псевдоніма: `import matplotlib as mpl`

## [Читання табличних даних у фреймах даних]({{ page.root }}/07-reading-tabular/)
- Використовуйте бібліотеку pandas для статистичної обробки табличних даних. Завантажуйте її за допомогою `import pandas as pd`.
  - Щоб прочитати дані у файлі csv, використовуйте команду: `pd.read_csv()`, включаючи шлях до файлу в дужках.
    - Щоб указати значення стовпця, слід використовувати наступний формат заголовків рядків: `pd.read_csv('path',index_col='column name')`, де `path` і `column name` замінюються відповідними значеннями. 
- Щоб отримати більше інформації про фрейм даних, використовуйте `DataFrame.info`, замінивши `DataFrame` назвою вашого файлу даних.
- Використовуйте команду `DataFrame.columns` щоб переглянути назви стовпців.
- Використовуйте `DataFrame.T` щоб транспонувати фрейм даних.
- Використовуйте `DataFrame.describe`, щоб отримати підсумкову статистику ваших даних.

## [Pandas DataFrames]({{ page.root }}/08-data-frames/)
- Вибір даних за допомогою `[i,j]`
  - Вибір за місцезнаходженням: `DataFrame.iloc[..., ...]`
    - Це включає весь діапазон, крім останнього індексу.
  - Для вибору за міткою запису використовуйте: `DataFrame.loc[..., ...]`
    - Можна вибрати кілька рядків або стовпців визначенням діапазону міток.
    - Кінцеві індекси включно з обох боків.
  - Використовуйте `:`, щоб обрати всі рядки або стовпці.
- Також можна вибирати дані на основі значень за допомогою `true` і `false`. Це Булева маска.
  - Наприклад, `mask = subset > 10000`
  - Ми можемо потім використовувати вище визначену маску для вибору значень.
- Формат комбінованої операції select-apply є таким: `data.apply(lambda x: x>x.mean())`, де `mean()` може бути будь-якою операцією, яку користувач хоче застосувати до набору даних x. 

## [Пoбудова графіків]({{ page.root }}/09-plotting/)
- `matplotlib` є найбільш широко використовуваною бібліотекою побудови графіків.
  - Зазвичай імпортується за допомогою `import matplotlib.pyplot as plt`.
  - Для побудови графіків використовується команда `plt.plot(time, position)`.
  - Для створення легенди використовується команда `plt.legend(['label1','label2', loc='upper left'])`
    - Можна також визначати мітки в операторах plot за допомогою команди `plt.plot(time, position, label='label')`. Щоб відобразити легенду, використовуйте `plt.legend()`
  - Для позначення осей x і y використовуються команди `plt.xlabel('label')` і `plt.ylabel('label')`.
- Pandas DataFrames можна використовувати для побудови графіків, застосовуючи команду `DataFrame.plot()`. Будь-які операції, які можна використовувати на DataFrame, можна застосовувати для побудови графіків.
  - Для побудови гістограми застосовуйте команду `data.plot(kind='bar')`

~~~
import matplotlib.puplot as plot
plt.plot(time,position,label='label')
plt.xlabel('x axis label')
plt.ylabel('y axis label')
plt.legend()
~~~
{: .language-python}

## [Списки]({{ page.root }}/11-lists/)
- Містяться у `[...]` і розділяються за допомогою `,`.
  - Порожній список можна створити за допомогою `[]`.
- Можна використовувати `len(...)`, щоб визначити кількість значень у списку.
- Можна індексувати так само, як це виконувалось в попередніх уроках.
  - Індексацію можна використовувати для перепризначення значень: `назва_списку[0] = нове значення`
- Щоб додати елемент до списку, використовуйте `list_name.append()`, указавши у дужках елемент, який потрібно додати.
- Щоб об’єднати два списки, використовуйте `list_name_1.extend(list_name_2)`.
- Щоб видалити елемент зі списку, використовуйте `del list_name[index]`.

## [Цикли for]({{ page.root }}/12-for-loops/)
- Почніть цикл for з `for number in [1,2,3]:` з відступом у наступних рядках.
  - `[1, 2, 3]` розглядається як колекція.
  - `number` є змінною цикла.
  - Дія, наступна за колекцією, є тілом циклу.
- Для повторення послідовності дій зі змінною циклу використовуйте `range(start, end)`

~~~
for number in range(0,5):
  print(number)
~~~
{: .language-python}

## [Умовні оператори]({{ page.root }}/13-conditionals/)
- Визначаються подібно до циклу з використанням формату `if variable умовне значення:` 
  - Наприклад, `if variable > 5:`.
- Використовуйте `elif:` для додаткових тестів.
- Використовуйте `else:`, якщо твердження if є невірним.
- Можна об’єднати більше ніж одну умову за допомогою `and` або `or`.
- Часто використовується в поєднанні з циклами for.
- Умови, які можна використовувати:
  - `==` дорівнює.
  - `>=` більше або дорівнює.
  - `<=` менше або дорівнює.
  - `>` більше за.
  - `<` менше за.

~~~
for m in [3, 6, 7, 2, 8]:
  if m > 5:
    print(m, 'is large')
  elif m == 5:
    print(m, 'is 5')
  else:
    print(m, 'is small')
~~~
{: .language-python}

## [Перегляд наборів даних в циклі]({{ page.root }}/14-looping-data-sets/)
- Використовуйте цикл for: `for filename in [file1, file2]:`
- Щоб знайти набір файлів за шаблоном, використовуйте `glob.glob`
  - Спочатку потрібно імпортувати відповідну бібліотеку за допомогою `import glob`.
  - `*` вказує, що "нуль або більше символів збігаються"
  - `?` вказує, що "тільки один символ збігається"
    - Наприклад: `glob.glob(*.txt)` знайде всі файли з розширенням .txt у поточному каталозі.
- Поєднайте це, написавши цикл за допомогою: `for filename in glob.glob(*.txt):`

~~~
for filename in glob.glob(*.txt):
  data = pd.read_csv(filename)
~~~
{: .language-python}

## [Написання функцій]({{ page.root }}/16-writing-functions/)
- Визначайте функцію за допомогою `def function_name(parameters):`. Змініть `parameters` на змінні, які використовуватимуться під час виконання функції.
- Запустіть функцію за допомогою `function_name(parameters)`.
- Щоб повернути результат у місце виклику, використовуйте `return ...` в тілі функції.

~~~
def add_numbers(a, b):
  result = a + b
  return result

add_numbers(1, 4)
~~~
{: .language-python}

## [Область видимості змінної]({{ page.root }}/17-scope/)
- Локальна змінна визначена у функції, і її можна побачити та використовувати лише в цій функції.
- Глобальна змінна визначається поза функцією, і її можна побачити або використати будь-де після її визначення.

## [Стиль програмування]({{ page.root }}/18-style/)
- Документуйте свій код.
- Використовуйте чіткі та зрозумілі назви змінних.
- Притримуйтесь [the PEP8 style guide](https://www.python.org/dev/peps/pep-0008) під час налаштування коду.
- Використовуйте твердження для перевірки внутрішніх помилок.
- Використовуйте docstrings для створення довідки.

## Словник

{:auto_ids}
Аргументи
:     Значення, що передаються функціям.

Масив
:     контейнер, що містить елементи одного типу

Булевий 
:     об’єкт, що складається з `true` і `false`

Фрейм даних
:     Засіб подання таблиці у Pandas; колекція серій.

Element
:     Окреме значення у списку або масиві. Для рядка це окремі символи.

Функція
:     блок коду, який можна викликати та повторно використовувати деінде.

Глобальна змінна
:     Змінна, визначена поза функцією, яку можна використовувати будь-де.

Індекс
:     Позиція даного елемента.

Jupyter Notebook
:   Інтерактивне середовище кодування, що дозволяє поєднувати код і розмітку.

Бібліотека
:     Колекція файлів, що містять функції, які використовуються іншими програмами.

Локальна змінна
:     Змінна, визначена всередині функції, яку можна використовувати лише всередині цієї функції.

Маска
:     Булевий об’єкт, який використовується для вибору даних з іншого об’єкта.

Метод
:     Дія, пов'язана з певним об'єктом. Викликається за допомогою `object.method`.

Модулі
:     файли в бібліотеці, що містять функції, які використовуються іншими програмами.

Параметри
:     Змінні, що використовуються під час виконання функції.

Серія 
:    Структура даних Pandas для подання стовпця.

Підрядок
:     Частина рядка.

Змінні
:     Назви значень.

