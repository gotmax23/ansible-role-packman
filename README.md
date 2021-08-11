# Ansible Role: packman
[![MIT Licensed][badge-license]][link-license]
[![Role gotmax23.packman][badge-role]][link-galaxy]
[![Role Version][badge-version]][link-version]
[![Commits since last version][badge-commits-since]][link-commits-since]
[![Galaxy Role Quality][badge-quality]][link-galaxy]
[![Galaxy Role Downloads][badge-downloads]][link-galaxy]
[![Github Actions Molecule workflow status][badge-molecule-workflow]][link-molecule-workflow]
[![Github Actions Galaxy workflow status][badge-galaxy-workflow]][link-galaxy-workflow]

Ansible role that installs the Packman repository on OpenSUSE Leap and OpenSUSE Tumbleweed.

## Requirements

For right now, I only test this role using the latest release of the `ansible` pip package, which includes all the collections that are no longer part of `ansible-core`. This is the supported method. However, if you choose to use `ansible-core` or still use Ansible 2.9, you must manually install the following collections:
- community.general

## Role Variables

Here are this role's variables and their default values, as set in [`defaults/main.yml`][link-defaults]. If you'd like, you may change them to customize this role's behavior.

``` yaml
---
# See http://packman.links2linux.org/mirrors for list of mirrors.
# The default option comes directly from the [OpenSUSE Wiki](https://en.opensuse.org/Additional_package_repositories).
packman_mirror: "https://ftp.gwdg.de/pub/linux/misc/packman"

# Whether to check the Packman RPM repo signing key's fingerprint before importing it.
packman_check_key_fingerprint: true

```

## Example Playbook
``` yaml
---
- name: Converge
  hosts: all
  tasks:
    - name: "Include gotmax23.packman"
      include_role:
        name: "gotmax23.packman"

```

## Compatibility
This role is compatible with the following distros:
|distro|versions|
|------|--------|
|opensuse|15.2, 15.3, tumbleweed|

## License
[MIT][link-license]

## Author
Maxwell G (@gotmax23)

[badge-license]: https://img.shields.io/github/license/gotmax23/ansible-role-packman.svg
[link-license]: https://github.com/gotmax23/ansible-role-packman/blob/main/LICENSE
[badge-role]: https://img.shields.io/ansible/role/55918.svg
[link-galaxy]: https://galaxy.ansible.com/gotmax23/packman
[badge-version]: https://img.shields.io/github/release/gotmax23/ansible-role-packman.svg
[link-version]: https://github.com/gotmax23/ansible-role-packman/releases
[badge-commits-since]: https://img.shields.io/github/commits-since/gotmax23/ansible-role-packman/latest.svg
[link-commits-since]: https://github.com/gotmax23/ansible-role-packman/commits/main
[badge-quality]: https://img.shields.io/ansible/quality/55918.svg
[badge-downloads]: https://img.shields.io/ansible/role/d/55918.svg
[badge-molecule-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/molecule.yml/badge.svg?branch=main
[link-molecule-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/molecule.yml
[badge-galaxy-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/galaxy.yml/badge.svg
[link-galaxy-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/galaxy.yml
[link-defaults]: https://github.com/gotmax23/ansible-role-packman/blob/main/defaults/main.yml
