Yii2-Start App
=========================
Демо блог, реализован на основе Framework Yii 2. Он преднозначен для демонстративных и обучающих целей, но в тоже время, может быть использован как основа для своих проектов на framework-е Yii 2.

Данные авторизации на демо сайте
--------------------------------
- Логин: userX (userXX)
- Пароль: user0X (userXX)


Структура папок
---------------
```
common
	config/				Общие конфигурационные файлы
	behaviors/			Общие поведения
	data/				Дамп БД и другие данные связаны с БД
	extensions/			Общие расширения
	helpers/			Общие 'helper' классы
	mails/				Общие шаблоны писем
	modules/			Общие модули
console
	config/             Консольные конфигурационные файлы
	controllers/        Консольные котролеры (команды)
	migrations/         Общая папка миграций
	runtime/            Файлы сгенерированые во время выполнения консольного-приложения
backend
    protected
        config/			Администраторские конфигурационные файлы
        modules/		Администраторские модули
        runtime/		Файлы сгенерированые во время выполнения админ-приложения
    web
	    assets/			JS, CSS файлы с публичным доступом
frontend
    protected
        config/			Конфигурационные файлы публичного-приложения
        modules/		Публичные модули
        runtime/		Файлы сгенерированые во время выполнения публичного-приложения
    web
	    assets/			JS, CSS файлы с публичным доступом
statisc/
vendor/                 Стороние библиотеки
environments/			Файлы доступных типов (сред) разработки
```

Установка
---------

### Установка из архива или .git репозитория

- Скачиваем репозиторий в виде .zip архива, или клонируем репозиторий.
- Распаковываем архив в нужную папке на локальной машине. (В случае клонирования .git репозитория этот шаг пропускаем).
- Открываем в браузерной строке страницу проверки совместимости: `http://my-site.com/requirements.php` и убеждаемся что наш сервер соответствует всем требованием.
- Выполняем команду:

~~~
cd path/to/app
php composer.phar install
~~~

- Выполняем команду инициализации `init` приложения, и выбираем нужный вариант установки. (`dev` - для разработки, `prod` - для рабочего проекта).

~~~
cd path/to/app
init
~~~

- Создаём новую базу данных.
- Открываем файл `my/app/common/config/params.php` если мы запускаем рабочий проект или `my/app/common/config/params-local.php` если работаем на локалхосте, и в разделе `params[components.db]` меняем доступы к БД на наши.
- Выполняем команду:

~~~
cd path/to/app
yii migrate
~~~

- В случае необходимости демо данных, выболняем импорт дампа БД который находится в папке `my/app/common/data/data.sql`.
- После того как все установлено, нам необходимо определить корневую папку для наших приложений:

1. Для frontend `my/app/frontend/web` определяем адрес `http://frontend`
2. Для backend `my/app/backend/web` определяем адрес `http://backend`
3. Для statics `my/app/statics/web` определяем адрес `http://statics`

- После этого в файле `my/app/common/config/params.php` правим значение доменов на наши:

~~~
'siteDomain' => 'http://frontend',
'staticsDomain' => 'http://statics'
~~~

*Заметка: В случае использования "OpenServer" в качестве локального сервера, при ошибки "PDO expect driver", или другие подобные ошибки касающийся БД и PDO драйверов, нужно выполнять миграции из консоли самого "OpenServer". Вкладка: `Дополнительно --> Консоль`

*Заметка: В случае использования "OpenServer" в качестве локального сервера на "Windows" системе, при ошибках связаных с созданием `symlink`-ок нужно запустить сервер от имени администратора.