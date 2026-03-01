# 📦 ansible‑mini‑project

**A Simple Ansible Mini Deployment Project for a Todo Application**  
This repository demonstrates how to use Ansible to deploy a basic Todo application using an inventory, playbook, and roles. It’s ideal as a mini project or learning exercise for Ansible beginners.

---

## 🚀 Table of Contents

- [About](#about)
- [Prerequisites](#prerequisites)
- [Repository Structure](#repository‑structure)
- [Getting Started](#getting‑started)
‑ [Usage](#usage)
‑ [Roles Explained](#roles‑explained)
‑ [Inventory](#inventory)
‑ [Playbook](#playbook)
‑ [Contributing](#contributing)
‑ [License](#license)

---

## 📘 About

This repository contains a small Ansible project which deploys a Todo application using an Ansible playbook. It uses a role to encapsulate the application deployment logic and inventories to define target hosts.  

_(Add more context about the app and your goals here.)_

---

## 🧰 Prerequisites

Before you begin, make sure you have:

- 📌 Ansible installed (e.g., `ansible‑core`, `ansible‑playbook`)
- 🖥️ A Linux host or VM reachable via SSH
- 🔑 Password‑less SSH access (recommended via SSH keys)
- 🗂️ Your application artifacts somewhere Ansible can reach

---

## 📁 Repository Structure


.
├── group_vars/ # Variables for host groups
├── host_vars/ # Variables for individual hosts
├── inventory.ini # Inventory file defining hosts
├── playbook.yaml # Main Ansible playbook
├── roles/
│ └── todo‑app/ # Ansible role that deploys the Todo app
│ └── tasks/
│ └── main.yml
└── vault.pass # (Optional) Encrypted secrets file


---

## 🏁 Getting Started

1. **Clone the project**
   ```bash
   git clone https://github.com/branson404/ansible‑mini‑project.git
   cd ansible‑mini‑project
   ```

2. **Prepare your inventory**
Modify inventory.ini to match your hosts and groups.

3. **Run the Playbook**
   ```bash
     ansible‑playbook ‑i inventory.ini playbook.yaml
   ```
---
##Usage

Use the playbook to deploy your Todo app:
```bash
ansible‑playbook ‑i inventory.ini playbook.yaml ‑‑ask‑vault‑pass
```
use `‑‑ask‑vault‑pass` , because i've secured the values inside

##Roles Explained
todo‑app

- The todo‑app role contains all tasks required to deploy and configure the Todo application:
 - Install dependencies
- Copy application file
- Start application process or service

##Inventory

Your inventory.ini defines host groups, e.g.:
`
```code
[app_servers]
todo‑server1 ansible_host=192.168.1.10 ansible_user=ubuntu
```
Group and host variables can live under `group_vars/` and `host_vars/.`

## Playbook

The playbook playbook.yaml includes your roles and orchestrates deployment:
```
‑ hosts: all
  become: yes
  vars_files:
    ‑ vault.pass
  roles:
    ‑ todo‑app

```
