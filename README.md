[![CI](https://github.com/de-it-krachten/ansible-role-docker_desktop/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker_desktop/actions?query=workflow%3ACI)


# ansible-role-docker_desktop

Manages Docker Desktop for Linux



## Dependencies

#### Roles
None

#### Collections
None

## Platforms

Supported platforms

- OracleLinux 9
- SUSE Linux Enterprise 15<sup>1</sup>
- openSUSE Leap 15
- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 39
- Fedora 40

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
docker_desktop_deb: >-
  https://desktop.docker.com/linux/main/amd64/docker-desktop-{{ docker_desktop_version }}-amd64.deb
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'docker_desktop'
  hosts: all
  become: 'yes'
  vars:
    gnome_desktop_wayland: false
    gnome_desktop_autologin_enable: true
    gnome_desktop_autologin: vagrant
    gnome_desktop_lock_disable: true
    gnome_desktop_lock_timeout: 0
  roles:
    - deitkrachten.python
    - deitkrachten.docker
    - deitkrachten.gnome_desktop
  tasks:
    - name: Include role 'docker_desktop'
      ansible.builtin.include_role:
        name: docker_desktop
</pre></code>
