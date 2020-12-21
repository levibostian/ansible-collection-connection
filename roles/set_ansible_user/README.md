# set_ansible_user

Provide a list of SSH usernames to test and role will set `ansible_user` once a username is found to connect successful. If none of the provided SSH usernames connect successfully, that node will fail. 

This role is very handy to do when you change the SSH username on your servers. You may have an inventory of old servers and new ones. This role will make sure a SSH connection can be established for each server without having to modify the SSH username in the inventory. 

# Role variables 

* `ssh_connect_timeout`
  * Default: `5`
  * Description: The number of seconds before the SSH connection attempt times out and is considered failed. 
* `ssh_users_test`
  * Default: `["root"]`
  * Description: The list of OS usernames to test a SSH connection with. It's recommended to set these values from most likely to work to least likely as this role tries them one at a time starting from first to last in this list. 
* `ssh_connect_fail_if_no_connect`
  * Default: `true`
  * Description: If none of the SSH usernames established a successful connection, fail. 
* `ssh_strict_host_checking`
  * Default: `"no"`
  * Description: If the SSH connection should perform strict host checking. Options: `"no"` or `"yes"`. `"no"` is recommended for a hands-free role experience. If you enable strict host checking, you will need to make sure that you setup SSH known hosts on your nodes before you run this role. 

# Output 

This role writes the following variables:

* `did_set_ansible_user` 
  * Possible values: `true | false`
  * Description: If the role successfully found a username to connect to the node with. 
* `ansible_user`
  * Possible values: a string that's one of the provided `ssh_users_test` values. 
  * Description: If the role successfully found an OS username to connect with SSH to the node with, this fact will be set. The `ansible_user` fact is a special fact used by Ansible to set the username to connect with SSH with. That means that after this role sets this fact for you, you do not need to do anything further. 

# Usage 

```yml
- hosts: all
  gather_facts: false # gathering facts will fail until a ssh connection can be established which, we are trying to do with this role. 
  collections:
    - levibostian.connection
  roles:
    - set_ansible_user
```

Then, [set your variables](https://docs.ansible.com/ansible/latest/user_guide/playbooks_variables.html). Set them however you wish. `group_vars`, playbook `vars`, a `vars_files`, etc. 

