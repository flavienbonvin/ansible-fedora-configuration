# Personal Ansible configuration for my workstation

This is my (very) simple ansible playbook that allow me to configure my Fedora Workstation installation.

## Getting Started

These instructions will allow you to install and run my script. 

### Prerequisites

You simply need to have Ansible installed

```
sudo dnf install ansible -y
```

Once Ansible is installed you simply have to clone the repository

```
git clone https://github.com/flavienbonvin/ansible-fedora-configuration
```

## Using the script

You can now launch the script with the following command (from inside of the directory)

```
ansible-playbook playbook.yml -K
```

Since I use this script on both my latop (with integrated graphics) and my workstation (with an Nvidia graphic card and a proprietary network card) I had to make some tags to avoid installing uncesseary drivers on my laptop, to avoid both Nvidia and Broadcom you can use

```
ansible-playbook playbook.yml -K --skip-tags "desktop"
```

Finally I have to use for my job both Skype and Slack, if you don't want them you can use the following command 

```
ansible-playbook playbook.yml -K --skip-tags "flatpak-avoidable"
```

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
