# MobaXtrem Setup in Linux

I am using Wine to install MobaXterm on an Ubuntu system.

## Steps

1. **Update your package list:**
    ```bash
    sudo apt update
    sudo apt install wine64 wine32
    ```

2. **Verify the Wine version:**
    ```bash
    wine --version
    ```

3. **Run MobaXterm using Wine:**
    Navigate to the directory where the MobaXterm `.exe` file is located and run it using Wine:
    ```bash
    wine 'filepath'/MobaXterm_Portable_vXX.exe
    ```
    Example for my case:
    ```bash
    wine /home/ajmain/Downloads/MobaXterm_Portable_v24.3/MobaXterm_Personal_24.3.exe
    ```

## Create a Desktop Shortcut

No, you don’t need to run the command manually every time. You can create a **desktop shortcut** or a **custom launcher** to make running MobaXterm easier.

### 1. **Locate the MobaXterm File**
Make sure you know the full path to the `MobaXterm_Portable_vXX.exe` file. For example:
```
/home/ajmain/Downloads/MobaXterm_Portable_v23.2.exe
```

### 2. **Create a Desktop Shortcut**
1. Open a terminal and create a `.desktop` file in your desktop folder:
    ```bash
    nano ~/Desktop/MobaXterm.desktop
    ```

2. Add the following content to the file:
    ```ini
    [Desktop Entry]
    Name=MobaXterm
    Comment=Run MobaXterm using Wine
    Exec=wine /home/ajmain/Downloads/MobaXterm_Portable_v24.3/MobaXterm_Personal_24.3.exe
    Type=Application
    Icon=utilities-terminal
    Terminal=false
    Categories=Utility;
    ```
    Replace `/path/to/MobaXterm_Portable_vXX.exe` with the full path to your MobaXterm file.

3. Save and exit the editor (`Ctrl+O`, then `Enter`, and `Ctrl+X`).

4. Make the shortcut executable:
    ```bash
    chmod +x ~/Desktop/MobaXterm.desktop
    ```

### 3. **Add to Application Menu**
If you prefer it to appear in your application menu:
1. Move the `.desktop` file to `/usr/share/applications/`:
    ```bash
    sudo mv ~/Desktop/MobaXterm.desktop /usr/share/applications/
    ```

2. You can now search for "MobaXterm" in your application menu and run it like any other app.

### 4. **Automate Wine Configuration**
If MobaXterm requires specific Wine configurations, you can ensure these are applied automatically:
- Use `winetricks` to install dependencies globally.
- Add any required Wine prefix setup commands in a shell script and point the shortcut to it.

Now, you can launch MobaXterm easily without typing the command manually every time. Let me know if you face any issues!
