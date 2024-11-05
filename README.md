# Ansible Server Setup and Configuration

![Ansible Logo](https://example.com/path/to/ansible_logo.png)

This guide provides instructions for setting up and configuring servers using Ansible to:
- Install Nginx, Docker, and Git.
- Start and enable essential services.
- Apply security updates.
- Deploy a simple website.
- Configure SSL for secure HTTPS access.
## Prerequisites

- Ensure you have sudo privileges on your server.
- SSH access to all servers you plan to manage with Ansible.

## Initial Setup

### 1. Install Ansible

1. Update the system repository:
   ```bash
   sudo apt update
2. Install Ansible

   ```bash
   sudo apt install ansible  
### 2. Configure Ansible Hosts File
```bash
sudo nano /etc/ansible/hosts
    Define your server groups and IP addresses. For example:
![alt text](image.png)

### 3. Test Connection to Server
Test the connection to the servers with Ansible:
    ```bash 
    ansible servers -m ping
5. Set Up SSH Key Permissions
If using an SSH key pair, ensure it has the correct permissions:

bash
Copy code
chmod 600 /path/to/your/ssh-key.pem
6. Run Ansible Commands and Playbooks
Navigate to your playbooks directory and create or execute Ansible playbooks as needed.

Key Commands and Playbook Execution
Create Playbook Directory: Organize your playbooks:

bash
Copy code
mkdir playbooks
cd playbooks
Create and Run Playbooks: Write a playbook, such as for installing Nginx, then execute it:

bash
Copy code
vim nginx_install_play.yml
ansible-playbook nginx_install_play.yml
Deploy Website Playbook: Execute the deployment playbook:

bash
Copy code
ansible-playbook deploy_web_play.yml
Multi-Server Configuration Playbook: Configure multiple servers:

bash
Copy code
ansible-playbook multiserver_configuration.yml
System Update: Update packages on all managed servers:

bash
Copy code
ansible servers -a "sudo apt update"
Configuration Files
Ansible Hosts: /etc/ansible/hosts (for defining server groups and IPs)
Ansible Config: /etc/ansible/ansible.cfg (for specifying global settings)
Edit these files as needed to customize your Ansible setup.

Useful Tips
Use ansible-inventory --list -y to check your inventory configuration.
Ensure all server IPs in the hosts file are accessible over SSH.
Customize your playbooks as needed for more advanced tasks or software installations.
Troubleshooting
Verify SSH connections to the servers.
Ensure Ansible is installed correctly and is the latest version.
Check that playbooks have the correct syntax and paths to files (e.g., website content files).
This guide provides a quick and structured approach to using Ansible for server configuration. For advanced setups, refer to Ansible's official documentation.