suppose an event occurs like student scans a qr code .
```python
/scan
we want to :
	mark_attendance
	send_sms_to_parent
	log_event_in_DB
	notify_teacher
```

problem 
if one service is taking longer than than others than whole process will get slow . if one service is down than entire service will go down . That means entire things are tightly coupled .

with queue , we will only do the most important task first and put all other task to queue , so that it can happen async.
benefit
now services are loosely coupled . That means if one go down than it wont affect the others .
if any task fails we need to handle it explicitly  , but with queue it can retry on it own.

another 

 Analogy: McDonald's Queue vs Single Worker

|Without Queue|With Queue|
|---|---|
|One person takes order, cooks, packs, delivers|One person takes order; tasks go to separate stations|
|Customer waits for everything|Customer is served quickly|
|If cooker fails → all customers wait|Other tasks still continue|