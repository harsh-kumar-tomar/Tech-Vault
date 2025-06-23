why ?
- Tracks which messages were delivered and acknowledged.
- Can re-deliver unacknowledged messages.
- Messages can be persisted to disk in RabbitMQ (if enable it). So even if RabbitMQ restarts, jobs are not lost.
- Supports multiple consumers pulling from the queue safely.
- You can route messages to different queues based on type.