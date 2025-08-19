# Домашнее задание к занятию 5 «Тестирование roles»


## Основная часть

Ваша цель — настроить тестирование ваших ролей.
Задача — сделать сценарии тестирования для vector.
Ожидаемый результат — все сценарии успешно проходят тестирование ролей.

## Molecule
1. Запустите molecule test -s ubuntu_xenial (или с любым другим сценарием, не имеет значения) внутри корневой директории clickhouse-role, посмотрите на вывод команды. Данная команда может отработать с ошибками или не отработать вовсе, это нормально. Наша цель - посмотреть как другие в реальном мире используют молекулу И из чего может состоять сценарий тестирования.

2. Перейдите в каталог с ролью vector-role и создайте сценарий тестирования по умолчанию при помощи molecule init scenario --driver-name docker.
 

<img width="887" height="481" alt="image" src="https://github.com/user-attachments/assets/a9c54d18-41aa-453d-b1a6-69f9f02de62d" />


   
4. Добавьте несколько разных дистрибутивов (oraclelinux:8, ubuntu:latest) для инстансов и протестируйте роль, исправьте найденные ошибки, если они есть.

Дистрибутивы добавлены:

```
---
driver:
  name: docker
platforms:
  - name: oraclelinux8
    image: docker.io/library/oraclelinux:8
    pre_build_image: true

  - name: ubuntu
    image: docker.io/pycontribs/ubuntu:latest
    pre_build_image: true
```

Ошибки исправлены и запущено тестирование.

<details>
<summary>Вывод</summary>

```
vova@Mynote:/mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/vector_role$ 
molecule test
WARNING  Driver docker does not provide a schema.
WARNING  Driver docker does not provide a schema.
INFO     default ➜ discovery: scenario test matrix: dependency, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, 
destroy
INFO     default ➜ prerun: Performing prerun with role_name_check=0...
INFO     default ➜ dependency: Starting
WARNING  default ➜ dependency: Skipping, missing the requirements file.
WARNING  default ➜ dependency: Skipping, missing the requirements file.
INFO     default ➜ dependency: Completed
INFO     default ➜ cleanup: Starting
WARNING  default ➜ cleanup: Skipping, cleanup playbook not configured.
INFO     default ➜ cleanup: Completed
INFO     default ➜ destroy: Starting
INFO     default ➜ destroy: ansible-playbook version: ansible-playbook
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
INFO     Sanity checks: 'docker'
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


PLAY [Destroy] *****************************************************************
TASK [Set async_dir for HOME env] **********************************************ok: [localhost]

TASK [Destroy molecule instance(s)] ********************************************changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) deletion to complete] *******************************ok: [localhost] => (item=oraclelinux8)
ok: [localhost] => (item=ubuntu)

TASK [Delete docker networks(s)] ***********************************************skipping: [localhost]

PLAY RECAP *********************************************************************localhost                  : ok=3    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     default ➜ destroy: Completed
INFO     default ➜ syntax: Starting
INFO     default ➜ syntax: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


playbook: /mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/vector_role/molecule/default/converge.yml
INFO     default ➜ syntax: Completed
INFO     default ➜ create: Starting
INFO     default ➜ create: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


PLAY [Create] ******************************************************************
TASK [Set async_dir for HOME env] **********************************************ok: [localhost]

TASK [Log into a Docker registry] **********************************************skipping: [localhost] => (item=(censored due to no_log)) 
skipping: [localhost] => (item=(censored due to no_log)) 
skipping: [localhost]

TASK [Check presence of custom Dockerfiles] ************************************ok: [localhost] => (item={'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})

TASK [Create Dockerfiles from image names] *************************************skipping: [localhost] => (item={'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})
skipping: [localhost]

TASK [Synchronization the context] *********************************************skipping: [localhost] => (item={'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
skipping: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})
skipping: [localhost]

TASK [Discover local Docker images] ********************************************ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'false_condition': 'not item.pre_build_image | default(false)', 'item': {'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 0, 'ansible_index_var': 'i'})
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'false_condition': 'not item.pre_build_image | default(false)', 'item': {'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 1, 'ansible_index_var': 'i'})

TASK [Build an Ansible compatible image (new)] *********************************skipping: [localhost] => (item=molecule_local/docker.io/library/oraclelinux:8) 
skipping: [localhost] => (item=molecule_local/docker.io/pycontribs/ubuntu:latest)
skipping: [localhost]

TASK [Create docker network(s)] ************************************************skipping: [localhost]

TASK [Determine the CMD directives] ********************************************ok: [localhost] => (item={'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
ok: [localhost] => (item={'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})

TASK [Create molecule instance(s)] *********************************************changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) creation to complete] *******************************FAILED - RETRYING: [localhost]: Wait for instance(s) creation to complete (300 retries left).
FAILED - RETRYING: [localhost]: Wait for instance(s) creation to complete (299 retries left).
changed: [localhost] => (item={'failed': False, 'started': True, 'finished': False, 'ansible_job_id': 'j116962100956.5800', 'results_file': '/home/vova/.ansible_async/j116962100956.5800', 'changed': True, 'item': {'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True}, 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'failed': False, 'started': True, 'finished': False, 'ansible_job_id': 'j654588080663.5825', 'results_file': '/home/vova/.ansible_async/j654588080663.5825', 'changed': True, 'item': {'image': 'docker.io/pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************localhost                  : ok=6    changed=2    unreachable=0    failed=0    skipped=5    rescued=0    ignored=0

INFO     default ➜ create: Completed
INFO     default ➜ prepare: Starting
WARNING  default ➜ prepare: Skipping, prepare playbook not configured.
INFO     default ➜ prepare: Completed
INFO     default ➜ converge: Starting
INFO     default ➜ converge: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


PLAY [Converge] ****************************************************************
TASK [Replace this task with one that validates your content] ******************ok: [oraclelinux8] => {
    "msg": "This is the effective test"
}
ok: [ubuntu] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************oraclelinux8               : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ubuntu                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     default ➜ converge: Completed
INFO     default ➜ idempotence: Starting
INFO     default ➜ idempotence: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


PLAY [Converge] ****************************************************************
TASK [Replace this task with one that validates your content] ******************ok: [oraclelinux8] => {
    "msg": "This is the effective test"
}
ok: [ubuntu] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************oraclelinux8               : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
ubuntu                     : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     default ➜ idempotence: Idempotence completed successfully.
INFO     default ➜ idempotence: Completed
INFO     default ➜ side_effect: Starting
WARNING  default ➜ sideeffect: Skipping, side effect playbook not configured.
INFO     default ➜ side_effect: Completed
INFO     default ➜ verify: Starting
INFO     default ➜ verify: Running Ansible Verifier
WARNING  default ➜ verify: Skipping, verify playbook not configured.
INFO     default ➜ verify: Verifier completed successfully.
INFO     default ➜ verify: Completed
INFO     default ➜ cleanup: Starting
WARNING  default ➜ cleanup: Skipping, cleanup playbook not configured.
INFO     default ➜ cleanup: Completed
INFO     default ➜ destroy: Starting
INFO     default ➜ destroy: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /home/vova/molecule-venv/lib/python3.12/site-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /home/vova/molecule-venv/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/home/vova/molecule-venv/bin/python3)
  jinja version = 3.1.6
  pyyaml version = 6.0.2 (with libyaml v0.2.5)
[WARNING]: Deprecation warnings can be disabled by setting `deprecation_warnings=False` in ansible.cfg.
[DEPRECATION WARNING]: DEFAULT_MANAGED_STR option. Reason: The `ansible_managed` variable can be set just like any other variable, or a different variable can be used.
Alternatives: Set the `ansible_managed` variable, or use any custom variable in 
templates. This feature will be removed from ansible-core version 2.23.


PLAY [Destroy] *****************************************************************
TASK [Set async_dir for HOME env] **********************************************ok: [localhost]

TASK [Destroy molecule instance(s)] ********************************************changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) deletion to complete] *******************************FAILED - RETRYING: [localhost]: Wait for instance(s) deletion to complete (300 retries left).
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Delete docker networks(s)] ***********************************************skipping: [localhost]

PLAY RECAP *********************************************************************localhost                  : ok=3    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     default ➜ destroy: Completed
INFO     default ➜ scenario: Pruning extra files from scenario ephemeral directory
vova@Mynote:/mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/vector_role$ 

```
</details>

