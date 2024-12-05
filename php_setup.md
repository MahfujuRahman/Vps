To install the latest version of PHP on Ubuntu, follow these steps:

### Step 1: Update the package list
Open a terminal and update the package list to ensure all repositories are up-to-date:

```bash
sudo apt update
sudo apt upgrade -y
```

### Step 2: Add the Ondřej Surý PPA (PHP Repository)
The Ondřej Surý PPA is a popular and reliable source for the latest PHP versions:

```bash
sudo apt install -y software-properties-common
sudo add-apt-repository ppa:ondrej/php
sudo apt update
```

### Step 3: Install the Latest PHP Version
At the time of writing, the latest PHP version is PHP 8.3. You can install it with:

```bash
sudo apt install -y php8.3
```

### Step 4: Verify the PHP Installation
Check the installed PHP version:

```bash
php -v
```

### Step 5: Install Additional PHP Modules (Optional)
Depending on your application requirements, you may need additional PHP modules. For example:

```bash
sudo apt install -y php8.3-mysql php8.3-xml php8.3-mbstring php8.3-curl php8.3-zip php8.3-bcmath
```

### Step 6: Restart the Web Server
If you're using a web server (e.g., Apache or Nginx), restart it to apply changes:

For Apache:

```bash
sudo systemctl restart apache2
```

For Nginx:

```bash
sudo systemctl restart nginx
```