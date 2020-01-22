# Orientation
Welcome to the ProDigitalWorx team!  This orientation is to help guide new team members through the setup process for your workstation and put you in touch with important members of the Toyota family.  

>Please follow the orientation sequentially.  Feel free to ask for help should you become stuck at any point.  We will be glad to assist you.  

Let's begin!

## Obtaining Your Keycard
This is definitely something you need.  But from where and who, I have no idea.
>Someone who knows, add this

## P1tStop!
Make friends with the friendly IT persons at P1tStop!  Located on the first floor of E2(our building), P1tStop is our one stop for all our IT needs.  Here you will request your laptop on day one and should receive it within the hour.  You will need to show your keycard to verify your identity.  When you receive your laptop, check to see that everything has been included.

>You should have:
1. Laptop with charge cord
2. Small pouch with headphones inside
3. Wireless USB mouse

## Setting Up Your Laptop
Now that you have your laptop, have a seat at your desk and familiarize yourself with your work environment.  Your login settings are shared across Toyota software and hardware.  

>To login to your laptop please enter your email firstname.lastname@toyota.com and the password which you chose at P1tStop at initial login.

First step will be getting a new browser.  Our recommendation is Google Chrome.  In the lower left on your desktop, search for Powershell and open it.  We will use a different terminal later in the process and for work.  

>Copy and paste commands from code blocks where indicated.  

Below is the code to copy and paste to Powershell which will install Google Chrome.
>You can easily highlight by triple clicking on a character.
```powershell
$LocalTempDir = $env:TEMP; $ChromeInstaller = "ChromeInstaller.exe"; (new-object    System.Net.WebClient).DownloadFile('http://dl.google.com/chrome/install/375.126/chrome_installer.exe', "$LocalTempDir\$ChromeInstaller"); & "$LocalTempDir\$ChromeInstaller" /silent /install; $Process2Monitor =  "ChromeInstaller"; Do { $ProcessesFound = Get-Process | ?{$Process2Monitor -contains $_.Name} | Select-Object -ExpandProperty Name; If ($ProcessesFound) { "Still running: $($ProcessesFound -join ', ')" | Write-Host; Start-Sleep -Seconds 2 } else { rm "$LocalTempDir\$ChromeInstaller" -ErrorAction SilentlyContinue -Verbose } } Until (!$ProcessesFound)
```
Now you can access very important web pages.
### Very Important Webpages

### Enable Linux for Windows
Please reopen Powershell and paste the following:
```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux
```
Next paste:
```powershell
Invoke-WebRequest -Uri https://aka.ms/wsl-ubuntu-1804 -OutFile Ubuntu.appx -UseBasicParsing
```
Next paste:
```powershell
Add-AppxPackage .\APP-NAME.appx
```
And finally close Powershell.  The rest of our work will be done in Ubuntu terminal.

### Ubuntu Terminal
In the lower left of your desktop, search for Ubuntu and open the result labeled as "App".
Specify a username and password which are distinct from your Toyota login credentials.

Perform the following commands:
```ubuntu
sudo apt-get update
```
```ubuntu
sudo apt upgrade
```

### Installing Required Software
The following command should take care of all your software needs.  We try to have a uniform working environment for everyone so that we can each easily jump in to help team members.

Navigate to the directory where you cloned this repository.

Run this in Ubuntu terminal:
```ubuntu
cat software.list | xargs sudo apt-get -y install
```
>If any errors occur retain the error information and notify someone.