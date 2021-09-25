# Домашнее задание к занятию «3.1. Docker»

**Важно**: задачи этого занятия не предполагают подключения к CI.

## Задача №1 - PostgreSQL
Необходимо подготовить приложение к тестированию на СУБД PostgreSQL (используйте образ 12-alpine, если он недоступен, то берите последний опубликованный на DockerHub). Возьмите собранный jar-файл `db-api.jar`, положите рядом файл `application.properties`, но в строке:
`jdbc:mysql://...` поменяйте `mysql` на `postgresql`.
Нужно дописать остальные настройки (хост, порт, БД, имя пользователя и пароль). Так же подготовить файл `docker-compose.yml`, в котором прописать настройки для запуска контейнера PostgreSQL. 

Запустите сначала `docker-compose up` и только после того, как БД запустится, запустите целевое приложение: `java -jar db-api.jar` (если нужно поменять порт запуска, по умолчанию он 9999, то добавьте в файл `application.properties` строку `server.port=<нужный номер порта>`).

Если вы сделали всё правильно, то приложение запустится и на `GET http://localhost:9999/api/cards` выдаст вам JSON с картами:
```json
[ 
   { 
      "id":1,
      "name":"Альфа-Карта Premium",
      "description":"Альфа-Карта вернёт ваши деньги",
      "imageUrl":"/alfa-card-premium.png"
   },
   { 
      "id":2,
      "name":"Alfa Travel Premium",
      "description":"Самая выгодная карта для путешествий",
      "imageUrl":"/alfa-card-travel.png"
   },
   { 
      "id":3,
      "name":"CashBack Premium",
      "description":"Заправь свою карту. Кэшбэк на АЗС, в кафе и ресторанах",
      "imageUrl":"/alfa-card-cashback.png"
   }
]
```

В результате выполнения этой задачи нужно положить в репозиторий следующие файлы:
* db-api.jar
* application.properties
* docker-compose.yml
