# Ansible roles and playbooks
## Changing multiple configuration files

```yml
- name: Change each file over that matches the given pattern
  lineinfile:
    path: "{% raw %}{{item}}{% endraw %}"
    state: present
    regexp: '^pid\.1\='
    line: 'pid.1=test'
  with_fileglob:
    - "h*.conf"
```
