# MailHog

Usually, you have to send emails in your web app e.g. in cases where

* a user registered
* a user wants to reset his/her password
* and a lot of other cases

It is annoying to create test users to avoid sending real mails to your customers.
Therefore you can enable [MailHog](https://github.com/mailhog/MailHog), a fake SMTP service, in the configuration.

```yml
provision:
  mailhog: true
```

After provisioning, you can access MailHog's web GUI at:  
http://10.0.0.42:8025

MailHog will intercept all outgoing emails and you can view them in the web GUI.

## Try it out
You can test MailHog by placing the following snippet in a php file, that
is served by your web app.
```php
mail('you@awesome-app.com', 'Testing mail', 'It works!');
```
After executing this code, you should see a new mail in MailHog's web GUI.
