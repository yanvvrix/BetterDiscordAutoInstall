# BetterDiscord Auto Installer & Repair Tool

A small C# utility that automatically checks whether **BetterDiscord** is still installed after Discord updates. If Discord removes the injection during an update, the tool silently reinstalls it and launches Discord again. If everything is already working, it simply exits without doing anything.

---

# How It Works

The program runs quietly in the background and follows these steps:

1. **Finds your Discord installation**
   - It scans your local `AppData` folder and automatically detects the newest installed version of Discord (for example, `app-1.0.9251`).

2. **Checks if BetterDiscord is installed**
   - The tool reads Discord's internal `index.js` file.
   - If BetterDiscord is already present, the program exits immediately.
   - If it isn't found (usually after a Discord update), the repair process begins.

3. **Closes Discord**
   - Any running Discord processes are terminated using `taskkill` to make sure no files are locked.
   - The program waits briefly before continuing.

4. **Reinstalls BetterDiscord**
   - It runs the included `bdcli.exe` (`bdcli\bdcli.exe`) with the following arguments:
     ```
     install --channel stable --silent
     ```
   - The installation is performed silently without requiring user interaction.

5. **Starts Discord**
   - Once the installation is complete, Discord is launched normally using `Update.exe`.
   - Your BetterDiscord plugins and themes should be available again.

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
