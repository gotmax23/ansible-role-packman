# Ansible Role: packman
[![Role gotmax23.packman][badge-role]][link-galaxy]
[![Github Repo][badge-github-repo]][link-github-repo]
[![SourceHut Repo][badge-srht-repo]][link-srht-repo]
[![MIT Licensed][badge-license]][link-license]
[![Github Open Issues][badge-github-issues]][link-github-issues]
[![Github Open PRs][badge-github-prs]][link-github-prs]
[![Role Version][badge-version]][link-version]
[![Commits since last version][badge-commits-since]][link-version]
[![Galaxy Role Quality][badge-quality]][link-galaxy]
[![Galaxy Role Downloads][badge-downloads]][link-galaxy]
[![Github Actions Molecule workflow status][badge-molecule-workflow]][link-molecule-workflow]
[![Github Actions Galaxy workflow status][badge-galaxy-workflow]][link-galaxy-workflow]

Ansible role that installs the Packman repository on OpenSUSE Leap and OpenSUSE Tumbleweed.

## Beta Warning
**This role is currently in beta and is not intended for production use. Breaking changes may occur between releases, so please make sure to read the release notes.**
## Requirements

This role depends on certain collections that are not included in ansible-core.


To install this role's requirements, create a `requirements.yml` file with the contents below and run the following commands:

``` shell
# ansible-base/ansible-core 2.10 and above
ansible-galaxy install -r requirements.yml

# ansible 2.9
ansible-galaxy collection install -r requirements.yml
```

``` yaml
# requirements.yml
---
collections:
  - name: community.general

```

## Role Variables

Here are this role's variables and their default values, as set in [`defaults/main.yml`][link-defaults]. If you'd like, you may change them to customize this role's behavior.

``` yaml
---
# Options:
# - `present` ensures that the Packman repository is installed.
# - `absent` ensures that the Packman repository is not installed.
packman_state: present

# See http://packman.links2linux.org/mirrors[1] for list of mirrors.
# The default option comes directly from the [OpenSUSE Wiki][2].
packman_mirror: "https://ftp.gwdg.de/pub/linux/misc/packman"

# Whether to check the Packman RPM repo signing key's fingerprint before importing it.
packman_check_key_fingerprint: true

```

\[1]: http://packman.links2linux.org/mirrors

\[2]: https://en.opensuse.org/Additional_package_repositories


