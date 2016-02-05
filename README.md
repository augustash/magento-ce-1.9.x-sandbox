# Magento CE 1.9.x Sandbox Environment


## Overview

This is solely to be used for demonstration or debugging/development purposes
for our Ash suite of Magento 1.x modules. Do not use this as a starting point
to a project!


## Project Setup for local development

To get started with this sandbox project, first clone the repository

```bash
$ git clone https://github.com/augustash/magento-ce-1.9.x-sandbox.git
```

Install community/Ash Suite of modules with composer:

```bash
$ composer install
```

--------------

Before you can run the site locally to test development, here are the basic steps required to run locally. This assumes local development on a Mac and an Apache web server; if you're using Nginx - you're awesome and should know what to do.


1. If you are using Apache, ensure you have a usable .htaccess file ( `cp .htaccess.sample .htaccess`)
2. Change permissions on files/directories (`chmod -R 777 var media` & `chmod +x mage` )
3. Setup your `hosts` file with local development domain (`mage.sandbox.dev`) and add `127.0.0.1 mage.sandbox.dev`
4. Create an Apache or NGINX virtual host that will respond to `mage.sandbox.dev`
5. Reload your local webserver
6. Setup `cron`

```bash
$ crontab -e
$ * * * * * ! test -e /path/to/project/maintenance.flag && /bin/bash /path/to/project/scheduler_cron.sh --mode always
$ * * * * * ! test -e /path/to/project/maintenance.flag && /bin/bash /path/to/project/scheduler_cron.sh --mode default
```
