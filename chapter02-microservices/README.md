# Services

- Has a trigger to start working
  - Ex: HTTP has request trigger
- Got input from trigger
- Process input to output
- Send response back to the user
- Can trigger another services

## HTTP Service

- Trigger by HTTP request (GET, POST, PUT, ...)
- Send response body back (JSON, HTML, ...)
- Suitable for frontend API
- Synchronous operation
- Short time operation (Because has timeout)

## Consumer Service

- Suitable for "Do it later" job
- Read one input message at a time
- Long process time job
- Asynchronous 
- Ex: Read message from MQ and send SMS to the user when finished

## Bulk Consumer Service

- Same as `Consumer Service`
- Input batch of messages

## Scheduler Service

- Run automatically as configured
- Like cronjob
- Asynchronous response

## Async Task

- Suitable for frontend API
- Work in asynchronous way
- API that need long time to process
- Frontend got the `Ref Code` back to query the response later
- Good against high load and huge amount for connection

## Parallel Task

- Use many worker process for parallel task
- Task that required many server/worker to do in time
- Task that can be stopped
- Request for action
  1. Client submit the task to run. What task todo and worker count
  2. Parallel task generate `refcode` and store in Redis
  3. Send `refcode` back to client
  4. Create worker to run the task
  5. Update task status in Redis
- Request for response
  1. Client use `refcode` to get status of the task