6. Добавьте несколько assert в verify.yml-файл для проверки работоспособности vector-role (проверка, что конфиг валидный, проверка успешности запуска и др.).

Добавил проверки

```
---
- name: Verify Vector installation
  hosts: all
  gather_facts: false
  tasks:

    - name: Check Vector binary exists
      stat:
        path: /usr/local/bin/vector
      register: vector_bin

    - name: Fail if Vector binary is missing
      fail:
        msg: "Vector installation failed - binary missing"
      when: not vector_bin.stat.exists

    - name: Check Vector process
      command: pgrep -f "vector --config"
      register: vector_process
      ignore_errors: true

    - name: Fail if Vector process is not running
      fail:
        msg: "Vector process is not running"
      when: vector_process.rc != 0

    - name: Get Vector version
      command: /usr/local/bin/vector --version
      register: vector_version
      changed_when: false

    - name: Extract Vector version number
      set_fact:
        vector_version_number: "{{ (vector_version.stdout | regex_search('([0-9]+\\.[0-9]+\\.[0-9]+)')) | string }}"

    - name: Ensure Vector version is at least 0.27.0
      assert:
        that:
          - vector_version_number is version('0.27.0', '>=')
        fail_msg: "Vector version is too old: {{ vector_version_number }}"
```
   
8. Запустите тестирование роли повторно и проверьте, что оно прошло успешно.

Запустил.

<details>
<summary>Вывод тестированя</summary>

