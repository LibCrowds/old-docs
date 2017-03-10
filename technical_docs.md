# LibCrowds Technical Documentation

The following document provides an outline of how the LibCrowds platform has
been deployed, including references to additional, more in depth documentation
related to the various pieces of software in use on the server.


## Configuration

Copies of any configuration files used on the platform can generally be found at /etc/\<application>.


## PyBossa

As LibCrowds is primarily a PyBossa platform, your main source of documentation
for installation, configuration and deployment is here:

[PyBossa Docs](http://docs.pybossa.com/en/latest/)


## Discourse

Documentation for the forum software can be found here:

[Discourse Docs](https://github.com/discourse/discourse/blob/master/docs)


## Logging

Errors are logged using [Sentry](https://sentry.io/libcrowds/), with new issues 
emailed to crowdsourcing@bl.uk.


## Themes

The LibCrowds themes can be found on the [LibCrowds organisation page](https://github.com/LibCrowds/).


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

The scripts can be found in /etc/cron.daily and /etc/cron.weekly

