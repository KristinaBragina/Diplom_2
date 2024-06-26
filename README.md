## Дипломный проект. Задание 2: тестирование API

#### Курс по автоматизации тестирования на Python, «Яндекс Практикум»
#### Спринт 9

---

### Автотесты для проверки API Stellar Burgers

Stellar Burgers — это внеземной фастфуд: здесь можно собрать и заказать бургер из необычных ингредиентов. Сервис тоже является учебным проектом: его написал студент «Практикума» в рамках другого курса.

### Структура проекта

- в директории `tests` расположены файлы с тестами, для каждого проверяемого эндпоинта — свой файл;
- файл `conftest` содержит фикстуры: здесь создаются уникальные пользователи и их заказы перед каждым требующим того тестом, а после — удаляются из базы;
- в файле `helpers` — функции, генерирующие рандомные тестовые данные с помощью библиотеки Faker;
- файл `data` хранит предопределенные тестовые данные, передаваемые в запросах;
- в файле `urls` определены адреса сервиса и его эндпоинтов;
- каталог `allure_results` хранит JSON-файлы с результатами выполнения тестов для генерации отчета;
- в файле `requirements.txt` перечислены все внешние зависимости исполняемых тестов для удобной установки одной командой;
- файл `README` объясняет суть происходящего и служит руководством. :)


### Реализованные сценарии

Задание проекта не требует от студента полностью покрыть API сервиса тестами. В рамках выполнения работы нужно было проверить исполнение конкретных функциональных требований:
- тесты в файле `test_registration` проверяют позитивный сценарий создания пользователя, а также отправку запросов с уже зарегистрированным email и незаполненными обязательными полями;
- тесты в файле `test_authentication` испытывают аутентификацию существующего в базе пользователя с валидным паролем, невалидным паролем, а также реакцию системы на запрос аутентификации с незарегистрированным паролем;
- тесты в файле `test_user_update` сверяют ответы сервера на запросы изменения данных аккаунта от аутентифицированных и неаутентифицированных пользователей;
- тесты в файле `test_create_order` проверяют создание заказа с верным, неверным и неуказанным хэшем ингредиентов, а также с аутентификацией и без аутентификации пользователя;
- тесты в файле `test_get_user_orders` отвечают за получение списка заказов при наличии токена аутентификации и без него.


### Запуск автотестов

**Установка зависимостей**

> `$ pip install -r requirements.txt`

**Запуск всех тестов одной командой**

>  `pytest -v`

**Allure-отчет о тестировании в формате веб-страницы**

>  `allure serve allure_results`