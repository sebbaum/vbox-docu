# Available PHP Frameworks
If activated the following framework installers will be available:

* [Laravel](https://laravel.com/)
* [Lumen](https://lumen.laravel.com/)
* [Yii](https://www.yiiframework.com/)
* [Symfony](https://symfony.com/)
* [Laminas](https://getlaminas.org/) // formerly known as Zend Framework

You can install the frameworks e.g. in the mapped `src` folder by running:

```bash
cd /var/www/html

laravel new <project-name>

# OR

$ lumen new <project-name>

# OR

$ yii-create <project-name>

# OR

$ symfony new <project-name> [--full]

# OR

$ laminas-create <project-name>
```

!!! note
    Make sure to change your webserver's config: `/etc/nginx/sites-available/default` or `/etc/apache2/sites-available/000-default.conf` and set the correct document root.
