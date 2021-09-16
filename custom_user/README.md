# Using a Custom User Model in a Django Project

This model uses the *email* as username.


## Steps

### Create root project directory

```
mkdir custom_user
```

### Start poetry, install django and use start virtualenv

```
cd custom_user
poetry init
poetry add django
poetry shell
```

### Start Django project in current directory (`.`)
```
django-admin startproject custom_user .
```

### Start `users` app

```
python manage.py startapp users
```

Edit files

- [users/models.py](users/models.py)
- [users/admin.py](users/models.py)

### Edit [setting.py](custom_user/settings.py)

Add `users` to `INSTALLED_APPS`

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'users',
]
```

Add `AUTH_USER_MODEL`

```python
AUTH_USER_MODEL = 'users.User'
```

### Update DB

```bash
python manage.py makemigrations
python manage.py migrate
```

### Create super user

```
python manage.py createsuperuser
```

### Run it!

```
python manage.py runserver
```