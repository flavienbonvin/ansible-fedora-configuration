# Personal Ansible configuration for my workstation

This is my (very) simple Ansible playbook that allow me to configure my Fedora Workstation installation. It allows me to install everything I need for both:

* my laptop, Lenovo X1 Carbon 4th gen
* my workstation, custom computer with Nvidia GPU

This script does:

* set the hostname [tasks/system.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/repo.yml)
* update the system [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
* add RPM Fusion repository [tasks/repo.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/repo.yml)
* install
  * packages [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
  * LateX packages [tasks/packages.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/packages.yml)
  * Docker [tasks/docker.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/docker.yml)
  * ZSH [tasks/zsh.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/zsh.yml)
  * some flatpaks [tasks/flatpak.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/flatpak.yml)
  * VSCodium from git [tasks/vscodium.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/vscodium.yml)
  * JetbrainsToolbox [tasks/jetbrain-toolbox.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/jetbrain-toolbox.yml)
* change gnome settings [tasks/gnome.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/tasks/gnome.yml)

Some variables can be changed in the [playbook.yml](https://github.com/flavienbonvin/ansible-fedora-configuration/blob/master/playbook.yml):

* laptop_hostname: hostname for my laptop
* workstation_hostname: hostname for my workstation

## Getting Started

These instructions will allow you to install and run my script.

### Prerequisites

You simply need to have Ansible installed

```bash
sudo dnf install ansible -y
```

Once Ansible is installed you simply have to clone the repository

```bash
git clone https://github.com/flavienbonvin/ansible-fedora-configuration
```

This script is compatible with:

* Fedora 29
* Ansible 2.7+

## Using the script

You can now launch the script with the following command (from inside of the directory)

```bash
ansible-playbook playbook.yml -K
```

Since I use this script on both my latop (with integrated graphics) and my workstation (with an Nvidia graphic card and a proprietary network card) I had to make some tags to avoid installing uncesseary drivers on my laptop, to avoid both Nvidia and Broadcom you can use

```bash
ansible-playbook playbook.yml -K --skip-tags "desktop"
```

Finally I have to use for my job both Skype and Slack, if you don't want them you can use the following command 

```bash
ansible-playbook playbook.yml -K --skip-tags "flatpak-avoidable"
```

## Using the script for different devices

Since the script supports my laptop and workstation here are the commands that are available for both of those devices. Those commands make for a full install (first comment is for laptop, second for workstation):

```bash
ansible-playbook playbook.yml -K --skip-tags "desktop"
```

```bash
ansible-playbook playbook.yml -K
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
