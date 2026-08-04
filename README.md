How the program Works:

This C# automation tool keeps BetterDiscord permanently active and automatically repairs it whenever Discord updates. It runs completely hidden in the background without opening any console windows.

Execution Sequence:
1. Targeting the Core: The program automatically scans your local AppData directory and locates the most recent Discord directory using robust semantic version parsing (e.g., prioritizing app-1.0.9251 over older builds).
2. Smart Injection Check: It physically opens and reads the internal JavaScript entry point of the Discord desktop core (index.js).
   If BetterDiscord is present: The program immediately terminates within a few milliseconds. Your running Discord is never interrupted.
   If BetterDiscord is missing (wiped by a fresh Discord update): It moves to the repair stage.
3. Hardcore Process Cleanup: The application invokes a system-level taskkill to forcefully flush all running Discord and hidden Electron instances from the RAM. It pauses for 1.5 seconds to let Windows release lock handles on files.
4. Silent Injection: It calls your pre-configured official executable (bdcli.exe) located at BetterDiscordAutoInstaller\bdcli\bdcli.exe. It passes the install --channel stable --silent arguments to apply the patch without triggering interactive user prompts or freezing.
5. Seamless Relaunch: Once the injection is completed successfully, it boots up the official Discord launcher (Update.exe), opening your Discord with all your themes and plugins restored.

How to Add It to Windows Startup (Automation Guide)

To make this program automatically monitor and fix BetterDiscord every time you turn on your PC, you should register it via Windows Task Scheduler. This method runs the application faster than the traditional "Startup" folder and keeps it completely invisible.

1. Press Win + R on your keyboard, type taskschd.msc, and hit Enter to open the Task Scheduler.
2. In the right-hand panel ("Actions"), click on "Create Basic Task...".
3. Name: Enter a clear name, for example: Auto BetterDiscord Repair. Click Next.
4. Trigger: Select "When I log on". This ensures the tool executes right when your desktop environment loads. Click Next.
5. Action: Select "Start a program". Click Next.
6. Program/script: Click "Browse..." and select your compiled .exe file.
7. Start in (Optional): Copy and paste the absolute path of the folder where your .exe file resides (e.g., D:\BetterDiscordAutoInstaller\). This prevents path-resolution issues. Click Next.
8. Click "Finish" to save your task.

Verify Background Operation:
You can test the setup immediately without restarting your PC:

1. Find your new task in the center list of the Task Scheduler.
2. Right-click it and choose "Run".

The application will seamlessly audit your Discord directories in the background. If your BetterDiscord patch is intact, you won't see any blinking windows, and your active Discord window won't even flinch.
