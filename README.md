# Mac Development Ansible Playbook

Inspired on https://github.com/geerlingguy/mac-dev-playbook

Preparation
```
xcode-select --install
sudo easy_install pip
sudo pip install ansible
ansible-galaxy install -r requirements.yml
```


### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook`'s `--tags` flag. The tags available are:
* `dotfiles`: oh-my-zsh install + mackup restore
* `osx`: run osx script for Mac finne tunning
* `homebrew`: install brew & cask applications
* `mas`: mac apple store installs, homebrew `mas`package needed
* `extra-packages`: composer, pip, gems and npm package install
* `fonts`: install all fonts inside files/fonts
* `keys`: install key pair from private_key, public_key config

    ansible-playbook main.yml -i inventory -K --tags "dotfiles,homebrew"


## Issues
* mackup only has sense if you have dotfiles previously there
* Dock setup automation
* Still don't trust a lot in .macos file
* vscode is backed by sync extension inside a gist


## Testing the Playbook

Many people have asked me if I often wipe my entire workstation and start from scratch just to test changes to the playbook. Nope! Instead, I posted instructions for how I build a [Mac OS X VirtualBox VM](https://github.com/geerlingguy/mac-osx-virtualbox-vm), on which I can continually run and re-run this playbook to test changes and make sure things work correctly.

Additionally, this project is [continuously tested on Travis CI's macOS infrastructure](https://travis-ci.org/geerlingguy/mac-dev-playbook).

