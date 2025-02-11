# ephemeralrogue\.debian Release Notes

**Topics**

- <a href="#v1-0-0">v1\.0\.0</a>
    - <a href="#release-summary">Release Summary</a>
    - <a href="#new-playbooks">New Playbooks</a>

<a id="v1-0-0"></a>
## v1\.0\.0

<a id="release-summary"></a>
### Release Summary

Initial release of ephemeralrogue\.debian\.
This release includes a number of playbooks designed to quickly provision Debian systems\.

<a id="new-playbooks"></a>
### New Playbooks

* ephemeralrogue\.debian\.git\_config \- set the global git configuration with a set of options
* ephemeralrogue\.debian\.install\_code \- installs dependencies\, signing key\, and apt repository for VS Code and installs VS Code
* ephemeralrogue\.debian\.install\_docker \- removes prior installs of Docker\, installs dependencies\, signing key \, and apt repository for Docker and installs Docker and Compose
* ephemeralrogue\.debian\.install\_gh \- installs dependencies\, signing key\, and apt repository for GitHub CLI and installs GitHub CLI
* ephemeralrogue\.debian\.install\_kdeconfigsddm \- installs package to configure sddm natively through KDE settings
* ephemeralrogue\.debian\.install\_kubectl \- installs signing key\, and apt repository for kubectl and installs kubectl
* ephemeralrogue\.debian\.install\_kvantum \- installs dependencies and clones\, builds\, makes\, installs Kvantum
* ephemeralrogue\.debian\.install\_minikube \- installs kubectl if not already present\, and retrieves\, installs\, and removed deb
* ephemeralrogue\.debian\.install\_protonvpn \- retrieves to install signing key and source\, and installs ProtonVPN
* ephemeralrogue\.debian\.install\_warp \- retrieves\, installs\, and removes Warp Terminal deb
* ephemeralrogue\.debian\.provision\_debian \- runs a series of playbooks to provision a Debian system
* ephemeralrogue\.debian\.remove\_apt\_packages \- removes numerous preloaded packages from a Debian system
* ephemeralrogue\.debian\.rootless\_docker \- executes pre\-installed script to run Docker in Rootless Mode
* ephemeralrogue\.debian\.utm\_shared \- installs dependencies\, inserts code\, run shell commands to configure UTM Shared clipboard and directory
