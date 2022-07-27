[![CI](https://github.com/de-it-krachten/ansible-role-docker_desktop/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-docker_desktop/actions?query=workflow%3ACI)


# ansible-role-docker_desktop

Manages Docker Desktop for Linux


## Platforms

Supported platforms

- Debian 10 (Buster)
- Debian 11 (Bullseye)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Fedora 35
- Fedora 36

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
  become: "{{ molecule['converge']['become'] | default('yes') }}"
  vars:
    gnome_desktop_wayland: False
    gnome_desktop_autologin_enable: True
    gnome_desktop_autologin: vagrant
    gnome_desktop_lock_disable: True
    gnome_desktop_lock_timeout: 0
  pre_tasks:
    - name: Create 'remote_tmp'
      file:
        path: /root/.ansible/tmp
        state: directory
        mode: "0700"
  roles:
    - python
    - docker
    - gnome_desktop
  tasks:
    - name: Include role 'docker_desktop'
      include_role:
        name: docker_desktop
</pre></code>
