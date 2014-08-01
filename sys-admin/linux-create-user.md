### Create User "vino"

```
useradd vino
mkdir /home/vino
chown vino:staff /home/vino/
passwd vino                   # Set password at prompt
adduser vino sudo
chsh vino -s /bin/bash        # Change default shell to bash
su vino

# Setup ~/.ssh
mkdir ~/.ssh
chmod 700 .ssh/

git clone https://github.com/corvino/.dotfiles.git
cd .dotfiles
./setup.sh
```
