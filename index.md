# How to set up a SearXNG instance for yourself
### (Done on Ubuntu 20.04 Windows Subsystem for Linux 2 (Windows 10) ) 
---
### For WSL configuration, refer [the Microsoft Docs](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps)
#### NOTE: When the password is needed for *sudo* commands, please enter it. It will not be mentioned in this manual henceforth.
- Preferably, start with a fresh install of Ubuntu (if on WSL) 
  - From the Microsoft Store
  - Or using winget - type `winget install Canonical.Ubuntu` in a CMD window.
  
You may now open Ubuntu from the Start Menu.
Type the commands & follow the instructions below:
---

Upgrade the system packages - `sudo apt-get update && sudo apt-get upgrade`

Enter *y* when prompted.

Install Python's package manager *pip* - `sudo apt install python3-pip`

Install the dependencies: `sudo apt-get install git build-essential python-babel zlib1g-dev libffi-dev libssl-dev libxslt-dev python-dev -y`

Move to the *\opt* directory: `cd /opt`

Clone the repository locally - `sudo git clone https://github.com/searxng/searxng.git searxng` to create a new folder **searxng** within /opt.

Move to *\searxng* : `cd /opt/searxng`

Install the Python Virtualenv now - `sudo apt install python3-virtualenv`

Add this to your ~/.bashrc file :

`sudo vim ~/.bashrc` - edit the file in vim

Add this to the end: `export PATH="/home/username/.local/bin:$PATH"` where 'username' is your Linux username.
  
Quit Vim with `:wq`
  
`source ~/.bashrc` 
  
### Close the window & reopen a Ubuntu terminal/window 
  
---
 
Back at the terminal: `sudo virtualenv -p python3 searxng-ve` - create a new  virtualenv called searxng-ve
    
Activate the virtualenv - `. ./searxng-ve/bin/activate`  
  
Within the virtualenv (prompt should change to `(searxng-ve).....$ ` etc.)
  
Type `sudo pip3 install -r requirements.txt ` - to install all the necessary packages/modules
  
#### Note: all Packages might not have gotten installed - can be installed later (using `pip install `[name-of-missing-package] )
  
Move to the Home directory - `cd ~ `
 
Change a few settings (some are optional) - `sudo vim /opt/searxng/searx/settings.yml`  
  - Change the port number - if desired
  - Change your instance name - if desired
  - Change the `ultrasecretkey` like this :
      ![image](https://user-images.githubusercontent.com/71964994/128127252-c44fdd8e-bda4-42bf-826d-f9c1dc141fe3.png)
  
      to any string of the same length (by changing the letter's cases for eg. )

---
  
DONE! 👍 😎
  
---
 
### How to use your instance
  
- Open a terminal window.
- Type `cd /opt/searxng`
- Type `sudo python3 -m searx.webapp`.
- Open a browser, type `localhost:`port-number | the port number will be shown in the terminal window. 
