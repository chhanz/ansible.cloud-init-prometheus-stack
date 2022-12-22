# ansible.cloud-init-prometheus-stack

This playbook is for installing Prometheus Stack on Amazon Linux 2 using Cloud-init.   

# Test Environment
* Amazon Linux 2   
* ansible-core: 2.11.12   

# Cloud-init Script
for cloud-init old version   
```
#cloud-config
packages_update: true
packages_upgrade: true
packages:
  - git
  - python2-pip

runcmd:
- [ pip, install, ansible ]
- [ ansible-pull, -U, "https://github.com/chhanz/ansible.cloud-init-prometheus-stack.git", -v, site.yml ]
```

for cloud-init latest version   
```
#cloud-config
packages_update: true
packages_upgrade: true
packages:
  - git
  - python2-pip

# for cloud-init v22.3.x or latest
# https://cloudinit.readthedocs.io/en/latest/topics/modules.html#module-cloudinit.config.cc_ansib
ansible:
  install_method: pip
  pull:
    url: "https://github.com/chhanz/ansible.cloud-init-prometheus-stack.git"
    playbook_name: site.yml
```   
