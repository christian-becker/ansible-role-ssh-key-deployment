ssh_key_deployment
==================

This ansible role is to deploy ssh keys.  
Place the ssh key files to "./files/*.pub" inside this role. These keys are deployed (added) to the target user on target systems.  
If you set "deploy_exclusive" to "yes", all keys not specified will be removed. So you can make sure that no unwanted key remains on the systems. 


Requirements
------------

This role has no special requirements.


Role Variables
--------------

Here is a list of variables defined in **defaults/main.yml**: 

```
# exclusive - Whether to remove all other non-specified keys from the authorized_keys file. (no/yes)
deploy_exclusive: no

# key - The SSH public key(s), as a string or (since Ansible 1.9) url (https://github.com/username.keys).
deploy_key: "*.pub"

# state - Whether the given key (with the given key_options) should or should not be in the file. (present/absent)
deploy_state: present

# user - The username on the remote host whose authorized_keys file will be modified.
deploy_user: 
  - root
```


Dependencies
------------

This role has no dependencies.


Example Playbook
----------------

This role can be used e.g. with the following playbook:
```
---
- name: deploy ssh keys
  hosts: linux_server
  remote_user: root
  roles:
    - ssh-key-deployment
```


License
-------

MIT


Author Information
------------------

* **Christian Becker** - [christian-becker](https://github.com/christian-becker)  

