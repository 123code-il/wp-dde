# WordPress Docker Development Environment (WP-DDE)

Damn, it's a long name for a simple docker wrapper for WordPress development.

So, want to develop / maintain a Theme or a Plugin in a clean WordPress environment? You came to the right place. 

## Installation

Start by `git clone` and `cp .env.example` to get things rolling, like so:
```
git clone git@github.com:123code-il/wp-dde.git
cp .env.example .env
```
After copying `.env` file please fill it with all the right for you data.

## Docker Images
This repo has the following Docker images:
- MySQL
- phpMyAdmin
- Wordmove
- WordPress
- WP CLI

and It also supports `Xdebug` with `VS Code` edittor.

## Development

Just create / drop a folder with what you want to develop inside the this project's repo and two set ups later you are good to go. 

You need 3 things to set up the development environment. Project folder you want to work on, link it to the wp_web container running, and link VS Code to the Xdebug running in wp_web container. 

#### Linkage Setup
Here is an example of how to set up a linkage between Theme or Plugin you are developing inside this repo and the WordPress (wp_web) container. 

Go and edit `docker-compose.yml` under `wp_web` container add one of the following lines to `volumes` adjusted to your needs 

```
# Plugin
- ./my-wordpress-plugin:/var/www/html/wp-content/plugins/my-wordpress-plugin:ro

# Theme
- ./my-wordpress-theme:/var/www/html/wp-content/themes/my-wordpress-theme:ro
```
** Attention **
Make sure you are leaving the `:ro` (readonly) suffix.

#### Xdebug Setup
Here is an example of how to set up Xdebug to work with Theme or Plugin you are developing inside this repo's folder.

Go and edit `.vscode/launch.json` under `pathMappings` adde the following line with the proper adjustments to your project.

```
"/var/www/html/wp-content/plugins/my-wordpress-plugin/": "${workspaceFolder}/my-wordpress-plugin"
```

## Commands
All you need are the 2 commands of running and shutting down this environment's Docker containers

Command to get thinks running:
```
docker-compose up -d
```

Command to shut down everything:
```
docker-compose down
```

Command to see logs of what's happening with the containers live:
```
docker-compose logs -f
```
