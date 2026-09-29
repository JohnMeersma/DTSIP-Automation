# DTSIP Automation

This repository contains Ansible files used in the DTSIP course to automate Cisco IOS XE routers.

## Ubuntu Setup

### Step 1: Update Ubuntu

Update the local package list.

```bash
sudo apt update
```

### Step 2: Install Required Software

Install Git, Python, the Python virtual environment package, and pip.

```bash
sudo apt install -y git python3 python3-venv python3-pip
```

### Step 3: Download the DTSIP Automation Repository

Move to the home directory and clone the GitHub repository.

```bash
cd ~
git clone https://github.com/JohnMeersma/DTSIP-Automation.git
cd DTSIP-Automation
```

### Step 4: Create a Python Virtual Environment

Create a virtual environment named `venv`.

```bash
python3 -m venv venv
```

Activate the virtual environment.

```bash
source venv/bin/activate
```

The command prompt should now begin with:

```text
(venv)
```

### Step 5: Install Ansible

Install Ansible inside the virtual environment.

```bash
pip install ansible
```

### Step 6: Install the Cisco IOS Ansible Collection

Install the Cisco IOS modules used to communicate with IOS XE routers.

```bash
ansible-galaxy collection install cisco.ios
```

### Step 7: Install Paramiko

Install Paramiko version 3.x for compatibility with the Cisco 1000v routers.

```bash
pip install "paramiko<4"
```

### Step 8: Verify the Repository Files

```bash
ls
```

You should see files similar to:

```text
cube_playbook.yml
hosts-pod1
hosts-pod2
hosts-pod3
hosts-pod4
hosts-pod5
hosts-pod6
hosts-pod7
hosts-pod8
README.md
```

## Test Ansible Connectivity

Each pod uses its own inventory file.

For Pod 1:

```bash
ansible-playbook -i hosts-pod1 cube_playbook.yml
```

For other pods, change the inventory filename to match the pod number.

Example for Pod 4:

```bash
ansible-playbook -i hosts-pod4 cube_playbook.yml
```
