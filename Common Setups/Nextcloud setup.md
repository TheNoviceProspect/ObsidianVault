based of of an nginx image: https://www.turnkeylinux.org/nginx-php-fastcgi

simply grab the [Installer Download](https://download.nextcloud.com/server/installer/setup-nextcloud.php) via wget and put it somewhere on the webserver (ie: `/var/www/nextcloud`)
Check the [Install Instructions](https://nextcloud.com/install/#instructions-server) for more information. Paying particular attention to the NGINX section!!

After the initial install, you'll also want to add a `trusted_proxies` array in config/config.php if you're running this *behind* an [[Common Setups/Reverse Proxy Setup/Nginx Setup]]