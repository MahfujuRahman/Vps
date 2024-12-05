# Apache2 Setup in Linux

## Steps

1. **Update your package list and install Apache:**
    ```bash
    sudo apt-get update
    sudo apt upgrade -y
    sudo apt install apache2 -y
    ```
    - `sudo apt-get update`: Updates the list of available packages and their versions.
    - `sudo apt upgrade -y`: Upgrades all the installed packages to their latest versions. The `-y` flag automatically answers 'yes' to any prompts.
    - `sudo apt install apache2 -y`: Installs the Apache2 package. The `-y` flag automatically confirms the installation.

2. **Check Apache status:**
    ```bash
    sudo systemctl status apache2
    ```
    - `sudo systemctl status apache2`: Checks the current status of the Apache2 service.

3. **Start and enable Apache service:**
    ```bash
    sudo systemctl start apache2
    sudo systemctl enable apache2
    ```
    - `sudo systemctl start apache2`: Starts the Apache2 service.
    - `sudo systemctl enable apache2`: Enables Apache2 to start on boot.

4. **Restart Apache after configuration changes:**
    ```bash
    sudo systemctl restart apache2
    ```
    - `sudo systemctl restart apache2`: Restarts the Apache2 service to apply any configuration changes.

5. **Stop Apache service:**
    ```bash
    sudo systemctl stop apache2
    ```
    - `sudo systemctl stop apache2`: Stops the Apache2 service.