## Example Playbook
``` yaml
---
- name: Set up Packman Repository
  hosts: all
  become: true

  tasks:
    - name: Set up Packamn Repository
      ansible.builtin.include_role:
        name: gotmax23.packman

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

[badge-role]: https://img.shields.io/ansible/role/55918.svg?logo=ansible
[link-galaxy]: https://galaxy.ansible.com/gotmax23/packman
[badge-github-repo]: https://img.shields.io/static/v1?label=GitHub&message=repo&color=blue&logo=github
[link-github-repo]: https://github.com/gotmax23/ansible-role-packman
[badge-srht-repo]: https://img.shields.io/static/v1?label=SourceHut&message=repo&color=blue&logo=data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0iVVRGLTgiIHN0YW5kYWxvbmU9Im5vIj8+CjxzdmcKICAgdmlld0JveD0iMCAwIDUxMiA1MTIiCiAgIHZlcnNpb249IjEuMSIKICAgaWQ9InN2ZzUxIgogICBzb2RpcG9kaTpkb2NuYW1lPSJzb3VyY2VodXQtd2hpdGUuc3ZnIgogICBpbmtzY2FwZTp2ZXJzaW9uPSIxLjEgKGM2OGUyMmMzODcsIDIwMjEtMDUtMjMpIgogICB4bWxuczppbmtzY2FwZT0iaHR0cDovL3d3dy5pbmtzY2FwZS5vcmcvbmFtZXNwYWNlcy9pbmtzY2FwZSIKICAgeG1sbnM6c29kaXBvZGk9Imh0dHA6Ly9zb2RpcG9kaS5zb3VyY2Vmb3JnZS5uZXQvRFREL3NvZGlwb2RpLTAuZHRkIgogICB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciCiAgIHhtbG5zOnN2Zz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPgogIDxkZWZzCiAgICAgaWQ9ImRlZnM1NSIgLz4KICA8c29kaXBvZGk6bmFtZWR2aWV3CiAgICAgaWQ9Im5hbWVkdmlldzUzIgogICAgIHBhZ2Vjb2xvcj0iIzUwNTA1MCIKICAgICBib3JkZXJjb2xvcj0iI2ZmZmZmZiIKICAgICBib3JkZXJvcGFjaXR5PSIxIgogICAgIGlua3NjYXBlOnBhZ2VzaGFkb3c9IjAiCiAgICAgaW5rc2NhcGU6cGFnZW9wYWNpdHk9IjAiCiAgICAgaW5rc2NhcGU6cGFnZWNoZWNrZXJib2FyZD0iMSIKICAgICBzaG93Z3JpZD0iZmFsc2UiCiAgICAgaW5rc2NhcGU6em9vbT0iMS42NTQyOTY5IgogICAgIGlua3NjYXBlOmN4PSIyNTYiCiAgICAgaW5rc2NhcGU6Y3k9IjI1NiIKICAgICBpbmtzY2FwZTp3aW5kb3ctd2lkdGg9IjE5MjAiCiAgICAgaW5rc2NhcGU6d2luZG93LWhlaWdodD0iMTA1OSIKICAgICBpbmtzY2FwZTp3aW5kb3cteD0iMCIKICAgICBpbmtzY2FwZTp3aW5kb3cteT0iMCIKICAgICBpbmtzY2FwZTp3aW5kb3ctbWF4aW1pemVkPSIxIgogICAgIGlua3NjYXBlOmN1cnJlbnQtbGF5ZXI9InN2ZzUxIiAvPgogIDxwYXRoCiAgICAgZD0iTTI1NiA4QzExOSA4IDggMTE5IDggMjU2czExMSAyNDggMjQ4IDI0OCAyNDgtMTExIDI0OC0yNDhTMzkzIDggMjU2IDh6bTAgNDQ4Yy0xMTAuNSAwLTIwMC04OS41LTIwMC0yMDBTMTQ1LjUgNTYgMjU2IDU2czIwMCA4OS41IDIwMCAyMDAtODkuNSAyMDAtMjAwIDIwMHoiCiAgICAgaWQ9InBhdGg0OSIKICAgICBzdHlsZT0iZmlsbDojZmZmZmZmIiAvPgo8L3N2Zz4K
[link-srht-repo]: https://git.sr.ht/~gotmax23/ansible-role-packman
[badge-license]: https://img.shields.io/github/license/gotmax23/ansible-role-packman.svg?logo=github
[link-license]: https://github.com/gotmax23/ansible-role-packman/blob/main/LICENSE
[badge-github-issues]: https://img.shields.io/github/issues/gotmax23/ansible-role-packman.svg?logo=github
[link-github-issues]: https://github.com/gotmax23/ansible-role-packman/issues
[badge-github-prs]: https://img.shields.io/github/issues-pr/gotmax23/ansible-role-packman.svg?logo=github
[link-github-prs]: https://github.com/gotmax23/ansible-role-packman/pulls
[badge-version]: https://img.shields.io/github/release/gotmax23/ansible-role-packman.svg?logo=github
[link-version]: https://github.com/gotmax23/ansible-role-packman/releases/latest
[badge-commits-since]: https://img.shields.io/github/commits-since/gotmax23/ansible-role-packman/latest.svg?logo=github
[badge-quality]: https://img.shields.io/ansible/quality/55918.svg?logo=ansible
[badge-downloads]: https://img.shields.io/ansible/role/d/55918.svg?logo=ansible
[badge-molecule-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/molecule.yml/badge.svg?branch=main
[link-molecule-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/molecule.yml
[badge-galaxy-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/galaxy.yml/badge.svg
[link-galaxy-workflow]: https://github.com/gotmax23/ansible-role-packman/actions/workflows/galaxy.yml
[link-defaults]: https://github.com/gotmax23/ansible-role-packman/blob/main/defaults/main.yml
