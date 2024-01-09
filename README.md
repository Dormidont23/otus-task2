## Занятие № 2. Первые шаги с Ansible ##

В корне системы был создан каталог Ansible, в котором создавались все остальные файлы и подкаталоги. Файл my.yml - это просто playbook без роли. Файл nginx.yml - это playbook на основе роли.

Для инициализации роли в каталоге **/Ansible/roles** была выполнена команда: **ansible-galaxy init nginx**. В результате чего была создана структура каталогов и файлов. Для  преобразования playbook'а в роль из файла my.yml были скопированы в файлы main.yml соответствующие части:
- Раздел handlers был скопирован в файл handlers/main.yml
- Раздел tasks - в файл tasks/main.yml
- Раздел vars - в файл vars/main.yml

Также был создан playbook (с ролью nginx) nginx.yml и выполнена команда:\
root@dazert:/Ansible# **ansible-playbook nginx.yml**

PLAY [Install nginx package] ***********************************************************************************************

TASK [Gathering Facts] *****************************************************************************************************\
ok: [otus-task2]

TASK [nginx : NGINX | Install EPEL Repo package from standart repo] ********************************************************\
changed: [otus-task2]

TASK [nginx : NGINX | Install NGINX package from EPEL Repo] ****************************************************************\
changed: [otus-task2]

TASK [nginx : NGINX | Create NGINX config file from template] **************************************************************\
changed: [otus-task2]

RUNNING HANDLER [nginx : restart nginx] ************************************************************************************\
changed: [otus-task2]

RUNNING HANDLER [nginx : reload nginx] *************************************************************************************\
changed: [otus-task2]

PLAY RECAP *****************************************************************************************************************\
otus-task2                 : ok=6    changed=5    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0   

root@dazert:/Ansible# **telnet 192.168.56.150 8080**\
Trying 192.168.56.150...\
Connected to 192.168.56.150.\
Escape character is '^]'.\
^]\
telnet> q\
Connection closed.

telnet на порт 8080 есть, следовательно задание выполнено.
