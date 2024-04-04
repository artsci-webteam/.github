# Washington University Arts and Science Web Team

## Other docs
1. [Local Environment Overview](https://github.com/artsci-webteam/deps/wiki)
2. [Config Splits](https://github.com/artsci-webteam/deps/wiki/Configuration-Splits)
3. [Local Files](#3-local-files)
4. [Commands](#4-commands)
5. [Locked Packages](#5-locked-packages)

<a id="local-files"></a>

## Local files

add a drush.local.yml file (in deps/drush directory) that points to your ssh key and username used to ssh into servers
example of code in file:
```bash
ssh:
  options: '-i ~/.ssh/id_rsa'
drush_user: servername
options:
  uri: "https://default.ddev.site"
```

add a [settings.php](https://wustl.app.box.com/s/snec2l80dfwjbwi866yvz3y4d4u753tu) file to your deps/web/sites/default/ directory

once you add the files, run `ddev start`. This will install composer packages and get your local ready to import a site.

<a id="commands"></a>

## Commands

Always add the ddev prefix when running common commands with drush or composer

 `ddev sync` To syncs your local environment with a site on the server

> `NOTE`: You must be connected to/signed into the vpn. The command asks you to input the environment (can enter number or text - so 1, 2, 3, dev, stage, or prod) and target alias (example: olympian, aggregator, fellowshipsoffice)

`ddev drush cr` WHENEVER you make changes to a twig template or scss file, you're going to need to run this command to rebuild the cache

 `ddev drush cex` Will export any configuration changes you made through the UI locally

 `ddev drush cim` Will import config files that might be different from the DB compared to your local

 `ddev drush uli` will help you login to the site locally

 `ddev yarn` will build the theme css files

 `ddev gulp` will gulp watch the theme css files while making changes


<a id="locked"></a>


## LOCKED PACKAGES


| Package                          | Reason                                                                                                                                            |
| -------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| node_revision_delete 8.x-1.0-rc3 | No stable release to compare with D9 that works.                                                                                                  |
| drupal/photoswipe 3.1.0          | Took away grouping images. I had to create the initial patch a year and a half ago and am desperately waiting for the next person to do the same. |
| admin_toolbar 3.3.0              | The updates break the toolbar styling. Leaving it here until it's fixed.                                                                          |
