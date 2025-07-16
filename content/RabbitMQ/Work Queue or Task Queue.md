Here , we encapsulate a task as a message and send it to the queue.A worker process running in the background will pop the tasks and eventually execute the job. When you run many workers the tasks will be shared between them.
This concept is especially useful in web applications where it's impossible to handle a complex task during a short HTTP request window.


Now we'll be sending strings that stand for complex tasks.