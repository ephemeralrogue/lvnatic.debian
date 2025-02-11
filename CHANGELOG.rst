===================================
ephemeralrogue.debian Release Notes
===================================

.. contents:: Topics

v1.0.0
======

Release Summary
---------------

Initial release of ephemeralrogue.debian.
This release includes a number of playbooks designed to quickly provision Debian systems.

New Playbooks
-------------

- ephemeralrogue.debian.git_config - set the global git configuration with a set of options
- ephemeralrogue.debian.install_code - installs dependencies, signing key, and apt repository for VS Code and installs VS Code
- ephemeralrogue.debian.install_docker - removes prior installs of Docker, installs dependencies, signing key , and apt repository for Docker and installs Docker and Compose
- ephemeralrogue.debian.install_gh - installs dependencies, signing key, and apt repository for GitHub CLI and installs GitHub CLI
- ephemeralrogue.debian.install_kdeconfigsddm - installs package to configure sddm natively through KDE settings
- ephemeralrogue.debian.install_kubectl - installs signing key, and apt repository for kubectl and installs kubectl
- ephemeralrogue.debian.install_kvantum - installs dependencies and clones, builds, makes, installs Kvantum
- ephemeralrogue.debian.install_minikube - installs kubectl if not already present, and retrieves, installs, and removed deb
- ephemeralrogue.debian.install_protonvpn - retrieves to install signing key and source, and installs ProtonVPN
- ephemeralrogue.debian.install_warp - retrieves, installs, and removes Warp Terminal deb
- ephemeralrogue.debian.provision_debian - runs a series of playbooks to provision a Debian system
- ephemeralrogue.debian.remove_apt_packages - removes numerous preloaded packages from a Debian system
- ephemeralrogue.debian.rootless_docker - executes pre-installed script to run Docker in Rootless Mode
- ephemeralrogue.debian.utm_shared - installs dependencies, inserts code, run shell commands to configure UTM Shared clipboard and directory
