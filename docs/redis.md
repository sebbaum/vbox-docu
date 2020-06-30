# Redis

You can enable [Redis](https://redis.io/) in the `box.yml`:
```yml
provision:
  [...]
  redis: true
```

This will install:

* redis

Redis will listen on `localhost:6379`. All the default configuration is applied. There is no special user or password for this service.

!!! important "Info"
    The module **php-redis** will be installed for you if PHP is installed.
