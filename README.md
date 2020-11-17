CIS - RHEL 8 Based Systems
=========

Asible role to apply CIS Benchmark on RHEL 8 based systems.


Requirements
------------

Create below partitions at the time of installation. The role will not create any of these partitions. 

```
1.1.6   | Ensure separate partition exists for /var (Scored)
1.1.7   | Ensure separate partition exists for /var/tmp (Scored)
1.1.11  | Ensure separate partition exists for /var/log (Scored)
1.1.12  | Ensure separate partition exists for /var/log/audit (Scored)
1.1.13  | Ensure separate partition exists for /home (Scored)

```

Support Matrix
--------------

| Destro | Status |
| --- | --- |
| CentOS 8 | Supported (Tested) | 
| RHEL 8 | Supported (Tested) |
| Oracle Linux 8 | Supported (Under Testing) |


Role Variables
--------------

deafult/main.yml variables are pretty self explanatory. 


Notes
------


The role will setup Authselect with a custom profile when you enable CIS rules 5.3.1, 5.3.2, 5.4.2, 5.4.3, 5.4.4. 

The recommended approch to join the node to an Active Directory domain with 'realmd'

Update realmd-distro conf (/usr/lib/realmd/realmd-distro.conf) with below.
```
[commands]
sssd-enable-logins = /usr/bin/sh -c "/usr/bin/systemctl enable oddjobd.service
&& /usr/bin/systemctl start oddjobd.service"

sssd-disable-logins = /bin/true
```
Example Playbook
----------------

```
  - name: CIS Baseline Setup
    hosts: cis
    remote_user: vagrant
    become: yes

    roles:
      - cis-centos
```

License
-------

MIT

Author Information
------------------

Muhammed Iqbal <iquzart@hotmail.com>
