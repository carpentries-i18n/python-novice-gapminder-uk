---
title: "Побудова графіків"
teaching: 15
exercises: 15
questions:
- "Я побудувати графік за моїми даними?"
- "Як зберегти графік для публікації?"
objectives:
- "Створити графік часового ряду для одного набору даних."
- "Створити діаграму розсіювання, що показує зв’язок між двома наборами даних."
keypoints:
- "[`matplotlib`](https://matplotlib.org/) є найбільш розповсюдженою графічною бібліотекою у Python."
- "Будуйте графіки безпосередньо з фрейму даних Pandas."
- "Виберіть і трансформуйте дані, а потім будуйте графік."
- "Доступно багато стилів графіку: перегляньте [Python Graph Gallery](https://python-graph-gallery.com/matplotlib/) for more options."
- "Можна будувати разом графіки за багатьма наборами даних."
---
## [`matplotlib`](https://matplotlib.org/)  є найбільш відомою науковою бібіліотекою візуалізації даних  на Python.

*   Найчастіше використовують підбібліотеку, що має назву [`matplotlib.pyplot`](https://matplotlib.org/api/pyplot_api.html).
*   Jupyter Notebook відтворюватиме графікі вбудовано, якщо ми попросимо його про це за допомогою «магічної» команди

~~~
%matplotlib inline
import matplotlib.pyplot as plt
~~~
{: .language-python}

*   Прості графіки (досить) легко створити.

~~~
time = [0, 1, 2, 3]
position = [0, 100, 200, 300]

plt.plot(time, position)
plt.xlabel('Time (hr)')
plt.ylabel('Position (km)')
~~~
{: .language-python}

![Simple Position-Time Plot](../fig/9_simple_position_time_plot.svg)
## Побудова графіків безпосередньо з [`Pandas dataframe`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).

*   Можна також використовувати [Pandas dataframes](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.html).
*   Це неявно використовує [`matplotlib.pyplot`](https://matplotlib.org/api/pyplot_api.html).
*   Перед побудовою графіка ми перетворюємо заголовки стовпців з типу даних "string" на тип даних "integer", оскільки вони представляють числові значення.

~~~
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')

# Вилучаємо рік з останніх 4 символів назви кожного стовпця
# Поточні назви стовпців структуровані як 'gdpPercap_(year)', 
# тому ми зберігаємо частину назви (рік) лише для ясності під час побудови ВВП за роками
# Для цього ми використовуємо strip(), яка видаляє з рядка символи, зазначені як аргумент
# Цей метод працює з рядками, тому ми викликаємо str перед strip()

years = data.columns.str.strip('gdpPercap_')

# Перетворіть значення років в цілі числа, зберігаючи результати назад у  dataframe

data.columns = years.astype(int)

data.loc['Australia'].plot()
~~~
{: .language-python}

![Графік ВВП Австралії](../fig/9_gdp_australia.svg)
## Виберіть і трансформуйте дані, а потім будуйте графік»

*  За замовчуванням, [`DataFrame.plot`](https://pandas.pydata.org/pandas-docs/stable/generated/pandas.DataFrame.plot.html#pandas.DataFrame.plot) зображує рядки на осі X.
*   Ми можемо транспонувати дані, щоб побудувати кілька графіків разом.

~~~
data.T.plot()
plt.ylabel('ВВП на душу населення')
~~~
{: .language-python}

![Графіки ВВП для Австралії та Нової Зеландії](../fig/9_gdp_australia_nz.svg)
## Доступно багато типів графіків.

*  Наприклад, створіть стовпчикову діаграму, використовуючи вишуканий стиль.

~~~
plt.style.use('ggplot')
data.T.plot(kind='bar')
plt.ylabel('ВВП на душу населення)
~~~
{: .language-python}

![ Стовпчикова діаграма для ВВП Австралії](../fig/9_gdp_bar.svg)

## Графік також можна побудувати, викликавши безпосередньо функцію `plot` бібліотеки `matplotlib` .
*   Формат команди є таким: `plt.plot(x, y)`
*   Колір / формат маркерів також можна вказати як оптичний аргумент: напр. «b-» — синя лінія, «g--» — зелена пунктирна лінія.

## Отримаємо дані Австралії з dataframe.

~~~
years = data.columns
gdp_australia = data.loc['Australia']

plt.plot(years, gdp_australia, 'g--')
~~~
{: .language-python}

![Отформатований графік для ВВП Австралії](../fig/9_gdp_australia_formatted.svg)

## Можна побудувати кілька графіків за різними наборами даних разом

~~~
# Виберіть дані для двох країн.
gdp_australia = data.loc['Australia']
gdp_nz = data.loc['New Zealand']

# Побудуйте графіки з маркерами різних кольорів.
plt.plot(years, gdp_australia, 'b-', label='Australia')
plt.plot(years, gdp_nz, 'g-', label='New Zealand')

# Створіть легенду.
plt.legend(loc='upper left')
plt.xlabel('Year')
plt.ylabel('ВВП на душу населення ($)')
~~~
{: .language-python}

> ## Додавання легенди
> 
> Часто при побудові  графіків з кількох наборів даних разом бажано мати 
> легенду,  що містить опис даних.
>
> Легенда може бути створеною  in `matplotlib` за два кроки:
> 
> * Забезпечимо мітку для кожного набору даних на графіку:
>
> ~~~
> plt.plot(years, gdp_australia, label='Australia')
> plt.plot(years, gdp_nz, label='New Zealand')
> ~~~
>
> * Доручимо `matplotlib` створити легенду.
>
> ~~~
> plt.legend()
> ~~~
>
> За замовчуванням matplotlib спробує розмістити легенду у відповідному місці. Якщо 
> необхідно вказати конкретне розташування, можна застосувати аргументи функції `loc=`, наприклад, щоб розмістити 
> легенду в лівому верхньому куті графіку, задайте `loc='upper left'`
> {: .language-python}
{: .callout}


![Отформатований графік ВВП Австралії та Нової Зеландії](../fig/9_gdp_australia_nz_formatted.svg)
*   Побудуємо точкову діаграму співвідношення ВВП Австралії та Нової Зеландії
*   Використаємо `plt.scatter` або `DataFrame.plot.scatter`

~~~
plt.scatter(gdp_australia, gdp_nz)
~~~
{: .language-python}

![Співвідношення ВВП  з використанням plt.scatter](../fig/9_gdp_correlation_plt.svg)
~~~
data.T.plot.scatter(x = 'Австралія', y = 'Нова Зеландія')
~~~
{: .language-python}

![ВВП залежності на основі data.T.plot.scatter](../fig/9_gdp_correlation_data.svg)

> ## Мінімум та максимум
>
> Заповніть порожні поля нижче, щоб побудувати графік мінімального ВВП на душу населення в часі
> для всіх країн Європи.
> Потім побудуйте графік максимального ВВП на душу населення в Європі.
>
> ~~~
> data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
> data_europe.____.plot(label='min')
> data_europe.____
> plt.legend(loc='best')
> plt.xticks(rotation=90)
> ~~~
> {: .language-python}
>
> > ## Рішення
> >
> > ~~~
> > data_europe = pd.read_csv('data/gapminder_gdp_europe.csv', index_col='country')
> > data_europe.min().plot(label='min')
> > data_europe.max().plot(label='max')
> > plt.legend(loc='best')
> > plt.xticks(rotation=90)
> > ~~~
> > {: .language-python}
> > ![Мінімум Максимум Рішення](../fig/9_minima_maxima_solution.png)
> {: .solution}
{: .challenge}

> ## Співвідношення
>
> Модифікуйте приклад у примітках, щоб створити діаграму розсіювання, що показує
> співвідношення між мінімальним і максимальним ВВП на душу населення
> серед країн Азії за кожен рік у наборі даних.
>Який зв’язок ви бачите (якщо такий є)?
>
> ~~~
> data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
> data_asia.describe().T.plot(kind='scatter', x='min', y='max')
> ~~~
> {: .language-python}
>
> > ## Рішення
> >
> > ![Кореляції Рішення 1](../fig/9_correlations_solution1.svg)
> >
> > Жодних особливих кореляцій між мінімальними та максимальними значеннями ВВП не видно
> > з року в рік. Здається, доля азіатських країн не зростає і не падає разом.
> {: .solution}
>
> Можна помітити, що варіабельність максимуму набагато вища, ніж
> мінімуму.  Подивіться на максимальний і максимальний індекси::
>
> ~~~
> data_asia = pd.read_csv('data/gapminder_gdp_asia.csv', index_col='country')
> data_asia.max().plot()
> print(data_asia.idxmax())
> print(data_asia.idxmin())
> ~~~
> {: .language-python}
> > ## Рішення
> > ![Кореляції Рішення 2](../fig/9_correlations_solution2.png)
> >
> > Здається, варіабельність цього значення пов’язана з різким падінням після 1972 року
> > Можливо, якісь геополітичні фактори грають роль? Враховуючи домінування нафтовидобувних країн,
> > можливо, індекс нафти Brent стане цікавим порівнянням?
> > У той час як М’янма постійно має найнижчий ВВП, найвищий ВВП країн варіюється 
> > більш помітно.
> {: .solution}
{: .challenge}

> ## Більше залежностей
>
> Ця невеличка програма створює графік, який демонструє
> кореляцію між ВВП between GDP і очікуваною тривалістю життя на 2007 рік,
> причому розмір маркера є нормалізованим за кількістю  населення:
>
> ~~~
> data_all = pd.read_csv('data/gapminder_all.csv', index_col='country')
> data_all.plot(kind='scatter', x='ВВП_на_душу_населення_2007', y='Тривалість_Життя_2007',
>               s=data_all['pop_2007']/1e6)
> ~~~
> {: .language-python}
>
> Використовуючи онлайн help та інші ресурси,
> поясніть кожний аргумент функції `plot`.
>
> > ## Рішення
> > ![Більше залежностей Рішення](../fig/9_more_correlations_solution.svg)
> >
> > Багато корисної інформації шодо функції  plot  -
> > help(data_all.plot).
> >
> > kind - Як уже було показано, цей параметр визначає тип графіку, який буде створено.
> >
> > x та y - Назва стовпця або індекс, який визначає, які дані будуть
> > розміщені на осях x і y графіка
> > 
> > s - Подробиці щодо цього параметру є в документації  по plt.scatter.
> > Це одне число або одне значення для кожної точки даних.  Визначає розмір
> > маркера.
> {: .solution}
{: .challenge}

> ## Збереження вашого графіка в файл
> 
> Якщо вас задовольняє графік, який ви бачите, ви можете зберегти його у файл,
> можливо, щоб включити його у публікацію. Існує функція в 
>  модулі matplotlib.pyplot , яка виконує це:
> [savefig](https://matplotlib.org/api/_as_gen/matplotlib.pyplot.savefig.html).
> Виклик цієї функції, наприклад, наступним чином:
> ~~~
> plt.savefig('my_figure.png')
> ~~~
> {: .language-python}
> 
> збереже поточний графік у файл `my_figure.png`. Формат файла
> буде автоматично визначений з розширення файлу у його назві (інші формати
> - це pdf, ps, eps and svg).
>
> Зауважимо, що функції в `plt` посилаються на глобальну змінну графіка
> і після того, як графік виведено на екран (наприклад, за допомогою `plt.show`) 
> matplotlib змусить цю змінну посилатися на новий порожній графік.
> Тому переконайтеся, що ви викликаєте `plt.savefig` перед тим, як графік буде відображено
> на екрані, інакше ви можете створити файл із порожнім графіком.
>
> При використанні  dataframes дані часто генеруються та відображаються на екрані в один рядок,
> тому `plt.savefig` вважається не найкращім рішенням.
> Однією з можливостей зберегти графік у файл є
>
> * зберегти посилання на поточний графік у  локальну змінну  (з `plt.gcf`) ,
> * та викликати метод `savefig` з класу тієї змінної.
>
> ~~~
> fig = plt.gcf() #  посилання на поточний графік у локальній змінній 
> data.plot(kind='bar')
> fig.savefig('my_figure.png')
> ~~~
> {: .language-python}
{: .callout}

> ## Зробіть ваш графік доступним
>
> Щоразу, коли ви створюєте графіки для статті чи презентації, ви можете зробити кілька речей, щоб переконатися, що всі зрозуміють ваші графіки.
> * Завжди переконайтеся, що ваш текст достатньо великий для читання. Використовуйте параметр `fontsize` в `xlabel`, `ylabel`, `title`, та `legend`, and [`tick_params` with `labelsize`](https://matplotlib.org/2.1.1/api/_as_gen/matplotlib.pyplot.tick_params.html) щоб збільшити розмір тексту чисел на ваших осях.
> * Подібним чином, ви маєте зробити  елементи графіка легкими для перегляду. Використовуйте `s` щоб збільшити розмір маркерів діаграми розсіювання, і `linewidth` щоб збільшити розміри ліній вашого графіка.
> * Використання кольору (і нічого іншого) для розрізнення різних елементів графіку зробить ваші графіки нечитабельними для будь-кого, хто є дальтоніком або має чорно-білий офісний принтер. Для ліній параметр `linestyle` дозволяє використовувати різні типи ліній. Для діаграм розсіювання `marker` дозволяє змінювати форму ваших точок. Якщо ви не впевнені щодо своїх кольорів, ви можете скористатися [Coblis](https://www.color-blindness.com/coblis-color-blindness-simulator/) or [Color Oracle](https://colororacle.org/) щоб імітувати, як виглядатимуть ваші графіки для людей з дальтонізмом
{: .callout}

