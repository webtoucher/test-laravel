Инструкция по установке
===========

У моего приложения url будет test.dev.ru (это локальный адрес). Разумеется придётся заменить на тот, что будет использоваться у вас.

Окружение такое: CentOS 6.4, PHP-FPM, PHP 5.4, SQLLite3

Устанавливаем фреймворк:

```bash
cd /var/www && curl -sS https://getcomposer.org/installer | php && php composer.phar create-project laravel/laravel --prefer-dist && mv laravel test.dev.ru && cd test.dev.ru && mkdir logs
```

Добавляем мой код:

```bash
wget -O - https://github.com/Webtoucher/test-laravel/archive/master.tar.gz | tar -xzp --strip=1
```

Прокидываем конфиг для nginx:

```bash
ln -s /var/www/test.dev.ru/app/config/nginx.conf /etc/nginx/conf.d/test.dev.ru.conf
```

Так же не забываем поправить хост в protected/config/nginx/nginx.conf. Перезапускаем nginx:

```bash
service nginx restart
```
