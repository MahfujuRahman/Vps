# VPS Setup


## Steps

1. **Update your package list:**
    ```bash
    sudo apt update
    sudo apt install wine64 wine32
    ```
<VirtualHost *:80>

  ServerName  workshop.shefat.info
  ServerAlias workshop.shefat.info

  DocumentRoot /var/www/laravel/public
  <Directory /var/www/laravel/public>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>


<VirtualHost *:80>

  ServerName  workshopsql.shefat.info
  ServerAlias workshopsql.shefat.info

  DocumentRoot /var/www/sql/phpMyAdmin-5.2.1-all-languages
  <Directory /var/www/sql/phpMyAdmin-5.2.1-all-languages>
    Options Indexes FollowSymLinks
    AllowOverride All
    Require all granted
  </Directory>

  ErrorLog ${APACHE_LOG_DIR}/error.log
  CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>