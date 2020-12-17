# connection

Ansible collection for **the connection between the nodes**. Not sure what SSH port a node/server is configured for? Not sure what OS user account to use to login? This collection is here to help. 

# Roles

| Name | Description | Learn more |
| -------------- | ---- | -----| 
| `set_ansible_ssh_port` | Provide a list of SSH ports to test and role will set `ansible_ssh_port` once a SSH port is found to connect successful. If none of the provided SSH ports connect successfully, that node will fail. | [Docs](docs/set_ansible_ssh_port.md) | 