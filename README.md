Role Name
=========

This role opens service ports for firewalld.

Requirements
------------

This role works for VMs based on 

* CentOS 7

Firewalld must be installed on those VMs.

Role Variables
--------------

The variables are used to define service ports:

```
{{ firewalld.service_path }}: location of the firewalld service definitions (e.g. /usr/lib/firewalld/services)
{{ firewalld.services.service }}: short service name (e.g. custom-http)
{{ firewalld.services.description }}: service description (e.g. Custom HTTP for my Service)
{{ firewalld.services.port }}: service port (e.g. 8090)
{{ firewalld.services.protocol }}: service protocol (e.g. tcp or udp)
```

The services are defined and configured per host using template/port_service.xml.

Dependencies
------------

No other role dependency.

Example Playbook
----------------

Add the role to a requirements.yml:

```
- src: https://github.com/lhintzsc/ansible_role_centos_firewalld.git
  version: master
  name: centos firewalld
```

Install the role:

```
ansible-galaxy install -r requirements.yml
```

Set the variables to define services such as a custom http and https port:

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

[How to install roles using requirements file](https://docs.ansible.com/ansible/latest/galaxy/user_guide.html)

License
-------

MIT

Author Information
------------------
lhintzsc@cisco.com
