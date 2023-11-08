                                                                            Проект REST API для туристических горных перевалов
Описание проекта:
Проект разрабатывается студентами SkillFactory для Федерации Спортивного Туризма и Развития (ФСТР) с целью упростить процесс учета горных перевалов и сократить время обработки данных.

Методы API:
Добавление информации о перевале:
Метод: POST /api/submitData/pereval/
Swagger: /api/schema/swagger-ui/#/api/api_submitData_pereval_create
Пример JSON-запроса для создания:
json
Copy code
{
    "beauty_title": "Куркурек",
    "title": "Северо-Чуйский хребет",
    "other_titles": "Звенящий",
    "connect": "",
    "user": {
        "email": "proba2@yandex.ru",
        "fam": "Иванов",
        "name": "Петр",
        "otc": "Михайлович",
        "phone": "89167854534"
    },
    "coords": {
        "latitude": 50.12536,
        "longitude": 87.65502,
        "height": 3989
    },
    "level": {
        "winter": "1b",
        "summer": "",
        "autumn": "",
        "spring": ""
    },
    "images": [
        { 
          "data": "",
          "title": ""
        }
    ]
}
Получение информации о перевале:

Метод: GET /api/submitData/pereval/id
Swagger: /api/schema/swagger-ui/#/api/api_submitData_pereval_retrieve
Редактирование информации о перевале:

Метод: PATCH /api/submitData/pereval/id
Swagger: /api/schema/swagger-ui/#/api/api_submitData_pereval_partial_update
Список данных пользователя:

Метод: GET /api/submitData/user__email=email
Swagger: /api/schema/swagger-ui/#/api/api_submitData_user__email%3D_list
Параметры реализации:
База данных:

PostgreSQL
Установка: pip install psycopg2
Переменные окружения: python-dotenv
Зависимости:

pip install -r requirements.txt
Swagger:

Визуальный интерфейс: /api/schema/swagger-ui
Документация: /api/schema/redoc
Тестирование:

Код покрыт тестами
Библиотека coverage
Работа с API (endpoints):
Создание нового перевала: POST /api/submitData/pereval/
Получение информации о перевале: GET /api/submitData/pereval/id
Редактирование перевала: PATCH /api/submitData/pereval/id
Список данных пользователя: GET /api/submitData/user__email=email
Админ-панель:
Смена статуса модерации: /admin
Создание модератора: python manage.py createsuperuser
Примеры вызова REST API:
Получение информации о перевале: /api/submitData/pereval/3/
Список данных пользователя: /api/submitData/user__email=sendmailsend@yandex.ru
Размещение проекта:
Хостинг: http://akchuranne.pythonanywhere.com
База данных: PostgreSQL (конвертация: ./manage.py dumpdata > dump.json, ./manage.py loaddata dump.json)
