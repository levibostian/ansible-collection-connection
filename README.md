# connection

Ansible collection for **the connection between the nodes**. Not sure what SSH port a node/server is configured for? Not sure what OS user account to use to login? This collection is here to help. 

> Note: This project is quite new. It's not recommended to install this collection from GitHub as commits may have bugs. At this time, only install from Ansible Galaxy pushes. 

# Roles

| Name | Description | Learn more |
| -------------- | ---- | -----| 
| `set_ansible_ssh_port` | Provide a list of SSH ports to test and role will set `ansible_ssh_port` once a SSH port is found to connect successful. If none of the provided SSH ports connect successfully, that node will fail. | [Docs](roles/set_ansible_ssh_port/README.md) | 
| `set_ansible_user` | Provide a list of SSH usernames to test and role will set `ansible_user` once a username is found to connect successful. If none of the provided SSH usernames connect successfully, that node will fail. | [Docs](roles/set_ansible_user/README.md) | 

# Tests

The roles in this collection have been tested, manually, with existing playbooks. At this time there are not any automated tests created. 

Things to test:
* Any of the given options (ssh port, ssh username) do not connect. Expect a failure in the node. 
* Given the first given option (ssh port, ssh username) is successful. Expect the future tests to be skipped. 

## Contributors

Thanks goes to these wonderful people ([emoji key](https://allcontributors.org/docs/en/emoji-key))

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="https://github.com/levibostian"><img src="https://avatars1.githubusercontent.com/u/2041082?v=4" width="100px;" alt=""/><br /><sub><b>Levi Bostian</b></sub></a><br /><a href="https://github.com/levibostian/ansible-collection-connection/commits?author=levibostian" title="Code">💻</a> <a href="https://github.com/levibostian/ansible-collection-connection/commits?author=levibostian" title="Documentation">📖</a> <a href="#maintenance-levibostian" title="Maintenance">🚧</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->