```
vova@Mynote:/mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/vector_role$ molecule test                  
WARNING  Driver docker does not provide a schema.
WARNING  Driver docker does not provide a schema.
INFO     default ➜ discovery: scenario test matrix: dependency, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     default ➜ prerun: Performing prerun with role_name_check=0...
WARNING  Another version of 'ansible.posix' 1.5.4 was found installed in /usr/lib/python3/dist-packages/ansible_collections, only the first one will be used, 2.1.0 (/home/vova/.ansible/collections/ansible_collections).    
WARNING  Another version of 'community.docker' 3.7.0 was found installed in /usr/lib/python3/dist-packages/ansible_collections, only the first one will be used, 4.7.0 (/home/vova/.ansible/collections/ansible_collections). 
WARNING  Another version of 'community.library_inventory_filtering_v1' 1.0.0 was found installed in /usr/lib/python3/dist-packages/ansible_collections, only the first one will be used, 1.1.1 (/home/vova/.ansible/collections/ansible_collections).
INFO     default ➜ dependency: Starting
WARNING  default ➜ dependency: Skipping, missing the requirements file.
WARNING  default ➜ dependency: Skipping, missing the requirements file.
INFO     default ➜ dependency: Completed
INFO     default ➜ cleanup: Starting
WARNING  default ➜ cleanup: Skipping, cleanup playbook not configured.
INFO     default ➜ cleanup: Completed
INFO     default ➜ destroy: Starting
INFO     default ➜ destroy: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True
INFO     Sanity checks: 'docker'

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: [localhost]: Wait for instance(s) deletion to complete (300 retries left).
FAILED - RETRYING: [localhost]: Wait for instance(s) deletion to complete (299 retries left).
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Delete docker networks(s)] ***********************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     default ➜ destroy: Completed
INFO     default ➜ syntax: Starting
INFO     default ➜ syntax: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

playbook: /mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/vector_role/molecule/default/converge.yml     
INFO     default ➜ syntax: Completed
INFO     default ➜ create: Starting
INFO     default ➜ create: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Create] ******************************************************************

TASK [Log into a Docker registry] **********************************************
skipping: [localhost] => (item=None) 
skipping: [localhost] => (item=None) 
skipping: [localhost]

TASK [Check presence of custom Dockerfiles] ************************************
ok: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
ok: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})

TASK [Create Dockerfiles from image names] *************************************
skipping: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
skipping: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})
skipping: [localhost]

TASK [Discover local Docker images] ********************************************
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'false_condition': 'not item.pre_build_image | default(false)', 'item': {'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 0, 'ansible_index_var': 'i'})
ok: [localhost] => (item={'changed': False, 'skipped': True, 'skip_reason': 'Conditional result was False', 'false_condition': 'not item.pre_build_image | default(false)', 'item': {'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item', 'i': 1, 'ansible_index_var': 'i'})

TASK [Build an Ansible compatible image (new)] *********************************
skipping: [localhost] => (item=molecule_local/docker.io/library/oraclelinux:8) 
skipping: [localhost] => (item=molecule_local/pycontribs/ubuntu:latest) 
skipping: [localhost]

TASK [Create docker network(s)] ************************************************
skipping: [localhost]

TASK [Determine the CMD directives] ********************************************
ok: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 'pre_build_image': True})
ok: [localhost] => (item={'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True})

TASK [Create molecule instance(s)] *********************************************
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) creation to complete] *******************************
FAILED - RETRYING: [localhost]: Wait for instance(s) creation to complete (300 retries left).
FAILED - RETRYING: [localhost]: Wait for instance(s) creation to complete (299 retries left).
changed: [localhost] => (item={'failed': 0, 'started': 1, 'finished': 0, 'ansible_job_id': 'j780009578963.84776', 'results_file': '/home/vova/.ansible_async/j780009578963.84776', 'changed': True, 'item': {'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'docker.io/library/oraclelinux:8', 'name': 'oraclelinux8', 
'pre_build_image': True}, 'ansible_loop_var': 'item'})
changed: [localhost] => (item={'failed': 0, 'started': 1, 'finished': 0, 'ansible_job_id': 'j357149382112.84801', 'results_file': '/home/vova/.ansible_async/j357149382112.84801', 'changed': True, 'item': {'command': '/bin/sh -c "while true; do sleep 10000; done"', 'image': 'pycontribs/ubuntu:latest', 'name': 'ubuntu', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=5    changed=2    unreachable=0    failed=0    skipped=4    rescued=0    ignored=0

INFO     default ➜ create: Completed
INFO     default ➜ prepare: Starting
INFO     default ➜ prepare: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Prepare] *****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [Update apt cache (Ubuntu)] ***********************************************
skipping: [oraclelinux8]
changed: [ubuntu]

TASK [Install common packages on Ubuntu] ***************************************
skipping: [oraclelinux8]
changed: [ubuntu]

TASK [Update yum cache (Oracle Linux)] *****************************************
skipping: [ubuntu]
ok: [oraclelinux8]

TASK [Install common packages on Oracle Linux] *********************************
skipping: [ubuntu]
changed: [oraclelinux8]

PLAY RECAP *********************************************************************
oraclelinux8               : ok=3    changed=1    unreachable=0    failed=0    skipped=2    rescued=0    ignored=0
ubuntu                     : ok=3    changed=2    unreachable=0    failed=0    skipped=2    rescued=0    ignored=0

INFO     default ➜ prepare: Completed
INFO     default ➜ converge: Starting
INFO     default ➜ converge: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Install dependencies] **************************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Ensure Vector binary is present] ***************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Create temp directory for Vector archive] ******************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [vector_role : Download Vector archive if binary is missing] **************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [vector_role : Create extraction directory for Vector] ********************
changed: [oraclelinux8]
changed: [ubuntu]

TASK [vector_role : Extract Vector archive if binary is missing] ***************
changed: [oraclelinux8]
changed: [ubuntu]

TASK [vector_role : Find Vector binary] ****************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [vector_role : Fail if Vector binary not found] ***************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Install Vector binary] *************************************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [vector_role : Create Vector config directory] ****************************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [vector_role : Apply Vector configuration] ********************************
changed: [oraclelinux8]
changed: [ubuntu]

TASK [vector_role : Create Vector run script] **********************************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [vector_role : Start Vector process] **************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [vector_role : Cleanup temp directory] ************************************
changed: [oraclelinux8]
changed: [ubuntu]

TASK [vector_role : Cleanup downloaded archive] ********************************
changed: [oraclelinux8]
changed: [ubuntu]

PLAY RECAP *********************************************************************
oraclelinux8               : ok=15   changed=10   unreachable=0    failed=0    skipped=1    rescued=0    ignored=0
ubuntu                     : ok=15   changed=10   unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     default ➜ converge: Completed
INFO     default ➜ idempotence: Starting
INFO     default ➜ idempotence: ansible-playbook version: ansible-playbook 
  config file = None
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Converge] ****************************************************************

TASK [Gathering Facts] *********************************************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Install dependencies] **************************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Ensure Vector binary is present] ***************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [vector_role : Create temp directory for Vector archive] ******************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Download Vector archive if binary is missing] **************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Create extraction directory for Vector] ********************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Extract Vector archive if binary is missing] ***************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Find Vector binary] ****************************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Fail if Vector binary not found] ***************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Install Vector binary] *************************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Create Vector config directory] ****************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Apply Vector configuration] ********************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Create Vector run script] **********************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [vector_role : Start Vector process] **************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [vector_role : Cleanup temp directory] ************************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [vector_role : Cleanup downloaded archive] ********************************
skipping: [oraclelinux8]
skipping: [ubuntu]

PLAY RECAP *********************************************************************
oraclelinux8               : ok=7    changed=0    unreachable=0    failed=0    skipped=9    rescued=0    ignored=0
ubuntu                     : ok=7    changed=0    unreachable=0    failed=0    skipped=9    rescued=0    ignored=0

INFO     default ➜ idempotence: Idempotence completed successfully.
INFO     default ➜ idempotence: Completed
INFO     default ➜ side_effect: Starting
WARNING  default ➜ sideeffect: Skipping, side effect playbook not configured.
INFO     default ➜ side_effect: Completed
INFO     default ➜ verify: Starting
INFO     default ➜ verify: Running Ansible Verifier
INFO     default ➜ verify: ansible-playbook version: ansible-playbook 
  config file = /home/vova/.ansible/tmp/molecule.4_or.default/ansible.cfg
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Verify Vector installation] **********************************************

TASK [Check Vector binary exists] **********************************************
ok: [ubuntu]
ok: [oraclelinux8]

TASK [Fail if Vector binary is missing] ****************************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [Check Vector process] ****************************************************
changed: [ubuntu]
changed: [oraclelinux8]

TASK [Fail if Vector process is not running] ***********************************
skipping: [oraclelinux8]
skipping: [ubuntu]

TASK [Get Vector version] ******************************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [Extract Vector version number] *******************************************
ok: [oraclelinux8]
ok: [ubuntu]

TASK [Ensure Vector version is at least 0.27.0] ********************************
ok: [oraclelinux8] => {
    "changed": false,
    "msg": "All assertions passed"
}
ok: [ubuntu] => {
    "changed": false,
    "msg": "All assertions passed"
}

PLAY RECAP *********************************************************************
oraclelinux8               : ok=5    changed=1    unreachable=0    failed=0    skipped=2    rescued=0    ignored=0
ubuntu                     : ok=5    changed=1    unreachable=0    failed=0    skipped=2    rescued=0    ignored=0

INFO     default ➜ verify: Verifier completed successfully.
INFO     default ➜ verify: Completed
INFO     default ➜ cleanup: Starting
WARNING  default ➜ cleanup: Skipping, cleanup playbook not configured.
INFO     default ➜ cleanup: Completed
INFO     default ➜ destroy: Starting
INFO     default ➜ destroy: ansible-playbook version: ansible-playbook
  config file = /home/vova/.ansible/tmp/molecule.4_or.default/ansible.cfg
  configured module search path = ['/home/vova/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /home/vova/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.12.3 (main, Jun 18 2025, 17:59:45)  (/usr/bin/python3)
  jinja version = 3.1.2
  libyaml = True

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: [localhost]: Wait for instance(s) deletion to complete (300 retries left).
FAILED - RETRYING: [localhost]: Wait for instance(s) deletion to complete (299 retries left).
changed: [localhost] => (item=oraclelinux8)
changed: [localhost] => (item=ubuntu)

TASK [Delete docker networks(s)] ***********************************************
skipping: [localhost]

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0

INFO     default ➜ destroy: Completed
INFO     default ➜ scenario: Pruning extra files from scenario ephemeral directory
```
</details>
   
10. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

[Ссылка на v1.0.1](https://github.com/vladmgb/hw-ansible-test-roles/releases/tag/v1.0.1)
    

## Tox
1. Добавьте в директорию с vector-role файлы из директории.
2. Запустите docker run --privileged=True -v <path_to_repo>:/opt/vector-role -w /opt/vector-role -it aragast/netology:latest /bin/bash, где path_to_repo — путь до корня репозитория с vector-role на вашей файловой системе.
   
   <img width="809" height="53" alt="image" src="https://github.com/user-attachments/assets/5e335373-45d9-481b-bbb5-a3b100761a4b" />

4. Внутри контейнера выполните команду tox, посмотрите на вывод.

Запустил.

<details>
<summary>Вывод</summary>
```
[root@8be4351a9124 vector_role]# tox
py37-ansible210 installed: ansible==2.10.7,ansible-base==2.10.17,ansible-compat==1.0.0,arrow==1.2.3,bcrypt==4.2.1,binaryornot==0.4.4,cached-property==1.5.2,Cerberus==1.3.7,certifi==2025.8.3,cffi==1.15.1,chardet==5.2.0,charset-normalizer==3.4.3,click==8.1.8,click-help-colors==0.9.4,cookiecutter==2.6.0,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,idna==3.10,importlib-metadata==6.7.0,Jinja2==3.1.6,jmespath==1.0.1,lxml==5.4.0,markdown-it-py==2.2.0,MarkupSafe==2.1.5,mdurl==0.1.2,molecule==3.6.1,molecule-podman==1.1.0,packaging==24.0,paramiko==2.12.0,pluggy==1.2.0,pycparser==2.21,Pygments==2.17.2,PyNaCl==1.5.0,python-dateutil==2.9.0.post0,python-slugify==8.0.4,PyYAML==6.0.1,requests==2.31.0,rich==13.8.1,selinux==0.2.1,six==1.17.0,subprocess-tee==0.3.5,text-unidecode==1.3,typing_extensions==4.7.1,urllib3==2.0.7,zipp==3.15.0
py37-ansible210 run-test-pre: PYTHONHASHSEED='2627599586'
py37-ansible210 run-test: commands[0] | molecule test -s compatibility --destroy always
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
CRITICAL 'molecule/compatibility/molecule.yml' glob failed.  Exiting.
ERROR: InvocationError for command /opt/vector_role/.tox/py37-ansible210/bin/molecule test -s compatibility --destroy always (exited with code 1)
py37-ansible30 installed: ansible==3.0.0,ansible-base==2.10.17,ansible-compat==1.0.0,arrow==1.2.3,bcrypt==4.2.1,binaryornot==0.4.4,cached-property==1.5.2,Cerberus==1.3.7,certifi==2025.8.3,cffi==1.15.1,chardet==5.2.0,charset-normalizer==3.4.3,click==8.1.8,click-help-colors==0.9.4,cookiecutter==2.6.0,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,idna==3.10,importlib-metadata==6.7.0,Jinja2==3.1.6,jmespath==1.0.1,lxml==5.4.0,markdown-it-py==2.2.0,MarkupSafe==2.1.5,mdurl==0.1.2,molecule==3.6.1,molecule-podman==1.1.0,packaging==24.0,paramiko==2.12.0,pluggy==1.2.0,pycparser==2.21,Pygments==2.17.2,PyNaCl==1.5.0,python-dateutil==2.9.0.post0,python-slugify==8.0.4,PyYAML==6.0.1,requests==2.31.0,rich==13.8.1,selinux==0.2.1,six==1.17.0,subprocess-tee==0.3.5,text-unidecode==1.3,typing_extensions==4.7.1,urllib3==2.0.7,zipp==3.15.0
py37-ansible30 run-test-pre: PYTHONHASHSEED='2627599586'
py37-ansible30 run-test: commands[0] | molecule test -s compatibility --destroy always
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
CRITICAL 'molecule/compatibility/molecule.yml' glob failed.  Exiting.
ERROR: InvocationError for command /opt/vector_role/.tox/py37-ansible30/bin/molecule test -s compatibility --destroy always (exited with code 1)
py39-ansible210 installed: ansible==2.10.7,ansible-base==2.10.17,ansible-compat==24.10.0,ansible-core==2.15.13,attrs==25.3.0,bracex==2.6,cffi==1.17.1,click==8.1.8,click-help-colors==0.9.4,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,importlib-resources==5.0.7,Jinja2==3.1.6,jmespath==1.0.1,jsonschema==4.25.1,jsonschema-specifications==2025.4.1,lxml==6.0.0,markdown-it-py==3.0.0,MarkupSafe==3.0.2,mdurl==0.1.2,molecule==6.0.3,molecule-podman==2.0.3,packaging==25.0,pluggy==1.6.0,pycparser==2.22,Pygments==2.19.2,PyYAML==6.0.2,referencing==0.36.2,resolvelib==1.0.1,rich==14.1.0,rpds-py==0.27.0,selinux==0.3.0,subprocess-tee==0.4.2,typing_extensions==4.14.1,wcmatch==10.1
py39-ansible210 run-test-pre: PYTHONHASHSEED='2627599586'
py39-ansible210 run-test: commands[0] | molecule test -s compatibility --destroy always
CRITICAL 'molecule/compatibility/molecule.yml' glob failed.  Exiting.
ERROR: InvocationError for command /opt/vector_role/.tox/py39-ansible210/bin/molecule test -s compatibility --destroy always (exited with code 1)
py39-ansible30 installed: ansible==3.0.0,ansible-base==2.10.17,ansible-compat==24.10.0,ansible-core==2.15.13,attrs==25.3.0,bracex==2.6,cffi==1.17.1,click==8.1.8,click-help-colors==0.9.4,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,importlib-resources==5.0.7,Jinja2==3.1.6,jmespath==1.0.1,jsonschema==4.25.1,jsonschema-specifications==2025.4.1,lxml==6.0.0,markdown-it-py==3.0.0,MarkupSafe==3.0.2,mdurl==0.1.2,molecule==6.0.3,molecule-podman==2.0.3,packaging==25.0,pluggy==1.6.0,pycparser==2.22,Pygments==2.19.2,PyYAML==6.0.2,referencing==0.36.2,resolvelib==1.0.1,rich==14.1.0,rpds-py==0.27.0,selinux==0.3.0,subprocess-tee==0.4.2,typing_extensions==4.14.1,wcmatch==10.1 
py39-ansible30 run-test-pre: PYTHONHASHSEED='2627599586'
py39-ansible30 run-test: commands[0] | molecule test -s compatibility --destroy always
CRITICAL 'molecule/compatibility/molecule.yml' glob failed.  Exiting.
ERROR: InvocationError for command /opt/vector_role/.tox/py39-ansible30/bin/molecule test -s compatibility --destroy always (exited with code 1)
___________________________________________________ summary ____________________________________________________ERROR:   py37-ansible210: commands failed
ERROR:   py37-ansible30: commands failed
ERROR:   py39-ansible210: commands failed
ERROR:   py39-ansible30: commands failed
[root@8be4351a9124 vector_role]# 
```
</details>

Создайте облегчённый сценарий для molecule с драйвером molecule_podman. Проверьте его на исполнимость.

<img width="922" height="472" alt="image" src="https://github.com/user-attachments/assets/9c09bfec-6e98-4c7b-9351-71074f9f2d10" />


Пропишите правильную команду в tox.ini, чтобы запускался облегчённый сценарий.

```
commands =
    {posargs:molecule test -s compatibility --destroy always}
```

Запустите команду tox. Убедитесь, что всё отработало успешно.

Запустил tox.

<details>
<summary>Вывод</summary>

 ```

[root@8d4ea73e0183 vector_role]# tox
py37-ansible210 installed: ansible==2.10.7,ansible-base==2.10.17,ansible-compat==1.0.0,arrow==1.2.3,bcrypt==4.2.1,binaryornot==0.4.4,cached-property==1.5.2,Cerberus==1.3.7,certifi==2025.8.3,cffi==1.15.1,chardet==5.2.0,charset-normalizer==3.4.3,click==8.1.8,click-help-colors==0.9.4,cookiecutter==2.6.0,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,idna==3.10,importlib-metadata==6.7.0,Jinja2==3.1.6,jmespath==1.0.1,lxml==5.4.0,markdown-it-py==2.2.0,MarkupSafe==2.1.5,mdurl==0.1.2,molecule==3.6.1,molecule-podman==1.1.0,packaging==24.0,paramiko==2.12.0,pluggy==1.2.0,pycparser==2.21,Pygments==2.17.2,PyNaCl==1.5.0,python-dateutil==2.9.0.post0,python-slugify==8.0.4,PyYAML==6.0.1,requests==2.31.0,rich==13.8.1,selinux==0.2.1,six==1.17.0,subprocess-tee==0.3.5,text-unidecode==1.3,typing_extensions==4.7.1,urllib3==2.0.7,zipp==3.15.0
py37-ansible210 run-test-pre: PYTHONHASHSEED='69510204'
py37-ansible210 run-test: commands[0] | molecule test -s light --destroy always
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
INFO     light scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Set ANSIBLE_LIBRARY=/root/.cache/ansible-compat/76a2e5/modules:/root/.ansible/plugins/modules:/usr/share/ansible/plugins/modules
INFO     Set ANSIBLE_COLLECTIONS_PATH=/root/.cache/ansible-compat/76a2e5/collections:/root/.ansible/collections:/usr/share/ansible/collections
INFO     Set ANSIBLE_ROLES_PATH=/root/.cache/ansible-compat/76a2e5/roles:/root/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles
INFO     Using /root/.ansible/roles/vladmgb.vector_role symlink to current repository in order to enable Ansible to find the role using its expected full name.
INFO     Running light > dependency
WARNING  Skipping, missing the requirements file.
WARNING  Skipping, missing the requirements file.
INFO     Running light > lint
INFO     Lint is disabled.
INFO     Running light > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running light > destroy
INFO     Sanity checks: 'podman'
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
changed: [localhost] => (item={'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': 
True})

TASK [Wait for instance(s) deletion to complete] *******************************
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '615469474518.1063', 'results_file': '/root/.ansible_async/615469474518.1063', 'changed': True, 'failed': False, 'item': {'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running light > syntax

playbook: /opt/vector_role/molecule/light/converge.yml
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
INFO     Running light > create

PLAY [Create] ******************************************************************

TASK [get podman executable path] **********************************************
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [localhost]

TASK [save path to executable as fact] *****************************************
ok: [localhost]

TASK [Log into a container registry] *******************************************
skipping: [localhost] => (item="instance registry username: None specified") 

TASK [Check presence of custom Dockerfiles] ************************************
ok: [localhost] => (item=Dockerfile: None specified)

TASK [Create Dockerfiles from image names] *************************************
skipping: [localhost] => (item="Dockerfile: None specified; Image: quay.io/centos/centos:stream8") 

TASK [Discover local Podman images] ********************************************
ok: [localhost] => (item=instance)

TASK [Build an Ansible compatible image] ***************************************
skipping: [localhost] => (item=quay.io/centos/centos:stream8) 

TASK [Determine the CMD directives] ********************************************
ok: [localhost] => (item="instance command: None specified")

TASK [Remove possible pre-existing containers] *********************************
changed: [localhost]

TASK [Discover local podman networks] ******************************************
skipping: [localhost] => (item=instance: None specified) 

TASK [Create podman network dedicated to this scenario] ************************
skipping: [localhost]

TASK [Create molecule instance(s)] *********************************************
changed: [localhost] => (item=instance)

TASK [Wait for instance(s) creation to complete] *******************************
FAILED - RETRYING: Wait for instance(s) creation to complete (300 retries left).
changed: [localhost] => (item=instance)

PLAY RECAP *********************************************************************
localhost                  : ok=8    changed=3    unreachable=0    failed=0    skipped=5    rescued=0    ignored=0

INFO     Running light > prepare
WARNING  Skipping, prepare playbook not configured.
INFO     Running light > converge

PLAY [Converge] ****************************************************************

TASK [Replace this task with one that validates your content] ******************
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [instance] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************
instance                   : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running light > idempotence

PLAY [Converge] ****************************************************************

TASK [Replace this task with one that validates your content] ******************
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [instance] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************
instance                   : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running light > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running light > verify
INFO     Running Ansible Verifier
WARNING  Skipping, verify playbook not configured.
INFO     Verifier completed successfully.
INFO     Running light > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running light > destroy

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible210/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
changed: [localhost] => (item={'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': 
True})

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: Wait for instance(s) deletion to complete (300 retries left).
FAILED - RETRYING: Wait for instance(s) deletion to complete (299 retries left).
FAILED - RETRYING: Wait for instance(s) deletion to complete (298 retries left).
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '336542714387.1326', 'results_file': '/root/.ansible_async/336542714387.1326', 'changed': True, 'failed': False, 'item': {'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
py37-ansible30 installed: ansible==3.0.0,ansible-base==2.10.17,ansible-compat==1.0.0,arrow==1.2.3,bcrypt==4.2.1,binaryornot==0.4.4,cached-property==1.5.2,Cerberus==1.3.7,certifi==2025.8.3,cffi==1.15.1,chardet==5.2.0,charset-normalizer==3.4.3,click==8.1.8,click-help-colors==0.9.4,cookiecutter==2.6.0,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,idna==3.10,importlib-metadata==6.7.0,Jinja2==3.1.6,jmespath==1.0.1,lxml==5.4.0,markdown-it-py==2.2.0,MarkupSafe==2.1.5,mdurl==0.1.2,molecule==3.6.1,molecule-podman==1.1.0,packaging==24.0,paramiko==2.12.0,pluggy==1.2.0,pycparser==2.21,Pygments==2.17.2,PyNaCl==1.5.0,python-dateutil==2.9.0.post0,python-slugify==8.0.4,PyYAML==6.0.1,requests==2.31.0,rich==13.8.1,selinux==0.2.1,six==1.17.0,subprocess-tee==0.3.5,text-unidecode==1.3,typing_extensions==4.7.1,urllib3==2.0.7,zipp==3.15.0
py37-ansible30 run-test-pre: PYTHONHASHSEED='69510204'
py37-ansible30 run-test: commands[0] | molecule test -s light --destroy always
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
INFO     light scenario test matrix: dependency, lint, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun...
INFO     Set ANSIBLE_LIBRARY=/root/.cache/ansible-compat/76a2e5/modules:/root/.ansible/plugins/modules:/usr/share/ansible/plugins/modules
INFO     Set ANSIBLE_COLLECTIONS_PATH=/root/.cache/ansible-compat/76a2e5/collections:/root/.ansible/collections:/usr/share/ansible/collections
INFO     Set ANSIBLE_ROLES_PATH=/root/.cache/ansible-compat/76a2e5/roles:/root/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles
INFO     Using /root/.ansible/roles/vladmgb.vector_role symlink to current repository in order to enable Ansible to find the role using its expected full name.
INFO     Running light > dependency
WARNING  Skipping, missing the requirements file.
WARNING  Skipping, missing the requirements file.
INFO     Running light > lint
INFO     Lint is disabled.
INFO     Running light > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running light > destroy
INFO     Sanity checks: 'podman'
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
changed: [localhost] => (item={'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': 
True})

TASK [Wait for instance(s) deletion to complete] *******************************
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '94604318877.1479', 'results_file': '/root/.ansible_async/94604318877.1479', 'changed': True, 'failed': False, 'item': {'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running light > syntax

playbook: /opt/vector_role/molecule/light/converge.yml
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
INFO     Running light > create

PLAY [Create] ******************************************************************

TASK [get podman executable path] **********************************************
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [localhost]

TASK [save path to executable as fact] *****************************************
ok: [localhost]

TASK [Log into a container registry] *******************************************
skipping: [localhost] => (item="instance registry username: None specified") 

TASK [Check presence of custom Dockerfiles] ************************************
ok: [localhost] => (item=Dockerfile: None specified)

TASK [Create Dockerfiles from image names] *************************************
skipping: [localhost] => (item="Dockerfile: None specified; Image: quay.io/centos/centos:stream8") 

TASK [Discover local Podman images] ********************************************
ok: [localhost] => (item=instance)

TASK [Build an Ansible compatible image] ***************************************
skipping: [localhost] => (item=quay.io/centos/centos:stream8) 

TASK [Determine the CMD directives] ********************************************
ok: [localhost] => (item="instance command: None specified")

TASK [Remove possible pre-existing containers] *********************************
changed: [localhost]

TASK [Discover local podman networks] ******************************************
skipping: [localhost] => (item=instance: None specified) 

TASK [Create podman network dedicated to this scenario] ************************
skipping: [localhost]

TASK [Create molecule instance(s)] *********************************************
changed: [localhost] => (item=instance)

TASK [Wait for instance(s) creation to complete] *******************************
FAILED - RETRYING: Wait for instance(s) creation to complete (300 retries left).
changed: [localhost] => (item=instance)

PLAY RECAP *********************************************************************
localhost                  : ok=8    changed=3    unreachable=0    failed=0    skipped=5    rescued=0    ignored=0

INFO     Running light > prepare
WARNING  Skipping, prepare playbook not configured.
INFO     Running light > converge

PLAY [Converge] ****************************************************************

TASK [Replace this task with one that validates your content] ******************
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [instance] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************
instance                   : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Running light > idempotence

PLAY [Converge] ****************************************************************

TASK [Replace this task with one that validates your content] ******************
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
ok: [instance] => {
    "msg": "This is the effective test"
}

PLAY RECAP *********************************************************************
instance                   : ok=1    changed=0    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Idempotence completed successfully.
INFO     Running light > side_effect
WARNING  Skipping, side effect playbook not configured.
INFO     Running light > verify
INFO     Running Ansible Verifier
WARNING  Skipping, verify playbook not configured.
INFO     Verifier completed successfully.
INFO     Running light > cleanup
WARNING  Skipping, cleanup playbook not configured.
INFO     Running light > destroy

PLAY [Destroy] *****************************************************************

TASK [Destroy molecule instance(s)] ********************************************
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/ansible/parsing/vault/__init__.py:44: CryptographyDeprecationWarning: Python 3.7 is no longer supported by the Python core team and support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.7.
  from cryptography.exceptions import InvalidSignature
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/pkey.py:82: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed 
from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "cipher": algorithms.TripleDES,
/opt/vector_role/.tox/py37-ansible30/lib/python3.7/site-packages/paramiko/transport.py:253: CryptographyDeprecationWarning: TripleDES has been moved to cryptography.hazmat.decrepit.ciphers.algorithms.TripleDES and will be removed from cryptography.hazmat.primitives.ciphers.algorithms in 48.0.0.
  "class": algorithms.TripleDES,
changed: [localhost] => (item={'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': 
True})

TASK [Wait for instance(s) deletion to complete] *******************************
FAILED - RETRYING: Wait for instance(s) deletion to complete (300 retries left).
FAILED - RETRYING: Wait for instance(s) deletion to complete (299 retries left).
FAILED - RETRYING: Wait for instance(s) deletion to complete (298 retries left).
changed: [localhost] => (item={'started': 1, 'finished': 0, 'ansible_job_id': '686940153253.1740', 'results_file': '/root/.ansible_async/686940153253.1740', 'changed': True, 'failed': False, 'item': {'image': 'quay.io/centos/centos:stream8', 'name': 'instance', 'pre_build_image': True}, 'ansible_loop_var': 'item'})

PLAY RECAP *********************************************************************
localhost                  : ok=2    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0

INFO     Pruning extra files from scenario ephemeral directory
py39-ansible210 installed: ansible==2.10.7,ansible-base==2.10.17,ansible-compat==24.10.0,ansible-core==2.15.13,attrs==25.3.0,bracex==2.6,cffi==1.17.1,click==8.1.8,click-help-colors==0.9.4,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,importlib-resources==5.0.7,Jinja2==3.1.6,jmespath==1.0.1,jsonschema==4.25.1,jsonschema-specifications==2025.4.1,lxml==6.0.0,markdown-it-py==3.0.0,MarkupSafe==3.0.2,mdurl==0.1.2,molecule==6.0.3,molecule-podman==2.0.3,packaging==25.0,pluggy==1.6.0,pycparser==2.22,Pygments==2.19.2,PyYAML==6.0.2,referencing==0.36.2,resolvelib==1.0.1,rich==14.1.0,rpds-py==0.27.0,selinux==0.3.0,subprocess-tee==0.4.2,typing_extensions==4.14.1,wcmatch==10.1
py39-ansible210 run-test-pre: PYTHONHASHSEED='69510204'
py39-ansible210 run-test: commands[0] | molecule test -s light --destroy always
WARNING  Driver podman does not provide a schema.
INFO     light scenario test matrix: dependency, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun with role_name_check=0...
ERROR    CompletedProcess(args=['ansible-galaxy', 'collection', 'list', '--format=json'], returncode=250, stdout='the full traceback was:\n\nTraceback (most recent call last):\n  File "/opt/vector_role/.tox/py39-ansible210/bin/ansible-galaxy", line 92, in <module>\n    mycli = getattr(__import__("ansible.cli.%s" % sub, fromlist=), myclass)\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/cli/galaxy.py", line 24, in <module>\n    from ansible.galaxy.collection import (\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/collection/__init__.py", line 90, in <module>\n    from ansible.galaxy.collection.concrete_artifact_manager import (\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/collection/concrete_artifact_manager.py", line 30, in <module>\n    from ansible.galaxy.api 
import should_retry_error\nImportError: cannot import name \'should_retry_error\' from \'ansible.galaxy.api\' (/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/api.py)\n', stderr="ERROR! Unexpected Exception, this is probably a bug: cannot import name 'should_retry_error' from 'ansible.galaxy.api' (/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/api.py)\n")
Traceback (most recent call last):
  File "/opt/vector_role/.tox/py39-ansible210/bin/molecule", line 8, in <module>
    sys.exit(main())
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/core.py", line 1161, in __call__    return self.main(*args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/core.py", line 1082, in main    
    rv = self.invoke(ctx)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/core.py", line 1697, in invoke  
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/core.py", line 1443, in invoke  
    return ctx.invoke(self.callback, **ctx.params)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/core.py", line 788, in invoke
    return __callback(*args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/click/decorators.py", line 33, in new_func
    return f(get_current_context(), *args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/molecule/command/test.py", line 113, in test
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args)
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/molecule/command/base.py", line 113, in execute_cmdline_scenarios
    scenario.config.runtime.prepare_environment(
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible_compat/runtime.py", line 726, 
in prepare_environment
    self.load_collections()
  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible_compat/runtime.py", line 295, 
in load_collections
    raise RuntimeError(msg)
RuntimeError: Unable to list collections: CompletedProcess(args=['ansible-galaxy', 'collection', 'list', '--format=json'], returncode=250, stdout='the full traceback was:\n\nTraceback (most recent call last):\n  File "/opt/vector_role/.tox/py39-ansible210/bin/ansible-galaxy", line 92, in <module>\n    mycli = getattr(__import__("ansible.cli.%s" % sub, fromlist=[myclass]), myclass)\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/cli/galaxy.py", line 24, in <module>\n    from ansible.galaxy.collection import (\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/collection/__init__.py", line 90, in <module>\n    from ansible.galaxy.collection.concrete_artifact_manager import (\n  File "/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/collection/concrete_artifact_manager.py", line 30, in <module>\n    from ansible.galaxy.api import should_retry_error\nImportError: cannot import name \'should_retry_error\' from \'ansible.galaxy.api\' (/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/api.py)\n', stderr="ERROR! Unexpected Exception, this is probably a bug: cannot import name 'should_retry_error' from 'ansible.galaxy.api' (/opt/vector_role/.tox/py39-ansible210/lib/python3.9/site-packages/ansible/galaxy/api.py)\n")
ERROR: InvocationError for command /opt/vector_role/.tox/py39-ansible210/bin/molecule test -s light --destroy always (exited with code 1)
py39-ansible30 installed: ansible==3.0.0,ansible-base==2.10.17,ansible-compat==24.10.0,ansible-core==2.15.13,attrs==25.3.0,bracex==2.6,cffi==1.17.1,click==8.1.8,click-help-colors==0.9.4,cryptography==45.0.6,distro==1.9.0,enrich==1.2.7,importlib-resources==5.0.7,Jinja2==3.1.6,jmespath==1.0.1,jsonschema==4.25.1,jsonschema-specifications==2025.4.1,lxml==6.0.0,markdown-it-py==3.0.0,MarkupSafe==3.0.2,mdurl==0.1.2,molecule==6.0.3,molecule-podman==2.0.3,packaging==25.0,pluggy==1.6.0,pycparser==2.22,Pygments==2.19.2,PyYAML==6.0.2,referencing==0.36.2,resolvelib==1.0.1,rich==14.1.0,rpds-py==0.27.0,selinux==0.3.0,subprocess-tee==0.4.2,typing_extensions==4.14.1,wcmatch==10.1 
py39-ansible30 run-test-pre: PYTHONHASHSEED='69510204'
py39-ansible30 run-test: commands[0] | molecule test -s light --destroy always
WARNING  Driver podman does not provide a schema.
INFO     light scenario test matrix: dependency, cleanup, destroy, syntax, create, prepare, converge, idempotence, side_effect, verify, cleanup, destroy
INFO     Performing prerun with role_name_check=0...
ERROR    CompletedProcess(args=['ansible-galaxy', 'collection', 'list', '--format=json'], returncode=250, stdout='the full traceback was:\n\nTraceback (most recent call last):\n  File "/opt/vector_role/.tox/py39-ansible30/bin/ansible-galaxy", line 92, in <module>\n    mycli = getattr(__import__("ansible.cli.%s" % sub, fromlist=), myclass)\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/cli/galaxy.py", line 24, 
in <module>\n    from ansible.galaxy.collection import (\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/collection/__init__.py", line 90, in <module>\n    from ansible.galaxy.collection.concrete_artifact_manager import (\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/collection/concrete_artifact_manager.py", line 30, in <module>\n    from ansible.galaxy.api import should_retry_error\nImportError: cannot import name \'should_retry_error\' from \'ansible.galaxy.api\' (/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/api.py)\n', stderr="ERROR! Unexpected Exception, this is probably a bug: cannot import name 'should_retry_error' from 'ansible.galaxy.api' (/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/api.py)\n")
Traceback (most recent call last):
  File "/opt/vector_role/.tox/py39-ansible30/bin/molecule", line 8, in <module>
    sys.exit(main())
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/core.py", line 1161, in __call__ 
    return self.main(*args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/core.py", line 1082, in main     
    rv = self.invoke(ctx)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/core.py", line 1697, in invoke   
    return _process_result(sub_ctx.command.invoke(sub_ctx))
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/core.py", line 1443, in invoke   
    return ctx.invoke(self.callback, **ctx.params)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/core.py", line 788, in invoke    
    return __callback(*args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/click/decorators.py", line 33, in new_func
    return f(get_current_context(), *args, **kwargs)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/molecule/command/test.py", line 113, in test
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args)
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/molecule/command/base.py", line 113, in execute_cmdline_scenarios
    scenario.config.runtime.prepare_environment(
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible_compat/runtime.py", line 726, in prepare_environment
    self.load_collections()
  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible_compat/runtime.py", line 295, in load_collections
    raise RuntimeError(msg)
RuntimeError: Unable to list collections: CompletedProcess(args=['ansible-galaxy', 'collection', 'list', '--format=json'], returncode=250, stdout='the full traceback was:\n\nTraceback (most recent call last):\n  File "/opt/vector_role/.tox/py39-ansible30/bin/ansible-galaxy", line 92, in <module>\n    mycli = getattr(__import__("ansible.cli.%s" % sub, fromlist=[myclass]), myclass)\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/cli/galaxy.py", line 24, in <module>\n    from ansible.galaxy.collection import (\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/collection/__init__.py", line 90, in <module>\n    from ansible.galaxy.collection.concrete_artifact_manager import (\n  File "/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/collection/concrete_artifact_manager.py", line 30, in 
<module>\n    from ansible.galaxy.api import should_retry_error\nImportError: cannot import name \'should_retry_error\' from \'ansible.galaxy.api\' (/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/api.py)\n', stderr="ERROR! Unexpected Exception, this is probably a bug: cannot import name 'should_retry_error' from 'ansible.galaxy.api' (/opt/vector_role/.tox/py39-ansible30/lib/python3.9/site-packages/ansible/galaxy/api.py)\n")
ERROR: InvocationError for command /opt/vector_role/.tox/py39-ansible30/bin/molecule test -s light --destroy always (exited with code 1)
___________________________________________________ summary ____________________________________________________  
py37-ansible210: commands succeeded
  py37-ansible30: commands succeeded
ERROR:   py39-ansible210: commands failed
ERROR:   py39-ansible30: commands failed
[root@8d4ea73e0183 vector_role]# 

```
</details>

Для py39 надо перебирать рабочую комбинацию пакетов.

Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

[ссылка на 1.0.2](https://github.com/vladmgb/hw-ansible-test-roles/releases/tag/v1.0.2)


