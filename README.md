# Ansible role that manages UNIX/Linux accounts

This role adds a basic account management via Ansible.

## Requirements

This module requires Ansible 2.x version.

## Role variables

There are **two hashes as role variables** for the convenience and readability:

```
users_private: # Values here will NOT be logged
  - name: tmolnar
    password: 'password-here'
    private_keys: # Optional parameter
        - file: /home/tmolnar/.ssh/key.priv
          content: xxxyyy
    
users: # Values here will be echoed and logged
  - name: tmolnar
    home: /home/tmolnar
    authorized: # Optional parameter
        - ed25519 abc123 user@host
        - rsa abc345 user2@host
    public_keys: # Optional parameter
        - file: /home/tmolnar/.ssh/key.pub
          content: yyyzzz
```

## Examples

```
- hosts: Desktops 
  roles:
    - users
```

## Dependencies

There are no external dependencies for this role.

## License

MIT

## Author

Tamas Molnar - <tmolnar0831@gmail.com>
