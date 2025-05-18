
# Kubernetes Cluster Deployment with Ansible

🚀 This repository contains Ansible playbooks designed to automate the deployment of a Kubernetes cluster. It facilitates the setup of a scalable, cloud-native environment, integrating essential components like monitoring tools and network configurations.

## Features

- **Automated Deployment**: Provision Kubernetes master and worker nodes using Ansible playbooks.
- **Network Configuration**: Set up Kubernetes networking components for seamless communication between pods.
- **Monitoring Integration**: Deploy Grafana for real-time monitoring and visualization of cluster metrics.
- **Modular Structure**: Organized playbooks for master, worker, and network configurations, allowing flexibility and scalability.

## Prerequisites

- **Operating System**: Ubuntu 20.04 LTS or compatible Linux distributions.
- **Ansible**: Version 2.9 or higher.
- **Python**: Version 3.6 or higher.
- **SSH Access**: Passwordless SSH access to all target nodes.
- **Inventory File**: An Ansible inventory file listing all master and worker nodes.

## Directory Structure

```
├── kubernetes_master/
│   └── tasks/
│       └── main.yml
├── kubernetes_worker/
│   └── tasks/
│       └── main.yml
├── kubernetes_network/
│   └── tasks/
│       └── main.yml
├── grafana.yml
├── site.yml
└── inventory/
    └── hosts
```

- `kubernetes_master/`: Playbook to configure the Kubernetes master node.
- `kubernetes_worker/`: Playbook to configure Kubernetes worker nodes.
- `kubernetes_network/`: Playbook to set up networking components (e.g., Calico, Flannel).
- `grafana.yml`: Playbook to deploy Grafana for monitoring.
- `site.yml`: Master playbook to run all configurations.
- `inventory/hosts`: Ansible inventory file with groupings for master and worker nodes.

## Usage

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/elyes2dev/Kubernetes-Cluster-Deployment-With-Ansible.git
   cd Kubernetes-Cluster-Deployment-With-Ansible
   ```

2. **Update Inventory File**:

   Edit the `inventory/hosts` file to include the IP addresses or hostnames of your master and worker nodes.

   ```ini
   [master]
   master-node ansible_host=192.168.1.10 ansible_user=ubuntu

   [workers]
   worker-node1 ansible_host=192.168.1.11 ansible_user=ubuntu
   worker-node2 ansible_host=192.168.1.12 ansible_user=ubuntu
   ```

3. **Run the Playbooks**:

   Execute the master playbook to set up the entire cluster.

   ```bash
   ansible-playbook -i inventory/hosts site.yml
   ```

   Alternatively, run individual playbooks as needed:

   - Set up the master node:

     ```bash
     ansible-playbook -i inventory/hosts kubernetes_master/tasks/main.yml
     ```

   - Configure networking:

     ```bash
     ansible-playbook -i inventory/hosts kubernetes_network/tasks/main.yml
     ```

   - Set up worker nodes:

     ```bash
     ansible-playbook -i inventory/hosts kubernetes_worker/tasks/main.yml
     ```

   - Deploy Grafana:

     ```bash
     ansible-playbook -i inventory/hosts grafana.yml
     ```

## Notes

- Ensure that all nodes have internet access to download necessary packages and Docker images.
- The playbooks assume passwordless SSH access; configure SSH keys accordingly.
- Modify the playbooks as needed to suit your specific environment and requirements.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

This project is part of the HackathonNet capstone at ESPRIT, developed by our dedicated team.
