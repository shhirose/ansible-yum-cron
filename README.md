# shhirose.yum-cron

[![Build Status](https://travis-ci.org/shhirose/ansible-yum-cron.svg?branch=master)](https://travis-ci.org/shhirose/ansible-yum-cron)
[![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat)](LICENSE)

This is Ansible role for yum-cron install and setting for RedHat Enterprise Linux.

## Requirements

None

## Role Variables

```
shhirose_yum_cron_daily:
  update_cmd: default
  update_messages: 'yes'
  download_updates: 'yes'
  apply_updates: 'no'
  random_sleep: 360
  system_name: None
  emit_via: stdio
  output_width: 80
  email_from: root@localhost
  email_to: root
  email_host: localhost
  group_list: None
  group_package_types: mandatory, default
  debuglevel: -2
  #skip_broken: 'True'
  mdpolicy: group:main
  #assumeyes: 'True'

shhirose_yum_cron_hourly:
  update_cmd: default
  update_messages: 'no'
  download_updates: 'no'
  apply_updates: 'no'
  random_sleep: 15
  system_name: None
  emit_via: stdio
  output_width: 80
  email_from: root
  email_to: root
  email_host: localhost
  group_list: None
  group_package_types: mandatory, default
  debuglevel: -2
  #skip_broken: 'True'
  mdpolicy: group:main
  #assumeyes: 'True'

shhirose_yum_cron:
  yum_parameter: ''
  check_only: 'no'
  check_first: 'no'
  download_only: 'no'
  error_level: 0
  debug_level: 0
  randomwaite: 60
  email_to: ''
  system_name: ''
  days_of_week: ''
  cleanday: '0'
  service_waits: 'yes'
  service_wait_time: 300
```

## Variable parameters

### shhirose_yum_cron_daily

This is variable paramters for RedHat Enterprise Linux 7 or later.

| key | required | default | type | values | notes |
| --- | --- | --- | --- | --- | --- |
| update_cmd | no | default | string | default, security, security-severity:Critical, minimal, minimal-security, or minimal-security-severity:Critical | What kind of update to use |
| update_messages | no | yes | string | yes or no | Whether a message should be emitted when updates are available, were downloaded, or applied. |
| download_updates | no | yes | string | yes or no | Whether updates should be downloaded when they are available. |
| apply_updates | no | no | string | yes or no | Whether updates should be applied when they are available. |
| random_sleep | no | 360 | int |  | Maximum amout of time to randomly sleep, in minutes. |
| system_name | no | None | string |  | Name to use for this system in messages that are emitted. |
| emit_via | no | stdio | string |  | How to send messages. |
| output_width | no | 80 | int |  | The width, in characters, that messages that are emitted should be formatted to. |
| email_from | no | root@localhost | string |  | The address to send email messages from. |
| email_to | no | root | string |  | List of addresses to send messages to. |
| email_host | no | localhost | string |  | List of groups to update. |
| group_list | no | None | string |  | This only works when group_command != objects, which is now the default List of groups to update |
| group_package_types | no | mandatory, default | string |  | The types of group packages to install |
| debuglevel | no | -2 | int | -4, -3, or -2 | Use this to filter Yum core messages: -4: critical, -3: critical+errors, -2: critical+errors+warnings (default) |
| skip_broken | no | comment out | string | True or False |  |
| mdpolicy | no | group:main | string |  |  |
| assumeyes | no | comment out | string | True or False | Uncomment to auto-import new gpg keys (dangerous) |

### shhirose_yum_cron_hourly

This is variable paramters for RedHat Enterprise Linux 7 or later.

| key | required | default | type | values | notes |
| --- | --- | --- | --- | --- | --- |
| update_cmd | no | default | string | default, security, security-severity:Critical, minimal, minimal-security, or minimal-security-severity:Critical | What kind of update to use |
| update_messages | no | no | string | yes or no | Whether a message should emitted when updates are available. |
| download_updates | no | no | string | yes or no | Whether updates should be downloaded when they are available. |
| apply_updates | no | no | string | yes or no | Whether updates should be applied when they are available. |
| random_sleep | no | 15 | int |  | Maximum amout of time to randomly sleep, in minutes. |
| system_name | no | None | string |  | Name to use for this system in messages that are emitted. |
| emit_via | no | stdio | string |  | How to send messages. |
| output_width | no | 80 | int |  | The width, in characters, that messages that are emitted should be formatted to. |
| email_from | no | root | string |  | The address to send email messages from. |
| email_to | no | root | string |  | List of addresses to send messages to. |
| email_host | no | localhost | string |  | Name of the host to connect to to send email messages. |
| group_list | no | None | string |  | List of groups to update. |
| group_package_types | no | mandatory, default | string |  | The types of group packages to install |
| debuglevel | no | -2 | int | -4, -3, or -2 | Use this to filter Yum core messages: -4: critical, -3: critical+errors, -2: critical+errors+warnings (default) |
| skip_broken | no | comment out | string | True or False |  |
| mdpolicy | no | group:main | string |  |  |
| assumeyes | no | comment out | string | True or False | Uncomment to auto-import new gpg keys (dangerous) |


### shhirose_yum_cron

This is variable paramters for RedHat Enterprise Linux 6

| key | required | default | type | values | notes |
| --- | --- | --- | --- | --- | --- |
| yum_parameter | no | None | string |  | Pass any given paramter to yum, as run in all the scripts invoked by this package. |
| check_only | no | no | string | yes or no | Don't install, just check |
| check_first | no | no | string | yes or no | Check to see if you can reach the repos before updating |
| download_only | no | no | string | yes or no | Don't install, just check and download |
| error_level | no | 0 | int | 6 | Error level, practical range 0-10, 0 means print only critical errors which you must be told, 1 means print all errors, even ones that are not important |
| debug_level | no | 0 | int | 6 | Debug level, practical range 0-10, higher number means more output Level 1 is a useful level if you want to see what's been done and don't want to read /var/log/yum.log |
| randomwaite | no | 60 | string | 60 | randomwait is used by yum to wait random time |
| email_to | no | root | string | hoge | List of addresses to send messages to. |
| system_name | no | hostname | string | 'hogehoge' | you may set SYSTEMNAME if you want your yum emails tagged differently |
| days_of_week | no | '0123456' | string | '016' | you may set DAYS_OF_WEEK to the days of the week you want to run |
| cleanday | no | '0' | string | '0' | which day should it do cleanup on?  defaults to 0 (Sunday). |
| service_waits | no | 'yes' | string | 'yes' | set to yes to make the yum-cron service to wait for transactions to complete |
| service_wait_time | no | 300 | int | 300 | set maximum time period (in seconds) for the yum-cron service to wait for transactions to complete. |

## Dependencies

None

## Example Playbook

```
- hosts: servers
  become: yes
  roles:
    - shhirose.yum-cron
  vars:
    shhirose_yum_cron_daily:
      apply_updates: 'yes'
```

## License

MIT
