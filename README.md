foreman_installer
=========
Install foreman-installer package and run the installer.</br>
The source of the role is from the [theforeman/forklift project](https://github.com/theforeman/forklift/tree/master/roles/foreman_installer).

Requirements
------------

Role Variables
--------------
| Name    | Description    | Required    | Default    | Values | Examples |
|:--|:--|:-:|:-:|:-:|:--|
| foreman_installer_verbose | enable verbose installer output | Yes | True | - | True |
| foreman_installer_additional_packages | additional packages to install | No | [] | - |  |
| foreman_installer_admin_password | admin password | No | changeme | - | Pa$$word |
| foreman_installer_command | foreman-installer | No | foreman-installer | - | foreman-installer |
| foreman_installer_options | string appended to the installer | No |  | - | --foreman-proxy-dhcp=false |
| foreman_installer_scenario | foreman_installer scenario | No | foreman | - | foreman |
| foreman_installer_skip_installer | skip installer | No | False | - | False |
| foreman_installer_upgrade | perform foreman upgrade | No | False | - | False |

Dependencies
------------
* `genadipost.epel_repositories`
* `genadipost.puppet_repositories`
* `genadipost.foreman_repositories`

Example Playbook
----------------

```yaml
---
- hosts: masters
  roles:
    - { role: genadipost.epel_repositories }
    - { role: genadipost.puppet_repositories }
    - { role: genadipost.foreman_repositories }
    - role: genadipost.foreman_installer
      scenario: foreman
      foreman_installer_options:
          - "--foreman-proxy-dhcp=false"
          - "--foreman-proxy-tftp=false"
```

License
-------
BSD

Author Information
------------------
genadipost@gmail.com
