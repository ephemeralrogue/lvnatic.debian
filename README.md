<h1 align="center">{ e }.bookworm ansible collection</h1>

<p align="center">
  <img src="./assets/e.bookworm-emblem.png" alt="ephemeralrogue.bookworm-emblem" width="120px" height="120px"/>
  <br>
  <i>ephemeralrogue.bookworm is an Ansible collection written to provision
    <br> Debian Bookworm virtual machines locally.</i>
  <br>
</p>

<p align="center">
  <a href="https://docs.ansible.com/ansible/latest/collections_guide/index.html">
  using ansible collections</a>
  •
  <a href="https://discord.gg/nh7mqGEfbw">ephemeralrogue's Discord Server</a>
  •
  <a href="https://blog.ephemeralrogue.xyz/detour-through-ansible#heading-ephemeralroguebookworm">project writeup</a>
  <br>
</p>
<hr>

## the quick and dirty

this collection is written for the express purpose of provisioning Debian 
12 (codename: Bookworm), virtual machines (VM) locally. It prepares the 
environment for and installs the following packages:

- [Docker](https://docs.docker.com/engine/)
- [Docker Compose](https://docs.docker.com/compose/) (plugin)
- [GitHub CLI](https://cli.github.com/)
- [VS Code](https://code.visualstudio.com/)
- [Oh My Bash](https://github.com/ohmybash/oh-my-bash)
- [Ble.sh](https://github.com/akinomyoga/ble.sh)

it also installs `spice-vdagent` and `bindfs` to enable clipboard sharing and 
directory sharing through VirtFS, as i use [UTM](https://getutm.app/) to spin 
up VMs, and finally configures git with my preferred options. that's pretty 
much it at the moment!

## usage

to get started using this collection, you'll need to set up passwordless sudo:
```bash
sudo visudo
```
`visudo` provides checks on this file to ensure syntax is appropriate. use 
other edits at your own discretion, caution, peril, whatever.
find the line defining the `sudo` group's permissions and change it to:
```bash
%sudo   ALL=(ALL:ALL) NOPASSWD:ALL
```
save and exit. then [install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html) 
on the machine you want to provision, as the playbooks are all written to run
locally (`hosts: localhost`):
```bash
sudo apt update
sudo apt install ansible
```
once installed, clone this repository and navigate to the `playbooks` 
directory:
```bash
git clone https://github.com/ephemeralrogue/ephemeralrogue.bookworm.git
cd /path/to/repository/playbooks
```

### using standalone playbooks

the main playbook is `provision_debian_vm.yaml` and can be run as:
```bash
ansible-playbook -i 127.0.0.1, -e "user={ username } email={ email}" provision_debian_vm.yaml
```
where "127.0.0.1" sets the targe as localhost, and "user" and "email" passes 
your username as a variable into the playbooks and requisite tasks. obviously, 
enter your own username and email and omit the brackets. also, that comma is 
fucking necessary. i failed to run this so many times when i was testing it 
because i didn't know about that stupid comma.

other playbooks you can run are `docker_prep.yaml`, `git_config.yaml`, and 
`omb.yaml`, where "omb" runs the Oh My Bash install tasks.

### using playbooks on remote hosts

if you want to run these playbooks on remote nodes, you'll need to edit 
the `hosts` directive on the playbooks. checkout a new branch, make your 
changes, and run from there. instead of passing an IP address with the 
inventory flag `-i`, you can pass an inventory file or hosts directive.

## future development

- i've started using [warp terminal](), and as this includes shell completion, 
  i may forego blesh
- create playbook to install kubernetes/minikube
- create playbook to set up [rootless Docker](https://docs.docker.com/engine/security/rootless/)
  the collection already installs the necessary packages, just need to 
  provision this
- 

