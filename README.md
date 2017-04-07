# Ansible role that manages UNIX/Linux accounts

[![build status](https://gitlab.com/stiron/ansible-users/badges/master/build.svg)](https://gitlab.com/stiron/ansible-users/commits/master)

## Requirements

This module requires Ansible 2.x version.

## Role variables

```
users:
  - name: tmolnar
    home: /home/tmolnar
    password: $6$7MbxEXX0Kgj61$vvVl2K/mrv/1qvID6TUH6wM/0.Q8juBLx6RcWPh/JiGHAdVcoU9I6d6NgprxMZ210z1.gfC/OeR49eugTmEmX/
    manage_vimrc: yes
    manage_tmuxconf: yes
	manage_emacs: yes
    ssh_public_key: ed25519 abc123 user@host
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

`name` - the name of the user

`home` - the home directory of the user

`password` - encrypted password

### Optional variables

`shell` - the default shell of the user (defaults to /bin/bash)

`manage_vimrc` - use a default vimrc file

`manage_tmuxconf` - use a well-configured tmux configuration file

`manage_emacs` - use my preconfigured .emacs file

`bashrc_lines` - a block of data to be inserted into the ~/.bashrc

`ssh_public_key` - a string or URL for the pub key of the user to be deployed as athorized key

## Examples

```
- hosts: Desktops 
  roles:
    - users
```

## Dependencies

None

## License

BSD

## Author

Tamas Molnar
