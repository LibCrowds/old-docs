# LibCrowds Technical Documentation

The following document provides an outline of how the LibCrowds platform has
been deployed, including references to additional, more in depth documentation
related to the various pieces of software in use on the server.


## PyBossa

As LibCrowds is primarily a PyBossa platform, your main source of documentation
for installation, configuration and deployment is here:

[PyBossa Docs](http://docs.pybossa.com/en/latest/)


## Logging

Errors are logged using [Sentry](https://sentry.io/libcrowds/), with new issues 
emailed to crowdsourcing@bl.uk.


## Version control

The [LibCrowds organisation page](https://github.com/LibCrowds) contains all of
the open-source software, specific to the LibCrowds platform. Much of the
additional software mentioned below is also available on GitHub. Refer to the
[GitHub Guides](https://guides.github.com/) for details of how to contribute.


## Configuration

Copies of any configuration files used on the platform can generally be found at:

```
/etc/{application} # e.g. /etc/pybossa
```

Non-standard configuration files are also backed up to the LibCrowds 
[Dropbox](https://www.dropbox.com/login) account. To back up any new configuration
files a symbolic link to that file should be created as follows:

```
# For the file /etc/{application}/{settings-file}
mkdir -p /etc/libcrowds-config/etc/{application}/
ln -s /etc/{application}/{settings-file} /etc/libcrowds-config/etc/{application}/{settings-file}
```

Files with symbolic links found in in `/etc/libcrowds-config` will be backed up daily. To 
confirm that the upload works run:

```
/etc/cron.daily/db-uploader config
```


## Discourse

Documentation for the forum software can be found here:

[Discourse Docs](https://github.com/discourse/discourse/blob/master/docs)


## Themes

The main LibCrowds theme can be found here:

[libcrowds-pybossa-theme](https://github.com/LibCrowds/libcrowds-pybossa-theme)

The supplementary Discourse theme can be found here:

[libcrowds-discourse-theme](https://github.com/LibCrowds/libcrowds-discourse-theme)


## Plugins

Various plugins are used to provide additional functionality, with the LibCrowds theme
designed to integrate with some of these plugins, but not necessarily require them.
The LibCrowds [About page](http://www.libcrowds.com/about) lists the plugins
currently running on the server and provides links to the relevant repositories
for each.


## Backups

The PostgreSQL database that holds all data for the PyBossa application is backed
up daily ([using this script](https://github.com/alexandermendes/PSQL-Dropbox-Backups)).
Backups are stored both locally and on Dropbox, with daily backups kept for seven
days and weekly backups kept for four weeks.

The Discourse database is backed up daily, with backups kept for 7 days.
Again, backups are stored both locally and on Dropbox.

Files uploaded to PyBossa (avatars etc.) are backed up daily, with only the most
recent backup kept.

Along with the backup of configuration files, mentioned above, this should provide
everything needed to entirely rebuild the system, should any disasters happen!


## Firewall

The firewall is configured using UFW, check the rules by running the following
command on the server:

```
sudo ufw status verbose
```


## SSL

The SSL certificate is issued by [Let's Encrypt](https://letsencrypt.org/).


## Emails

[Mailgun](https://www.mailgun.com/) is used to forward all incoming emails to
crowdsourcing@bl.uk. This email address also receives any PyBossa
error logs, as well as updates from various external services (Digital Ocean,
Twitter etc.).


## Hosting

LibCrowds is hosted at [Digital Ocean](https://www.digitalocean.com/).


## Startup

[Supervisor](http://supervisord.org/) handles the automatic starting of programs
whenever the system reboots.


## Scheduled Tasks

The following cron jobs are running on the server:

- Backup the main PSQL database, both locally and on Dropbox (daily).
- Upload config files, the Discourse database and PyBossa uploads to Dropbox (daily).
- Optimise uploaded images (weekly).
- Download and install security updates (weekly).
- Renew SSL certificate (weekly).
