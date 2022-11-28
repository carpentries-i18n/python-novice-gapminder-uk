## Використовуйте бібліотеку Pandas, щоб отримати статистику з табличних даних.

*   Pandas — це бібліотека Python, яка  широко використовується для статистики, зокрема на основі табличних даних.
*   Ця бібліотека запозичує багато функцій із фреймів даних R.
    *   Двовимірна таблиця, стовпці якої мають імена
        і потенційно мають різні типи даних.
*   Завантажте цю бібліотеку за допомогою `import pandas as pd`. Псевдонім pd зазвичай використовується для Pandas.
*   Читайте файл даних із роздільними комами (Comma Separate Values - CSV) за допомогою `pd.read_csv`.
    *   Аргумент - це ім'я файлу, який потрібно прочитати.
    *   Призначте результат змінній для збереження даних, які було прочитано.

~~~
import pandas as pd

data = pd.read_csv('data/gapminder_gdp_oceania.csv')
print(data)
~~~
{: .language-python}
~~~
       country  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \
0    Australia     10039.59564     10949.64959     12217.22686
1  New Zealand     10556.57566     12247.39532     13175.67800

   gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \
0     14526.12465     16788.62948     18334.19751     19477.00928
1     14463.91893     16046.03728     16233.71770     17632.41040

   gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \
0     21888.88903     23424.76683     26997.93657     30687.75473
1     19007.19129     18363.32494     21050.41377     23189.80135

   gdpPercap_2007
0     34435.36744
1     25185.00911
~~~
{: .output}

