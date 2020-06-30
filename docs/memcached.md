# Memcached

You can enable [Memcached](https://memcached.org/) in the `box.yml`:
```yml
provision:
  [...]
  memcached: true
```

This will install:

* memcached
* libmemcached-tools

Memcached will listen on `localhost:11211`. All the default configuration is applied. There is no special user or password for this service.

!!! important "Info"
    The module **php-memcached** will be installed for you if PHP is installed.
