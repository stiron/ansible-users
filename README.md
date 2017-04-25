# Ansible role that manages UNIX/Linux accounts

[![build status](https://gitlab.com/stiron/ansible-users/badges/master/build.svg)](https://gitlab.com/stiron/ansible-users/commits/master)

## Requirements

This module requires Ansible 2.x version.

## Role variables

```
users_private:
  - name: tmolnar
    password: $6$7MbxEXX0Kgj61$vvVl2K/mrv/1qvID6TUH6wM/0.Q8juBLx6RcWPh/JiGHAdVcoU9I6d6NgprxMZ210z1.gfC/OeR49eugTmEmX/
    private_keys:
        - file: /home/tmolnar/.ssh/key.priv
          content: xxxyyy
    
users:
  - name: tmolnar
    home: /home/tmolnar
    manage_vimrc: yes # Either yes or leave this key out
    manage_tmuxconf: yes # Either yes or leave this key out
	manage_emacs: yes # Either yes or leave this key out
    authorized:
        - ed25519 abc123 user@host
        - rsa abc345 user2@host
    public_keys:
        - file: /home/tmolnar/.ssh/key.pub
          content: yyyzzz
    bashrc_lines: |
      # Perlbrew
      source ~/perl5/perlbrew/etc/bashrc

      # PyEnv
      export PYENV_ROOT="$HOME/.pyenv"
      export PATH="$PYENV_ROOT/bin:$PATH"
      eval "$(pyenv init -)"

      # Golang
      export PATH=$PATH:/usr/local/go/bin
      export GOPATH=~/local_stuff/projects/go
      export PATH=$PATH:$GOPATH/bin
```

### Mandatory variables

There are two main hashes for this role:

**users:** the content will be logged

**users_private:** the content will **NOT** be logged

The possible content:

**users:**

`name` - the name of the user

`home` - the home directory of the user

**users_private:**

`password` - encrypted password

### Optional variables

**users:**

`shell` - the default shell of the user (defaults to /bin/bash)

`manage_vimrc` - use a preconfigured vimrc file

`manage_tmuxconf` - use a preconfigured tmux configuration file

`manage_emacs` - use my preconfigured .emacs file

`bashrc_lines` - a block of data to be inserted into the ~/.bashrc

`authorized` - a list of the pub keys of the user to be deployed

`public_keys` - a list of hashes about the public key file URL and content

**users_private:**

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
