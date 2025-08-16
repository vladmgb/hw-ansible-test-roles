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
7. Запустите тестирование роли повторно и проверьте, что оно прошло успешно.
8. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

## Tox
Добавьте в директорию с vector-role файлы из директории.
Запустите docker run --privileged=True -v <path_to_repo>:/opt/vector-role -w /opt/vector-role -it aragast/netology:latest /bin/bash, где path_to_repo — путь до корня репозитория с vector-role на вашей файловой системе.
Внутри контейнера выполните команду tox, посмотрите на вывод.
Создайте облегчённый сценарий для molecule с драйвером molecule_podman. Проверьте его на исполнимость.
Пропишите правильную команду в tox.ini, чтобы запускался облегчённый сценарий.
Запустите команду tox. Убедитесь, что всё отработало успешно.
Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.
После выполнения у вас должно получится два сценария molecule и один tox.ini файл в репозитории. Не забудьте указать в ответе теги решений Tox и Molecule заданий. В качестве решения пришлите ссылку на ваш репозиторий и скриншоты этапов выполнения задания.

