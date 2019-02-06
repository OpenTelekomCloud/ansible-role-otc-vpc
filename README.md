VPC role for Open Telekom Cloud 
===============================

An Ansible role to create a VPC for the Open Telekom Cloud with a
network and a subnet.

About VPCs
----------

A VPC (virtual private cloud) is an abstraction of an independent
networking namespace in the Open Telekom Cloud. In general, it
consists of an IP address space that is divided into smaller subnets
and that is connected via a router to other networks, most importantly
the Internet. It is possible to create several VPCs within one domain
or project.


Requirements
------------

It is required to have
[openstacksdk](https://docs.openstack.org/openstacksdk/latest/)
installed on the execution host. Valid credentials to connect to the
Open Telekom Cloud need to be in place. This role is compatible with
any Ansible version. If `openstacksdk` has a version before 0.15,
`enable_snat` will be disabled and there is no possibility to
re-enable it from Ansible (only CLI or UI).

Role Variables
--------------

Available variables are listed below along with default values (see `defaults/main.yml`):
  # Use prefix for resource naming (when using default naming constructions)
  prefix: test-

  # Define router name to be used:
  router_name: "{{ (prefix + router_name_suffix) }}"

  # Network name:
  network_name: "{{ (prefix + network_name_suffix) }}"

  # Subnet name:
  subnet_name: "{{ (prefix + subnet_name_suffix) }}"

  # Default subnet CIDR
  subnet_cidr: "192.168.110.0/24"

  # Default DNS servers:
  subnet_dns_servers: "{{ ['100.125.4.25', '8.8.8.8'] }}"

  # State (`present` for creation, `absent` for deletion)
  state: present


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users, too:

    - hosts: localhost
      roles:
         - otc_vpc

Cleanup of the VPC is as easy as its creation. For that a variable 'state': 'absent' should be passed:

    - hosts: localhost
      roles:
        - { role: otc_vpc, state: 'absent'}

License
-------

Apache

Author Information
------------------

Ecosystem Squad at Open Telekom Cloud <TBD@telekom.com>

