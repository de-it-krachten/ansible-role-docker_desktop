[![CI](https://github.com/de-it-krachten/ansible-role-docker_desktop/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker_desktop/actions?query=workflow%3ACI)


# ansible-role-docker_desktop

Manages Docker Desktop for Linux

## Platforms

Supported platforms

- Red Hat Enterprise Linux 7<sup>1</sup>
- Red Hat Enterprise Linux 8<sup>1</sup>
- CentOS 7
- RockyLinux 8
- AlmaLinux 8<sup>1</sup>
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 18.04 LTS
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# docker desktop version
docker_desktop_version: 4.9.0

# docker desktop RPM (RedHat-family)
docker_desktop_rpm: >-
  https://desktop.docker.com/linux/main/amd64/docker-desktop-{{ docker_desktop_version }}-x86_64.rpm

# docker desktop DEB (Debian-family)
docker_destop_deb: >-
  https://desktop.docker.com/linux/main/amd64/docker-desktop-{{ docker_desktop_version }}-amd64.deb
</pre></code>



## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'docker_desktop'
  hosts: all
  vars:
  tasks:
    - name: Include role 'docker_desktop'
      include_role:
        name: docker_desktop
</pre></code>
