# ansible-role-systemd-timesyncd

This role configures systemd-timesyncd (man 5 systemd-timesyncd)

## Description

You can configure timezone and time synchronisation with this role.
Timezone is set through Ansibles `timezone` module. It looks up neccessary utilities.
Time synchronisation is done with `systemd-timesyncd.service`. See man 5 systemd-timesyncd.

## Role Variables


| Name                                     |                             Default                              | Description                                                                                            |
| :--------------------------------------- | :--------------------------------------------------------------: | ------------------------------------------------------------------------------------------------------ |
| `systemd_timesyncd_timezone`             |                             Etc/UTC                              | Takes the timezone as [Posix TZ](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones) format. |
| `systemd_timesyncd_ntp_servers`          | [0.pool.ntp.org, 1.pool.ntp.org, 2.pool.ntp.org, 3.pool.ntp.org] | List of NTP servers. Either as DNS-Name or as IP-Address.                                              |
| `systemd_timesyncd_fallback_ntp_servers` |                                []                                | List of Fallback NTP servers. If all of the NTP servers are not available.                             |
| `systemd_timesyncd_root_distance_max`    |                                5                                 | Seconds for how long the maximum root distances is.                                                    |
| `systemd_timesyncd_poll_interval_min`    |                                32                                | Minimum poll time until a new poll is started.                                                         |
| `systemd_timesyncd_poll_interval_max`    |                               2048                               | Maximum poll time until a new poll has to be started.                                                  |

## Role Tags

| Name                                | Description                                        |
| ----------------------------------- | -------------------------------------------------- |
| systemd_timesyncd_all               | Run everything in this role.                       |
| systemd_timesyncd_install           | Only run the install and removal tasks.            |
| systemd_timesyncd_timezone          | Only run configuration of timezone tasks.          |
| systemd_timesyncd_systemd_timesyncd | Onyl run configuration of systemd-timesyncd tasks. |

## Dependencies

**None**

## Example Playbook


```yaml
- name: All
  hosts: all
  debugger: on_failed
  roles:
    - role: ansible-role-systemd-timesyncd
```

## License

MIT License

## Contributors

Daniel von Essen
