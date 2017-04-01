# Ansible Role: Homebrew

[![Build Status](https://travis-ci.org/engboilers/ansible-role-homebrew.svg?branch=master)](https://travis-ci.org/engboilers/ansible-role-homebrew)

Installs [Homebrew](http://brew.sh/) on macOS, and configures packages, taps, and cask apps according to supplied variables.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    homebrew_repo: https://github.com/Homebrew/brew

The GitHub repository for Homebrew core.

    homebrew_prefix: /usr/local
    homebrew_install_path: "{{ homebrew_prefix }}/Homebrew"

The path where Homebrew will be installed (`homebrew_prefix` is the parent directory). It is recommended you stick to the default, otherwise Homebrew might have some weird issues. If you change this variable, you should also manually create a symlink back to /usr/local so things work as Homebrew expects.

    homebrew_brew_bin_path: /usr/local/bin

The path where `brew` will be installed.

    homebrew_installed_packages: []

Packages you would like to make sure are installed via `brew install`.

    homebrew_upgrade_all_packages: false

Whether to upgrade homebrew and all packages installed by homebrew. If you prefer to manually update packages via `brew` commands, leave this set to `no`.

    homebrew_taps:
      - homebrew/core
      - caskroom/cask

Taps you would like to make sure Homebrew has tapped.

    homebrew_cask_apps: []

Apps you would like to have installed via `cask`. Search for popular apps on http://caskroom.io/ to see if they're available for install via Cask. Cask will not be used if it is not included in the list of taps in the `homebrew_taps` variable.

    homebrew_cask_appdir: /Applications

Directory where applications installed via `cask` should be installed.

    homebrew_use_brewfile: false

Whether to install via a Brewfile. If so, you will need to install the `homebrew/bundle` tap, which could be done within `homebrew_taps`.

    homebrew_brewfile_dir: '~'

The directory where your Brewfile is located.

## Dependencies

  - [elliotweiser.osx-command-line-tools](https://galaxy.ansible.com/elliotweiser/osx-command-line-tools/)

## Example Playbook

    - hosts: localhost
      vars:
        homebrew_installed_packages:
          - mysql
      roles:
        - { role: engboilers.homebrew, homebrew_execute: true }

## License

MIT / BSD

## Author Information

[engboilers/ansible-role-homebrew](https://github.com/engboilers/ansible-role-homebrew), 2017 (originally inspired by [Jeff Geerling](https://www.jeffgeerling.com/), 2014).
