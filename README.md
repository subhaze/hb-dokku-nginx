# Deploying on dokku

[Dokku](https://github.com/progrium/dokku) is a Docker powered mini-Heroku in around 100 lines of Bash.

If you’re familiar with using git in the command line, you’ll have no trouble deploying your Harp app to Dokku.

## Setup a dokku environment

You can install Dokku on your own by following the instructions [here](https://github.com/progrium/dokku#requirements) or another approach is using a DigitalOcean [dropplet](https://www.digitalocean.com/community/tutorials/how-to-use-the-digitalocean-dokku-application).

## Overriding nginx configurations

With this dokku buildpack you should be able to override some nginx settings. I've not tried this yet, but, for information on how to override the settings checkout the [nginx buildpack repo](https://github.com/rhy-jot/buildpack-nginx)

## Setuping a development environment

**Requirements:** git, node 0.10.x, npm 1.2.x

### 1. Running locally

You'll need harp installed globally `npm install -g harp` then you can initiate the project via `harp init -b subhaze/hb-dokku-nginx <app-name-here>`. Harp will create a new directory based on your app's name with the files in this repository inside it. Now you can `cd <app-name-here>` and run `harp server` so get the project up and running locally.

### 2. Setting up the remote repo

You'll need to intiate a git repo via `git init` then you'll need to add files for git to track `git add .` and commit them `git commit -am "init commit"`. Now you'll need to setup your remote repo to connect to your dokku setup which would be something like the following: `git remote add dokku dokku@<your_domain>:<your_app_name>`. `<your-app-name>` can really be anything you like, but, remember this will be the sub-domain used to serve your app.

### 3. Deploying your app

First compile your app via `harp compile`

Now all you have to do is commit the new compile you've create then `git push dokku master` and you've just deployed your [harp](http://harpjs.com/) app!
