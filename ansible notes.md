To install on macOS:
pip3 install ansible
or
pip3 install ansible==2.6.4

To configure target hosts:
Create file /etc/ansible/hosts
to have content
[my-target-hosts]
ussm00m@rc51b10098dv00.bnymellon.net
myhost
or for more details, see
https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html#intro-inventory
note:
For convenience, I suggest defining a Host such as "myhost" in ~/.ssh/config and then listing "myhost" in the ansible hosts file.

To run something:
ansible my-target-hosts -m ping
or
ansible all -m ping

To run a single file playbook:
ansible-playbook ./my-playbook.yml

where the file contents are:
---
- name: My Playbook
  hosts: all
  become: true
  tasks:
  - name: Install the Nginx
    yum:
      name: nginx
      state: latest
