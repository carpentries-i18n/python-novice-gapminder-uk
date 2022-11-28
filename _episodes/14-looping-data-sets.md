---
title: "Перегляд наборів даних в циклі"
teaching: 5
exercises: 10
questions:
- "Як я можу обробити багато наборів даних за допомогою однієї команди?"
objectives:
- "Вміти читати та писати  вирази глоббінгу, які відповідають наборам файлів"
- "Використовувати glob для створення списків файлів."
- "Писати цикли for для виконання операцій над файлами, названими у списку."
keypoints:
- "Використовуйте цикл `for` для обробки файлів із списком їх імен."
- "Використовуйте `glob.glob`, щоб знайти набори файлів, імена яких відповідають шаблону."
- "Використовуйте `glob` і `for` для обробки пакетів файлів."
---

## Використовуйте цикл `for`  для обробки файлів, заданих списком їхніх імен.

*   Ім'я файлу - це рядок символів.
*   І списки можуть містити рядки символів.

~~~
import pandas as pd
for filename in ['data/gapminder_gdp_africa.csv', 'data/gapminder_gdp_asia.csv']:
    data = pd.read_csv(filename, index_col='country')
    print(filename, data.min())
~~~
{: .language-python}
~~~
data/gapminder_gdp_africa.csv gdpPercap_1952    298.846212
gdpPercap_1957    335.997115
gdpPercap_1962    355.203227
gdpPercap_1967    412.977514
⋮ ⋮ ⋮
gdpPercap_1997    312.188423
gdpPercap_2002    241.165877
gdpPercap_2007    277.551859
dtype: float64
data/gapminder_gdp_asia.csv gdpPercap_1952    331
gdpPercap_1957    350
gdpPercap_1962    388
gdpPercap_1967    349
⋮ ⋮ ⋮
gdpPercap_1997    415
gdpPercap_2002    611
gdpPercap_2007    944
dtype: float64
~~~
{: .output}

## Використовуйте [`glob.glob`](https://docs.python.org/3/library/glob.html#glob.glob), щоб знайти набори файлів, імена яких відповідають шаблону.

*   В Unix термін "globbing" означає "відповідність набору файлів шаблону".
*   Найпоширеніші моделі:
    *   `*` означає "відповідати нулю або більшій кількості  символів"
    *   `?` означає "відповідати в точності одному символу"
*   Python містить бібліотеку [`glob`](https://docs.python.org/3/library/glob.html) для забезпечення функції зіставлення шаблонів
*   Бібліотека [`glob`](https://docs.python.org/3/library/glob.html) містить функцію, яка також називається `glob` для відповідності шаблонам файлів.
*   Наприклад, `glob.glob('*.txt')` відповідає всім файлам у поточному каталозі,
    імена яких закінчуються на `.txt`.
*   Результатом є (можливо, порожній) список рядків символів.

~~~
import glob
print('all csv files in data directory:', glob.glob('data/*.csv'))
~~~
{: .language-python}
~~~
all csv files in data directory: ['data/gapminder_all.csv', 'data/gapminder_gdp_africa.csv', \
'data/gapminder_gdp_americas.csv', 'data/gapminder_gdp_asia.csv', 'data/gapminder_gdp_europe.csv', \
'data/gapminder_gdp_oceania.csv']
~~~
{: .output}

~~~
print('all PDB files:', glob.glob('*.pdb'))
~~~
{: .language-python}
~~~
all PDB files: []
~~~
{: .output}

## Використовуйте `glob` і `for` для обробки пакетів файлів.

*   Дуже допомагає, якщо файли мають імена та зберігаються систематично та послідовно,
 так що прості шаблони знайдуть потрібні дані.

~~~
for filename in glob.glob('data/gapminder_*.csv'):
    data = pd.read_csv(filename)
    print(filename, data['gdpPercap_1952'].min())
~~~
{: .language-python}
~~~
data/gapminder_all.csv 298.8462121
data/gapminder_gdp_africa.csv 298.8462121
data/gapminder_gdp_americas.csv 1397.717137
data/gapminder_gdp_asia.csv 331.0
data/gapminder_gdp_europe.csv 973.5331948
data/gapminder_gdp_oceania.csv 10039.59564
~~~
{: .output}

*   Це включає всі дані, а також дані по регіонах.
*   Використовуйте більш конкретний шаблон у вправах, щоб виключити весь набір даних.
*   Але зауважте, що мінімум усього набору даних також є мінімумом одного з наборів даних,
    що є хорошою перевіркою правильності.

> ## Визначення збігів
>
> Який із цих файлів *не* відповідає виразу `glob.glob('data/*as*.csv')`?
>
> 1. `data/gapminder_gdp_africa.csv`
> 2. `data/gapminder_gdp_americas.csv`
> 3. `data/gapminder_gdp_asia.csv`
> 4. 1 and 2 are not matched.
>
> > ## Рішення
> >
> > 1 не відповідає glob.
> {: .solution}
{: .challenge}

> ## Мінімальний розмір файлу
>
> Змініть цю програму так, щоб вона друкувала кількість записів
> файлі, який містить найменшу кількість записів
>
> ~~~
> import glob
> import pandas as pd
> fewest = ____
> for filename in glob.glob('data/*.csv'):
>     dataframe = pd.____(filename)
>     fewest = min(____, dataframe.shape[0])
> print('smallest file has', fewest, 'records')
> ~~~
> {: .language-python}
> Зауважте, що [shape method](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.shape.html)
> повертає кортеж із кількістю рядків і стовпців фрейму даних.
>
> > ## Рішення
> > ~~~
> > import glob
> > import pandas as pd
> > fewest = float('Inf')
> > for filename in glob.glob('data/*.csv'):
> >     dataframe = pd.read_csv(filename)
> >     fewest = min(fewest, dataframe.shape[0])
> > print('smallest file has', fewest, 'records')
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

> ## Порівняння даних
>
> Напишіть програму, яка читає регіональні набори даних
> і будує графік середнього ВВП на душу населення для кожного регіону в часі
> в одній діаграмі.
> > ## Рішення
> > Це рішення створює корисну легенду за допомогою методу string [`split`](https://docs.python.org/3/library/stdtypes.html#str.split) для
> > вилучення  `region` зі шляху 'data/gapminder_gdp_a_specific_region.csv'. [`pathlib module`]
> > також забезпечує корисні абстракції для маніпулювання файлами та шляхами, такі як  повернення назви файлу 
> > без розширення файлу.
> > ~~~
> > import glob
> > import pandas as pd
> > import matplotlib.pyplot as plt
> > fig, ax = plt.subplots(1,1)
> > for filename in glob.glob('data/gapminder_gdp*.csv'):
> >     dataframe = pd.read_csv(filename)
> >     # вилучіть <region> з імені файла, який має бути у форматі 'data/gapminder_gdp_<region>.csv'.
> >     # ми розділимо рядок за допомогою методу split та з викоританням `_` як роздільника,
> >     # отримаємо останній рядок у списку, який повертає розділений (`<region>.csv`), 
> >     # та потім видалимо розширення `.csv` з того рядка.
> >     region = filename.split('_')[-1][:-4] 
> >     dataframe.mean().plot(ax=ax, label=region)
> > plt.legend()
> > plt.show()
> > ~~~
> > {: .language-python}
> {: .solution}
{: .challenge}

