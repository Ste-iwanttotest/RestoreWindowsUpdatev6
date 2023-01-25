# Notes

1. In this guide, NT5 refers to XP, Server 2003 and 2000

   NT6 refers to Vista and newer.

2. This procedure hasn't been tested for Windows 7.

3. For technical reasons, if you enable Microsoft Update on XP RTM, SP1, SP2 will cause Automatic Updates to stop working.

# Clients configuration

1. Install required packages. If Windows Update Agent refuses to install, see Force Install section below.

2. Open Internet Explorer, go to Internet options, open Connections tab and clic Lan Settings

   Select Use a proxy server ... and clic Advanced.
 
   Insert your server IP address into Secure, put 8079 as port.

3. Confirm the two dialog windows and return to Internet options.

   Go to Advanced and enable:

   Use HTTP/1.1 over proxy connections.

   SSL 3.0

   TLS 1.0
4. Now confirm and close IE.

5. Open a CMD and run:

   copy C:\winnt\system32\winhttp.dll C:\winnt\system32\winhttp5.dll  (only on 2000)

   proxycfg -u (on NT5)

   netsh winhttp import proxy source=ie (on NT6)

6. Copy CA.crt from your server's ProxHTTPSProxy folder (will appear after first run)

7. Import it. Be sure to place it in Trusted Root Certifications Authorities / Local Computer

# Websites

Windows Update: fe2.update.microsoft.com/windowsupdate/v6/default.aspx?g_sconsumersite=1

Microsoft Update: fe2.update.microsoft.com/microsoftupdate/v6/default.aspx?g_sconsumersite=1

To enable Microsoft Update, find muweb.dll on the web, download it and run regsvr32 muweb.dll (in muweb.dll folder).
# Force Install

On NT5:
   
   Run windowsupdateagent30 with /WUforce option.

On NT6:

   Go to C:\Windows\system32, select wuaueng.dll and open properties.

   Go to security tab, clic advanced, select owner and clic Change Owner

   Put your username into the field and confirm all the dialog windows.

   Reopen properties and go to security, clic modify and select your username.

   Select full controll (consent), clic OK and OK.

   Run windowsupdateagent30. Do not clic finish!

   Go to C:\some_letters_and_numbers

   Copy wuaueng.dll to C:\windows\system32 (overwrite)

   Reboot your system

# Bonus: use website on NT6

   Run windowsupdateagent30. Do not clic finish!

   Go to C:\some_letters_and_numbers

   Copy wuweb.dll to C:\windows\system32

   Run regsvr32 wuweb.dll