*   Стовпці у фреймі даних є спостережуваними змінними, а рядки – спостереженнями
*   Pandas використовує зворотну скісну риску `\`, щоб показати перенесені рядки, коли вивід занадто широкий, щоб поміститися на екран.

> ## Файл не знайдено
>
> Наші уроки зберігають свої файли даних у підкаталозі `data`,
> тому шлях до файлу – `data/gapminder_gdp_oceania.csv`.
> Якщо ви забули включити `data/`,
> або якщо ви включите його, але ваша копія файлу знаходиться в іншому місці,
> ви отримаєте [runtime error]({{ page.root }}/04-built-in/#runtime-error)
> який закінчується таким рядком:
>
> ~~~
> OSError: File b'gapminder_gdp_oceania.csv' does not exist
> ~~~
> {: .error}
{: .callout}

## Використовуйте `index_col`, щоб вказати, що значення стовпця мають використовуватися як заголовки рядків.

*  Заголовки рядків є числами (0 і 1 у цьому випадку).
*   Дійсно краще індексувати за країнами.
*   Для цього передайте назву стовпця в `read_csv` як його параметр `index_col`.

~~~
data = pd.read_csv('data/gapminder_gdp_oceania.csv', index_col='country')
print(data)
~~~
{: .language-python}
~~~
             gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
country
Australia       10039.59564     10949.64959     12217.22686     14526.12465
New Zealand     10556.57566     12247.39532     13175.67800     14463.91893

             gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
country
Australia       16788.62948     18334.19751     19477.00928     21888.88903
New Zealand     16046.03728     16233.71770     17632.41040     19007.19129

             gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
country
Australia       23424.76683     26997.93657     30687.75473     34435.36744
New Zealand     18363.32494     21050.41377     23189.80135     25185.00911
~~~
{: .output}

## Використовуйте `DataFrame.info`, щоб дізнатися більше про фрейми даних.

~~~
data.info()
~~~
{: .language-python}
~~~
<class 'pandas.core.frame.DataFrame'>
Index: 2 entries, Australia to New Zealand
Data columns (total 12 columns):
gdpPercap_1952    2 non-null float64
gdpPercap_1957    2 non-null float64
gdpPercap_1962    2 non-null float64
gdpPercap_1967    2 non-null float64
gdpPercap_1972    2 non-null float64
gdpPercap_1977    2 non-null float64
gdpPercap_1982    2 non-null float64
gdpPercap_1987    2 non-null float64
gdpPercap_1992    2 non-null float64
gdpPercap_1997    2 non-null float64
gdpPercap_2002    2 non-null float64
gdpPercap_2007    2 non-null float64
dtypes: float64(12)
memory usage: 208.0+ bytes
~~~
{: .output}

*   Це `DataFrame`
*   Містить два рядки з назвами `'Australia'` та `'New Zealand'`
*   А також дванадцять стовпців, кожен з яких містить два фактичних 64-розрядних значення з плаваючою комою.
    *   Пізніше ми поговоримо про нульові значення, які використовуються для представлення відсутніх спостережень.
*   Використано 208 байт пам'яті.

## Змінна `DataFrame.columns` зберігає інформацію про стовпці фрейму даних.

*   Зауважте, що це дані, а не метод.
    *   Подібно `math.pi`.
    *   Тому не використовуйте `()`, щоб спробувати його викликати.
*   Ця змінна Називається *змінною-членом* або просто *членом*.

~~~
print(data.columns)
~~~
{: .language-python}
~~~
Index(['gdpPercap_1952', 'gdpPercap_1957', 'gdpPercap_1962', 'gdpPercap_1967',
       'gdpPercap_1972', 'gdpPercap_1977', 'gdpPercap_1982', 'gdpPercap_1987',
       'gdpPercap_1992', 'gdpPercap_1997', 'gdpPercap_2002', 'gdpPercap_2007'],
      dtype='object')
~~~
{: .output}

## Використовуйте `DataFrame.T`, щоб транспонувати фрейм даних.

*  Іноді потрібно розглядати стовпці як рядки і навпаки.
*   Транспонування (written `.T`) не копіює дані, а лише змінює вигляд програми.
*   Як і `columns`, це змінна-член.

~~~
print(data.T)
~~~
{: .language-python}
~~~
country           Australia  New Zealand
gdpPercap_1952  10039.59564  10556.57566
gdpPercap_1957  10949.64959  12247.39532
gdpPercap_1962  12217.22686  13175.67800
gdpPercap_1967  14526.12465  14463.91893
gdpPercap_1972  16788.62948  16046.03728
gdpPercap_1977  18334.19751  16233.71770
gdpPercap_1982  19477.00928  17632.41040
gdpPercap_1987  21888.88903  19007.19129
gdpPercap_1992  23424.76683  18363.32494
gdpPercap_1997  26997.93657  21050.41377
gdpPercap_2002  30687.75473  23189.80135
gdpPercap_2007  34435.36744  25185.00911
~~~
{: .output}

## Використовуйте `DataFrame.describe`, щоб отримати зведену статистику даних.

DataFrame.describe() отримує зведену статистику лише для стовпців, які містять числові дані.
Усі інші стовпці ігноруються, якщо ви не використовуєте аргумент `include='all'`.
~~~
print(data.describe())
~~~
{: .language-python}
~~~
       gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  gdpPercap_1967  \
count        2.000000        2.000000        2.000000        2.000000
mean     10298.085650    11598.522455    12696.452430    14495.021790
std        365.560078      917.644806      677.727301       43.986086
min      10039.595640    10949.649590    12217.226860    14463.918930
25%      10168.840645    11274.086022    12456.839645    14479.470360
50%      10298.085650    11598.522455    12696.452430    14495.021790
75%      10427.330655    11922.958888    12936.065215    14510.573220
max      10556.575660    12247.395320    13175.678000    14526.124650

       gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  gdpPercap_1987  \
count         2.00000        2.000000        2.000000        2.000000
mean      16417.33338    17283.957605    18554.709840    20448.040160
std         525.09198     1485.263517     1304.328377     2037.668013
min       16046.03728    16233.717700    17632.410400    19007.191290
25%       16231.68533    16758.837652    18093.560120    19727.615725
50%       16417.33338    17283.957605    18554.709840    20448.040160
75%       16602.98143    17809.077557    19015.859560    21168.464595
max       16788.62948    18334.197510    19477.009280    21888.889030

       gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  gdpPercap_2007
count        2.000000        2.000000        2.000000        2.000000
mean     20894.045885    24024.175170    26938.778040    29810.188275
std       3578.979883     4205.533703     5301.853680     6540.991104
min      18363.324940    21050.413770    23189.801350    25185.009110
25%      19628.685413    22537.294470    25064.289695    27497.598692
50%      20894.045885    24024.175170    26938.778040    29810.188275
75%      22159.406358    25511.055870    28813.266385    32122.777857
max      23424.766830    26997.936570    30687.754730    34435.367440
~~~
{: .output}

*   Не дуже корисно лише з двома записами,
   але дуже корисно, коли таких записів тисячі.

> ## Читання інших даних
>
>Зчитати дані з файлу `gapminder_gdp_americas.csv`
> (який має бути в тому ж каталозі, що й .`gapminder_gdp_oceania.csv`)
> у змінну `americas`
> і відобразити його підсумкову статистику.
>
> > ## Рішення
> > Для зчитування в форматі CSV ми використовуємо функцію `pd.read_csv` і назвою файлу 'data/gapminder_gdp_americas.csv' в якості аргументу. МИ також передаємо 
> > назву стовпцю 'country' як параметр `index_col`, щоб індексувати за назвами країн:
> > ~~~
> > americas = pd.read_csv('data/gapminder_gdp_americas.csv', index_col='country')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}



> ## Перевірка даних.
>
> Прочитавши дані для Південної Америки,
> використовуйте `help(americas.head)` та `help(americas.tail)`,
>щоб дізнатися про призначення `DataFrame.head` and `DataFrame.tail`.
>
> 1.  Виклик якого методу відобразить перші три рядки цих даних?
> 2.  Виклик якого методу відобразить останні три стовпці цих даних?
>     (Підказка: вам може знадобитися змінити спосіб перегляду даних.)
>
> > ## Рішення
> > 1. Ми можемо перевірити перші п’ять рядків `americas` за викликом `americas.head()` (що дозволяє нам переглянути заголовок 
> > DataFrame). Ми можемо вказати кількість рядків, які ми хочемо бачити, визначивши параметр `n` у нашому виклику
> > `americas.head()`. TЩоб переглянути перші три рядки, виконайте:
> >
> > ~~~
> > americas.head(n=3)
> > ~~~
> >{: .language-python}
> > 
> > Результат є таким:
> > ~~~
> >          continent  gdpPercap_1952  gdpPercap_1957  gdpPercap_1962  \
> >country                                                               
> >Argentina  Americas     5911.315053     6856.856212     7133.166023   
> >Bolivia    Americas     2677.326347     2127.686326     2180.972546   
> >Brazil     Americas     2108.944355     2487.365989     3336.585802   
> >
> >           gdpPercap_1967  gdpPercap_1972  gdpPercap_1977  gdpPercap_1982  \
> >country                                                                     
> >Argentina     8052.953021     9443.038526    10079.026740     8997.897412   
> >Bolivia       2586.886053     2980.331339     3548.097832     3156.510452   
> >Brazil        3429.864357     4985.711467     6660.118654     7030.835878   
> >
> >           gdpPercap_1987  gdpPercap_1992  gdpPercap_1997  gdpPercap_2002  \
> >country                                                                     
> >Argentina     9139.671389     9308.418710    10967.281950     8797.640716   
> >Bolivia       2753.691490     2961.699694     3326.143191     3413.262690   
> >Brazil        7807.095818     6950.283021     7957.980824     8131.212843   
> >
> >           gdpPercap_2007  
> >country                    
> >Argentina    12779.379640  
> >Bolivia       3822.137084  
> >Brazil        9065.800825 
> > ~~~ 
> >{: .output}
> > 2. Щоб перевірити останні три рядки `americas`, ми можемо використати команду, `americas.tail(n=3)`,
> > analogous to команді `head()` used, що застосовувалась вище. Однак тут ми хочемо переглянути останні три стовпці, отже, нам потрібно
> > змінити подання інформації, а потім використати `tail()`. Для цього ми створюємо новий DataFrame, у якому рядки та
> > стовпці транспонуються
> > 
> > ~~~
> > americas_flipped = americas.T
> > ~~~
> >{: .language-python}
> >
> > Потім ми можемо переглянути останні три стовпці `americas`, переглянувши останні три рядки `americas_flipped`:
> > ~~~
> > americas_flipped.tail(n=3)
> > ~~~
> >{: .language-python}
> > Результат є таким:
> > ~~~
> > country        Argentina  Bolivia   Brazil   Canada    Chile Colombia  \
> > gdpPercap_1997   10967.3  3326.14  7957.98  28954.9  10118.1  6117.36   
> > gdpPercap_2002   8797.64  3413.26  8131.21    33329  10778.8  5755.26   
> > gdpPercap_2007   12779.4  3822.14   9065.8  36319.2  13171.6  7006.58   
> > 
> > country        Costa Rica     Cuba Dominican Republic  Ecuador    ...     \
> > gdpPercap_1997    6677.05  5431.99             3614.1  7429.46    ...      
> > gdpPercap_2002    7723.45  6340.65            4563.81  5773.04    ...      
> > gdpPercap_2007    9645.06   8948.1            6025.37  6873.26    ...      
> > 
> > country          Mexico Nicaragua   Panama Paraguay     Peru Puerto Rico  \
> > gdpPercap_1997   9767.3   2253.02  7113.69   4247.4  5838.35     16999.4   
> > gdpPercap_2002  10742.4   2474.55  7356.03  3783.67  5909.02     18855.6   
> > gdpPercap_2007  11977.6   2749.32  9809.19  4172.84  7408.91     19328.7   
> > 
> > country        Trinidad and Tobago United States  Uruguay Venezuela  
> > gdpPercap_1997             8792.57       35767.4  9230.24   10165.5  
> > gdpPercap_2002             11460.6       39097.1     7727   8605.05  
> > gdpPercap_2007             18008.5       42951.7  10611.5   11415.8  
> > ~~~ 
> >{: .output}
> > Примітка: ми могли б зробити вищезазначене в одному рядку коду, «поєднавши» команди:
> > ~~~
> > americas.T.tail(n=3)
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}

> ## Читання файлів в інших каталогах
>
> Дані вашого поточного проекту зберігаються у файлі під назвою `microbes.csv`,
> який знаходиться в папці під назвою `field_data`.
> Ви виконуєте аналіз у блокноті під назвою `analysis.ipynb`
> у спорідненій папці під назвою `thesis`:
>
> ~~~
> Ваш_домашній_каталог
> +-- field_data/
> |   +-- microbes.csv
> +-- thesis/
>     +-- analysis.ipynb
> ~~~
> {: .output}
>
> Які значення потрібно передати в `read_csv`, щоб прочитати `microbes.csv` у `analysis.ipynb`?
> 
> > ## Рішення
> > Нам потрібно вказати шлях до потрібного файлу як аргумент у виклику `pd.read_csv`. По-перше, потрібно «вискочити» з
> > папки `thesis` за допомогою '../', а потім зайти у папку  `field_data` за допомогою 'field_data/'. Після цього вказати назву файлу `microbes.csv.
> > Результат є таким:
> > ~~~
> > data_microbes = pd.read_csv('../field_data/microbes.csv')
> > ~~~
> >{: .language-python}
> {: .solution}
{: .challenge}

