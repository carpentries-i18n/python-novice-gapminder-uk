## Встановлення Python за допомогою Anaconda

[Python][python] це популярна мова для наукових обчислень, яка чудово підходить для 
програмування загального призначення. Встановлення всіх його наукових пакетів 
однак окремо може бути трохи складніше, тому ми рекомендуємо інсталятор все-в-одному
 [Anaconda][anaconda].

Незалежно від того, як ви вирішите його встановити, переконайтеся, що ви встановили Python
версія 3.x (наприклад, 3.4 добре підходить). Крім того, налаштуйте середовище python 
принаймні за день до семінару. Якщо у вас виникли проблеми з
процедури встановлення, зверніться по допомогу до організаторів семінару електронною поштою, 
щоб ви були готові, як тільки почнеться семінар.

### Windows - [Video tutorial][video-windows]

1. Відкрийте [https://www.anaconda.com/distribution/][anaconda-windows] у вашому веб браузері

2. Завантажте програму встановлення Python 3 для Windows.

3. Двічі клацніть виконуваний файл і встановіть Python 3 із рекомендованими налаштуваннями. Переконайтеся, що опція **Зареєструвати Anaconda як мій Python 3.x** за замовчуванням позначена — вона має бути в останній версії Anaconda

### Mac OS X - [Video tutorial][video-mac]

1. Відкрийте [https://www.anaconda.com/distribution/][anaconda-mac] у вашому веб браузері.

2. Завантажте інсталятор Python 3 для OS X. У цих інструкціях передбачається, що ви використовуєте графічний файл інсталятора `.pkg`.

3. Follow the Python 3 installation instructions. Make sure that the install location is set to "Install only for me" so Anaconda will install its files locally, relative to your home directory. Installing the software for all users tends to create problems in the long run and should be avoided.


### Linux

Note that the following installation steps require you to work from the shell. 
If you run into any difficulties, please request help before the workshop begins.

1.  Open [https://www.anaconda.com/distribution/][anaconda-linux] with your web browser.

2.  Download the Python 3 installer for Linux.

3.  Install Python 3 using all of the defaults for installation.

    a.  Open a terminal window.

    b.  Navigate to the folder where you downloaded the installer

    c.  Type

    ~~~
    $ bash Anaconda3-
    ~~~
    {: .bash}

    and press tab.  The name of the file you just downloaded should appear.

    d.  Press enter.

    e.  Follow the text-only prompts.  When the license agreement appears (a colon
        will be present at the bottom of the screen) press the space bar until you see the 
        bottom of the text. Type `yes` and press enter to approve the license. Press 
        enter again to approve the default location for the files. Type `yes` and 
        press enter to prepend Anaconda to your `PATH` (this makes the Anaconda 
        distribution your user's default Python).

## Getting the Data

The data we will be using is taken from the [gapminder][gapminder] dataset.
To obtain it, download and unzip the file 
[python-novice-gapminder-data.zip]({{page.root}}/files/python-novice-gapminder-data.zip).
In order to follow the presented material, you should launch the JupyterLab 
server in the root directory (see [Starting JupyterLab]({{ page.root }}/01-run-quit/#starting-jupyterlab)).


[anaconda]: https://www.anaconda.com/
[anaconda-mac]: https://www.anaconda.com/download/#macos
[anaconda-linux]: https://www.anaconda.com/download/#linux
[anaconda-windows]: https://www.anaconda.com/download/#windows
[gapminder]: https://en.wikipedia.org/wiki/Gapminder_Foundation
[jupyter]: http://jupyter.org/
[python]: https://python.org
[video-mac]: https://www.youtube.com/watch?v=TcSAln46u9U
[video-windows]: https://www.youtube.com/watch?v=xxQ0mzZ8UvA

