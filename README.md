# larakit/sf-animate.min

### Установка пакета 
~~~bash
composer require larakit/sf-animate.min
~~~
Ничего дополнительно инициализировать не надо, добавив этот пакет в зависимости в composer.json, он сам установится и пропишется на всех страницах автоматически.

### Отключение пакета на некоторых роутах
В файле  ./app/Http/staticfiles.php добавьте
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-animate.min')
    ->addExclude('home')
    ->addExclude('admin.*');
~~~    
тогда пакет не будет включен на главной странице и на всех страницах админки.

### Изменение состава подключаемой статики пакета
Если вы использовали какой-то пакет, который за собой потянул этот пакет, но вас не устраивает версия библиотеки, подключаемая по умолчанию (например не хотите использовать CDN, а хотите отдавать со своего сайта), то вместо базового способа инициализации пакета
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-animate.min')
    ->css('//cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.1/animate.min.css');
~~~
вы можете переопределить его, вызвав инициализацию пакета еще раз
~~~php
\Larakit\StaticFiles\Manager::package('larakit/sf-animate.min')
    //очистить список подключенных JS и CSS
    ->clearJs()
    ->clearCss()
    //добавить свои
    ->css('/css/animate.min.css');
~~~
