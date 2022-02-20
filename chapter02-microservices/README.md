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