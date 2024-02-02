# Minecraft Server Ansible Role

This Ansible role is designed for the quick deployment and configuration of a Minecraft server. It simplifies the process of setting up a Minecraft server, allowing for easy customization and management of server settings and plugins.
Requirements

- Ansible 2.9 or higher.
- Target systems should be a Linux distribution compatible with the Minecraft server requirements (e.g., Debian 12).

# Features

- Automated Minecraft server installation.
- Easy plugin management.
- Customizable server properties.

# Getting Started
## Installing the Role

To use this role, clone it into your Ansible roles directory:

```bash
git clone https://github.com/boubik/LTP.git
cd LTP
```

or

```bash
ansible-galaxy install git+https://github.com/boubik/LTP.git
```

Installation may differ from the first option.

# Configuring Your Inventory

Edit the inventory.yaml file to include the target hosts where LTP will be deployed. For example:

```yml
all:
  hosts:
    server1:
      ansible_host: 192.168.1.100
    server2:
      ansible_host: 192.168.1.101
  vars:
    ansible_user: your_user
    ansible_ssh_private_key_file: /path/to/your/key
```

# Customizing Role Variables

Configure role-specific parameters in vars/main.yml to tailor the LTP deployment to your needs. Common settings include:

```yml
# java
java_version_debian: "openjdk-17-jdk"
java_executable_path: "/usr/lib/jvm/java-17-openjdk-amd64/bin/java"

# minecraft
minecraft_eula: true
minecraft_user: "minecraft"
minecraft_dir: "vanila-1.20.4"
...
```

## Configuring Plugins

To add plugins, list them in vars/main.yml including their download URLs or adding them to files/plugins. Example:

```yml
minecraft_plugin_urls:
  - "http://example.com/plugin/plugin1.jar"
  - "http://example.com/plugin/plugin2.jar"
  - "http://example.com/plugin/plugin3.jar"
```

# Running the Role

Create a playbook (e.g., mcPlaybook.yml) including the LTP (mc-1.20.4) role:

```yml
- name: Setup Minecraft Server
  hosts: vms
  become: yes
  roles:
    - mc-1.20.4
```

Execute the playbook using the following command:

```yml
ansible-playbook -i inventory.yaml mcPlaybook.yml
```

# Additional Configuration

Firewall Settings: Adjust your firewall settings to allow traffic on the Minecraft server port (default is 25565).

# Author Information

This role was created in 2024 by Jan Chlouba.
