
```python
# it is necessary to be at project level to run this command
# as manage.py is only available inside the project_name folder
python manage.py startapp app_name 

# create urls.py inside app_name
```

```python
app_name/  
	__init__.py  
__init__.py  
admin.py  
apps.py  
models.py  
tests.py  
views.py
urls.py
```

```python
# to show html create templates folder inside app_name
app_name/  
	__init__.py  
templates/
	first.html
	second.html
__init__.py  
admin.py  
apps.py  
models.py  
tests.py  
views.py
urls.py
```

```python
# register app_name in setting.py at project level
# (method inside apps of app_name)
app_name.apps.app_nameConfig
```

