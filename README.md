## Проект YaMDb
Проект YaMDb собирает отзывы (Review) пользователей на произведения (Titles). Произведения делятся на категории: «Книги», «Фильмы», «Музыка». Список категорий (Category) может быть расширен администратором (например, можно добавить категорию «Фильм» или «Ювелирка»).
Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.
В каждой категории есть произведения: книги, фильмы или музыка. Например, в категории «Книги» могут быть произведения «Винни-Пух и все-все-все» и «Марсианские хроники», а в категории «Музыка» — песня «Давеча» группы «Насекомые» и вторая сюита Баха.
Произведению может быть присвоен жанр (Genre) из списка предустановленных (например, «Сказка», «Рок» или «Артхаус»). Новые жанры может создавать только администратор.
Благодарные или возмущённые пользователи оставляют к произведениям текстовые отзывы (Review) и ставят произведению оценку в диапазоне от одного до десяти (целое число); из пользовательских оценок формируется усреднённая оценка произведения — рейтинг (целое число). На одно произведение пользователь может оставить только один отзыв.
### Cписок используемых технологий:
Django, DRF

### Ссылка на проект:

http://84.201.179.139/admin/


![This is an image](https://github.com/abdurazak1/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### Как запустить проект:

Клонировать репозиторий и перейти в папку infra_sp2/infra/

```
cd infra_sp2/infra/
```

Запустить создание образов и контейнеров:

```
sudo docker compose up
```

Запустить выполнение миграций:

```
sudo docker compose exec web python manage.py migrate
```

Создать суперпользователя:

```
sudo docker compose exec web python manage.py createsuperuser
```

Собрать всю статику:

```
sudo docker compose exec web python manage.py collectstatic --no-input
```

Наполнить базу данных:
```
sudo docker compose exec web python manage.py load_category_data
sudo docker compose exec web python manage.py load_genre_data
sudo docker compose exec web python manage.py load_titles_data
sudo docker compose exec web python manage.py load_users_data
sudo docker compose exec web python manage.py load_review_data
sudo docker compose exec web python manage.py load_comment_data
sudo docker compose exec web python manage.py load_genre_title_data
```


### API
Документация API размещена по адресу: http://127.0.0.1/redoc/

### Авторы проекта: 

**[Ника](https://github.com/nikamasi)**. Управление пользователями (Auth и Users): система регистрации и аутентификации, права доступа, работа с токеном, система подтверждения через e-mail.

**[Абдул](https://github.com/abdurazak1)**.  Категории (Categories), жанры (Genres) и произведения (Titles): модели, представления, эндпойнты.

**[Алексей](https://github.com/alexeynickulin-web)**. Отзывы (Review) и комментарии (Comments): модели, представления, эндпойнты. Загрузка данных из CSV в БД.
