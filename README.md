# Ansible role that manages UNIX/Linux accounts

## Requirements

This module requires Ansible 2.x version.

## Role variables

```
users_private:
  - name: tmolnar
    password: 'hashed-password-here'
    private_keys:
        - file: /home/tmolnar/.ssh/key.priv
          content: xxxyyy
    
users:
  - name: tmolnar
    home: /home/tmolnar
    authorized:
        - ed25519 abc123 user@host
        - rsa abc345 user2@host
    public_keys:
        - file: /home/tmolnar/.ssh/key.pub
          content: yyyzzz
```

### Mandatory variables

There are two main hashes for this role:

**users:** the content will be logged to stdout or file

```
users:
  - name: tmolnar
    home: /home/tmolnar
```

**users_private:** the content will **NOT** be logged neither to stdout nor file

```
users_private:
  - name: tmolnar
    password: 'hashed-password-here'
```

The possible content:

#### users

`name` - the name of the user

`home` - the home directory of the user

#### users_private

`password` - encrypted password

## Examples

```
- hosts: Desktops 
  roles:
    - users
```

## Dependencies

None

## License

MIT

## Author

Tamas Molnar - <tmolnar0831@gmail.com>
