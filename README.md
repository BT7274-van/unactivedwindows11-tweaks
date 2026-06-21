# unactivedwindows11-tweaks
list of work arounds using cmd for windows so you don't have to active windows.

Windows 11 Unactivated Control List
When Windows 11 is not activated, the Personalization menu is locked. You can bypass these locks and alter hidden features using background registry commands.
Execution Protocol

   1. Select the text inside any target command code block.
   2. Search for cmd in your taskbar, right-click Command Prompt, and select Run as administrator.
   3. Paste the target command line directly into the terminal window and hit Enter.
   4. Restart your system immediately afterward to commit the registry variations to the OS layer.

Personalization and System Customization

   1. Windows Dynamic Lighting API
   Controls accessory illumination profiles. Disabling this stops the Bluetooth drop/reconnect loop on DualSense/PS5 controllers.
   Turn OFF:

reg add "HKCU\Software\Microsoft\Lighting" /v AmbientLightingEnabled /t REG_DWORD /d 0 /f

Turn ON:

reg add "HKCU\Software\Microsoft\Lighting" /v AmbientLightingEnabled /t REG_DWORD /d 1 /f


   1. System Display Themes (Dark Mode vs. Light Mode)
   Forces the system applications and general OS shell to switch out of the locked default Light Mode.
   Turn ON Dark Mode:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 0 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v SystemUsesLightTheme /t REG_DWORD /d 0 /f

Turn ON Light Mode:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v AppsUseLightTheme /t REG_DWORD /d 1 /f
reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v SystemUsesLightTheme /t REG_DWORD /d 1 /f


   1. Taskbar Layout Positioning
   Controls whether the Windows Start button layout sits centered or shifts to the left quadrant.
   Move Taskbar Alignment to Left Side:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarAl /t REG_DWORD /d 0 /f

Move Taskbar Alignment to Center:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarAl /t REG_DWORD /d 1 /f


   1. Accent Color Sync Layer
   Applies your custom chosen system highlights to window borders and Title bars.
   Turn ON Accent Border Colors:

reg add "HKCU\Software\Microsoft\Windows\DWM" /v ColorPrevalence /t REG_DWORD /d 1 /f

Turn OFF Accent Border Colors:

reg add "HKCU\Software\Microsoft\Windows\DWM" /v ColorPrevalence /t REG_DWORD /d 0 /f


   1. Transparency Acrylic Effects
   Toggles the translucent background layer effect on the taskbar and system windows.
   Turn OFF Translucent Transparency:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableTransparency /t REG_DWORD /d 0 /f

Turn ON Translucent Transparency:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Themes\Personalize" /v EnableTransparency /t REG_DWORD /d 1 /f

Interface De-bloating and Menu Restoration

   1. Legacy Context Right-Click Menus
   Restores the functional Windows 10 right-click context menu, skipping the nested Windows 11 Show More Options layer.
   Turn ON Classic Context Right-Click Menu:

reg add "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32" /ve /t REG_SZ /d "" /f

Revert to Default Stock Windows 11 Menu:

reg delete "HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}" /f


   1. Taskbar Feed Widgets
   Removes the left-hand taskbar pop-up layout pane that aggregates MSN news feeds and weather items.
   Turn OFF Taskbar Widgets:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarDa /t REG_DWORD /d 0 /f

Turn ON Taskbar Widgets:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v TaskbarDa /t REG_DWORD /d 1 /f


   1. Microsoft Copilot Interface
   Removes the native AI sidebar integration toggle icon sitting on the taskbar field.
   Turn OFF Copilot Icon Placement:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowCopilotButton /t REG_DWORD /d 0 /f

Turn ON Copilot Icon Placement:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowCopilotButton /t REG_DWORD /d 1 /f


   1. Taskbar Search Box Formats
   Changes how much physical footprint the desktop search engine takes up along your bottom bar.
   Hide Search Layout Entirely:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v SearchboxTaskbarMode /t REG_DWORD /d 0 /f

Show Search as an Icon Only:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v SearchboxTaskbarMode /t REG_DWORD /d 1 /f

Show Search as a Wide Long Box:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v SearchboxTaskbarMode /t REG_DWORD /d 3 /f

Telemetry, Diagnostics and Privacy Isolation

   1. Core Windows Diagnostic Telemetry
   Restricts the depth of system usage profiles compiled and shipped off to outbound monitoring endpoints.
   Turn OFF Advanced Telemetry (Drop to Minimal Security Tier):

reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 0 /f

Restore Default Diagnostic Reporting Data:

reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\DataCollection" /v AllowTelemetry /t REG_DWORD /d 3 /f


   1. Start Menu Bing Web Integration
   Stops local keyword menu queries from spawning slow web searches across Edge and Bing engines.
   Turn OFF Start Menu Bing Web Searches:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 0 /f

Turn ON Start Menu Bing Web Searches:

reg add "HKCU\Software\Microsoft\Windows\CurrentVersion\Search" /v BingSearchEnabled /t REG_DWORD /d 1 /f


   1. Tailored Experiences Data Tracking
   Blocks personalization engines from logging app usage behaviors to build consumer advertising IDs.
   Turn OFF Tailored Experiences:

reg add "HKCU\Software\Policies\Microsoft\Windows\CloudContent" /v DisableTailoredExperiences /t REG_DWORD /d 1 /f

Turn ON Tailored Experiences:

reg add "HKCU\Software\Policies\Microsoft\Windows\CloudContent" /v DisableTailoredExperiences /t REG_DWORD /d 0 /f


   1. Lock Screen Content Interceptions
   Skips the multi-layer lock screen display to bypass wallpaper restrictions and load directly into your secure credential input field.
   Turn OFF Lock Screen (Direct to PIN Prompt):

reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization" /v NoLockScreen /t REG_DWORD /d 1 /f

Turn ON Lock Screen Window:

reg add "HKLM\SOFTWARE\Policies\Microsoft\Windows\Personalization" /v NoLockScreen /t REG_DWORD /d 0 /f

Disclaimer: Registry modifications alter core backend data nodes. Verify code strings exactly before attempting execution routines.

Would you like me to supply a template for a setup instruction file to go with this repository, or would you like to focus on setting up a specific configuration next?

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/C0C01UE2MH)
