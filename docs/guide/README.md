# Guide 

## Development Environment Setup

### Mac 
#### Initial Settings
* Install Homebrew (if not already installed).   
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

* Check if PHP is installed on your machine.        
In a terminal window run the following command.        
`php -v`         
If no results are shown then install PHP by running.        
`brew install php`        

#### Installing Composer       
First open a terminal window. For ease of use, create a folder on the desktop (to hold the installer file) and then cd into that folder.        

Your terminal window should not be set to the directory of new folder on your desktop.

* Insall Composer by copy/pasting the following block of code into your terminal window.      

`php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === 'a5c698ffe4b8e849a443b120cd5ba38043260d5c4023dbf93e1558871f1f07f58274fc6f4c93bcfd858c6bd0775cd8d1') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"`             

Inside your directory folder (on Desktop) there will now be a file called `composer.phar`.       
This new file will have to be set as a global variable, if not it will be needed everytime a new laravel project is created. It's easier to set it as a global variable and call it anytime it's needed.       

* Set Composer.phar as a global variable by running the following command in your terminal window.    

`mv composer.phar /usr/local/bin/composer`        

Now at any point, you can type `composer` in your terminal window, regardless of the directory you are in, and it will run the composer.phar file.    

#### Install Laravel      
* Run the following command to install Laravel.      

`composer global require "laravel/installer"`         

We now need to set the vendor bin for Laravel.

Enter the following commands.        

`cd ~/.composer`  - This will display the vendor file for Laravel.        
Run the `ls` command. There should be a folder titled `vendor` in this directory, if there is not reinstall Laravel with the composer command above. 

`cd vendor`  - Move directories inside of vendor.      
Run the `ls` command again. There should be a folder titled `Laravel` inside the bin directory. If this is here, the install was done correctly.      

* Add the path variable inside Laravel. 

I am using the Zsh shell on Mac. The following command will open the file using Vim.     

`sudo vi ~/.zshrc`          

Inside Vim click the `i` key to activate insert mode.        
* The first line of the file will start with the keyword `export`          

Add a new line under this keyword - this will be the location we write out the PATH variable.     

Write the following underneath the first export statement in the file. 

`export PATH=~/.composer/vendor/bin:$PATH `     

Then click the `esc` key and type `:wq` to save and exit the Vim editor. 

#### Setting Up Initial Project (Test Project)
In a terminal window, `cd` to any folder you want. This is where we will create a test project to ensure Laravel is working correctly. 

Run `laravel new myfirstproject` where `myfirstproject` is the name you will give to the project. 

At this point Laravel should handle installing all the files and you can open the directory in an editor to start working.


### PC 
1.	Step one is to install the latest version of PHP which can be found on the following website 
  a.	https://www.php.net/downloads.php
  b.	Download the zip file that is thread safe and compatible for Windows 10
  c.	Create a file on your C drive called “php”
  d.	Extract the zip file into the php folder located in your C drive
  e.	Delete the zip file


2.	Install a composer to manage our dependencies
  a.	Visit the following link: https://getcomposer.org/doc/00-intro.md and download the Composer-Setup.exe under the heading Installation – Windows
  b.	Run the composer setup and you will automatically see php.exe is suggested as an option for command line 
  c.	Leave the default settings when installing and after installation, close all file explorer windows, command line prompts and proceed to logoff and then login
  d.	Test usage by opening CMD and typing in “composer -V” without quotes and you should see the composer version and time of installation


3.	Time to install Laravel! 
  a.	Type the following into CMD: composer global require laravel/installer 


4.	Make sure your environmental $PATH variable is set up properly. You can do this by opening command prompt and typing without quotes "PATH" and hitting enter. The last entry displayed should show the composer entry. If not, do the following:
  a.	Click the windows button
  b.	Type in “This PC”
  c.	Right-click the icon and hit properties
  d.	Click Advanced system settings located on the left side of the new window
  e.	Select Environmental Variables located near the bottom 
  f.	Select the Path variable and click edit
  g.	Verify you have the following line C:\Users\<your username>\AppData\Roaming\Composer\vendor\bin tied to your user account on Windows
  h.  Full link for myself: C:\Users\Owners\AppData\Roaming\Composer\vendor\bin
  
  A good tutorial to follow for this is here: https://www.architectryan.com/2018/03/17/add-to-the-path-on-windows-10/
  
  
5.	Go to your C:\php folder and find the php.ini-development, php.ini-production 
  a.	Control F to search for ;extension=intl
  b.	Remove the semi-colon in front to allow for extensions 
  c.	Remove all semi-colons from all extensions EXCEPT extension=openssl & extension=mbstring to allow for the use of extensions
  d.	Do this to both files, save and close
  e.	In your address bar in file explorer, type C:\php\php.ini
    i.	Once you hit enter it will open the config file for php
    ii.	Do the same procedure by removing the semi-colon in front of all extensions EXCEPT extension=openssl & extension=mbstring
    iii.	The image below is what all three files should look like
    
    
6.	If you receive a warning for pdo_firebird extension do the following
  a.	Visit this website: https://firebirdsql.org/en/firebird-3-0/#Win64
  b.	Download the 32/64 bit kit ZIP file for manual installation
  c.	Extract the file and search for fbclient.dll
  d.	Copy the file and open the C:\php directory and paste the dll file there
  e.	This will solve the warning message


7.	Open CMD and type Laravel new * where * is the name of your project 
  a.	If you receive a pdo_oci error you will need to download Oracle 12c from the vendors website (optional)

You’re now ready to begin! 
Note: Optional extensions can be installed based off needs

## Tools 

* PHP storm PC/Mac
* Vagrant / Homestead PC
* MYSQL Workbench PC
* Sequel PRO Mac
* iTerm2 Mac
* Cmder / Gitbash PC
