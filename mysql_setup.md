# Install MySQL

To install MySQL on a Linux system, follow these steps based on your distribution.

## For Ubuntu/Debian-based systems:

1. **Update the package index:**

    ```bash
    sudo apt update
    ```

2. **Install MySQL server:**

    ```bash
    sudo apt install mysql-server
    ```

3. **Secure MySQL installation:**

    After installation, run the security script to configure MySQL:

    ```bash
    sudo mysql_secure_installation
    ```

    This will help you set a root password and configure other security settings.

4. **Check MySQL status:**

    Make sure MySQL is running:

    ```bash
    sudo systemctl status mysql
    ```

5. **Log into MySQL:**

    You can log into the MySQL server using the following command:

    ```bash
    sudo mysql -u root -p
    ```

6. **Set the root password (for MySQL 5.7 and newer):**

    Once you're inside the MySQL shell, you can set or change the root password by running the following commands:

    ```sql
    ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your_new_password';
    ```

    Replace `your_new_password` with your desired password. Make sure to choose a strong password.


# Uninstall Mysql

1. **Fix Broken Dependencies**

    Run the following command to attempt to fix broken dependencies:

    ```bash
    sudo apt-get install -f
    ```

    This will try to fix any missing or broken packages.

2. **Remove dbconfig-mysql and MySQL-related Packages**

    Next, try removing the problematic `dbconfig-mysql` package, which is causing the dependency error:

    ```bash
    sudo apt-get purge dbconfig-mysql
    ```

3. **Try Removing MySQL Again**

    After removing `dbconfig-mysql`, attempt to remove MySQL packages again:

    ```bash
    sudo apt-get remove --purge mysql-server mysql-client mysql-common mysql-server-core-8.0 mysql-client-core-8.0
    ```

4. **Remove Unused Dependencies**

    Remove any unused dependencies and leftover packages:

    ```bash
    sudo apt-get autoremove --purge
    ```

5. **Clean Up Residual Files**

    Remove residual configuration and data files:

    ```bash
    sudo apt-get autoclean
    sudo rm -rf /etc/mysql /var/lib/mysql /var/log/mysql
    ```

6. **Check MySQL Service Status**

    Check the status of MySQL to ensure it’s fully removed:

    ```bash
    sudo systemctl status mysql
    ```

    It should report that MySQL is not found or inactive.

7. **Remove MySQL User and Group (Optional)**

    If you still want to remove the MySQL user and group from your system:

    ```bash
    sudo deluser mysql
    sudo delgroup mysql
    ```

## Install phpMyAdmin

1. **Install phpMyAdmin:**

    ```bash
    sudo apt install phpmyadmin
    ```

2. **Enable mbstring and restart Apache:**

    ```bash
    sudo phpenmod mbstring
    sudo systemctl restart apache2
    ```

3. **Download phpMyAdmin:**

    Download phpMyAdmin from [phpMyAdmin.net](https://www.phpmyadmin.net/).

4. **Upload and unzip phpMyAdmin:**

    Upload and unzip it into your VPS at `/var/www/'yourfoldername'`.

5. **Configure Apache:**

    Go to `/etc/apache2/sites-available` and create a file using your web name address, ending with `.conf`. For example, `workshopsql.shefat.info.conf`.

    Add the following configuration:

    ```apache
    <VirtualHost *:80>
        ServerName domain
        DocumentRoot /var/www/domain/public

        <Directory /var/www/domain/public>
            Options Indexes FollowSymLinks
            AllowOverride All
            Require all granted
        </Directory>
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
    </VirtualHost>
    ```

    For proxy setup:

    ```apache
    <VirtualHost *:80>
        ServerName domain
        ProxyPreserveHost on
        ProxyPass / http://localhost:5001/
        ProxyPassReverse / http://localhost:5001/
    </VirtualHost>
    ```

6. **Enable the site and restart Apache:**

    ```bash
    sudo a2ensite 'yoursitename'
    sudo systemctl restart apache2
    ```

    For example:

    ```bash
    sudo a2ensite 'workshopsql.shefat.info.conf'
    sudo systemctl restart apache2
    ```