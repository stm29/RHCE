## RHCE
### Control Node
- # ansible.cfg 
  - [defaults]
  - roles_path=
  - inventory=
  - [privilege_escalation]
  - become=true
  - Inventory
  - server[a:f].lab.example.com
- ansible all -a id
- ansible all -m shell -a “command” -b -K -s
- # Roles  
  - ansible-galaxy install -r req.yml -p roles
  - ansible-galaxy init roles/apache
- # Handlers - 
  - notify: - can be placed in any tasks
  - handlers: 
    - name: same as “notify: name”
  - debug: - needs “listen” attribute to work in case of handlers
- # Jinja2 files -
  - {%for host in groups.all%}
  - {{hostvars[host].ansible_hostname}}
  - {%endfor%}
  - when: inventory_hostname in groups.dev
- # vars_files:
 - import_tasks: & include_tasks:
 - import_playbook: & include_playbook:
 - ansible-vault create file.yml --ask-vault-pass
 - ansible-vault create file.yml --vault-password-file
 - ansible-vault rekey file.yml
- ## Modules
 - yum_repository
 - user,group
 - service
 - firewald
 - files
 - replace
 - Copy
 - # Block
 - # Rescue
 - # Always
