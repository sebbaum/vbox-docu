# Webservers

There are two webservers available in Vbox. These are certainly the most common once out there:

* Nginx
* Apache

# Installation
## Nginx
Nginx can be installed by setting:
Nginx can be installed by setting:
```yml
provision:
  nginx: true
```

## Apache
Apache can be installed by setting:
```yml
provision:
  apache: true
```

# Configuration
The configuration files for both webservers are templates and the following
variables shape the behavior of the server:

* **`WEB_ROOT: /var/www/html`**  
Root path where a webserver can find the source files.

* **`SERVER_NAME: dev.box`**  
An alternative web server name.

* **`USE_SSL: false`**  
If this is set to `true` the webserver will use a self-signed certificate and root
all traffic to `https`.
