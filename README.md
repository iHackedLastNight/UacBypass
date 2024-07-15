# UAC Bypass with Shellcode Execution

## Overview

This project demonstrates a method to bypass User Account Control (UAC) on Windows systems using a combination of registry manipulation and shellcode execution. It leverages a vulnerability in the "fodhelper.exe" application to escalate privileges and execute arbitrary code.

## Prerequisites

- Visual Studio or another C++ compiler to build the executable.
- Knowledge of compiling and running Windows applications.

## Usage

### Build the Executable

1. Open the provided source code in Visual Studio or compile it using your preferred C++ compiler.
   
### Generate Shellcode

1. Generate your own shellcode using tools like `msfvenom` or any other preferred method.
2. Replace the `shellcode` array in the source code with your generated shellcode.

### Execution Steps

1. The program performs the following steps:
   - Creates a registry key under `HKEY_CURRENT_USER\Software\Classes\ms-settings\shell\open\command` to set the payload executable (`cmd.exe` in this case).
   - Modifies the `DelegateExecute` and default values of the registry key to trigger the UAC bypass when `fodhelper.exe` is executed.
   - Launches `fodhelper.exe` to escalate privileges.
   - Writes a test file to `C:\Windows\System32\uac_bypass_test.txt` to verify successful bypass.
   - If bypass is successful, executes the embedded shellcode to gain elevated privileges.
   - Deletes the registry keys created to clean up.

### Notes

- This code is provided for educational purposes and should be used responsibly.
- Ensure you have the necessary permissions and antivirus exclusions to run and test such code.
- Understand the implications and legality of executing shellcode and bypassing UAC in your environment.

## Disclaimer

This code is provided as-is without any warranty. Use at your own risk. Misuse of this code may violate laws and regulations.
