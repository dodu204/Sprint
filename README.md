# Проект REST API для туристических горных перевалов.
### Описание:
Этот проект разрабатывается студентами [SkillFactory](https://skillfactory.ru/python-developer) для Федерации Спортивного Туризма и Развития (ФСТР) с целью упростить
процесс учета горных перевалов и сократить время обработки данных. По заданию необходимо усовершенствовать  REST API 
для ведения базы горных перевалов, которая пополняется туристами.
Реализованы методы: API POST/submitData для добавления туристом информации о новом перевале; 
GET /submitData/<id> — получение одной записи о перевале по ее id, в том числе статус модерации;
PATCH /submitData/<id> — редактирование существующей записи, если она еще не поступила в работу модератору, 
а также GET /submitData/?user__email=<email> — список данных обо всех объектах, которые пользователь с почтой <email> отправил на сервер.

###  Параметры реализации:
1.При подготовке проекта использована база данных PostgreSQL, установка производится командой: 
```
pip install psycopg2
```
Порт, логин, пароль и путь к базе данных берется из переменных окружения с использованием библиотеки dotenv: 
```
pip install python-dotenv
```
2.В файле requirements.txt приведен список внешних зависимостей, который формируется командoй pip freeze > requirements.txt.
Установите зависимости командой:
```
pip install -r requirements.txt
```
3. Добавлен визуальный интерфейс Swagger. За основу при установке взят следующий [источник](https://appliku.com/post/django-rest-framework-swagger-openapi-tutorial)
Его работа доступна по адресу /api/schema/swagger-ui, для генерирования документации /api/schema/redoc/
4. Код приложения был покрыт тестами, установлена библиотека coverage. 
5. Проект размещен на хостинге http://dodu204.pythonanywhere.com В нем используется база данных db.sqlite3.
Рабочий проект на базе данных PostgreSQL(конвертация с помощью ./manage.py dumpdata > dump.json,
./manage.py loaddata dump.json)
Примеры вызова REST API с хостинга http://dodu204.pythonanywhere.com/api/submitData/pereval/1 - получение информации о перевале по его id.
http://dodu204.pythonanywhere.com/api/submitData/user__email=student@yandex.ru - список данных обо всех объектах, созданных пользователем с электронной почтой student@yandex.ru


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
