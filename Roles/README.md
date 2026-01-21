# Created httpd role
ansible-galaxy role init httpd

mv index.html httpd/files/

vi httpd/tasks/main.yml
---------
# tasks file for httpd
- name: Install apache httpd
  ansible.builtin.apt:
    name: apache2
    state: present
    update_cache: yes
- name: Copy file with Owner and permissions
  ansible.builtin.copy:
    src: index.html
    dest: /var/www/html
    owner: root
    group: root
    mode: '0644'

 ansible-playbook -i inventory.ini first-playbook.yaml
---------
PLAY [all] ***************************************************************************************************************************************************

TASK [Gathering Facts] ***************************************************************************************************************************************
ok: [51.21.195.59]
ok: [13.61.10.84]

TASK [httpd : Install apache httpd] **************************************************************************************************************************
ok: [13.61.10.84]
ok: [51.21.195.59]

TASK [httpd : Copy file with Owner and permissions] **********************************************************************************************************
ok: [51.21.195.59]
ok: [13.61.10.84]

PLAY RECAP ***************************************************************************************************************************************************
13.61.10.84                : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
51.21.195.59               : ok=3    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
