we can render variables inside html content 

```python
# using {{ }}
<h1>Hello {{ firstname }}, how are you? </h1>

# to create variable 
{% with var_name = 42 %}

# FOR LOOP

 {% for x in mymembers %}
 
    <li>{{ x.firstname }}</li>
  
{% endfor %}


# IF ELSE

{% if greeting == 1 %}
  <h1>Hello</h1>
{% else %}
  <h1>Bye</h1>
{% endif %}

# in html
{%block content%} {%endblock%}

# in html
{%extends "base.html"%}
{%block content%} 
	{data}
{%endblock%}
```