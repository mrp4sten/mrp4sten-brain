- [[Relational Data Bases and SQL]]
- [[PostgreSQL]]

# Practical Patterns and Antipatterns for Queues in PostgreSQL

Practical patterns for implementing queues in PostgreSQL include using a dedicated table to store queue items, leveraging the `FOR` `UPDATE` `SKIP` `LOCKED` clause to safely dequeue items without conflicts, and partitioning tables to manage large volumes of data efficiently. Employing batch processing can also enhance performance by processing multiple queue items in a single transaction. Antipatterns to avoid include using high-frequency polling, which can lead to excessive database load, and not handling concurrency properly, which can result in data races and deadlocks. Additionally, storing large payloads directly in the queue table can degrade performance; instead, store references to the payloads. By following these patterns and avoiding antipatterns, you can build efficient and reliable queuing systems in PostgreSQL.

```sql
id   | status   | updated_at
------------------------------------------
UUID | SMALLINT | TIMESTAMP WITH TIME ZONE
```

```python
for _ in shutdown_handler.loop():  # see appendix below
    event_meta = get_event_to_process(
        where_status_eq=TO_PROCESS,
        set_status_to=PROCESSING,
    )
    if event_meta is None:
        time.sleep(x)  # be gentle on the DB
        continue

    try:
        # Perform task!
        set_status(event_meta, PROCESSED)
    except:
        set_status(event_meta, ERRORED, ...)
```

```sql
WITH ids AS MATERIALIZED (
    SELECT id FROM event_queue
    WHERE status = {where_status_eq}
    ORDER BY updated_at
    LIMIT 1
    FOR UPDATE SKIP LOCKED
)
UPDATE event_queue
SET status = {set_status_to}, updated_at = {now}
WHERE id = ANY(SELECT id FROM ids)
RETURNING id
```

# Skytools PGQ

Skytools is a set of tools developed by Skype to assist with using PostgreSQL databases. One of the key components of Skytools is PGQ, a queuing system built on top of PostgreSQL that provides efficient and reliable data processing.