CrowdStrike_Falcon
=========

This Ansible role installs the CrowdStrike Falcon agent on Windows and RHEL6/RHEL7 virtual machines.

![ALT TEXT](http://1.bp.blogspot.com/-TIzivoi3R38/VX7lm0C1QkI/AAAAAAAAA3Y/DtsVH26o1CI/s1600/star-fox-space-crew.jpg)

Requirements
------------

For Windows hosts the WinRM package is utilized, so it must be installed. I recommend the following Ansible Guide:
- https://docs.ansible.com/ansible/2.5/user_guide/windows_setup.html#winrm-setup

Role Variables
--------------

```
# Global
csf_customer_id: "CrowdStrike Customer ID" 

# Windows related variables
csf_windows:
  - pkg_checksum: "Checksum"
  - pkg_url: "Package URL"
  - product_id: "Product ID"

# RHEL 7 related variables
csf_rhel7:
  - pkg_checksum: "Checksum"
  - pkg_url: "Package URL"

# RHEL 6 related variables
csf_rhel6:
  - pkg_checksum: "Checksum"
  - pkg_url: "Package URL"

# Suse 11 related variables
csf_suse11:
  - pkg_checksum: "Checksum"
  - pkg_url: "Package URL"

# Suse 12 related variables
csf_suse12:
  - pkg_checksum: "Checksum"
  - pkg_url: "Package URL"
```

Dependencies
------------

- Ansible 2.5+
- Python 2.7x/3x
- WinRM
- Windows/RHEL7

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```
- name: agents
  hosts: all
  gather_facts: true

  vars:
    ansible_connection: winrm
    ansible_user: admin
    ansible_password: password
    ansible_port: 5985
    ansible_winrm_scheme: http
    ansible_winrm_transport: kerberos
    ansible_winrm_server_cert_validation: ignore

  roles:
    - role: crowdstrike_falcon
```

File Tree
-------

```
.
├── README.md
├── defaults
│   └── main.yml
├── handlers
│   └── main.yml
├── meta
│   └── main.yml
├── molecule
│   └── default
│       ├── Dockerfile.j2
│       ├── INSTALL.rst
│       ├── molecule.yml
│       ├── playbook.yml
│       └── tests
│           ├── test_default.py
│           └── test_default.pyc
├── tasks
│   ├── main.yml
│   ├── redhat.yml
│   └── windows.yml
├── tests
│   ├── inventory
│   └── test.yml
└── vars
    └── main.yml
```


Author Information
------------------

- Andrew Kuttor
- andrew.kuttor@gmail.com
