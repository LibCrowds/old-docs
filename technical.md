# LibCrowds Technical Documentation

The following document provides an outline of how the LibCrowds platform has
been deployed, including references to additional, more in depth documentation
related to the various pieces of software in use on the server.


## PyBossa

As LibCrowds is primarily a PyBossa platform, your main source of documentation
for installation, configuration and deployment is here:

[PyBossa Docs](http://docs.pybossa.com/en/latest/)


## Version control

The [LibCrowds organisation page](https://github.com/LibCrowds) contains all of
the open-source software specific to the LibCrowds platform. Much of the additional
software mentioned below is also available via GitHub. Refer to the
[GitHub Guides](https://guides.github.com/) for details of how to contribute.


## Configuration

Copies of the configuration files used on the platform can be found in the
LibCrowds [Dropbox](https://www.dropbox.com/login) account, where a README file
lists the actual locations of each configuration file on the server. Whenever a
new configuration file is added, a symbolic link to that file should be created
as follows:

```
ln -s /path/to/config/file /etc/libcrowds/config
```

This folder is automatically synced with Dropbox, to provide backups of the
server configuration.


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

The PostgreSQL database that holds all data for the platform is backed up daily,
using this script:

[PSQL-Dropbox-Backups](https://github.com/alexandermendes/PSQL-Dropbox-Backups)

Backups are stored both locally and on Dropbox, with daily backups kept for seven
days and weekly backups kept for four weeks.


## Security

- The firewall is configured using UFW.
- The SSL certificate is issued by [Let's Encrypt](https://letsencrypt.org/).


## Email

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

- The database is backed up daily.
- Uploaded images are optimised weekly.
- Security updates are downloaded and installed weekly.
- The SSL certificate is renewed weekly.
