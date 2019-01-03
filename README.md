# Windows/Linux Setup for Web Development Immersive

This guide was last updated in January 2019.

This is Bitmaker's guide to setting up a development environment for the Web Development Immersive course. This guide is for Linux users (or Windows users who need to start using Linux).  If you are using a Mac you should refer to [this guide](https://github.com/bitmakerlabs/python-dev-setup-guide-mac) instead.  Using Windows for this course is not recommended at all.  

If you have a Windows laptop, this guide will walk you through installing Linux.  

If you already have Linux installed, you can [skip to this part of the guide](#Linux-Development-Environment-and-Tools).

## Installing Linux

Before starting this process, **backup all important files from your computer**.  Most likely this process will go smoothly and all your data will be preseved, but in the unlikely event that something goes wrong, you don't want to regret not backing up first.

### Glossary

Let's get some terms out of the way.

* __BIOS__ or [Basic Input/Output System](http://en.wikipedia.org/wiki/BIOS "Wikipedia entry for BIOS") is to your operating system what a starter motor is to your car's engine.
* __UEFI__ or [Unified Extensible Firmware Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface "Wikipedia Entry for UEFI") is essentially a new and improved BIOS. UEFI has gotten more popular in the last year or two and is expected to gradually displace the older BIOS implementation over time. Machines running Windows8 are typically optimized using UEFI. On the other hand Ubuntu typically plays nicer with BIOS. The conflict between the two can derail a dual-boot implementation in a hurry.
* __Boot order__ is a setting in BIOS/UEFI that dictates what happens when your machine starts up. Typically the boot order tells the machine to load the operating system on the hard drive first thing. To install Linux from USB or DVD, you will typically need to modify the boot order setting to allow access to these devices _before_ the hard drive is accessed. On newer machines modifying the bootorder can itself require other changes to settings in the BIOS/UEFI (i.e. you might need to disable a boot order security setting, etc.)
* __Boot loader__ is a 'menu' that allows a user to select one of several options when starting up your computer. Ubuntu comes with the [GRand Unified Bootloader](http://en.wikipedia.org/wiki/GRand_Unified_Bootloader "Wikipedia entry for GRUB") (GRUB). If you dual boot Linux/Windows side-by-side you will typically -- after installation -- have to select one or the other from the boot loader menu at startup.

Got all that? Great. Here's what you need to do to get Ubuntu onto your computer:

	1. Designate a physical space where to put Linux on your system
	2. Download Ubuntu from the internet, then transfer it to a USB or DVD
	3. Install Ubuntu from that media to the designated space on your machine

The section that follows is cribbed from Ubuntu's [official install guide](http://www.ubuntu.com/download/desktop/install-desktop-latest). Feel free to follow along from the source instead.

### Part One Preparing Your Hard Drive

#### Partitioning Your Drive

In the not too distant past, the best way to partition your drive was using the tools that came with your Linux install, particularly [gparted](http://gparted.org/). Now the tools natively on Windows and Mac machines are better choices. Not only do they now rival gparted in functionality but using them lessens the possibility of either native OS flagging disk errors after partitioning. We recommend you use the Disk Manager on Windows or the Disk Utility on Mac machines to 'shrink' your current volume. 15 GB is plenty for Ubuntu but feel free to split your system 50/50 if you want to. At this stage don't worry about the format of the new space -- it will end up being reformatted and overwritten later in the process in any case.

#### To Swap or Not to Swap?

A simple rule: if you are dual-booting or the machine is older (pre-2010), add a swap partition that is sized at 10% of the Linux partition itself.
If Linux is the only OS on the machine and it's relatively new, don't bother.

<hr>

### Part Two Creating Bootable Media

#### Selecting and Downloading a Version of Ubuntu

Next, you need to [download the ISO to use](http://www.ubuntu.com/download/desktop). But which one?

* '64 bit' versus '32 bit': if you have a new machine choose 64bit. If your computer is older, you may need to Google to see if it supports 64 bit program and if not choose the 32 bit version. Unlike many things in the installation process, this is not something you can change later.
* 'Long Term Support' (LTS) versus 'latest release': LTS versions of Ubuntu are guaranteed to be supported with software updates and security fixes for 5 years, whereas other versions are supported for just nine months after their release.  If you hate having to upgrade your operating system, choose the LTS version (which is currently version 14.04).  If you like having the latest technology, choose the latest release.

#### Creating a Bootable Disk

Ubuntu provides instructions on how to burn a bootable DVD for both [Windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-mac-osx). Be warned that burning an ISO disk is not the same process as burning something like a music CD!

#### Creating a Bootable USB

The easiest way to get a bootable USB stick is to find a friend (or a Bitmaker instructor) with Ubuntu already installed and ask them to use the start-up disk creator that comes with Ubuntu.

Otherwise, Ubuntu provides official instructions [for Windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) and [Mac](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-mac-osx).  The process is a little long and annoying because it requires installing new software, but it works.

<hr>

#### Using your USB/DVD to begin the Installation Process

With your drive all set and your media ready, you are now ready to begin the installation process. Unfortunately, this bit can be the most frustrating.

First you will want to see if there is shortcut to modify your boot order. How do you do that you ask? We can't tell you. Because we don't know. Because every machine is different. On newer Lenovo and Dell machines, for example, this shortcut is `F12` (`ESC` is another common choice). When the laptop begins to boot -- after the power button has been pressed but before the OS boots -- pressing F12 will redirect the process to a user-modifiable boot menu. A user can then choose to boot from their DVD or USB and then are off to the races. The best way to find out if your machine has such a shortcut is to google it. But be warned that not every manufacturer adds a shortcut. Some insist you change the bootorder permanently -- for all subsequent starts, not just a single one -- in the BIOS/UEFI.

The next thing you need to consider is some manufactures have such a shortcut, but it's been disabled. To re-enable it or simply bypass it you will have to know the shortcut to get into your BIOS/UEFI. How do you do that? Same story. We can't tell you, but Google is your friend. On Lenovos the key is `F2`.

On some newer Windows systems (Windows 8 and up) there is a 'feature' called SecureBoot that requires you to adjust the firmware settings from within Windows itself. The steps for Windows 8 are to the right-hand sidebar, click on PC Settings at the bottom, go to General, and scroll down to "Advanced Startup." Click on this, then go to Troubleshooting>Advanced>UEFI Firmware Settings.  Newer versions of Windows will have some similar series of menus for accomplishing this, so you can either click around and try to find it or try to google it for your version.

Once you get into changing settings in the BIOS/UEFI it's possible to screw up your machine so be cautious. Don't be afraid to exit out of the menu if you think you made a mistake. Before exiting you will be asked to commit your changes, so you can always say no and start again.

Once you get confident navigating in the BIOS/UEFI, your goal is to change your boot order or unlock access to the boot menu. If you're on Windows 8 or later you may have to enable "legacy booting" in order to dual boot. Unfortunately this part varies from computer to computer.  If you get stuck and Google isn't fruitful, feel free to contact a Bitmaker instructor for help.

##### Some Trouble Shooting Help
* If you have graphics problems at this stage (which might take the form of a black or purple screen) it might be the `nomodeset` parameter in the boot menu. See [this post on askubuntu](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it#answer-162076) for a possible solution.
* As an aside, if you get a non-responsive black screen later in the install, the boot process might be corrupted. If that happens, ['the boot-repair` functionality on the liveMedia will fix it](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/). Shut off your computer. Restart. Boot into the live environment, open the Terminal, then install and run Boot-Repair:

```bash
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install boot-repair
```

### Part Three Ubuntu Installation (USB or DVD)

The Ubuntu installation process has seven main screens:

#### Screen One - Choose to Install Then Select Your Language
* English

![Install Type](/assets/screen1.png)

#### Screen Two - Ready Your Setup
* Plug into a power source
* Connect to the internet
* The options to 'update from the internet while installing' and/or including the proprietary codecs for MP3s and Flash, etc. are optional

![Ready Your Setup](/assets/screen2.png)

#### Screen Three - Choose Your Installation Type
* If you are dual booting with Windows, select the 'alongside' option or select 'Something Else' to target your partition manually (if you go the manual route, don't forget to add a mount point)
* If you want to install Linux as your only operating system choose 'Erase Disk for Installation' or 'Replace X with Ubuntu'

![Choose Your Installation Type](/assets/screen3.jpg)

#### Screen Four - Choose Your Time Zone
* Eastern time for Toronto

![Choose Your Time Zone](/assets/screen4.jpg)

#### Screen Five - Choose Your Keyboard Layout
* Typically English(US) or English (US, MacIntosh)

![Choose Your Keyboard Layout](/assets/screen5.jpg)

#### Screen Six - Create a User Name and Password
* Add a name for you and your computer
* Include, then confirm, a password

![Create a User Name and Password](/assets/screen6.jpg)

#### Screen Seven - Ubuntu One
* Choose 'Log in later'.

![Ubuntu One](/assets/screen7.jpg)

Restart!

![restart](/assets/restart.jpg)

You're almost done!

#### Updating

If above you chose not to 'install updates when installing' you will want to do that now.
CTRL-ALT + T will open the commmand line via terminal.

Once the system reboots and you login, open the terminal.
When prompted, run the following three commands at the command line, one at a time and in order:

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

#### Cleaning House

At this point you can spend a few minutes in the "Ubuntu Software Centre" uninstalling anything you don't want to keep. We recommend you at least de-Amazonify your system.

![Amazon in Search Results Ubuntu. Hotlinked from a now out of date Lifehacker post](/assets/de_amazon.jpeg)

Click on the top icon in the left-hand navigation (the button that [looks like](/assets/bond.jpeg) it's from the opening credit sequence of the James Bond movies). This button is called 'Dash' in Ubuntu-ese. A search bar will appear. To the right of that search bar click on 'Filter results'. You will likely want to deselect 'Amazon' as a source for your search results. Also for good measure deselect Soundcloud, the Ubuntu Music store, and any other option that is likely to pollute the results in the Dash launcher.

To make these changes permanent, see [How to remove Amazon and Ubuntu One Music?](http://askubuntu.com/questions/363912/how-to-remove-amazon-and-ubuntu-one-music) at askubuntu.com

<hr>


## Linux Development Environment and Tools

This process should take about 1 hour to 1.5 hours to complete, depending on the speed of your machine and your internet connection.

### Web Browser

First off, you are going to want to install Chrome. Ubuntu comes with Firefox pre-installed and while we love Firefox, we want [Chrome](https://www.google.com/intl/en_uk/chrome/browser/) for its developer tools.

### Text Editor

The text editor of choice at Bitmaker is [Atom](https://atom.io/).  When you click on that link, the Atom website should recognize that you're on Linux and give you the option to download a `.deb` file:

![atom download page]('assets/atom_homepage.png')

Choose "Download .deb".  When the download finishes, you might get a warning like this:

![are you sure you want to keep this file]('assets/atom_are_you_sure.png')

This warning happens because a `.deb` file is for installing programs, which you only want to do if the source is one you trust.  We _do_ trust the creators of Atom, though, so choose to keep the file despite the warning.

If you open that file, it should automatically open the Ubuntu Software Centre and give you the option to "install".

When the installation process is complete, open the terminal (with CTRL-ALT + t) and type `atom`.  If the installation was successful, the text editor should open.

## Bash

This guide assumes that you're using bash shell, which is the default pre-installed shell for Ubuntu terminal. We also assume that you use `.bashrc` to setup `$PATH` and other environment variables. If you happen already use a different shell or a different bash config file, be sure to substitute it where appropriate below.  If that doesn't sound like something you know you've set up, just keep following along!

### Configuring Atom as the Default Editor

Now that you've installed Atom, you might also want to set it as your default system editor.

```bash
echo 'export EDITOR="atom -w"' >> ~/.bashrc
```

### Alias ls

By default, when you view a listing of your files with the `ls` command, hidden files won't show up (i.e. files beginning with a '.'), nor will the details about each file appear. More often than not, we want to see those details, so let's `alias ls` to show these details everytime we use `ls`.

Enter the following from within your terminal:

```bash
echo "alias ls='ls -al'" >> ~/.bashrc
source ~/.bashrc
```

## Some Essentials
Certain flavours of Ubuntu ship with fewer developer essentials than others.  You will likely need to install the following packages:

```bash
sudo apt-get install libssl-dev
sudo apt-get install libsqlite3-dev
sudo apt-get install libreadline-dev
sudo apt-get install build-essential
```

If you aren't using Ubuntu you may want to search for equivalent packages for your version of Linux.

## Git

Next we want to install Git, either from the software centre or the terminal with the command:

```bash
sudo apt-get install git
```

Git and Github are different things. You have just installed Git. It provides version control on your local machine alone, not to be confused with Github.com which is a website where you can upload your projects.

In the prep work you were asked to create a user account on GitHub, but if you haven't yet you should do that now.

Now let's configure git so it knows your username and email address for Github:

```bash
git config --global user.name "your github.com username"
git config --global user.email "your_email@example.com"
```

### Generate SSH Keys

SSH keys are definitely a better setup to use with Git than HTTPS. This is so you don't have to type your password every time you push. Don't worry if these terms don't mean anything to you right now, you'll eventually learn what they are during your journey as a developer.

Github provides good documentation for how to set this up:

1. [Checking for existing SSH keys](https://help.github.com/articles/checking-for-existing-ssh-keys/)
2. [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)
3. [Adding the SSH key to your Github account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

## Install Pyenv

We may need to manage multiple versions of Python during the course. Run the following in your terminal:

```bash
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
echo export PATH="/home/natalie/.pyenv/bin:$PATH" >> ~/.bashrc
source ~/.bashrc
echo eval "$(pyenv init -)" >> ~/.bashrc
echo eval "$(pyenv virtualenv-init -)" >> ~/.bashrc
source ~/.bashrc
```
## Install Python

List the possible Python installations:
```bash
pyenv install --list
```

Choose the latest version. Scroll up - it should just be a version number without any prefix or suffix. Eg. `3.7.1`, not `3.7.1-dev` or `pypy3.5-6.0.0`.
```bash
pyenv install 3.7.1
python --version   # <-- should output 3.7.1, or whatever version you installed.
```

To check that you'll be able to install new Python packages using pip, run:

```bash
pip --version
```

If you see a version number, you're good to go!

### Install Virtualenv

`Virtualenv` is a tool that allows each project you create to separately manage its Python dependencies. We'll be using it throughout the course. `virtualenvwrapper` is simply a tool that makes it a bit easier to work with `virtualenv`. We'll install them both at once.

```bash
pip install virtualenv virtualenvwrapper
printf '\n%s\n%s\n%s' '# virtualenv' 'export WORKON_HOME=~/virtualenvs' \
'source /usr/local/bin/virtualenvwrapper.sh' '' >> ~/.bashrc
```

Then we'll create the directory that will store our virtual environments.

```bash
source ~/.bashrc
mkdir -p $WORKON_HOME
```

Lastly, o get `pyenv`, which manages our Python versions, working nicely with `virtualenv`:

```bash
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
source ~/.bashrc
```

Let's test that everything works together!

```bash
pyenv virtualenv my_first_env # create an environment
pyenv activate my_first_env # activate the environment
pyenv deactivate # deactivate the environment
pyenv uninstall my_first_env # type 'y' or 'yes' and press enter when prompted
```

------------

## Node.js

You'll need NodeJS! This used to be a pain, but the Node community has come together and created a great solution that lets you easily manage all your node installations and change node versions whenever you feel like it. It's called NVM, or the Node Version Manager. But there are a few steps needed before we're ready to go!

First let's update our sources:

```bash
sudo apt-get update
```

Then we'll add nvm using its native installation script (make sure you're including the most up to date version of nvm where it says VERSION UMBER GOES HERE in the URL below.  The format should be three numbers separated by dots, such as 0.33.4. [Check for the latest release version here.](https://github.com/creationix/nvm/releases):

```bash
curl -o- https://raw.githubusercontent.com/creationix/nvm/v + VERSION NUMBER GOES HERE + /install.sh | bash
```

Then refresh our new nvm settings:

```bash
. ~/.bashrc
```

Now we need to find an appropriate node version to install:

```bash
nvm ls remote | grep -i lts
```

This will find all of the Long Term Support versions of Node available to us. The very last version in the looooong list that will appear is going to be the version we will install! (Currently this is version 6.10.2), so let's install it!

```bash
nvm install 6.10.2
```

Now we need to set our version of Node to be our global version:

```bash
nvm use 6.10.2
```

NOTE: If you don't see this line at the end of the install:

```bash
Creating default alias: default -> 6.10.2 (-> v6.10.2)
```

Run this command to set your default version:

```bash
nvm alias default 6.10.2
```

Now to see if it's all worked!

```bash
node -v
```

You should see the version number of node display in your terminal (in this case 6.10.2).

NOTE: Sometimes you might see tutorials etc that use `nodejs`in place of `node` in the command line. This is because they're not using `nvm` to manage their node versions! Remember that in our case we're using `node` as seen in the previous command.

But wait! There's more!
Now we need to set our global package manager, in this case we'll use npm. Npm comes along with nvm when you install it so you just have to run the following:

```bash
npm install -global npm
```

This updates our version just in case any new updates have been released for npm.

Then let's double check that all went well:

```bash
npm -v
```

And you should see a version number pop up which means npm is happily installed!

The documentation for nvm is available in their Github [page](https://github.com/creationix/nvm). Don't worry too much about the docs at this stage - they look pretty intimidating right now! We'll dive deeper into Node as the course progresses!


## Installing PostgreSQL

The DBMS du jour is [postgreSQL](http://www.postgresql.org).

### Installation

Install Postgres with the following commands:

```bash
sudo apt-get install postgresql postgresql-contrib
sudo apt-get install libpq-dev
```

The next step is to allow Postgres commands in the comand line by adding 'psql' to the command path in your bashrc file:

 ```bash
 echo 'export PATH=/usr/local/psql/bin:$PATH' >> ~/.bashrc
 ```

### Credentials

With the database software installed we can move on to setting up a username and password for it with the commands:

```bash
sudo -u postgres createuser --superuser $USER
```

For the final step of this process you need to know what your laptop username is.  If you aren't confident you know your username, you can ask your computer to display your username to you by running this command:

```bash
echo $USER
```

Keep that username in mind for the step after next.

Now run this command:

```bash
sudo -u postgres psql
```

You should now be in a psql shell with the prompt `postgres=#`.  Enter the following command, replacing insert\_your\_laptop\_username\_here with your actual username (which you verified a moment ago):

```bash
\password insert_your_laptop_username_here
```


And you will be prompted to create a password for your new user.  CTRL + d will exit the psql shell when you're done.

You can consult the [Ubuntu Community page](https://help.ubuntu.com/community/PostgreSQL#Installation "PostgreSQL at Ubuntu.com") if you need more guidance.

### Congratulations

You're done everything!
