# Ansible Server Setup and Configuration

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
   sudo apt install ansible
### 2. Configure Ansible Hosts File
 1. Open the Ansible hosts file:
   ```bash
      sudo nano /etc/ansible/hosts
2. Define your server groups and IP addresses. For example:
![image](https://github.com/user-attachments/assets/be7ca4a9-7981-4ede-922f-75b237bd6d4d)

Replace your_server_ip1 and your_server_ip2 with actual server IP addresses.
Set the appropriate ansible_user and ansible_ssh_private_key_file if needed.
3. Configure Ansible Configuration File (Optional)
Open the Ansible configuration file:
bash
Copy code
sudo nano /etc/ansible/ansible.cfg
Update or uncomment the following settings as needed:
ini
Copy code
[defaults]
inventory = /etc/ansible/hosts
remote_user = your_default_user
private_key_file = /path/to/your/ssh-key.pem
host_key_checking = False
Inventory: Specifies the path to the hosts file.
remote_user: Default user for SSH connections.
private_key_file: Specifies the SSH key path.
host_key_checking: Disables SSH host key checking for easier initial setup.
4. Test Connection to Servers
Test the connection to the servers with Ansible:

bash
Copy code
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
