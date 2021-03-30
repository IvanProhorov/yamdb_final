

# REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке. (Совместный проект студентов Яндекс.Практикум)

Проект YaMDb собирает отзывы (*Review*) пользователей на произведения (*Title*). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (*Category*) может быть расширен (например, можно добавить категорию *«Изобразительное искусство»* или *«Ювелирка»*).

Сами произведения в YaMDb не хранятся, **здесь нельзя посмотреть фильм или послушать музыку**.

В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха. Произведению может быть присвоен жанр из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.

Благодарные или возмущённые читатели оставляют к произведениям текстовые отзывы (*Review*) и выставляют произведению рейтинг (оценку в диапазоне от одного до десяти). Из множества оценок автоматически высчитывается средняя оценка произведения.

## Подготовка к работе:

Клонируйте репозиторий на локальную машину.
```
git clone https://github.com/IvanProhorov/yamdb_final.git
```
Создайте файл .env и заполните его своими значениями. Все нужные переменные и их примерные значения описаны файле .env.template.

Запустите процесс сборки и запуска контейнеров.
```
docker-compose up
```
Чтобы применить миграции, введите
```
docker-compose -f docker-compose.yaml exec web python manage.py migrate --noinput
```
Для создания суперпользователя, необходимо ввести
```
docker-compose -f docker-compose.yaml exec web python manage.py createsuperuser
```
Если необходимо заполнить базу тестовыми данными, введите
```
docker-compose -f docker-compose.yaml exec web python manage.py loaddata fixtures.json
```
Чтобы собрать статические файлы, используйте команду
```
docker-compose -f docker-compose.yaml exec web python manage.py collectstatic
```
Остановить работу можно командой
```
docker-compose stop
```

## Технологии

* [Django](https://www.djangoproject.com/) - фреймворк для веб-приложений;
* [Django REST framework](https://www.django-rest-framework.org/) - API фреймворк для Django;
* [PostgreSQL](https://www.postgresql.org/) - объектно-реляционная система управления базами данных;
* [Docker](https://www.docker.com/) - ПО для автоматизации развёртывания и управления приложениями в средах с поддержкой контейнеризации;
* [Docker-Compose](https://docs.docker.com/compose/) - инструмент для создания и запуска многоконтейнерных Docker приложений. 

[![yamdb workflow](https://github.com/IvanProhorov/yamdb_final/actions/workflows/main.yml/badge.svg)](https://github.com/IvanProhorov/yamdb_final/actions/workflows/main.yml)