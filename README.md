OpenTelekomCloud VPC role
=========================

A quick role to create VPC with network and subnet.

Requirements
------------

It is required, that openstacksdk is installed on the execution host and connection to the OTC is provided. If openstacksdk has a version before 0.15
`enable_snat` will be disabled and there is no possibility to re-enable it from Ansible (only CLI or UI).

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):
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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      roles:
         - otc_vpc

Cleanup of the router is as easy, as it's creation. For that a variable 'state': 'false' should be passed:

    - hosts: localhost
      roles:
        - { role: otc_vpc, state: 'absent'}

License
-------

Apache

Author Information
------------------

OpenTelekomCloud
