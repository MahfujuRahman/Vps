## Laravel Setup

### Step 1: Install Composer Dependencies
```bash
composer install
```

### Step 2: Move Project Code
Move the project code to the following directory:
```bash
/var/www/foldername
```

### Step 3: Set Permissions
Set the necessary permissions for the Laravel project directories:
```bash
sudo chmod -R 777 /var/DirectoryName
sudo chown -R www-data:www-data /var/DirectoryName
sudo chown -R www-data:www-data /var/www/html/laravel/storage
sudo chown -R www-data:www-data /var/www/html/laravel/bootstrap/cache
```

### Step 4: Configure Apache
Navigate to the Apache sites-available directory and create a new site configuration. Enable the site using `a2ensite`:
```bash
cd /etc/apache2/sites-available
# Create and edit your site configuration file
sudo a2ensite your-site-config.conf
```

If using a proxy, set the necessary proxy settings in the site configuration file.
```