> ## Запис даних
> 
> Подібно функції `read_csv` для читання даних із файлу,
> Pandas має функцію `to_csv` для запису кадрів даних у файли.
> Застосовуючи те, що ви дізналися про читання з файлів,
> запишіть один із ваших фреймів даних у файл під назвою `processed.csv`.
> Ви можете скористатися `help`, щоб отримати інформацію про те, як використовувати `to_csv`.
> > ## Рішення
> > Щоб записати DataFrame `americas` у файл під назвою `processed.csv`, виконайте таку команду:
> > ~~~
> > americas.to_csv('processed.csv')
> > ~~~
> >{: .language-python}
> >Щоб отримати допомогу щодо `to_csv`, ви можете виконати, наприклад,
> > ~~~
> > help(americas.to_csv)
> > ~~~
> >{: .language-python}
> > Зауважте, що `help(to_csv)` видає помилку! Це тонкощі, і це пов’язано з тим, що `to_csv` НЕ є функцією сама по собі
> > а фактичним викликом є `americas.to_csv`. Front Matte: python-novice-gapminder/_episodes/08-data-frames.md:sgid "---
title: "Pandas DataFrames"
teaching: 15
exercises: 15
questions:
- "How can I do statistical analysis of tabular data?"
objectives:
- "Select individual values from a Pandas dataframe."
- "Select entire rows or entire columns from a dataframe."
- "Select a subset of both rows and columns from a dataframe in a single operation."
- "Select a subset of a dataframe by a single Boolean criterion."
keypoints:
- "Use `DataFrame.iloc[..., ...]` to select values by integer location."
- "Use `:` on its own to mean all columns or all rows."
- "Select multiple columns or rows using `DataFrame.loc` and a named slice."
- "Result of slicing can be used in further operations."
- "Use comparisons to select data based on value."
- "Select values or NaN using a Boolean mask."
---sgstr "---
title: "Pandas DataFrames"
teaching: 15
exercises: 15
questions:
- "Як я можу зробити статистичний аналіз табличних даних?"
objectives:
- "Вибір окремих значень з фрейму даних Pandas."
- "Вибір цілих рядків або цілих стовпців з фрейму даних"
- "Вибір підмножини рядків і стовпців з кадру даних за одну операцію."
- "Вибір підмножини кадрів даних за одним бульовим критерієм."
keypoints:
- "Використовуйте `DataFrame.iloc[..., ...]` для вибору значень за цілим розташуванням."
- "Використовуйте `:` окремо для позначення всіх стовпців або всіх рядків."
- "Вибирайте кілька стовпців або рядків за допомогою `DataFrame.loc` і назви зрізу."
- "Результат зрізу можна використовувати в подальших операціях."
- "Використовуйте порівняння для вибору даних на основі цінності."
- "Виберіть значення або NaN за допомогою бульової маски."
---
> {: .solution}
{: .challenge}

