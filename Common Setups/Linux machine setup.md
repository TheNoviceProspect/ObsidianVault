this all assumes a 'debian-esque' Linux such as ubuntu or linux mint and other such derivatives.
```bash
apt update; apt upgrade -yq; apt dist-upgrade -yq; apt full-upgrade -yq; apt autoremove --purge -yq; apt autoclean -yq
apt install -yq sudo zsh tmux byobu emacs mc curl wget neofetch lolcat git
useradd -U -s /usr/bin/zsh -m -G sudo -d /home/smzb smzb
passwd smzb
```
then enter a password
probably time to reboot as-well

first login:
simply hit either '0' or 'q' to not worry about zsh config

```zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
omz theme set bira
omz plugin enable git sudo extract command-not-found
```

install emacs prelude:
```zsh
curl -L https://git.io/epre | sh
nano ~/.emacs.d/personal/prelude-modules.el
```

and enable/disable plugins by commenting them in/out

first emacs start will take a while, during initialization of plugins through ELPA/MELPA

finally a zsh tweak: add this 
```rc
[[ -f ~/.zshrc-personal ]] && . ~/.zshrc-personal
```

to ~/.zshrc at the end.

That's it, you should now have a running linux system ready to install whatever packages you want to.

At the very end you *can* if you so choose, enable password less sudo via this:
```shell
sudo emacs /etc/sudoers.d/smzb
```
and then inserting the following line (hitting TAB whenever you see the \<T> tag in this line)
```shell
smzb <T> ALL=(ALL) <T> NOPASSWD: ALL
```

> it may be worthwhile to include a screenshot here to show what it's supposed to look like