# Guide 

## Development Environment Setup

### PC 
* Step 1

### Mac 
## Initial Settings
* Install Homebrew (if not already installed).   
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`

* Check if PHP is installed on your machine.        
In a terminal window run the following command.        
`php -v`         
If no results are shown then install PHP by running.        
`brew install php`        

## Installing Composer       
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

## Install Laravel      
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

## Setting Up Initial Project (Test Project)
In a terminal window, `cd` to any folder you want. This is where we will create a test project to ensure Laravel is working correctly. 

Run `laravel new myfirstproject` where `myfirstproject` is the name you will give to the project. 

At this point Laravel should handle installing all the files and you can open the directory in an editor to start working.

## Tools 

* PHP storm PC/Mac
* Vagrant / Homestead PC
* MYSQL Workbench PC
* Sequel PRO Mac
* iTerm2 Mac
* Cmder / Gitbash PC