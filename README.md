# Ansible collection for using Weblogic Deploy Tooling (WDT)  

This collection contains [Weblogic Deploy Tooling (WDT)](https://github.com/oracle/weblogic-deploy-tooling) related Ansible roles maintained by [Yilmaz Guleryuz (zeusbaba)](https://beerstorm.net).  

It includes:  
- `zeusbaba.wdt_setup`  
- `zeusbaba.wdt_createdomain`    
- `zeusbaba.wdt_updatedomain`  
- `zeusbaba.wdt_discoverdomain`  


## Using this collection

Installing this collection locally:  
```
ansible-galaxy collection install zeusbaba.wdt -p ./collections  
```  
  
Then you can use the roles from the collection in your playbooks:  
```
---
- hosts: all

  collections:
    - zeusbaba.wdt

  roles:
    - wdt_setup
    - wdt_createdomain
    - wdt_updatedomain  
    - wdt_discoverdomain
```

Examples  
```
# this will install WDT into /home/wdt_user/weblogic-deploy  
- name: "setup WDT binaries using 'WDT_setup role'"
  import_role:
    name: wdt_setup
  vars:
    # NB! change if you want to override which WDT version will be installed
    # See https://github.com/oracle/weblogic-deploy-tooling/releases
    wdt_distribution_version: "1.9.20"
    wdt_user: zeus
    wdt_group: zeus
    

# This will discoverDomain of existing Weblogic installation    
# Successful run will yield wdt_archive_file and wdt_template_file which contains domain details as WDT template  
- name: Discover existing domain via WDT-offline
  import_role:
    name: wdt_discoverdomain
  vars:
    run_wdt_action: discover-domain-offline
    wdt_user: "zeus"
    wdt_group: "zeus"
    workdir: "/home/{{ wdt_user }}"
    java_home: "{{ workdir }}/mw/jdk1.8.0_281"
    mw_home: "{{ workdir }}/mw/Oracle_Home"
    domain_home: "{{ workdir }}/mw/domain/mywlsdomain"
    wdt_home: "{{ workdir }}/weblogic-deploy"
    wdt_templates_home: "{{ workdir }}/wdt-templates"
    wdt_archive_file: "WDT_template-discovered_offline.zip"
    wdt_template_file: "WDT_template-discovered_offline.yaml"

```

TODO: add example playbook for all Roles!!!  


## Contributing to this collection

Contributions are welcome.  
Fork [this repo](https://github.com/zeusbaba/ansible-collection-wdt), prepare your changes/fixes, then send a pull request.  


## Release notes

See the [changelog](https://github.com/ansible-collections/REPONAMEHERE/tree/main/CHANGELOG.rst).

## Licensing

GNU General Public License v3.0 or later.

See [LICENSE](https://www.gnu.org/licenses/gpl-3.0.txt) to see the full text.  

Attribution is welcome but not obligatory.  

=======
# Ansible Collection - zeusbaba.wdt

Documentation for the collection.

TBC...  
TODO: add example playbook!!!  
TODO: write a medium article explaining example setup with Ansible, docker etc  
