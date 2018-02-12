# atlassian-sdk-on-vagrant
Vagrant and Ansible support files for doing Atlassian SDK development.

This requires Vagrant, Ansible and Virtual Box

Run it by doing:
```bash
vagrant up
vagrant provision
vagrant ssh
```
See help with command: vagrant help

Vagrant automatically shares the directory where this file is hosted as /vagrant. So you can connect to the machine you created and list the shared files by doing:

```bash
vagrant ssh
ls /vagrant
```
