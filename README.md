# [Ansible role php](#ansible-role-php)

Install and configure php on your system.

|GitHub|GitLab|Downloads|Version|
|------|------|---------|-------|
|[![github](https://github.com/buluma/ansible-role-php/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-php/actions)|[![gitlab](https://gitlab.com/shadowwalker/ansible-role-php/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-php)|[![downloads](https://img.shields.io/ansible/role/d/buluma/php)](https://galaxy.ansible.com/buluma/php)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-php.svg)](https://github.com/buluma/ansible-role-php/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-php/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: buluma.httpd
    - role: buluma.php
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-php/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: false

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
    - role: buluma.python_pip
    - role: buluma.buildtools
    - role: buluma.openssl
      openssl_items:
        - name: apache-httpd
          common_name: "{{ ansible_fqdn }}"
    - role: buluma.httpd
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-php/blob/master/defaults/main.yml):

```yaml
---
# defaults file for php

# The role discovers the ini location automatically, but can be overwritten.
# php_ini_location: /etc/php/7.4/apache/php.ini

# Alpine has both php5 and php7. Select the desired version here.
php_alpine_version: 7

# All the settings for PHP.
php_display_errors: false
php_startup_errors: false
php_error_reporting: false
php_html_errors: true
php_log_errors: true
php_max_input_time: 60
php_max_execution_time: 60
php_output_buffering: 4096
php_register_argc_argv: false
php_request_order: GP
php_session_gc_divisor: 1000
php_session_hash_bits_per_character: 5
php_short_open_tag: false
php_track_errors: false
php_variables_order: GPCS
php_engine: true
php_date_timezone: Africa/Nairobi
php_memory_limit: 128M
php_upload_max_filesize: 2M
php_post_max_size: 8M
# php_extensions:
#   - mcrypt.so
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-php/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Build Status GitHub](https://github.com/buluma/ansible-role-bootstrap/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-bootstrap/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.buildtools](https://galaxy.ansible.com/buluma/buildtools)|[![Build Status GitHub](https://github.com/buluma/ansible-role-buildtools/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-buildtools/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-buildtools/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-buildtools)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Build Status GitHub](https://github.com/buluma/ansible-role-epel/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-epel/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-epel/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-epel)|
|[buluma.httpd](https://galaxy.ansible.com/buluma/httpd)|[![Build Status GitHub](https://github.com/buluma/ansible-role-httpd/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-httpd/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-httpd/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-httpd)|
|[buluma.openssl](https://galaxy.ansible.com/buluma/openssl)|[![Build Status GitHub](https://github.com/buluma/ansible-role-openssl/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-openssl/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-openssl/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-openssl)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Build Status GitHub](https://github.com/buluma/ansible-role-python_pip/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-python_pip/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-python_pip)|
|[buluma.scl](https://galaxy.ansible.com/buluma/scl)|[![Build Status GitHub](https://github.com/buluma/ansible-role-scl/workflows/Ansible%20Molecule/badge.svg)](https://github.com/buluma/ansible-role-scl/actions)|[![Build Status GitLab](https://gitlab.com/shadowwalker/ansible-role-scl/badges/master/pipeline.svg)](https://gitlab.com/shadowwalker/ansible-role-scl)|

## [Dependencies](#dependencies)

Most roles require some kind of preparation, this is done in `molecule/default/prepare.yml`. This role has a "hard" dependency on the following roles:

- {'role': 'buluma.httpd'}

## [Context](#context)

This role is part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-php/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|

The minimum version of Ansible required is 2.12, tests have been done on:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them on [GitHub](https://github.com/buluma/ansible-role-php/issues).

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-php/blob/master/LICENSE).

## [Author Information](#author-information)

[buluma](https://buluma.github.io/)

