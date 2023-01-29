# Uptimebot
> Lightweight uptime monitoring and reporting tool for FreeBSD.

If you're looking for a simple monitoring tool that can be setup in less than a minute, keep reading! `uptimebot` monitors IP addresses, ports, http servers, changes in DNS records and expiration date of TLS certificates. When stuff breaks, you will be notified via log or a Telegram bot.

## Features
* Extremely easy to setup and use.
* Supports both IPv4 & IPv6.
* Supports A, AAAA, CNAME, TXT, MX, NS, SOA and PTR records.
* Outputs alerts to log and Telegram.
* Uses basic shell and FreeBSD tools.
* Automatic cronjob creation.

## Installing / Getting started
There is a install script to get you started right away. This installs the files to the correct directories and sets ownership and permissions.
```
wget https://raw.githubusercontent.com/nozel-org/freebsd-uptimebot/master/install_uptimebot
sh install_uptimebot
```
When installed, add a monitoring target to `/usr/local/etc/uptimebot_targets.conf` and fire away by running `uptimebot --all --cli`.

## Configuration
General settings and automated tasks can be configured in `/usr/local/etc/uptimebot.conf`. Automated tasks can be effectuated with `uptimebot --cron`. Monitoring targets can be set in `/usr/local/etc/uptimebot_targets.conf`.

## How to use
`uptimebot` has **features**, **methods** and **options**. Options can be used standalone, but a feature always requires a method and vice versa. Some examples:"

```
# options
$ uptimebot --help                           # Displays help text
$ uptimebot --cron                           # Effectuates automated tasks

# features/methods
$ uptimebot --all --list                     # Shows an overview of all configured monitoring targets
$ uptimebot --ping --cli                     # Runs the ping feature and outputs to CLI and log
$ uptimebot --port --logonly                 # Runs the port feature and outputs only to log
$ uptimebot --http --telegram                # Runs the http feature and outputs to Telegram and log
```
For a full list of features, methods and options run `uptimebot --help`.

## Support
If you have questions, suggestions or find bugs, please let us know via the issue tracker.

## Changelog
### 1.4.0-RELEASE ([28-04-2022](https://github.com/nozel-org/freebsd-uptimebot/commit/51dba5a9b1ba660a47cfae408f71137162c7c985))
- Renamed method logonly to log.
- Made method list consistent with the method cli output.
- Fixed a bug in feature tls that would generate errors for already expired certificates.
- Added a basic check for monitoring target validity.
- Added requirement check for curl.
- Added inverted functionality to feature port.

### 1.3.0-RELEASE ([27-04-2022](https://github.com/nozel-org/freebsd-uptimebot/commit/92d2b83e1ac36080f5d9832f7c3854ac43325148))
- Added feature TLS.
- Added emoji to method Telegram.

### 1.2.0-RELEASE ([26-04-2022](https://github.com/nozel-org/freebsd-uptimebot/commit/e09c7c897472a25ededeaf43635e0feca40c2bb8))
- Got rid of similar pieces of code by combining functions.
- Fixed a lot of shellcheck warnings and errors.
- Added check for telegram configuration.

### 1.1.0-RELEASE ([25-04-2022](https://github.com/nozel-org/freebsd-uptimebot/commit/46166dd48c44df563f1b7b703a900755de9a5b91))
- Added feature DNS with support for A, AAAA, CNAME, TXT, MX, NS, SOA and PTR records.
- Delay between monitoring actions (to prevent flooding) is now configurable.
- Logging output layout is now more consistent across all methods.
- Made certain checks more efficient to speed up the program.
- Feature port now supports both IPv4 and IPv6 (configurable).
- Changed default cron values.

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
