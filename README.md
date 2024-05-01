# 12 FACTOR APP

![](ZZZ/ZZZ.jpg) 

### CODEBASE
* Central codebase management using git and github
* If running multiple service, each service should be having different repo(codebase)
* Each codebase will be deployed to different env like (dev, staging(test), prod)

### DEPENDENCIES
* Never rely on implicit existence of a system-wide package
* Always explicitly declare and isolate dependencies
* Always specify version of packages to avoid mishaps and other type of fuckups
* Install all dependencies at build time
* If multiple projects in same system require different version of same package : create isolated/virtial env to run and use them or the better way use docker

### CONCURRENCY
* Stateless app 
* Run multiple instance of same app (concurrently) leading to vertical scaling

### PROCESSES
* Processes must be stateless and do not share data with other processes
* Data stored on database or another backing service like redis or rabbitmq, not on processes locally (leads to ambiguity and mishaps)
* Do not use sticky sessions

### BACKING SERVICES
* Must be treated as attached resources (must work without changing the app logic)
* We should be able to access it by pointing our app to another instance

### CONFIG
* None of the config should be hard coded, all must be in a config file of env variables
* Enable to have different configs for different env (dev, staging, prod)

### BUILD, RELEASE and RUN
* Build app after changes (shippable format)
* After build we get release candidate or object
* Each reelase object is having a unique release id (version or timestamp or signature)
* Finally we can ship and run the product
* Each minor change triggers a new build proess
* Allow to easily roll back in mishaps
* There must be a very strict seperation between dev, staging and prod env

### PORT BINDING
* App must be self contained and must run all machines, even if multiple instance of same service are running on same network

### DISPOSABILITY
* Processes must be able to start and stop on a momment's notice (start, stop, scale)
* There must be no need of complex startup scripts for any of the task
* Processes must shutdown gracefully when they receive a SIGTERM signal from te process manager
* If a process do not exit after SIGTERM, process manager sends a SIGKILL

### DEV PROD PARITY
* CD gap between dev and prod env must be small
* Do not use different backing services on dev and prod env

### LOGS
* Allow to troubleshoot
* We generally use containers, as soon as the coantainer is stopped, logs are lost 
* Try to use central logging service like fluentd or elk or splunk
* Never consern with routing and storage of output streams

### ADMIN PROCESSES
* Admin tasks should be kept seperated from application processes no matter periodic or non periodic and they should be run on an identical setup and be reproducable and scaleable
* Example : database migrations and server restarts

## TO NOTE
* no time for downtime (99.999)
* portability
* continous deployment
* scalability
* coloud platforms


