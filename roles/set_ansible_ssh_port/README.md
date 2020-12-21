# set_ansible_ssh_port

Provide a list of SSH ports to test and role will set `ansible_ssh_port` once a SSH port is found to connect successful. If none of the provided SSH ports connect successfully, that node will fail. 

This role is very handy to do when you change the SSH port on your servers. You may have an inventory of old servers and new ones. This role will make sure a SSH connection can be established for each server without having to modify the SSH port in the inventory. 

# Role variables 

* `ssh_connect_timeout`
  * Default: `5`
  * Description: The number of seconds before the SSH connection attempt times out and is considered failed. 
* `ssh_ports_test`
  * Default: `[22]`
  * Description: The list of SSH ports to test. It's recommended to set these values from most likely to work to least likely as this role tries them one at a time starting from first to last in this list. 
* `ssh_connect_fail_if_no_connect`
  * Default: `true`
  * Description: If none of the SSH ports established a successful connection, fail. 

# Output 

This role writes the following variables:

* `did_set_ansible_ssh_port` 
  * Possible values: `true | false`
  * Description: If the role successfully found a SSH port to connect to the node with. 
* `ansible_ssh_port`
  * Possible values: a number that's one of the provided `ssh_ports_test` values. 
  * Description: If the role successfully found a SSH port to connect to the node with, this fact will be set. The `ansible_ssh_port` fact is a special fact used by Ansible to set the SSH port to connect with. That means that after this role sets this fact for you, you do not need to do anything further. 

# Usage 

```yml
- hosts: all
  gather_facts: false # gathering facts will fail until a ssh connection can be established which, we are trying to do with this role. 
  collections:
    - levibostian.connection
  roles:
    - set_ansible_ssh_port
```

Then, [set your variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html). Set them however you wish. `group_vars`, playbook `vars`, a `vars_files`, etc. 

