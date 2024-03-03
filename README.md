Ansible Role: Minikube
======================

[![Tests](https://github.com/gantsign/ansible_role_minikube/workflows/Tests/badge.svg)](https://github.com/gantsign/ansible_role_minikube/actions?query=workflow%3ATests)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-gantsign.minikube-blue.svg)](https://galaxy.ansible.com/gantsign/minikube)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/gantsign/ansible_role_minikube/master/LICENSE)

Role to download and install [Minikube](https://github.com/kubernetes/minikube)
the tool for running Kubernetes locally.

Requirements
------------

* Ansible Core >= 2.12

* Linux Distribution

    * Debian Family

        * Debian

            * Buster (10)
            * Bullseye (11)

        * Ubuntu

            * Bionic (18.04)
            * Focal (20.04)

    * RedHat Family

        * Rocky Linux

            * 9

        * Fedora

            * 35

    * SUSE Family

        * openSUSE

            * 15.4

    * Note: other versions are likely to work but have not been tested.

* VirtualBox / Docker (already installed)

Role Variables
--------------

The following variables will change the behavior of this role (default values
are shown below):

```yaml
# Minikube version number
minikube_version: '1.30.1'

# Directory to store files downloaded for Minikube
minikube_download_dir: "{{ x_ansible_download_dir | default(ansible_facts.env.HOME + '/.ansible/tmp/downloads') }}"
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
    - role: gantsign.minikube
```

Tab Completion for Zsh
----------------------

### Using Ansible

We recommend using the
[gantsign.antigen](https://galaxy.ansible.com/gantsign/antigen) role to enable
tab completion for Minikube (this must be configured for each user).

```yaml
- hosts: servers
  roles:
    - role: gantsign.minikube

    - role: gantsign.antigen
      users:
        - username: example
          antigen_libraries:
            - name: oh-my-zsh
          antigen_bundles:
            # Oh My Zsh Minikube plugin
            - name: minikube
```

### Using Antigen

If you prefer to use [Antigen](https://github.com/zsh-users/antigen) directly
add the following to your Antigen configuration:

```bash
antigen use oh-my-zsh
antigen bundle minikube
```

### Manual configuration

To manually configure Zsh add the following to your `.zshrc`:

```bash
eval "$(minikube completion zsh)"
```

More Roles From GantSign
------------------------

You can find more roles from GantSign on
[Ansible Galaxy](https://galaxy.ansible.com/gantsign).

Development & Testing
---------------------

This project uses the following tooling:
* [Molecule](http://molecule.readthedocs.io/) for orchestrating test scenarios
* [Testinfra](http://testinfra.readthedocs.io/) for testing the changes on the
  remote
* [pytest](http://docs.pytest.org/) the testing framework
* [Tox](https://tox.wiki/en/latest/) manages Python virtual
  environments for linting and testing
* [pip-tools](https://github.com/jazzband/pip-tools) for managing dependencies

A Visual Studio Code
[Dev Container](https://code.visualstudio.com/docs/devcontainers/containers) is
provided for developing and testing this role.

License
-------

MIT

Author Information
------------------

John Freeman

GantSign Ltd.
Company No. 06109112 (registered in England)
