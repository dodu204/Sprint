# Проект REST API для туристических горных перевалов.
### Описание проекта:
Этот проект выполняется студентами [SkillFactory](https://skillfactory.ru/python-developer) для Федерации Спортивного Туризма и Развития (ФСТР) с целью упростить процесс учета горных перевалов и сократить время обработки данных. По заданию необходимо усовершенствовать REST API для ведения базы горных перевалов, которая пополняется туристами.

Реализованы следующие методы:

1. POST /submitData: Добавление информации о новом перевале туристом.
2. GET /submitData/<id>: Получение одной записи о перевале по ее id, включая статус модерации.
3. PATCH /submitData/<id>: Редактирование существующей записи, если она еще не поступила в работу модератору.
4. GET /submitData/?user__email=<email>: Получение списка данных обо всех объектах, которые пользователь с указанным адресом электронной почты отправил на сервер.

### Параметры Реализации:
База данных PostgreSQL:

Используется база данных PostgreSQL.
Установка выполняется с помощью команды:
```
pip install psycopg2
```
Порт, логин, пароль и путь к базе данных берутся из переменных окружения с использованием библиотеки dotenv:
```
pip install python-dotenv
```
Установка зависимостей:

В файле requirements.txt представлен список внешних зависимостей.
Формирование файла выполняется командой:
```
pip freeze > requirements.txt
```
Установка зависимостей осуществляется с помощью команды:
```
pip install -r requirements.txt
```
Визуальный интерфейс Swagger:

Добавлен визуальный интерфейс Swagger.
Используется источник: [ссылка](https://appliku.com/post/django-rest-framework-swagger-openapi-tutorial).
Доступ к Swagger: /api/schema/swagger-ui.
Документация генерируется по адресу: /api/schema/redoc/.
Тестирование кода:
```
Код приложения покрыт тестами.
Используется библиотека coverage.
```
### Хостинг:

Проект размещен на хостинге http://akchuranne.pythonanywhere.com.
В данном хостинге используется база данных db.sqlite3.
Для переноса проекта на рабочую среду с базой данных PostgreSQL рекомендуется использовать конвертацию с помощью команд:
bash
```
./manage.py dumpdata > dump.json
./manage.py loaddata dump.json
```
### Как работать с API (endpoints):
1. По адресу /api/submitData/pereval/ или api/schema/swagger-ui/#/api/api_submitData_pereval_create можно создать информацию о новом перевале с помощью POST.
2. По адресу /api/submitData/pereval/id или api/schema/swagger-ui/#/api/api_submitData_pereval_retrieve можно получить одну запись о перевале по ее id, в том числе статус модерации c помощью GET;
3. По адресу /api/submitData/pereval/id или /api/schema/swagger-ui/#/api/api_submitData_pereval_partial_update можно редактировать существующую запись, если она еще не поступила в работу модератору с помощь PATCH;
4. Сменить статус модерации можно только через админ-панель по адресу: /admin. Возможность работы в ней обеспечивается созданием модератора по команде:
```
python manage.py createsuperuser
```
5. По адресу /api/submitData/user__email=<str:email> или /api/schema/swagger-ui/#/api/api_submitData_user__email%3D_list  можно с помощью GET получить список данных обо всех объектах, которые пользователь с почтой <email> отправил на сервер.
Пример JSON-запроса для создания, редактирования сведений о перевале:
```
{
    "beauty_title": "Бурятия",
    "title": "Баргузинский хребет",
    "other_titles": "Здравушка",
    "connect": "",
    "user": {
        "email": "student@yandex.ru",
        "fam": "Сивицкий",
        "name": "Евгений",
        "otc": "Федорович",
        "phone": "8125551234"
    },
    "coords": {
        "latitude": 54.70000000,
        "longitude": 110.40000000,
        "height": 2840
    },
    "level": {
        "winter": "1b",
        "summer": "",
        "autumn": "",
        "spring": ""
    },
    "images": [
        { 
          "data": ""
          "title" ""
        }
    ]
}
```
