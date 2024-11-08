# Ansible Server Setup and Configuration

![Ansible Logo](https://upload.wikimedia.org/wikipedia/commons/0/05/Ansible_Logo.png)

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

   sudo apt update
2. Install Ansible

   sudo apt install ansible  
### 2. Configure Ansible Hosts File
        sudo nano /etc/ansible/hosts
    Define your server groups and IP addresses. For example:
![alt text](image.png)

### 3. Test Connection to Server
    Test the connection to the servers with Ansible:
        ansible servers -m ping
### 4. Set Up SSH Key Permissions
    If using an SSH key pair, ensure it has the correct permissions:
    chmod 600 /path/to/your/"your-key-name".pem
### 5. Run Ansible Commands and Playbooks
    Navigate to your playbooks directory and create or execute Ansible playbooks as needed.
    Key Commands and Playbook Execution
    Create Playbook Directory: Organize your playbooks:

    mkdir playbooks
    cd playbooks
    Create and Run Playbooks:
    ansible-playbook multiserver_configuration.yml



### Useful Tips
- Use ansible-inventory --list -y to check your inventory configuration.
- Ensure all server IPs in the hosts file are accessible over SSH.
- Customize your playbooks as needed for more advanced tasks or software installations.
### Troubleshooting
- Verify SSH connections to the servers.
- Ensure Ansible is installed correctly and is the latest version.
- Check that playbooks have the correct syntax and paths to files (e.g., website content files).
- This guide provides a quick and structured approach to using Ansible for server configuration. For advanced setups, refer to Ansible's official documentation.