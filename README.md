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
    manage_vimrc: yes # Either yes or leave this key out
    manage_tmuxconf: yes # Either yes or leave this key out
	manage_emacs: yes # Either yes or leave this key out
    authorized:
        - ed25519 abc123 user@host
        - rsa abc345 user2@host
    private_keys:
        - file: /home/tmolnar/.ssh/key.priv
          content: xxxyyy
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

`name` - the name of the user

`home` - the home directory of the user

`password` - encrypted password

### Optional variables

`shell` - the default shell of the user (defaults to /bin/bash)

`manage_vimrc` - use a preconfigured vimrc file

`manage_tmuxconf` - use a preconfigured tmux configuration file

`manage_emacs` - use my preconfigured .emacs file

`bashrc_lines` - a block of data to be inserted into the ~/.bashrc

`authorized` - a list of the pub keys of the user to be deployed

`private_keys` - a list of hashes about the private key file URL and content

`public_keys` - a list of hashes about the public key file URL and content

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
