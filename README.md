# adburchfie42-csc2510-infrastructure
# CSC 2510 - DevOps Lab 12: Ansible I

This repository contains the files and configurations for automating the installation and configuration of Apache, as well as deploying a custom `index.html` file using Ansible. The goal of this lab is to familiarize students with Ansible's capabilities for automating server management tasks.

## Repository Structure

```
<repository root>/
│ 
├── ansible_inventory/
│   └── inventory.yml
│
├── files/
│   ├── config/
│   │   └── apache.conf
│   │
│   └── site/
│       └── index.html
│
├── ansible.cfg
└── webserver_playbook.yml
```

### Description of Files

- **ansible_inventory/inventory.yml**
  - This file contains the inventory of servers that Ansible will manage. It includes the `webservers` group with the internal IP address of your Ansible VM.

- **files/config/apache.conf**
  - The configuration file for the Apache web server. This file will be copied to the appropriate location on the managed servers.

- **files/site/index.html**
  - A simple HTML file to be served by the Apache web server. This file will be copied to the web server's document root.

- **ansible.cfg**
  - The Ansible configuration file that sets the default inventory location, disables host key checking, and specifies the private key file for SSH connections.

- **webserver_playbook.yml**
  - The main Ansible playbook that performs the following tasks:
    - Updates the APT package cache.
    - Installs the `python-apt` and `apache2` packages.
    - Copies the `index.html` file to the web server's document root.
    - Copies the `apache.conf` file to the appropriate location.
    - Creates a symbolic link for the Apache headers module.
    - Restarts the Apache service.

## Running the Playbook

To run the Ansible playbook and configure your web server, use the following command:

```bash
ansible-playbook webserver_playbook.yml
```

Ensure that you have established SSH connections between your primary VM and the Ansible VM, and that the necessary SSH keys are properly configured.

## Additional Information

- **Ansible Roles**
  - Ansible roles are a way to organize and package Ansible automation content in a reusable and modular format. Roles encapsulate a set of tasks, variables, handlers, files, and many other things. They enhance scalability, maintainability, and shareability.
  
- **Alternative IaC Tools**
  - Terraform
  - Pulumi
  - Chef

## Troubleshooting

- If you encounter SSH connection issues, try restarting your VMs.
- Ensure that your YAML files are properly formatted (avoid using tabs for indentation).
- Verify that you are running the Ansible commands from the correct directory.


