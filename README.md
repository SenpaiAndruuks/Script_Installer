# Script_Installer
This is just something I made using ChatGPT to make a scrpit for my work to download all the installers for example like google chrome it would excicute a code from notepad that would be using through powershell.




## How to run the Script: 

1. Prepare the Flash Drive
   A. Insert your flash drive into the computer
   B. Create a folder on the flash drive named `Installers`. This folder will hold all the `.exe` installer          files for the programs you want to install.

   Example:
   Flash Drive (X:)
   ```
   Installers
     ChromeSetup.exe
     7z1900-x64.exe
     SteamSetup.exe
     DiscordSetup.exe
   ```

## 2. Copy the Installers
   A. Download the offline installers for the programs you want to install.
     <br>
     <br>
     * Google Chrome: Download the Chrome Offline Installer.
     <br>
     <br>
     *  7-Zip: Download from 7-Zip Official Website.
     <br>
     <br>
     *  team: Download from Steam Official Website. 
     <br>
     <br>
     * Discord: Download from Discord Official Website.
     <br>
     <br>
     * Additional programs (e.g., VLC Media Player, Notepad++): Use their official websites to download             offline installers.
     <br>
     <br>

   B. Place all `.exe` files in the `Installer` folder on your flash drive


## 3. Setup PowerShell Script
  1. Copy the updated `InstallPrograms.ps1` script (Provided above) to the root of your flash drive
     (outisde the `Installers` folder)
  2. Open the script file with a text editor (Notepad)
     

## 4. Enable PowerShell Script Excution
By default, PowerShell scripts are restricted from running. You need to temporarily enable script execution.

  1. Open PowerShell as Administrator:
       * Press `Window Symbol` Type `PowerShell`on the search bar and run as Administrator.
  2. Allow the script to run by entering:
     <br>
     `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`
      <br>

## 5. Run the Script
  1. Navigate to the flash drive in PowerShell. Replace `X` with the drive letter of the flash drive:
     ```
     cd X:\
     ```
  2. Run the script:
     ```
     .\InstallPrograms.ps1
     ```

## 6. Use the Script
  1. The script will display a list of all `.exe` files in the `Installers` folder, like this:
     ```
      1. ChromeSetup.exe
      2. 7z1900-x64.exe
      3. SteamSetup.exe
      4. DiscordSetup.exe
    
  2. It will prompt you to select which program(s) you want to install by entering the corresponding numbers:
     ```
     Enter the number(s) of the installer(s) you want to install (e.g., 1,2,3):

  3. Enter the numbers, separated by commas, for the programs you want to install (e.g., `1,3,5` for Chrome, 
  Steam).

     
  4. The script will then install the selected programs silently. It will create a `install_log.txt` file in the script       directory to log installation progress and errors.



## 7. Check Installations
  1. Once the script finishes, review the output in PowerShell to see if any programs failed to install.

  2. Open the `install_log.txt` file to verify installation success or troubleshoot errors.


## Customizing (Optional)
  A. If you add new programs that require specific silent installation flags, follow these steps:
  
   1. Identify the program's silent install flag by searching online (e.g., for "ProgramName silent install command").
    
   2. Open the script in a text editor and add an `elseif` block for the program with its specific flag.

  ## Example:
      elseif ($installer.Name -like "vlc*.exe") {
    Write-Log "Detected VLC installer. Installing VLC..."
    Start-Process -FilePath $installerPath -ArgumentList "/S" -Wait -NoNewWindow
    }

      
## 8. Troubleshooting Common Issues
  1. Script Fails to Run: Ensure you’ve enabled script execution with:
     ```
     Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
  2. Installer Fails to Install:
       Check the `install_log.txt` for errors. Ensure the installer supports silent installation and uses          the correct flags.
  3. Administrator Privileges Required:
     Some programs require admin rights. Run PowerShell as Administrator.

 ## Summary 
  
   1. Place all installers in the Installers folder on the flash drive.
   2. Run the InstallPrograms.ps1 script.
   3. Select programs to install when prompted.
   4. Review the log file for errors or successful installations.


















       
