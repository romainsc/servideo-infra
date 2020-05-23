# Infrastructure as code for Servidéo

Aka Servidéo 3.0

## Abstract

* 1 host

* many virtual machines to host:
  
  * RHOCP
  
  * RHEL 8 (if not in RHOCP CNV)

## Virtual Machines management

### Native KVM vs RHV/RHOSP

As stated in the [Chapter 20. Feature support and limitations in RHEL 8 virtualization Red Hat Enterprise Linux 8](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/configuring_and_managing_virtualization/feature-support-and-limitations-in-rhel8-virtualization_configuring-and-managing-virtualization#resource-allocation-limits-in-rhel8-virtualization_feature-support-and-limitations-in-rhel8-virtualization) from the Red Hat Customer Portal, only 4 VMs are supported at the same time on a RHEL 8 and also some virtualization features are not supported neither. Most of them are supported with RHV and others via RHOSP. KVM binaries are now the same in RHV and RHEL and RHOSP.

(un)fortunately, hosting RHOCP on VMs is not a supported setup. And all the features are available even if not supported. And everything will be managed with ansible.

Then, why bothering with another management VM (RHV-M) consuming resources.

Conclusion: Native KVM.

## Playbook house

<img src="doc/img/IaaC%20house.png" title="" alt="" width="363">

The playbooks are organized in collections with roles:

* **redhat**:
  Everything related to Red Hat specific action:
  
  * **insight**:
    
    * insight registration
    
    * remediation playbook.
  
  * **rhn**:
    
    * repositories & registration management

* **pinfra**:
  Everything related to the physical setup:
  
  * **volume**: extra storage setup not part of the SOE
  
  * **Additional Net IF**: extra net setup not part of the SOE
  
  * **certificate**: certificate management (Let’s Encrypt)

* **services**:
  Everything related to hosted services, whatever the hosting resources (hypervisor, VM, CNV or containers):
  
  * **VPN**: ?
  
  * **antispam**: 
  
  * **antivirus**
  
  * **mailing list**
  
  * **backup**: Backup software/capability only, the service backup and restore are in the service role.
  
  * **dns**
  
  * **dhcp**
  
  * **mails**
  
  * **ldap**
  
  * **nfs**
  
  * **pxe**
  
  * **httpd**
  
  * **wiki**
  
  * **redmine**
  
  * **webmail**

* **vinfra**:
  Everything related to the virtualization:
  
  * **virtualization**: everything to enable the hypervisor capabilities
  
  * **hypervisor__UI**: The cockpit related features
  
  * **network**: the SDN
  
  * **vm**: compute

Everything in blue is performed manually.
