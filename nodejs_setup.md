# Setting Up a VPS for Node.js

## Step 1: Update Your System
First, make sure your package lists are up to date by running:
```bash
sudo apt update
```

## Step 2: Install nvm
Run the following script to install nvm:
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```
After installation, either restart your terminal or run:
```bash
source ~/.bashrc
```
List available Node.js versions:
```bash
nvm ls-remote
```
Then install the desired version:
```bash
nvm install <version_name>
```

## Step 3: Verify the Installation
Check the version of Node.js and npm to confirm that the installation was successful:
```bash
node -v
npm -v
```
You should see the version numbers for both Node.js and npm.

## Step 4: Install PM2
Make sure you have Node.js and npm installed, then install PM2 globally:
```bash
npm install -g pm2
```
Verify the installation:
```bash
pm2 --version
```

## Step 5: Start an Application with PM2
To run a Node.js application in the background, use:
```bash
pm2 start app.js
```
Replace `app.js` with the entry point of your application. List running applications:
```bash
pm2 list
```

## Step 6: Manage Applications with PM2
Restart an application:
```bash
pm2 restart app.js
```
Stop an application:
```bash
pm2 stop app.js
```
Delete an application:
```bash
pm2 delete app.js
```

## Step 7: Run Applications on System Reboot
PM2 can be configured to start your applications on system boot. Set up startup scripts:
```bash
pm2 startup
```
Save the current list of processes:
```bash
pm2 save
```
Restart your server and confirm the application restarts automatically:
```bash
sudo reboot
```

## Step 8: Set Permissions
Set the correct permissions for your application directory:
```bash
sudo chmod -R 755 /var/www/node
sudo chown -R www-data:www-data /var/www/node
```

## Step 9: Configure Apache
Enable necessary Apache modules:
```bash
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod rewrite
```
Restart Apache:
```bash
sudo systemctl restart apache2
```

## Step 10: Configure Firewall Rules
Ensure that port 80 is open on your server. Check your firewall settings:
```bash
sudo ufw status
```
If HTTP is not listed as "Allow," run:
```bash
sudo ufw allow http
```

## Step 11: Verify Node.js Application
Confirm that your Node.js application is running on port 3000. You can check with:
```bash
curl http://localhost:3000
```

## Step 12: Configure Apache Virtual Host
Create a virtual host configuration in `sites-available`:
```apache
<VirtualHost *:80>
    ServerName workshopnode.shefat.info

    ProxyPreserveHost On
    ProxyPass / http://localhost:3000/
    ProxyPassReverse / http://localhost:3000/

    ErrorLog ${APACHE_LOG_DIR}/workshopnode_error.log
    CustomLog ${APACHE_LOG_DIR}/workshopnode_access.log combined
</VirtualHost>
```