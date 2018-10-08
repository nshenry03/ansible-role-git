Ansible Role: bash
==================

[![Build Status](https://travis-ci.org/nshenry03/ansible-role-git.svg?branch=master)](https://travis-ci.org/nshenry03/ansible-role-git)

Installs git

The following roles where designed to neatly work together with this role:

- [user](https://github.com/GROG/ansible-role-user), for managing users.
- [authorized-key](https://github.com/GROG/ansible-role-authorized-key), for managing authorized-keys.
- [sudo](https://github.com/GROG/ansible-role-sudo), for managing sudo rights.

The [management-user](https://github.com/GROG/ansible-role-management-user) role combines all these roles in
one easy to use role.

Requirements
------------

- [Ansible 2.1 or later](https://docs.ansible.com/ansible/2.6/modules/git_config_module.html)

Role Variables
--------------

| Variable          | Description                  | Default value |
|-------------------|------------------------------|---------------|
| `user_git_config` | Default git\_config settings | `[]`          |

See [user](https://github.com/GROG/ansible-role-user) role for additional role variables.

#### `user_list` details

`user_list`, `user_list_host` and `user_list_group` are merged when
managing the users. You can use the host and group lists to specify
users per host or group of hosts.

The user list allows you to define which users must be managed. Each item in
the list can have following attributes in addition to those defined in
[grog.user](https://github.com/GROG/ansible-role-user/blob/master/README.md#user_list-details):

| Variable     | Description                 | Required | Default           |
|--------------|-----------------------------|----------|-------------------|
| `git_config` | User's git\_config settings | no       | `user_git_config` |

###### Example `user_list`

```yaml
user_list:
  - name: user1
  - name: jdoe
    git_config:
      user.name: John Doe
      user.email: john.doe@example.com
      user.signingkey: 0A46826A
```

Dependencies
------------

-   [grog.user](https://github.com/GROG/ansible-role-user)

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
         - src: https://github.com/nshenry03/ansible-role-bash

License
-------

MIT

Author Information
------------------

This role was created in 2018 by [Nick Henry](http://TechNickal.net).
