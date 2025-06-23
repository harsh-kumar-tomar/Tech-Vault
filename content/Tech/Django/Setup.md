[[_Django]] setup

```python
# for setting up virtual env
python -m venv name_of_virtual_env

# run activate venv
.\Scripts\activate

# this command to deactivate venv
deactivate
```

possible error

```
cannot be loaded because running scripts is disabled on this system
```

solution

```
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```


```python
# to install Django
python -m pip install Django

# to check django version
# note : no spaces in django-admin

django-admin --version

# to set up django project
django-admin startproject project_name

# to run server
# it will listen on port http://127.0.0.1:8000/
# ctr + c to exit server
python manage.py runserver

```


```python
python manage.py migrate
```

```python
# when we create django project it create a sqlite db with name 
db.sqlite3
```