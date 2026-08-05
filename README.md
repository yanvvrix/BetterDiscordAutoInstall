# BetterDiscord Auto Installer

Never reinstall BetterDiscord manually after a Discord update again.

This lightweight utility automatically checks whether BetterDiscord is still installed whenever you sign in to Windows. If Discord has removed the injection during an update, the tool silently reinstalls BetterDiscord and launches Discord for you. If everything is already installed, it exits immediately without interrupting Discord.

## Features

- Automatically detects the latest Discord installation.
- Checks whether BetterDiscord is already installed.
- Reinstalls BetterDiscord only when necessary.
- Launches Discord after a successful repair.
- Runs silently in the background.
- One-click installation with `install_task.bat`.
- Easy removal with `uninstall_task.bat`.
- No manual Task Scheduler configuration required.

## Why use it?

If you use BetterDiscord every day, you've probably experienced Discord updates removing it unexpectedly. Normally, you'd have to open the installer and patch Discord again yourself.

This tool automates that process. Once it's set up, it quietly checks your installation every time you log in. If BetterDiscord is still there, nothing happens. If it was removed by a Discord update, the tool restores it automatically so Discord is ready to use without any extra steps.

---

# Running It Automatically at Startup

If you want BetterDiscord to be checked every time you sign in to Windows, you can add this tool to **Task Scheduler**. This allows it to run silently in the background without opening any visible windows.

## Method 1 (Recommended)

1. Place `AutoInstallBetterDiscord.exe` and the `bdcli` folder somewhere permanent (for example, `D:\BetterDiscordAutoInstaller\`).
2. Double-click `install_task.bat`.
3. That's it. The task will be created automatically.

---

## Method 2 (Manual)

1. Press **Win + R**, type `taskschd.msc`, and press **Enter**.
2. Click **Create Basic Task...**
3. Give it a name, such as **Auto BetterDiscord Repair**.
4. Choose **When I log on** as the trigger.
5. Select **Start a program**.
6. Browse to `AutoInstallBetterDiscord.exe`.
7. In **Start in (optional)**, enter the folder containing the executable (for example, `D:\BetterDiscordAutoInstaller\`). This helps avoid path-related issues.
8. Click **Finish**.

---

# Testing the Installation

You don't need to reboot your PC to make sure everything works.

1. Open **Task Scheduler**.
2. Locate the **Auto BetterDiscord Repair** task.
3. Right-click it and choose **Run**.

If BetterDiscord is already installed, the program will exit almost instantly without interrupting Discord. If Discord has removed BetterDiscord after an update, the tool will automatically reinstall it and restart Discord for you.
