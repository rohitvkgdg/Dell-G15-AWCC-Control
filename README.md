# Dell G15 AWCC Controller for Linux

This repository provides a pre-built tool to control the "G-Mode" (or "Game Shift") functionality on Dell G15 laptops running Arch-based Linux distributions. Since Alienware Command Center (AWCC) isn't officially supported on Linux, this tool offers a way to enable/disable G-Mode and control your fan settings, which can boost performance when gaming or doing resource intensive tasks.

## Installation

1.  Clone this repository:
    ```bash
    git clone https://github.com/rohitvkgdg/Dell-G15-AWCC-Control.git
    ```

2.  This repository contains a pre-built package that's ready to be installed on your system.
    
3. **Dependencies:**
    - Make sure you have `python` installed on your system.
    - Install `acpi_call` using an AUR helper like yay or manually
        ```bash
        yay -S acpi_call 
        ```
       or
        ```bash
            git clone https://aur.archlinux.org/acpi_call.git
            cd acpi_call
            makepkg -si
        ```
        Alternatively, you can install `acpi_call_lts` or `acpi_call-dkms` if needed.
    - **Note:** This tool requires root privileges to control system settings. If you're using a standard Arch Linux setup, you likely already have the necessary tools for handling sudo. If not you might need to install a tool like `sudo` which lets you run commands with administrator rights.

## Configuration: 

-   The `g15-fan-cli.py` script is the core of the utility, allowing the control of fan settings.
-   By default, using this script will prompt you for password when you execute the command, which you might not want every time you try to activate g-mode.

###  Using G-Mode without password prompts

 - **Important Security Note:** The following workaround requires you to include your password directly in the command, which is generally **NOT RECOMMENDED** due to security risks. We will use `sudo -S` to input the password, however this means it can be stored in your shell's history. Instead, it's recommended to use a method like `pkexec` if possible to avoid this security risk, but that will be left to the user's discretion.

 - To avoid password prompts every time, the following command can be added to your shortcuts. **Replace `'YourPasswordHere'` with your actual password:**
          ```bash
          echo 'YourPasswordHere' | sudo -S -k python ~/.local/bin/g15-fan-cli.py g
          ```
         **Recommendation:**  Consider looking into alternatives like `pkexec` which allows graphical applications to request root access without exposing password.
         
 - To bind the command to a keyboard shortcut, open your system's keyboard shortcut settings (usually found in "Settings" or "System Settings"). Add a new custom shortcut, giving it a name like "Toggle G-Mode". Paste the above command into the "Command" field and assign the F9 key (or another key of your choice) to it.


## Reporting Issues and Contributing
If you encounter any bugs or issues, please open an issue on this repository. Contributions are welcome! Feel free to fork this project and submit a pull request with your changes.
