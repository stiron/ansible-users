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

**users_private:** the content will **NOT** be logged neither to stdout nor file

The possible content:

#### users

`name` - the name of the user

`home` - the home directory of the user

#### users_private

`password` - encrypted password

### Optional variables

#### users

`shell` - the default shell of the user (defaults to /bin/bash)

`authorized` - a list of the pub keys of the user to be deployed

`public_keys` - a list of hashes about the public key file URL and content

#### users_private

`private_keys` - a list of hashes about the private key file URL and content

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
