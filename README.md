# kittygram_final
![kittygram_final workflow](https://github.com/herrShneider/kittygram_final/actions/workflows/main.yml/badge.svg)

  Учебный проект социальной сети про котиков. Целью проекта является закрепление знаний в области запуска проекта Kittygram в контейнерах, настройки автоматического тестирования и деплоя этого проекта на удалённый сервер.
Автоматизация настроена с помощью сервиса GitHub Actions.
При пуше в ветку main:
проект тестируется и деплоится на удалённый сервер,
при пуше в любую другую ветку проект только тестируется.
В случае успешного прохождения тестов образы обновляются на Docker Hub.
На сервере запускаются контейнеры из обновлённых образов.

Стэк: Python 3.9.10 / Django 3.2.3 / Docker / GitHub Actions / Docker Hub


Установка:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone git@github.com:herrShneider/kittygram_final.git
```

```
cd kittygram/
```
Создать файл .env по образцу .env.example


Выполнить pull образов с Docker Hub:

```
sudo docker compose -f docker-compose.production.yml pull
```

Запустить/Перезапустить все контейнеры в Docker Compose:
```
sudo docker compose -f docker-compose.production.yml down
```
```
sudo docker compose -f docker-compose.production.yml up -d
```

Выполнить миграции и сбор статики:
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```
```
sudo docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
```
sudo docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /backend_static/static/
```


Авторы: 

- [Ласовский Владимир](https://github.com/herrShneider?tab=repositories) 
