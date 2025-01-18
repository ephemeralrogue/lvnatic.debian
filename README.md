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

<a id="contents"></a>
## contents

- [usage](#usage)
  - [running playbooks locally](#usage_local)
  - [running playbooks on remote hosts](#usage_remote)
- [project updates](#updates)
- [future development](#future_dev)
- [contributing](#contributing)

<a id="usage"></a>
## usage

this collection is not yet ready to be uploaded to Ansible Galaxy, therefore 
the best way to make use of it at the moment is to clone it to the machine 
on which you want to locally run playbooks.

to get started, you'll need to set up passwordless sudo:
```bash
sudo visudo
```
running a playbook will assume passwordless sudo, as Ansible will not prompt 
you to enter a password at each juncture it requires. if you like, you can 
return and turn off passwordless sudo once you've completed running the 
playbooks.  

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
once installed, clone this repository and navigate to it 
directory:
```bash
git clone https://github.com/ephemeralrogue/ephemeralrogue.bookworm.git
cd /path/to/repository/
```

once here, make a copy of `vars.yaml.template`, rename it to `vars.yaml` and 
fill in the blanks:  
- "user" is the username you want to use;  
- "email" should be the email you use for git.

[back to contents](#contents)

<a id="usage_local"></a>
### running playbooks locally

the main playbook is `provision_debian_vm.yaml` and can be run as:
```bash
ansible-playbook -i 127.0.0.1, provision_debian_vm.yaml
```
where "127.0.0.1" sets the targe as localhost. also, that comma is 
fucking necessary. i failed to run this so many times when i was testing it 
because i didn't know about that stupid comma.

other playbooks you can run are `docker_prep.yaml`, `git_config.yaml`, and 
`omb.yaml`, where "omb" runs the Oh My Bash install tasks.

[back to contents](#contents)

<a id="usage_remote"></a>
### running playbooks on remote hosts

if you want to run these playbooks on remote nodes, you'll need to edit 
the `hosts` directive on the playbooks. checkout a new branch, make your 
changes, and run from there. instead of passing an IP address with the 
inventory flag `-i`, you can pass an inventory file or hosts directive.

[back to contents](#contents)

<a id="updates"></a>
## project updates

- [warp terminal](https://www.warp.dev/) tasks were added to retrieve gpg 
  key and add apt repository to source list. Warp install is now automated.
- with some exception, `command` and `shell` tasks were migrated to their 
  respective `get_url` and `apt_repository` modules.

see [CHANGELOG](./CHANGELOG.md) for full details.

[back to contents](#contents)

<a id="future_dev"></a>
## future development

- create playbook to install kubernetes/minikube
- create playbook to set up [rootless Docker](https://docs.docker.com/engine/security/rootless/);
  the collection already installs the necessary packages, just need to 
  provision this
- set up ansible-lint GitHub action on PR
- write unit and integration tests where applicable
- set up debug points and prompts where applicable
- look into providing the option of installing one terminal set over another 
  during playbook execution

[back to contents](#contents)

<a id="contributing"></a>
## contributing

if you would like to contribute to this project, feel free to fork and write! 
please adhere to most best practices as developed by the Ansible community. 
submit a PR when you feel your work is ready. and please adhere to the code of 
conduct and contributing guidelines when discussing issues and proposed 
changes.

[back to contents](#contents)