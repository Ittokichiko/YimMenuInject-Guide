# YimMenu under Proton
This is a basic guide on how to run YimMenu under Proton for people who play Grand Theft Auto V on Linux and do not feel like dual booting to "have some fun." There are probably more optimal ways of accomplishing this; however, these methods works, and do not appear to introduce any stability problems.

<img width="2559" height="1409" alt="361622826-34fa15b8-fafc-45a8-a905-8c1f512419f1" src="https://github.com/user-attachments/assets/a0f5eef7-1463-4d3f-8133-89580c1506b2" />


> [!NOTE]
> I am in no way involved with the development of YimMenu, or any other open source projects mentioned in this guide. I simply figured this may be useful information for other users I've seen inquiring about this topic.

> [!IMPORTANT]
Before you begin, ensure you have Grand Theft Auto V installed, as well as the `protontricks` package via your system's package manager.

# Injectors
You have several options as far as injectors go, just ensure the injector itself works under Proton. I have verified two to work perfectly fine, one being GUI based and the other being simply terminal; this guide will cover both. If you choose to use a different injector than listed here, adjust the specifics accordingly, but the overall concepts should apply.

This guide will cover:
- [Process Hacker 2](https://github.com/lucasg/processhacker2), to inject YimMenu using a GUI.
- [Injector](https://github.com/nefarius/Injector), to inject YimMenu using your terminal.

> [!IMPORTANT]
> Regardless of which injection method you move forward with, you will need the `YimMenu.dll` file to inject. You can download the latest release of YimMenu [here](https://github.com/YimMenu/YimMenu/releases/nightly). Ensure this file is placed somewhere easily navigatable, preferably outside of the Proton prefix's filesystem for the game.

## Injection via Process Hacker 2
### Setup
1. Download the latest `processhacker-<version>-bin.zip` file, which you can find [here](https://sourceforge.net/projects/processhacker/files/processhacker2/).
2. Extract the `x86` or `x64` folder (depending on your system) from the Process Hacker 2 zip archive to somewhere easily navigatable.

### Injection
1. Launch the game, wait until game window opens.
2. Alt-tab out of game, open a terminal and run the following command:
```
protontricks-launch --no-bwrap --appid 271590 <Linux path to ProcessHacker.exe>
```
3. Within the Process Hacker window, find ``GTA5.exe`` in the list of applications. **NOT ``PlayGTAV.exe``, THIS WILL NOT WORK!**
4. Right click on ``GTA5.exe``, navigate to ``Miscellaneous`` > ``Inject DLL...``
5. In the file browser that pops up, navigate to your YimMenu.dll file and open it.
6. If injection was successful, a "YimMenu" console will appear. This is identical to the one that opens on Windows.

> [!TIP]
> To automatically launch the Process Hacker executable alongside the game each time you start it, you can set your launch parameters to launch it as a background task. You can do this on Steam by setting this as your launch options:
> ```
> (sleep 10 && protontricks-launch --no-bwrap --appid 271590 <path to ProcessHacker.exe>) & %command%
> ```

## Injection via Injector
### Setup
1. Download the latest Injector release's archive file, which you can find [here](https://github.com/nefarius/Injector/releases/).
2. Extract the `Win32` or `x64` folder (depending on your system) from the Injector zip archive to somewhere easily navigatable.
  
### Injection
1. Launch the game, wait until game window opens.
2. Alt-tab out of game, open a terminal and run the following command:
```
protontricks-launch --appid 271590 <Linux path to GTA V Proton prefix>/drive_c/windows/system32/cmd.exe /c "<Windows path to Injector.exe> --inject --process-name GTA5.exe <Windows path to YimMenu.dll>"
```
3. If injection was successful, a "YimMenu" console will appear. This is identical to the one that opens on Windows.

# Adding Lua extensions
Adding Lua extensions to YimMenu works the exact same way as it does on Windows, you just simply need to ensure you are accessing the `%appdata%/YimMenu/scripts` within the correct Proton prefix. You can find this using the button ingame (`Settings` > `Lua Scripts` > `Open Lua Scripts Folder`), or, by navigating to the following path (assuming you are using Steam):
```
<Linux path to GTA V Proton prefix>/drive_c/users/steamuser/AppData/Roaming/YimMenu/scripts
