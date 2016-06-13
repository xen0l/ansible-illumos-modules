# Ansible modules for managing Solarish systems

This repository contains modules for managing certain aspects of Solarish systems. There are plans to bring these modules into [ansible-modules-extra](https://github.com/ansible/ansible-modules-extras) repository in the future. These modules are developed under [OpenIndiana](http://www.openindiana.org) or [SmartOS](http://www.smartos.org). Modules are also known to work on [Oracle Solaris](https://www.oracle.com/solaris/solaris11/index.html).

So far, following modules have been developed:

## Solaris/illumos networking
- [dladm_etherstub](https://github.com/xen0l/ansible-illumos/blob/master/library/dladm_etherstub) - Manage etherstubs on Solaris/illumos systems.
- [dladm_vnic](https://github.com/xen0l/ansible-illumos/blob/master/library/dladm_vnic) - Manage VNICs on Solaris/illumos systems.
- [ipadm_addr](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/ipadm_addr.py) - manage IP addresses on Solaris/illumos systems.
- [ipadm_if](https://github.com/xen0l/ansible-illumos/blob/master/library/ipadm_if) - Manage IP interfaces  on Solaris/illumos systems.
- [ipadm_prop](https://github.com/xen0l/ansible-illumos/blob/master/library/ipadm_prop) - Manage protocol properties on Solaris/illumos systems.

## Solaris/illumos processes
- [solaris_project](https://github.com/xen0l/ansible-illumos/blob/master/library/solaris_project) - Manage Solaris/illumos projects

## SmartOS
- ~~[smartos_image_facts](https://github.com/ansible/ansible-modules-extras/blob/devel/cloud/smartos/smartos_image_facts.py) - Get SmartOS image details.~~ (already upstreamed)
- [smartos_image_source](https://github.com/xen0l/ansible-illumos/blob/master/library/smartos_image_source) - Manage image sources on SmartOS compute nodes.

# How to install
Download desired modules and place it under library/ directory in your ansible repository.

# Future development and desired modules
I plan to develop more modules. The list of following modules, which I will be working on in the near future:

## Solaris/illumos
### Networking
- dladm_aggr - manage link aggregations on Solaris/illumos systems
- dladm_linkprop - manage link properties on Solaris/illumos systems
- ipadm_ifprop - manage interface properties on Solaris/illumos systems
- ipadm_addrprop - manage IP address properties on Solaris/illumos systems
- flowadm_flow - manage flows on Solaris/illumos systems
- flowadm_flowprop - manager flow properties on Solaris/illumos systems

### Logging
- logadm - manage log rotations on Solaris/illumos systems

### SMF
- svccfg - manage SMF properties on Solaris/illumos systems

### Boot Environments
- beadm - manage ZFS boot environments on Solaris/illumos/FreeBSD systems

### IPS
- pkg5_mediator - manage IPS mediators on Solaris/illumos systems

### Other ideas
I am also open to new ideas for modules and collaboration.

## SmartOS
In the future, I might also develop modules for [SmartOS](http://www.smartos.org). However, I am not using it on a daily basis nowadays, so development might lag.

### Networking
- nictagadm - manage nic tags on SmartOS systems

