# freebsd-uptimebot
Lightweight uptime monitoring and reporting tool for FreeBSD.

## Features
### General features
* Extremely easy to use.
* Full IPv4 and IPv6 support.
* Uses basic shell only.
* Uses basic FreeBSD tools.
* Automatic cronjob creation.

### Monitoring features
| Monitoring features | Description |
| ------------------- | ----------- |
| ping | Monitors IP addresses with ping |
| port | Monitors configurable ports on predefined hosts |
| http | Monitors webservers port(s) 80 and/or 443 |
| dns | Monitors changes in DNS records.<br> Supported DNS records: A, AAAA, CNAME, TXT, MX, NS, SOA, PTR.
| tls | Monitors expiration date of TLS certificates. |

### Monitoring methods
| Monitoring methods | Description |
| ------------------ | ----------- |
| list | Lists all configured monitoring targets in a overview. |
| logonly | Start monitoring the configured targets and sent outages to the error log. |
| cli | Start monitoring the configured targets and sent output to CLI and outages to the error log. |
| telegram | Start monitoring the configured targets and sent outages to Telegram and the error log. |

## How to use
When using a option, `uptimebot` just needs one of the option arguments. For example:
```
$ uptimebot --help
$ uptimebot --cron
```
When using the monitoring features, `uptimebot` needs both a feature and a method in order to work. For example:
```
$ uptimebot --ping --list
$ uptimebot --port --logonly
$ uptimebot --http --cli
$ uptimebot --dns --telegram
```
When in doubt, ask the help page for a overview of the available arguments:
```
user@server:/ $ uptimebot --help
Usage:
 uptimebot [feature]... [method]...
 uptimebot [option]...

Features:
 --ping                 Monitor IP address status
 --port                 Monitor port status
 --http                 Monitor HTTP webserver status
 --dns                  Monitor DNS records status
 --tls                  Monitor expiration date for TLS certs
 --tor                  Monitor Tor Relay availability
 --all                  Monitor all configured Features

Methods:
 --list (default)       Output configured rules to cli
 --logonly              Start monitoring and only output to log
 --cli                  Start monitoring and output to cli
 --telegram             Start monitoring and output to Telegram

Options:
 --cron                 Effectuate cron changes from uptimebot config
 --help                 Display this help and exit
 --version              Display version information and exit
```

## How to install
### Requirements
Only `curl` is required to run `uptimebot`.

### Install
1. Copy `uptimebot` to `/usr/local/bin/uptimebot` (owner=`root`, group=`wheel`, permissions=`555`). 
2. Copy `uptimebot.conf` to `/usr/local/etc/uptimebot.conf` (owner=`root`, group=`wheel`, permissions=`555`).
3. Copy `uptimebot_targets.conf` to `/usr/local/etc/uptimebot.conf` (owner=`root`, group=`wheel`, permissions=`555`).

This will look something like:
```
wget https://raw.githubusercontent.com/nozel-org/freebsd-uptimebot/master/uptimebot -O /usr/local/bin/uptimebot
wget https://raw.githubusercontent.com/nozel-org/freebsd-uptimebot/master/uptimebot.conf -O /usr/local/etc/uptimebot.conf
wget https://raw.githubusercontent.com/nozel-org/freebsd-uptimebot/master/uptimebot.conf -O /usr/local/etc/uptimebot_targets.conf
chown root:wheel /usr/local/bin/uptimebot /usr/local/etc/uptimebot*
chmod 555 /usr/local/bin/uptimebot /usr/local/etc/uptimebot*
```

## Support
If you have questions, suggestions or found bugs, please let us know via the issue tracker.

## Changelog
### 1.1.0-RELEASE (25-04-2022)


### 1.0.0-RELEASE ([24-04-2022](https://github.com/nozel-org/freebsd-uptimebot/commit/9495797794eed0c5bf48484198303fea632e1fd2))
- Added basic program framework.
- Added configuration file.
- Added configuration file for monitoring targets.
- Added automatic cron jobs for automated tasks.
- Added logging of monitoring results.
- Added ping monitoring feature.
- Added port monitoring feature.
- Added http monitoring feature.
- Added all monitoring feature.
- Added method list.
- Added method logonly.
- Added method CLI.
- Added method Telegram.
