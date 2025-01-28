## prerelease 01-27-25
- added playbook to enable Rootless Mode for Docker
- added playbook to install ProtonVPN
- added playbook to install Kvantum Manager
- updated provisioning playbook
- patched Warp Terminal install

## prerelease 01-24-25
- added git config option to set default Remote Name
- added prompts to customize default branch and remote names during playbook 
    execution

## prerelease 01-22-25
- added `kics-security-scan.yaml` to PR workflow runs

## prerelease 01-21-25
- added more packages to `remove-apt-packages.yaml`
    - when installing KDE Plasma Desktop, KDE adds numerous packages
- added docker post-install support in `install_docker.yaml`
- returned to `vars.yaml` for variable management

## prerelease 01-20-25
- added playbook to remove apt packages
- updated provision vm playbook

## prerelease 01-19-25
- added `ansible-lint` workflow
- added task to set pager.branch to false in global git config
- moved README and LICENSE to .github/
- added CODEOWNERS and FUNDING.yaml
- broke up apt_keys.yaml into files of respective tasks
- created playbooks to install individual apps
- created load_apt_keys.yaml with prompt for testing purposes
- edited and updated provision playbooks to incorporate changes
- removed unnecessary task and playbook files
- removed Oh My Bash, Ble.sh playbooks and tasks
- replaced `vars.yaml` with vars_prompt in `git_config.yaml`
- added minikube and kubectl install tasks and playbooks
- corrected linting errors

## prerelease 01-17-25
- copied provisioning script and removed ohmybash and blesh from copy
- updated `apt_keys.yaml` to acquire warp terminal keyring and add source list
- updated `apt_install.yaml` to include installation of warp terminal
- certain tasks in `apt_keys.yaml` were migrated from `command` or `shell` to 
    their respective `get_url` and `apt_repository` replacements
- linting fixes