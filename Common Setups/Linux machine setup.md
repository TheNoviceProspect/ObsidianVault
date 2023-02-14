### Please be aware that you should be replacing the name smzb *everytime* you see it in the scripts

## Update and installing software

this all assumes a 'debian-esque' Linux such as ubuntu or linux mint and other such derivatives.
```bash
apt update; apt upgrade -yq; apt dist-upgrade -yq; apt full-upgrade -yq; apt autoremove --purge -yq; apt autoclean -yq
apt install -yq sudo zsh tmux byobu emacs-nox mc curl wget neofetch lolcat git
useradd -U -s /usr/bin/zsh -m -G sudo -d /home/smzb smzb
passwd smzb
```
then enter a password
probably time to reboot as-well

## Securing 'root' user

```bash
sudo usermod -L root
```
this locks the root user account and prevents login attempts against it

## First login
simply hit either '0' or 'q' to not worry about zsh config

Oh My Zsh Install
```zsh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
omz theme set bira
omz plugin enable git sudo extract command-not-found
```

(optional) install emacs prelude:
```zsh
curl -L https://git.io/epre | sh
nano ~/.emacs.d/personal/prelude-modules.el
```

and enable/disable plugins by commenting them in/out

first emacs start will take a while, during initialization of plugins through ELPA/MELPA

## Final tweaks

finally a zsh tweak: add this 
```rc
[[ -f ~/.zshrc-personal ]] && . ~/.zshrc-personal
```

to ~/.zshrc at the end.

And now for a little *pizzaz*
```bash
echo "neofetch|lolcat" >> ~/.zshrc-personal
```

That's it, you should now have a running linux system ready to install whatever packages you want to.

At the very end you *can* if you so choose, enable password-less sudo via this:
```shell
sudo emacs /etc/sudoers.d/smzb
```
and then inserting the following line (hitting TAB whenever you see the \<T> tag in this line)
```shell
smzb <T> ALL=(ALL) <T> NOPASSWD: ALL
```

> screenshot: ![[Common Setups/attachments/Pasted image 20230131101608.png]]

## Updating your machine
Once you are a "standard" user you should be updating your system (periodically) thusly:
```shell
sudo apt update; sudo apt upgrade -yq; sudo apt dist-upgrade -yq; sudo apt full-upgrade -yq; sudo apt autoremove --purge -yq; sudo apt autoclean -yq
```

## Git settings
```sh
git config --global user.email "<email>"
git config --global user.name "<Your full name>"
git config --global init.defaultBranch main
```