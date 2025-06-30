1. Define celery app .
2. Define Task .
3. Define celery woker.
4. send task .

```python
my_project/
│
├── tasks.py         # Contains background tasks
├── main.py          # Your main app that triggers tasks
```


```python
# task.py
# 1. celery app
app = Celery("tasks", broker="redis://localhost:6379/0")

# 2. task
@app.task
def add(x, y):
    print(f"Running task: {x} + {y}")
    return x + y

# 3. Celery worker 
celery -A tasks worker --loglevel=info

```

```python
result = add.delay(5, 7)   # .delay() sends task to worker
```