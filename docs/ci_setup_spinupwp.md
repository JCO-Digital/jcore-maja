# JCORE® CI setup for SpinupWP

## 1. Add new SpinupWP site

### Domain name

Example projectname.vc.bojaco.com. Each server has wildcard domain name that works without DNS configurations.

### Installation

Change admin email to support@jco.fi. Use _projectname_ as admin username. Store username and password to Bitwarden right away.

On the database page **save database prefix** to your notes - you will need it later. You will also need siteuser and server so it is good to include them in you notes at this point aswell.

When install has finished building go to SFTP & SSH page and activate **GitHub SSH key** and your own key(s) from the list. You can also check known other project team members keys at this point to make things smoother.

## 2. Create Github repository

If possible use _projectname_ as reporsitory name. Make private repository and choose not to generate .gitignore (use template none).

## 3. Create JCORE project using JCORE® CLI

Login to terminal and goto your projects folder.

run `jcore init <projectname>`

Go to newly created project dir: `cd <projectname>`

run `make install`

If you get error related to vendor/composer, check vendor dir permissions: `chown <username>:<username> vendor`

## 4. Setup CI connection parameters

Now lets hope you made notes at step one.

jcore.toml

    projectName = "projectname"
    template = "jcore2"
    localDomain = "projectname.localhost"
    domains = [ "projectname.localhost" ]
    branch = "grasshopper"
    theme = "projectname"
    remoteDomain = "projectname.wf.bojaco.com"
    remoteHost = "siteuser@server"
    remotePath = "/sites/projectname.wf.bojaco.com/files"
    replace = [ "//projectname.wf.bojaco.com|//projectname.localhost" ]
    pluginInstall = "composer"
    dbPrefix = "xxx_"

.github/workflows/deploy.yml

    name: Deploy site

    on:
    push:
        branch:
        - main

    jobs:
    build:
        uses: jco-digital/deploy-wp-action/.github/workflows/build-project.yml@v2.0.1
        with:
        is_jcore2: true
        php_version: 8.2
        slack_channel: C07C91377D4
        secrets: inherit
    deploy:
        needs: [build]
        uses: jco-digital/deploy-wp-action/.github/workflows/server-deploy.yml@v2.0.0
        with:
        server_url: siteuser@server
        base_path: /sites/projectname.wf.bojaco.com/files
        paths: >-
            wp-content/themes/projectname/:wp-content/themes/projectname/,
            wp-content/themes/jcore2/:wp-content/themes/jcore2/,
            wp-content/plugins/:wp-content/plugins/,
            vendor/:vendor/
        known_hosts: ${{ vars.VC_HOSTS }}
        slack_channel: C07C91377D4
        secrets: inherit

Get Slack channel ID by right-clicking on channel -> show channel details. Add Buildbot 9000 app to this channel in slack.

If your project has no slack channel yet, you can leave this as it is and join #devnull channel.

## 5. Make initial commit

### Connect local repository to Github remote

Copy and run add remote command from Github:

`git remote add origin git@github.com:JCO-Digital/projectname.git`

Commit your changes and push. You should now see build process results in the slack channel. If build fails, you can see details in the GitHub repository's Action tab.

## 6. Finalize setup

### Login to WP admin panel at SpinupWP

At this point you should have login credidentials stored to Bitwarden. If not, do it now. Make sure the dev URL and the localhost URL are set up correctly in Bitwarden record. Finally move Bitwarden record to JCO organzation. You can use **WP Admin Medium** collection if other security level has not been agreed.

### Go through initial WP setup

- set active theme to _projectname_
- set timezone to Helsinki (usually)
- set date format: d.m.Y
- set time format: H:i

## 7. Run project locally

### Run local host and pull

If on Windows, make sure you have Docker running. Go to your local project directory and run `jcore start`

Update you local WordPress setup to match server by running `jcore pull`

After update is finished run `make watch`

Enjoy coding!
