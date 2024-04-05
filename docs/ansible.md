Packages

ansible

Files and Directories
``` sh
/etc/ansible
/etc/ansible.cfg
/etc/ansible/hosts
```
Send the ansible master public keys over to the ansible slaves

```sh
ssh-copy-id -i ANSIBLE_PUB_KEY USER@ANSIBLE_SLAVE
```

#### Basic Ansible Usage with ad-hoc Commands

Using the same username on the ansible host and remote hosts

To test connectivity to hosts from the hosts file

```sh
ansible all -m ping
```

**all**: reads all hosts from the hosts file

**-m**: module

To test individual hosts or host groups defined in the hosts file

```bash
ansible 'HOST_GROUP | HOST' -m ping
```

To execute a bash shell command on a remote host or groups

```sh
ansible 'HOST' -a "SHELL COMMAND"
```

**-a**: ad-hoc

System executables can have different paths across Linux distributions and commands might fail if the system is not looking in the correct path. Use full paths to executables instead of aliases or '$(which COMMAND) ARGUMENT'

```sh
ansible HOST -a "/PATH_TO_EXECUTABLE ARGUMENTS"
```

#### Running Commands with Escalated Privileges

``` title='/etc/ansible/ansible.cfg'
[privilege_escalation]
become=True
become_method=sudo
become_user=root
become_ask_pass=True
```

Sudo password prompt can be invoked manually

```sh
ansible --ask-become-pass HOSTS -a "PRIVILEGED COMMAND"
BECOME password:
```

#### Ansible Playbooks
