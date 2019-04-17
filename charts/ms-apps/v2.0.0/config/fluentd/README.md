# Buffer Parameters Configuration


### Set the buffer type to file to improve the reliability and reduce the memory consumption
@type file

### Set queue_full action to block because we want to pause gracefull in case of the off-the-limits load 
instead of throwing an exception
overflow_action block

### Set the chunk limit conservatively to avoid exceeding the GCL limit of 10MiB per write request.
chunk_limit_size 16m

### Cap the combined memory usage of this buffer and the one below to 2MiB/chunk * (6 + 2) chunks = 16 MiB
queue_limit_length 256

### Never wait more than 5 seconds before flushing logs in the non-error case.
flush_interval 5s

### Never wait longer than 30 seconds between retries.
retry_max_interval 17

### Disable the limit on the number of retries (retry forever).
retry_forever true

### Use multiple threads for processing.
flush_thread_count 4
