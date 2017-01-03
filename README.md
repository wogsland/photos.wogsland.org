# photos.wogsland.org

Basically this is a photo site for personal photos that I am building from with
[Laravel](http://laravel.com/docs).

## Setup

Install the composer packages (in the project root directory):

    composer install

Add the following to `/etc/apache2/extra/httpd-vhosts.conf` to enable the virtual
host and then restart apache:

    <VirtualHost *:80>
        ServerAdmin bradley@wogsland.org
        ServerName photos.wogsland.local
        DocumentRoot "/Library/Webserver/Documents/photos.wogsland.org/public"

        <Directory "/Library/Webserver/Documents/photos.wogsland.org/public">
                Options -Indexes +FollowSymLinks +MultiViews
                AllowOverride All
                Require all granted
        </Directory>

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
    </VirtualHost>

and then to `/etc/hosts` Add

    127.0.0.1  photos.wogsland.local

Then change up permissions for logging (in the project root directory):

    sudo chown -R _www storage
    sudo chown -R _www bootstrap/cache/

more on configuration [here](https://laravel.com/docs/master#configuration). And
you may also need to

    php artisan key:generate

## License

The code for this site is open-sourced software licensed under the
[MIT license](http://opensource.org/licenses/MIT).
