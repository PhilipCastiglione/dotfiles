# Dotfiles

## Contents

* Xresources

TODO:

* bashrc
* bash_aliases
* neovim stuff

From ~/workspace:

```
ln -s ~/workspace/dotfiles/Xresources ~/.config/regolith3/
```

## Software

* [asdf](https://asdf-vm.com/)
* [neovim](https://neovim.io/)
* [slack](https://slack.com/intl/en-au/downloads/)
* [1password](https://1password.com/downloads)

## Development

```sh
# set some global git config
git config --global user.name "Philip Castiglione"
git config --global user.email philipcastiglione@gmail.com
git config --global core.editor nvim
git config --global init.defaultBranch main

# add ssh key, add it to the agent, cat it to be able to copy-paste in a bit
ssh-keygen -t ed25519 -C "philipcastiglione@gmail.com"

eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
cat ~/.ssh/id_ed25519.pub

# generate gpg key
gpg --full-generate-key
gpg --list-secret-keys --keyid-format=long
# grab the id of the key and use it for <key_id> below
gpg --armor --export <key_id>

# tell git to use the gpg key to sign all commits by default:
git config --global --unset gpg.format
git config --global user.signingkey <key_id>
git config --global commit.gpgsign true

# add to bash
[ -f ~/.bashrc ] && echo -e '\nexport GPG_TTY=$(tty)' >> ~/.bashrc
```

## Notes

* On ubuntu/regolith I had to uninstall the snap version of firefox and install it from apt to get a version not in the snap sandbox, so that 1password can talk to firefox (after installing the ff extension).

