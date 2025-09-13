# AQA Shop - Автоматизация тестирования
Автоматизированное тестирование веб-приложения для покупки туров.
Проверяются UI, API и взаимодействие с базами данных (PostgreSQL и MySQL).
Реализованы тесты на успешную и неуспешную оплату,

## Предустановка
Перед запуском автотестов необходимо установить:
- Docker
- Java 11+
- IntelliJ IDEA
- Allure

## Настройка зависимостей
В корне проекта в файле build.gradle указаны зависимости для:
- JUnit 5
- Selenide
- REST Assured
- Драйверы баз данных (PostgreSQL и MySQL)
- Плагина Allure
- Lombok

## Запуск БД в Docker
В корне проекта находится файл docker-compose.yml. Для запуска двух баз данных (PostgreSQL и MySQL) выполните команду в терминале:
- docker-compose up -d

## Запуск приложения
* В папке artifacts находится JAR-файл: aqa-shop.jar
* во втором терминале выполнить команды для запуска:
java -jar artifacts/aqa-shop.jar

## Подключение к БД
в третьем терминале выполнить команды:
* для с Postgres: docker compose exec postgres psql -U app -d app

* для MySQL: docker compose exec mysql mysql -u app -p app

## Запуск автотестов
Тесты написаны с использованием JUnit 5 + Selenide + REST Assured.
Команды для запуска:
- Для PostgreSQL: ./gradlew clean test "-Ddb.url=jdbc:postgresql://localhost:5432/app" "-Dspring.profiles.active=postgres"
- Для MySQL: ./gradlew clean test "-Ddb.url=jdbc:mysql://localhost:3306/app" "-Dspring.profiles.active=mysql"

## Генерация и просмотр отчёта Allure
После запуска тестов выполнить команду для генерации и просмотра отчёта:
- ./gradlew allureServe
