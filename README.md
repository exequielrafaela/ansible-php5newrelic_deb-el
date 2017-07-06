# Ansible exequielrafaela.php5-newrelic role

> `exequielrafaela.php5-newrelic` is an [Ansible](http://www.ansible.com) role which:
>
> * installs newrelic php agent
> * configures newrelic php agent
>
> Note: Tests are failing due to invalid key

## Installation

Using `ansible-galaxy`:

```shell
$ ansible-galaxy install exequielrafaela.php5-newrelic
```

Using `requirements.yml`:

```yaml
- src: exequielrafaela.php5-newrelic
```

Using `git`:

```shell
$ git clone https://github.com/exequielrafaela/ansible-php5-newrelic.git exequielrafaela.php5-newrelic
```

## Dependencies

* Ansible >= 2.0

## Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---
# newrelic_license_key: yourkey
# php5_newrelic_extra_config:
#   newrelic.enabled: true

# Sets the name of the file to send log messages to.
php5_newrelic_logfile: /var/log/newrelic/php_agent.log
# Sets the level of detail to include in the log file.
php5_newrelic_loglevel: info
# Sets the name of the file to send daemon log messages to.
php5_newrelic_daemon_logfile: /var/log/newrelic/newrelic-daemon.log
# Sets the level of detail to include in the daemon log.
php5_newrelic_daemon_loglevel: info
# Enables high security for all applications.
php5_newrelic_high_security: no
# Sets the name of the application that metrics will be reported into.
php5_newrelic_appname: myapp
# Sets the desination location of the newrelic.ini file
# Note: for php7 it's /etc/php/7.0/mods-available
php5_newrelic_config_dest: /etc/php5/mods-available
# Writes other config options to newrelic.ini.
php5_newrelic_extra_config: {}

```


## Usage

This is an example playbook:

```yaml
---

- hosts: all
  become: yes
  roles:
    - franklinkim.newrelic
    - exequielrafaela.php5-newrelic
  vars:
    apt_repositories:
      - 'ppa:ondrej/php5-oldstable'
    newrelic_license_key: ab2fa361cd4d0d373833cad619d7bcc424d27c16
    php5_newrelic_appname: "My App"
    php5_newrelic_extra_config:
      newrelic.enabled: true

```

## License
Copyright (c) We Are Interactive under the MIT license.
