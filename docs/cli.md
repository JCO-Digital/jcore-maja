# JCORE® CLI

JCORE® CLI is used to create and manage local development environments for JCORE® projects. It's written in TypeScript and requires Node.js to run.

## Installation

On Windows, even though JCORE® CLI should work from any shell, you should install it inside WSL. This is because the whole environment needs to be run from WSL, or it will be painfully slow.

Copy the file to somewhere in your PATH. If you install it globally, it needs to be updated with `sudo` (`sudo jcore update self`), but should otherwise work. It is recommended to install it in your home folder. The `~bin` folder might need to be added to the path, but most distros should have this done automatically if it exists. This requires restarting your shell after creating the folder.

You can install it by running the following commands:

    mkdir ~/bin
    curl -o ~/bin/jcore https://github.com/JCO-Digital/jcore-cli/releases/latest/download/jcore
    chmod 755 ~/bin/jcore

If you want to install it globally you can do that by running:

    sudo curl -o /usr/local/bin/jcore https://github.com/JCO-Digital/jcore-cli/releases/latest/download/jcore
    sudo chmod 755 /usr/local/bin/jcore

## Migrating older projects

From version 3.2 forward JCORE-CLI will not run projects that don't use the jcore.toml settings format. In this situation you can run `jcore migrate` to update the project to the new format. This should be relatively automatic, but might require some manual intervention.

When migrating, CLI will attempt to convert the old `config.sh` file to the new `jcore.toml` format. It also requires the new format `docker-compose.yml` in order for the container to read the settings.

### package.json

The `package.json` file is not overwritten, unless the file checksum matches, which in turn requires a fairly new project. If you want to update to using the new build system, run `jcore update package.json` to overwrite `package.json`. The migrate script will add `smol-toml` as a dependency if it deems it at all necessary. This is not required for old style gulp projects.

## Usage

    Usage: jcore <command> [options] <target>

    Possible commands:
    attach           - Attach to the logs of all containers
    checksum         - Manages file checksums.
    child            - Makes project child theme by copying the local jcore2-child folder.
    clean            - Delete image / container / temp files.
    clone            - Clones a project from bitbucket, and sets everything up.
    doctor           - Checks the status of the environment.
    init             - Creates a new project in the <target> folder.
    pull             - Syncs content from upstream.
    run              - Runs a command in container.
    config           - Set options in config file. Currently mode/debug.
    shell            - Opens a shell in the container / VM.
    status           - Shows information about running projects.
    start            - Installs composer and npm dependencies, and starts container.
    stop             - Shutdown container. Removes docker
    update           - Updates project. If the target is 'self' this script updates itself.

    Possible options:
    --branch / -b    - Set the JCORE branch to use, used in the init command.
    --force / -f     - Overwrites existing files.
    --global / -g    - Write settings globally.
    --help / -h      - This info.
    --install / -i   - Installs node modules even if they are already installed.
    --local / -l     - Write settings locally.
    --nochild / -n   - Doesn't install child theme on init command.
    --quiet / -q     - Print only errors.
    --template / -t  - Set template to use.
    --verbose / -v   - Print more text.
    --debug / -d     - Print everything.
    --loglevel / -p  - Set numeric log level.

### Commands

#### attach

Attach to the logs of all containers.

#### checksum

Manages file checksums. This is used to check which files have been changed manually, and should not be overwritten automatically. You can list all existing checksums, and reset checksums for specific files.

#### child

Makes project child theme by copying the local jcore2-child folder. It uses a file copy operation, rather than checking out the git repository, so uncommitted files in the folder will be included. The default name will be the same as the project name, but a different name can be specified as the target.

#### clean

Delete image / container / temp files.

#### clone

Clones a project from bitbucket, and sets everything up. This does a `git clone`, but also some basic project file checks and setup.

#### doctor

Checks the status of the environment.

#### init

Creates a new project in the <target> folder.
This command creates a sub-folder with the name you specify and copies all the needed files into it. It also sets up needed config files, initializes git and adds all the files to git. The files can then be committed and pushed, but you have to create the git repository yourself at Bitbucket.

#### pull

Syncs content from upstream.

#### run

Runs a command in container.

#### config

Set options in config file.

#### shell

Opens a shell in the container.

#### status

Attach to the logs of all containers

#### start

Installs composer and npm dependencies, starts container and gulp.

#### stop

#### update

Updates project. If the target is 'self' this script updates itself.
