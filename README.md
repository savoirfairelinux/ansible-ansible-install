# ansible-install

*Installs ansible on the target host, possibly in a virtualenv*

## Requirements

* Ansible 2.0+
* Debian jessie target

## What it does

Eventually, it will take care of any ansible installation scenario, but for now, it handles only
one: installing ansible with pip in an isolated virtualenv.

Before doing that, we make sure that the system has all the system packages we need.

You'll see that we explicitly install setuptools in our `pip` call. That's because on debian
jessie, the system version of setuptools is too old to properly install `cryptography`, one of
ansible's dependency. That's why we have to do this whole dance. Otherwise, we could simply
pip-install ansible globally and call it a day.

## Example

```
- role: ansible-install
  ansible_install_virtualenv_path: /root/ansibleenv
  ansible_install_versionspec: ">=2.0,<2.1"
```
