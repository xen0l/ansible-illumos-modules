# Ansible modules for managing Solarish systems

This repository contains modules for managing certain aspects of Solarish systems. There are plans to bring these modules into [ansible-modules-extra](https://github.com/ansible/ansible-modules-extras) repository in the future. These modules are developed under [OpenIndiana](http://www.openindiana.org) or [SmartOS](http://www.smartos.org). Modules are also known to work on [Oracle Solaris](https://www.oracle.com/solaris/solaris11/index.html).

So far, following modules have been developed:

## Solaris/illumos networking
- ~~[dladm_etherstub](https://github.com/xen0l/ansible-illumos/blob/master/library/dladm_etherstub) - Manage etherstubs on Solaris/illumos systems.~~ (already upstreamed)
- ~~[dladm_vnic](https://github.com/xen0l/ansible-illumos/blob/master/library/dladm_vnic) - Manage VNICs on Solaris/illumos systems.~~ (already upstreamed)
- ~~[dladm_iptun](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/dladm_iptun.py) - manage IP tunnel interfaces on Solaris/illumos systems.~~ (already upstreamed)
- ~~[dladm_vlan](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/dladm_vlan.py) - manage VLAN links on Solaris/illumos systems~~ (already upstreamed)
- ~~[dladm_linkprop](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/dladm_linkprop.py) - manage link properties on Solaris/illumos systems.~~ (already upstreamed)
- ~~[ipadm_addr](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/ipadm_addr.py) - manage IP addresses on Solaris/illumos systems.~~ (already upstreamed)
- ~~[ipadm_addrprop](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/ipadm_addrprop.py) - manage IP address properties on Solaris/illumos systems.~~ (already upstreamed)
- ~~[ipadm_if](https://github.com/xen0l/ansible-illumos/blob/master/library/ipadm_if) - Manage IP interfaces  on Solaris/illumos systems.~~ (already upstreamed)
- ~~[ipadm_ifprop](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/ipadm_ifprop.py) - manage interface properties on Solaris/illumos systems.~~ (already upstreamed)
- ~~[ipadm_prop](https://github.com/xen0l/ansible-illumos/blob/master/library/ipadm_prop) - Manage protocol properties on Solaris/illumos systems.~~ (already upstreamed)
- ~~[flowadm](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/flowadm.py) -  Manage bandwidth resource control and priority for protocols, services and zones.~~ (already upstreamed)

## Solaris/illumos processes
- [solaris_project](https://github.com/xen0l/ansible-illumos/blob/master/library/solaris_project) - Manage Solaris/illumos projects

## ZFS datasets and pools
- ~~[zfs_facts](https://github.com/xen0l/ansible-illumos/blob/master/library/zfs_facts.py) - Gather facts about ZFS datasets.~~ (already upstreamed)
- ~~[zpool_facts](https://github.com/xen0l/ansible-illumos/blob/master/library/zpool_facts.py) - Gather facts about ZFS pools.~~ (already upstreamed)

## Boot Environments
- ~~[beadm](https://github.com/xen0l/ansible-illumos-modules/blob/master/library/beadm.py) - manage ZFS boot environments on Solaris/illumos/FreeBSD systems.~~ (already upstreamed)

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
- dladm_bridge - manage bridges on Solaris/illumos systems
- routeadm - manage IP forwarding and routing configuration on Solaris/illumos systems

### System
- coreadm - core file administration
- dumpadm - configure operating system crash dump
- ldom_facts - gather facts about LDOMs
- kstat_facts - query kstats for facts

### Storage
- zpool - manage (Open)ZFS pools on Linux/FreeBSD/Solaris/illumos systems

### Logging
- logadm - manage log rotations on Solaris/illumos systems

### SMF
- smf_property - manage SMF properties on Solaris/illumos systems
- smf_manifest - manage SMF manifests on Solaris/illumos systems
- smf_instance - manage SMF instances on Solaris/illumos systems

### Boot Environments
- beadm_facts - get facts about boot environments on Solaris/illumos/FreeBSD systems

### IPS
- pkg5_mediator - manage IPS mediators on Solaris/illumos systems

### Other ideas
I am also open to new ideas for modules and collaboration.

## SmartOS
In the future, I might also develop modules for [SmartOS](http://www.smartos.org). However, I am not using it on a daily basis nowadays, so development might lag.

### Networking
- nictagadm - manage nic tags on SmartOS systems

