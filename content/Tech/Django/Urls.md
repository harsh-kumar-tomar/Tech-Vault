[[_Django]]

It is used to map url to view 

use path method to link views and route from django.urls 

```python
# method name is from views.py
# path method is from django.url 
path(route,method_name,)
```

```python
# important :
# it is impt to know wether to put "/" at the end of project level url string 
# or to the beg. of url string in app level

# project level
urlpatterns = [
    path('admin/', admin.site.urls),
    path('team_members',include("app_name.urls")),
]

# app level
urlpatterns = [
    path('/', views.function1,name="xyz"),
    path('/1', views.function2,name="xyz"),
]
```

django looks for the matching url in project level , if anything matches than it chops off the matching part . 
that means if 

```
url = team_members/1
```

it matches team_members with the project level url , 
removes team_members 

so we left with 

```
/1
```

now the remaining part will be matched with 

```
team_members.urls file
```

