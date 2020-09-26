Role Name
=========

This role allows to open service ports for firewalld.

Requirements
------------

For this role you will need a VM based on CentOS 7. Further firewalld must be installed.

Role Variables
--------------

The variables are used to define service ports that should be opened using firewalld:

firewalld:
    service_path: location of the firewalld service definitions (e.g. /usr/lib/firewalld/services)
    services:
        service: short service name (e.g. custom-http)
        description: service description (e.g. Custom HTTP for my Service)
        port: service port (e.g. 8090)
        protocol: service protocol (e.g. tcp or udp)

The service definition will be created using the template/port_service.xml.

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
# ansible_role_centos_firewalld
