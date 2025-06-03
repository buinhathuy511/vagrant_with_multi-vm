# Vagrant Multi-VM Environment

This project provides an automated development environment with multiple virtual machines using Vagrant and VirtualBox. Each VM comes with NGINX installed and can be customized through environment variables.

## System Requirements

- [Vagrant](https://www.vagrantup.com/downloads) (version 2.4.6 recommended)
- [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (version 7.1.4 recommended)

## Required Plugin

Before starting, install the hostmanager plugin:

```bash
vagrant plugin install vagrant-hostmanager
```

## Installation

1. Clone repository:

```bash
git clone https://github.com/your-username/vagrant_with_multi-vm.git
cd vagrant_with_multi-vm
```

2. Create `.env` file:

```bash
cp .env.example .env
```

## Configuration

You can customize the following parameters in the `.env` file:

- `VM_COUNT`: Number of virtual machines
- `VM_BOX`: Vagrant box to use
- `VM_RAM`: RAM allocation for each VM (MB)
- `VM_CPU`: Number of CPU cores for each VM
- `VM_PREFIX`: VM name prefix
- `VM_BASE_IP`: Base IP for private network

## Usage

1. Start the environment:

```bash
vagrant up
```

2. SSH into a specific VM:

```bash
vagrant ssh web1  # Replace web1 with the VM name you want to access
```

3. Stop the environment:

```bash
vagrant halt
```

4. Remove the environment:

```bash
vagrant destroy
```

## Project Structure
```
├── README.md # Project documentation
├── Vagrantfile # Main Vagrant configuration file
├── provision.sh # Automated installation script (NGINX)
├── .env.example # Example environment variables
└── .env # Environment configuration (create from .env.example)
```
## Features

- Automatic creation of multiple identical VMs
- NGINX pre-installed on each VM
- Automatic hostname management
- Pre-configured private network
- Easy customization through environment variables

## Important Notes

- The hostmanager plugin works best with Vagrant version 2.4.6 and VirtualBox version 7.1.4
- Make sure to create your `.env` file from `.env.example` before running `vagrant up`
- Each VM will be accessible via its hostname (configured through hostmanager)
