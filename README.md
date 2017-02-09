
# About

Ansible role to configure a Raspberry Pi to connect to a GPS device over serial. It also installs the [`gps3` python binding](https://pypi.python.org/pypi/gps3/).

# Dependencies

* A GPS device with the ability to connect to GPIO serial pins. I've tested this
with the a GP-20U7. You can read more about it at https://robrant.github.io.

* It has been tested on Raspberry Pi B+, but should work on all versions before
Raspberry Pi 3. Raspberry Pi 3 introduces (at least) 1 breaking change.
The Serial/UART GPIO pins is disabled by default. When I have a Raspberry Pi 3
to test with, I'll make changes to make it handle all Pi versions.

# Usage

You can either just clone down this repo and copy folders into the correct place
 or you can use `git submodule` and then move the folders around.

**Folders:** Move folders as follows:

    $> cd ansible-role-pi-serial-gps
    $> mv top_level_handlers /your_playbook/roles/
    $> mv library /your_playbook/
    $> mkdir -p /your_playbook/roles/pi-serial-gps
    $> mv defaults /your_playbook/roles/pi-serial-gps
    $> mv meta /your_playbook/roles/pi-serial-gps
    $> mv tasks /your_playbook/roles/pi-serial-gps

**Define Play**. Add the following to your playbook (YMMV):

    - hosts: pis
      roles:
        - pi-serial-gps
      tags: pi-serial-gps
      become: true
      gather_facts: true

Defaults and descriptions for the 3 vars can be found in `defaults/main.yml`.

# Example Playbook

[This repo](https://github.com/robrant/ansible-role-pi-serial-gps-example-playbook.git)
provides an example playbook that incorporates and runs this role.
