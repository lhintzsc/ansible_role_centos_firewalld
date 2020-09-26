Role Name
=========

This role allows to open service ports for firewalld.

Requirements
------------

For this role you will need a VM based on CentOS 7. Further firewalld must be installed.

Role Variables
--------------

The variables are used to define service ports that should be opened using firewalld:

```
firewalld:
    service_path: location of the firewalld service definitions (e.g. /usr/lib/firewalld/services)
    services:
        service: short service name (e.g. custom-http)
        description: service description (e.g. Custom HTTP for my Service)
        port: service port (e.g. 8090)
        protocol: service protocol (e.g. tcp or udp)
```

The service definition will be created using the template/port_service.xml.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Add the role to a requirements.yml:

```
- src: https://github.com/lhintzsc/ansible_role_centos_firewalld.git
  version: master
  name: centos firewalld
```

Install the role using:

```
ansible-galaxy install -r requirements.yml
``

Use the variables to define a custom http and https port:
```
firewalld:
  service_path: "/usr/lib/firewalld/services"
  services: # can be multiple lines
    - { service: "custom-http", description: "Custom HTTP for my Service", port: "9080", protocol: tcp }
    - { service: "custom-https", description: "Custom HTTPS for my Service", port: "8443", protocol: tcp }
```

Use the role in your playbook

```
    - hosts: servers
      roles:
         - centos firewalld
```

Related Links
-------

https://docs.ansible.com/ansible/latest/galaxy/user_guide.html

License
-------

GNU

Author Information
------------------
lhintzsc@cisco.com
# ansible_role_centos_firewalld
