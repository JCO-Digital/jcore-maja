# JCORE® Onboarding

## Docker
Docker is used to run the project on the local development machine. It works a bit differently based on what OS it's running on. It is most native on Linux, since the containers use Linux to run their services. Under Mac it runs in a Linux VM under Apple's Hypervisor Framework, and on Windows it runs under WSL2.

More info can be found on the [How the docker workflow works](docker.md) page.

## Composer
Composer is a package manager for PHP packages, and can be used to install WP plugins as well as libraries needed for JCORE®. Composer is used in different degrees in different projects. Sometimes it is only used to install Timber and ACF, and sometimes to manage all plugins in the project.

More info can be found on the [Composer](composer.md) page.

## Npm / Node / Esbuild
JCORE® uses Esbuild to transpile SCSS and to bundle/transpile Javascript files. It also uses Node for the new CLI tool, and for build scripts. At January 2023, Node LTS 16 is recommended (14 might work).

## Developer computer setup
This section tells you how to set up the development environment. There is one section for Windows, one for Linux, one for Mac, especially M1 macs, and one common section.

### Windows Setup
This part needs to be done on Windows machines. These steps are unique to the Windows Workflow.

#### 1. Install Windows Terminal
This is technically an optional step, but it is very strongly recommended, even if you end up using something else. Windows Terminal is a decent fallback terminal, and so much better than cmd.exe. [Install instructions](https://docs.microsoft.com/en-us/windows/terminal/install)

#### 2. Install WSL2
In most cases this consists of running `wsl –install` as administrator in Windows Terminal.
But there might be more to it, so here are some links:

[Install Linux on Windows with WSL](https://docs.microsoft.com/en-us/windows/wsl/install)

[Manual installation steps for older versions of WSL](https://docs.microsoft.com/en-us/windows/wsl/install-manual)

#### 3. Install Ubuntu on WSL2
This step should probably already be done from the WSL2 step, but I recommend setting Ubuntu as the default option in the terminal, since you will be using it a lot.

Also create or copy in your SSH keys to `~/.ssh`
Once you get to a point when the keys are used, in case you get an error saying “Warning:  Unprotected private key file”, have a look at [this article](https://stackabuse.com/how-to-fix-warning-unprotected-private-key-file-on-mac-and-linux/)

You should be able to open the Ubuntu terminal from the start menu in case it doesn't open on its own. Search for Ubuntu and launch it. If the Ubuntu prompt starts in the Windows home directory, just type `cd` or `cd ~` to get to your home directory.

You can also install some other distribution than Ubuntu. For now Ubuntu is the default, since it's officially supported, but some software like composer are quite old, and node needs to be installed from a third party repository, since the Ubuntu version is many years old, and doesn't work with the scripts used in JCORE®.

#### 4. Install Docker
Download and install Docker from [here](https://www.docker.com/get-started/). Docker can’t access your WSL Ubuntu by default, so this needs to be turned on from the settings.

### Linux Setup
These steps are unique to the Linux workflow, and are based on Ubuntu, because the rest of the instructions assumes Ubuntu. If you use something else, just adapt them to your distro of choice. You can also add the needed commands here if you wish.
Please not that this is only for native Linux, the rest of the WSL install process is found in the common section.

#### 1. Install Docker
Install docker and docker-compose. Docker compose is built into newer versions of docker, and might not be needed, but leave it out at your own risk.
`sudo apt install docker docker-compose`
See to it that you can run docker as your normal user. This is usually done by adding yourself to the docker group.
`usermod -aG docker $USER`
It probably needs a re-login to take effect.
You can set docker to run at startup with `systemctl enable docker`.

### MacOs Setup
These steps are unique to Mac workflow.

#### 1. Install Docker
Download and install Docker from [here](https://www.docker.com/get-started/). Intel or Apple chip, depending on what you have. You might need to install docker-compose separately.

### Common Setup
These steps should be more or less the same for all versions. And on Windows these should always be run inside the Ubuntu WSL environment.

#### 1. Install IDE.
VS Code or PHPStorm or something else, but then you're on your own.
PHPStorm can connect to WSL automatically and VSCode needs an [extension](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode).

#### 2. Install Git if not installed.
`sudo apt install git`
To avoid confusion, do not install git-bash or other git tools on Windows unless you know you need it outside this workflow, because it will not work for this.
Learn Git: [Git tutorials](https://www.atlassian.com/git/tutorials)

Git should not be necessary to install for WSL, this will most likely be preinstalled in WSL Ubuntu.

#### 2. Install prerequisites for tooling.
There is some software that will be needed for everything to work properly that doesn't really fit into any categories directly. You will have problems with later steps if you skip this.

It can be installed with this or similar command:
`sudo apt install curl php php-mbstring php-xml php-zip php-curl php-xdebug dos2unix unzip`

If you’re on WSL for the first time, run `sudo apt-get update` before running the above installs.

#### 3. Install Node.js and npm.
For WSL, follow [these steps](https://docs.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl#install-nvm-nodejs-and-npm)

But if you're lazy, run these:
1. `curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/master/install.sh | bash`
2. Restart terminal
3. `nvm install --lts`

#### 4. Install JCOre CLI
Follow the instructions in the [JCORE CLI](cli.md) documentation. TL;DR is:
1. `mkdir ~/bin`
2. `curl -o ~/bin/jcore https://github.com/JCO-Digital/jcore-cli/releases/latest/download/jcore`
3. `chmod 755 ~/bin/jcore`

#### 5. Install composer.
`sudo apt install composer` for Ubuntu version.

or (not both):

For WSL, follow the Command-line installation in [Docs](https://getcomposer.org/download/).
If you have trouble running the script, you can download it manually as well with the following commands:

`mkdir -p ~/bin`

`cd ~/bin`

`wget -O composer https://getcomposer.org/download/latest-stable/composer.phar`

`chmod +x composer`


#### 6. Generate SSH-keys
Keys can be generated with this command:

`ssh-keygen -t ed25519`

These keys should be added to Bitbucket to allow access to git upsteam. They can be added to public keys in Bitwarden if you want.

[Instructions](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

#### 7. Browser certificates
The tlscerts container creates a CA certificate that you should add as trusted to your browser. The container creates project specific keys signed by the CA certificate.
The CA certificate is located in `~/.config/jcore/ssl`

#### 8. Add Public SSH-key
Add the public key from `~/.config/jcore/ssh` to [WPEngine](https://my.wpengine.com/ssh_keys). This is used by `jcore pull` command to fetch live site data to local development environment.
