[TOC]

# Main config file
The main configuration file that determines the setup of your vbox is
`vbox.yml`.
You can find a default config file in `configure/box.sample.yml` that can serve
as a base for your own config file.

The main config file can be placed in different locations. The Vagrantfile
gives precedence to the locations.

1. Outside of the vbox folder. This is useful if the vbox is integrated into an
other project.
1. Inside of the vbox itself. This is useful if the vbox is the new base of your
project and your source code is located inside of `/src`.
1. Inside the `configuration` folder of vbox where the `box.example.yml` is
placed, too. This is useful for developing the vbox itself.

## File structure
```bash
.
├── box.yml               # <-- 2. precedence
├── ca-certificates
├── configure
│   ├── box.sample.yml
│   └── box.yml           # <-- 3. precedence
├── provisioning
│   ├── apache.sh
│   ├── composer.sh
│   ├── configs
│   ├── createSSLCert.sh
│   ├── docker-compose.sh
│   ├── docker.sh
│   ├── frameworks.sh
│   ├── loadNvm.sh
│   ├── mailhog.sh
│   ├── memcached.sh
│   ├── mysql.sh
│   ├── nginx.sh
│   ├── nvm.sh
│   ├── packages.sh
│   ├── php.sh
│   ├── redis.sh
│   ├── scripts
│   ├── templates
│   └── welcome.sh
├── README.md
├── src
│   ├── application
│   └── index.php
└── Vagrantfile
```

!!! important "Info"
    You can see which configuration Vagrant uses by running any vagrant command.

        vagrant status
        Used box configuration: /tmp/vbox-1.8.1/box.yml

# Basic box settings
Possible settings:

* `BOX_BASE: "ubuntu/bionic64"`   
The base box of your vagrant environment. You
can find other base boxes [here](https://app.vagrantup.com/boxes/search).

* `BOX_VERSION: "20190726.0.0"`  
Specifies the version of the base box. By using a fixed version you can ensure
that everyone in your team uses the same box.

* `BOX_NAME: "yourbox"`  
Give your box a name. This name is shown in the
console, if you login via SSH and in the Virtualbox GUI.

* `BOX_IP: "10.0.0.101"`  
This is the private IP of your box. You can e.g. point your browser to this IP
to show your application.

* `BOX_CPU: 1`  
Number of CPU resources.

* `BOX_MEMORY: 2048`  
Amount of memory.

* `BOX_CHECK_UPDATES: false`  
Should the box check for updates on each start? Defaults to false.

* Plugins  
Additional vagrant-plugins that should be used with your vagrant box.  
```yaml
PLUGINS:
  - vagrant-vbguest
```

## Additional box settings
* `WEB_ROOT: /var/www/html`  
Root path where a webserver can find the source files. This is independent from
Nginx or Apache.

* `SERVER_NAME: dev.box`  
An alternative web server name. This is independent from Nginx or Apache.

* `USE_SSL: false`  
Should the setup process create a self-signed certificate that is used with Nginx
or Apache.

* `OPEN_BROWSER: true`  
Open your default browser after a `vagrant up` if Nginx or Apache is used.

## Additional CA certificates
If you want to trust additional CA certificates e.g. that belong to your company,
you can configure a path to a folder where the CA certificates are located.
```yml
extra_certificates: ./ca-certificates
```
All containing certificates are copied to the box and trusted by running:
```bash
rm -rf /usr/local/share/ca-certificates/extra
mv /home/vagrant/extra /usr/local/share/ca-certificates
update-ca-certificates
```

## Port forwarding
If required you can define additional ports that should be forwarded form the host
to the quest system.
```yaml
ports:
  - localhost: 8080
    box: 80
  - localhost: 8088
    box: 8080
```
For example, this will forward requests to http://localhost:8080 to a server inside your box
that listens on port 80.

## Shared folders
You can define shared folders between your host and your guest system (vbox).
folders:
```yml
folders:
  - host: ./src
    guest: /var/www/html
    owner: www-data
    group: www-data
  - host: ./some-folder
    guest: /home/vagrant/some-folder
```
!!! note Info
    If `owner` and `group` are not defined, the shared folder in the vbox will
    belong to `vagrant:vagrant`

## Additional OS packages
If you want to install additional packages via `apt-get` you can define these
packages in the `box.yml` as well.  
You can decide, if which packages are installed before the provisioning and which
packages should be installed after the provisioning.
```yml
packages:
  preprovision:
    - unzip
    # - htop
  postprovision:
    - tmux
    # - supervisor
```

## Provisioned applications
This section is probably the most interesting part. Here you can define which
services should be installed in your vbox.
```yaml
provision:
  php: true
  nginx: true
  apache: false
  nvm: false
  mysql: true
  memcached: false
  redis: false
  docker: false
  welcome: true
  frameworks: true
  custom: false
```

### Frameworks
By setting `frameworks: true` some commonly used php frameworks are installed
and can be used in your box to create a new project. This requires that `php: true`
is set. For more information see the [Frameworks](frameworks.md) section.

### Welcome
Welcome will print a console logo in the console if your run `vagrant ssh`.

### Custom provisioning script
If you need additional provisioning for services, that are not integrated in Vbox
you can write your own shell-provisioning scripts.

!!! note "Important"
    Make sure to enable your custom scripts in the `provision` section:

        custom: true

Then you can integrate your provisioning scripts in `box.yml`:
```yml
custom:
  scripts:
    - name: script-1
      path: path-to/touch.sh
      privileged: false
      env:
        KEY1: value1
        KEY2: value2
```
* **name** - Must be unique
* **path** - Path to your scripts. This path can also point to a folder outside of
your vbox.
* **privileged**: Run the script with root privileges or as user `vagrant`.
*(opional; default: true)*
* **env** - Key value pairs for environment variables. These are passed to your
provisioning scripts and be used there.



## PHP
In Vbox it is possible to use different PHP versions and modules. You can
configure this in the PHP section.
```yml
php:
  current: 7.2
  versions:
    - 7.2
    - 7.4
  modules:
    - curl
    - zip
    - common
    - json
    - mysql
    - readline
    - xml
    - gd
    - mbstring
    - opcache
    - sqlite3
    - intl
```
!!! note "Info"
    The **current** version is active and used by the webserver.

## Mysql
In the **mysql** scection you can configure the Mysql service.
```yml
mysql:
  MYSQL_DATABASE: mydb
  MYSQL_ROOT_PASSWORD: root!
  MYSQL_USER_NAME: app
  MYSQL_USER_PASSWORD: app!
  MYSQL_MIGRATION_FILE: path/to/migration.sql
```
!!! danger
    Do not use these settings in a production environment. ;-)
