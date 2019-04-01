# Personal Ansible configuration for my workstation

This is my (very) simple Ansible playbook that allow me to configure my Fedora Workstation installation. It allows me to install everything I need for both:

* my laptop, Lenovo X1 Carbon 4th gen
* my workstation, custom computer with Nvidia GPU and proprietary network card

## Getting Started

These instructions will allow you to install and run my script.

### Prerequisites

#### Compatibility

This script is compatible with:

* Fedora 29
* Ansible 2.7+

#### Before using the script

You simply need to have Ansible installed

```bash
sudo dnf install ansible -y
```

Once Ansible is installed you simply have to clone the repository

```bash
git clone --depth 1 https://github.com/flavienbonvin/ansible-fedora-configuration
```

## Using the script

You can now launch the script with the following command

```bash
ansible-playbook playbook.yml -K
```

Since I use this script on both my laptop (with integrated graphics) and my workstation (with an Nvidia graphic card and a proprietary network card) I had to make some tags to avoid installing unnecessary drivers on my laptop, to avoid both Nvidia and Broadcom you can use

```bash
ansible-playbook playbook.yml -K --skip-tags "desktop"
```

Finally I have to use for my job both Skype and Slack, if you don't want them you can use one of the following commands

```bash
ansible-playbook playbook.yml -K --skip-tags "flatpak-avoidable"

ansible-playbook playbook.yml -K --skip-tags "skype"
```

## Details about the script

Here is a list of all the things the the script change, do:

* Set the hostname [tasks/system.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/repo.yml), variable to set the hostname is in the [playbook.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/playbook.yml)
* Update the system [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
* Add RPM Fusion repository (free and non-free) [tasks/repo.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/repo.yml)
* Installs:
  * packages [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
  * LateX packages [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
  * Docker [tasks/docker.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/docker.yml)
  * ZSH [tasks/zsh.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/zsh.yml)
  * some flatpaks [tasks/flatpak.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/flatpak.yml)
  * VSCodium from git [tasks/vscodium.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/vscodium.yml)
  * JetbrainsToolbox [tasks/jetbrain-toolbox.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/jetbrain-toolbox.yml)
* Change gnome settings [tasks/gnome.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/gnome.yml)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
