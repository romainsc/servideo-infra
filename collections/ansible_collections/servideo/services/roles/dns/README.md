DNS server for Servidéo
=========

## References

- Based on [Core DNS](https://coredns.io/)
- Built on top of the [Red Hat CoreDNS Container distribution](https://catalog.redhat.com/software/containers/rhacm1-tech-preview/coredns-rhel8/5ea9b377bed8bd66f8426bf4)
- [Chapter 4. Running Containers as systemd Services with Podman Red Hat Enterprise Linux Atomic Host 7 | Red Hat Customer Portal](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_atomic_host/7/html/managing_containers/running_containers_as_systemd_services_with_podman)
- [Building, running, and managing containers Red Hat Enterprise Linux 8 | Red Hat Customer Portal](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/building_running_and_managing_containers/index)

## Service logic

- run as non priviledged user

- Expose port 1053 (`-p 1053:1053/udp` is your friend)

- Runned via systemd

- Deployed via the [podman_container_systemd role](https://galaxy.ansible.com/ikke_t/podman_container_systemd)

## Requirements

* containers.podman

* ikke_t.podman_container_systemd

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

# 
