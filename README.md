# Дипломный проект по профессии «Инженер по тестированию»
***Цель проекта***:   автоматизация тестирования комплексного сервиса, взаимодействующего с СУБД и API Банка.

***Задача*** — автоматизировать позитивные и негативные сценарии покупки тура.

*Приложение* — это веб-сервис, который предлагает купить тур по определённой цене двумя способами:

1. Обычная оплата по дебетовой карте.
2. Уникальная технология: выдача кредита по данным банковской карты.

Само приложение не обрабатывает данные по картам, а пересылает их банковским сервисам:

1. Сервису платежей - Payment Gate;
2. Кредитному сервису - Credit Gate.

Приложение в собственной СУБД должно сохранять информацию о том, успешно ли был совершён платёж и каким способом. Данные карт при этом сохранять не допускается.

Заявлена поддержка двух СУБД:

- **MySQL**;
- **PostgreSQL**.

[Ссылка на Дипломное задание](https://github.com/netology-code/qa-diploma)

## Тестовая документация
План тестирования;

Отчёт по итогам тестирования;

Отчет по итогам автоматизации

## Запуск приложения
#### Подготовительный этап
Установить и запустить IntelliJ IDEA;
Установать и запустить Docker Desktop;
Скопировать репозиторий с Github по ссылке.
Открыть проект в IntelliJ IDEA.
#### Запуск тестового приложения
Запустить MySQL, PostgreSQL, NodeJS через терминал командой:
docker-compose up
В новой вкладке терминала запустить тестируемое приложение:
Для MySQL:
java -Dspring.datasource.url=jdbc:mysql://localhost:3306/app -jar artifacts/aqa-shop.jar
Для PostgreSQL:
java -Dspring.datasource.url=jdbc:postgresql://localhost:5432/app -jar artifacts/aqa-shop.jar
.
Убедиться в готовности системы. Приложение должно быть доступно по адресу:
http://localhost:8080/
Запуск тестов
В новой вкладке терминала запустить тесты:

Для MySQL:
gradlew clean test -Ddb.url=jdbc:mysql://localhost:3306/app
Для PostgreSQL:
gradlew clean test -Ddb.url=jdbc:postgresql://localhost:5432/app
Перезапуск тестов и приложения
Для остановки приложения в окне терминала нужно ввести команду Ctrl+С и повторить необходимые действия из предыдущих разделов.

Формирование отчёта о тестировании
Предусмотрено формирование отчётности через Allure. Для этого в новой вкладке терминала вводим команду

gradlew allureServe