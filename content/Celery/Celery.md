we cannot use celery without [[Message Broker]] .

|Component|Role|
|---|---|
|**FastAPI App**|Sends tasks (producer)|
|**Message Broker** (Redis/RabbitMQ)|Holds queued tasks|
|**Celery Worker**|Pulls tasks from broker & executes them|
|**Result Backend** _(optional)_|Stores task results/status|
