# Домашнее задание к занятию 5 «Тестирование roles»


## Основная часть

Ваша цель — настроить тестирование ваших ролей.
Задача — сделать сценарии тестирования для vector.
Ожидаемый результат — все сценарии успешно проходят тестирование ролей.

## Molecule
1. Запустите molecule test -s ubuntu_xenial (или с любым другим сценарием, не имеет значения) внутри корневой директории clickhouse-role, посмотрите на вывод команды. Данная команда может отработать с ошибками или не отработать вовсе, это нормально. Наша цель - посмотреть как другие в реальном мире используют молекулу И из чего может состоять сценарий тестирования.
```
vova@Mynote:/mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/clickhouse$ molecule test -s ubuntu_xenial
WARNING  Driver docker does not provide a schema.
CRITICAL Failed to validate /mnt/c/Users/Vova/hw-ansible-test-roles/playbook/roles/clickhouse/molecule/ubuntu_xenial/molecule.yml


Traceback (most recent call last):
  File "/home/vova/.local/bin/molecule", line 7, in <module>
    sys.exit(main())
             ^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1442, in __call__
    return self.main(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1363, in main        
    rv = self.invoke(ctx)
         ^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1830, in invoke      
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1226, in invoke      
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 794, in invoke       
    return callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/decorators.py", line 34, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/click_cfg.py", line 416, in wrapper
    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd         ^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1830, in invoke
    return _process_result(sub_ctx.command.invoke(sub_ctx))
                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1226, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 794, in invoke
    return callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/decorators.py", line 34, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/click_cfg.py", line 416, in wrapper       
    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test        
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd                           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 1226, in invoke
    return ctx.invoke(self.callback, **ctx.params)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 794, in invoke
    return callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/decorators.py", line 34, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/click_cfg.py", line 416, in wrapper       
    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test        
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/core.py", line 794, in invoke
    return callback(*args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/decorators.py", line 34, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/click_cfg.py", line 416, in wrapper       
    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test        
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/click/decorators.py", line 34, in new_func
    return f(get_current_context(), *args, **kwargs)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/click_cfg.py", line 416, in wrapper       
    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test        
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd    return func(ctx)
           ^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/test.py", line 81, in test        
    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd    base.execute_cmdline_scenarios(scenario_name, args, command_args, ansible_args, exclude)
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmd  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 151, in execute_cmdline_scenarios
line_scenarios
    configs.extend(get_configs(args, command_args, ansible_args, glob_str))
    configs.extend(get_configs(args, command_args, ansible_args, glob_str))
                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 425, in get_configs                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 425, in get_configs    config.Config(
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/command/base.py", line 425, in get_configs    config.Config(
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/config.py", line 133, in __init__
    self._validate()
    config.Config(
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/config.py", line 133, in __init__
    self._validate()
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/config.py", line 133, in __init__
    self._validate()
    self._validate()
  File "/home/vova/.local/share/pipx/venvs/molecule/lib/python3.12/site-packages/molecule/config.py", line 690, in _validate        
    raise MoleculeError(msg)
molecule.exceptions.MoleculeError
```
   

2. Перейдите в каталог с ролью vector-role и создайте сценарий тестирования по умолчанию при помощи molecule init scenario --driver-name docker.
3. Добавьте несколько разных дистрибутивов (oraclelinux:8, ubuntu:latest) для инстансов и протестируйте роль, исправьте найденные ошибки, если они есть.
4. Добавьте несколько assert в verify.yml-файл для проверки работоспособности vector-role (проверка, что конфиг валидный, проверка успешности запуска и др.).
5. Запустите тестирование роли повторно и проверьте, что оно прошло успешно.
6. Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.

## Tox
Добавьте в директорию с vector-role файлы из директории.
Запустите docker run --privileged=True -v <path_to_repo>:/opt/vector-role -w /opt/vector-role -it aragast/netology:latest /bin/bash, где path_to_repo — путь до корня репозитория с vector-role на вашей файловой системе.
Внутри контейнера выполните команду tox, посмотрите на вывод.
Создайте облегчённый сценарий для molecule с драйвером molecule_podman. Проверьте его на исполнимость.
Пропишите правильную команду в tox.ini, чтобы запускался облегчённый сценарий.
Запустите команду tox. Убедитесь, что всё отработало успешно.
Добавьте новый тег на коммит с рабочим сценарием в соответствии с семантическим версионированием.
После выполнения у вас должно получится два сценария molecule и один tox.ini файл в репозитории. Не забудьте указать в ответе теги решений Tox и Molecule заданий. В качестве решения пришлите ссылку на ваш репозиторий и скриншоты этапов выполнения задания.

