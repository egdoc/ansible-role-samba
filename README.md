Ansible role: samba
=========

Ansible role to install and configure samba on Linux

Requirements
------------

None

Role Variables
--------------
Users and their passwords in the samba database can be declared using the `samba_users`
variable:

```Yaml
samba_users:
  - name: sambauser
    password: sambapassword
```

Shares can be described using the `samba_shares` variable:

```Yaml
samba_shares:
  - name: Data
    comment: Shared files
    path: /srv/samba/data
    writable: true
    guest_ok: false
    shared_dir_owner: sambauser
    shared_dir_group: sambauser
    shared_dir_mode: '755'
```

The packages installed by this role are declared using the `samba_packages`
variable:

```Yaml
samba_packages:
  - samba
```

The services started and enabled at boot are declared using the `samba_services`
variable:

```Yaml
samba_services:
  - smbd
  - nmbd
```

Dependencies
------------

None

Example Playbook
----------------

```Yaml
- hosts: servers
  roles:
    - role: egdoc.samba
      samba_users:
        - name: sambauser
          password: sambapassword
      samba_shares:
        - name: Data
          comment: Shared files
          path: /srv/samba/data
          writable: false
          guest_ok: false
```

License
-------

GPLv2

Author Information
------------------

Role created by Egidio Docile
