# PHP

## Versions
As mentioned in the [configuration](configuration.md) section, it is possible to install multiple PHP versions.
However only one is active. This version is called the current version:

```yml
php:
  current: 7.2
  versions:
    - 7.2
    - 7.3
    - 7.4
```

### Changing the PHP version
If you want to change your current PHP version, all you have to do is changing the value of `current` and provision your box:
```bash
vagrant provision
```

If this is not working, you can den destroy and recreate your box.
```bash
vagrant destroy
vagrant up
```

The current version is used in the webservers configuration to handle PHP requests.

## Modules
The following PHP module are installed by default:
```yml
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

## Composer
Composer is PHP's dependency manager and is installed by default if PHP provisioning is enabled.

## Xdebug
Xdebug the famous PHP debugging extension is installed and configured as well.  
You can enable your favorite IDE to use Xdebug.

## Additional modules
Even if you do not use Redis or Memcached, appropriate modules for PHP are installed for you.

## Ioncube
> Using ionCube encoded and secured PHP files requires a file called the ionCube Loader to be installed on the web server and made available to PHP.

You can enable installation of [ionCube loader](https://www.ioncube.com/loaders.php) for your PHP version by setting:

```yml
php:
  current: 7.2
  versions:
    - 7.2
  ioncube: true
```
