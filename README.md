OpenTelekomCloud VPC role
=========================

A quick role to create VPC with network and subnet.

Requirements
------------

It is required, that openstacksdk is installed on the execution host and connection to the OTC is provided. If openstacksdk has a version before 0.15
`enable_snat` will be disabled and there is no possibility to re-enable it from Ansible (only CLI or UI).

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: localhost
      roles:
         - otc-vpc

Cleanup of the router is as easy, as it's creation. For that a variable 'state': 'false' should be passed:

    - hosts: localhost
      roles:
        - { role: otc-vpc, state: 'absent'}

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
