# BetterDiscord Auto Install

A small utility that automatically restores BetterDiscord after Discord updates.

Discord updates sometimes remove BetterDiscord, which means you have to run the installer again before your plugins and themes work. This tool automates that process by checking your Discord installation whenever you sign in to Windows. If BetterDiscord is missing, it reinstalls it automatically. If it's already installed, the program exits immediately without doing anything.

## Features

- Detects the latest installed version of Discord.
- Checks whether BetterDiscord is already installed.
- Reinstalls BetterDiscord only when necessary.
- Launches Discord after a successful repair.
- Runs silently in the background.
- One-click setup with `install_task.bat`.
- Easy removal with `uninstall_task.bat`.
- No manual configuration required.

---

# Running at Startup

To automatically check BetterDiscord every time you sign in, register the program with **Windows Task Scheduler**.

## Method 1 (Recommended)

1. Place `AutoInstallBetterDiscord` folder in a permanent location (for example, `D:\BetterDiscordAutoInstaller\`).
2. Double-click `install_task.bat`.
3. Approve the UAC prompt if Windows asks.
4. The scheduled task will be created automatically.

---

## Method 2 (Manual)

1. Press **Win + R**, type `taskschd.msc`, and press **Enter**.
2. Click **Create Basic Task...**
3. Enter a name (for example, `Auto BetterDiscord Repair`).
4. Select **When I log on** as the trigger.
5. Choose **Start a program**.
6. Browse to `AutoInstallBetterDiscord.exe`.
7. In **Start in (optional)**, enter the folder containing the executable (for example, `D:\BetterDiscordAutoInstaller\`).
8. Click **Finish**.

---

# Testing

You can verify that everything is working without restarting your computer.

1. Open **Task Scheduler**.
2. Find the **Auto BetterDiscord Repair** task.
3. Right-click it and select **Run**.

If BetterDiscord is already installed, the program will exit immediately. If a Discord update has removed BetterDiscord, the tool will reinstall it automatically and launch Discord once the process is complete.
