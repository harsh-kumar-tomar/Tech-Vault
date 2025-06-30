```python
docker run -d --hostname my-rabbit --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3-management


# 5672 : backend communication
# 15672 : for rabbitmq dashboard (http://localhost:15672)
# Username: `guest`, Password: `guest`

```
