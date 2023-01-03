# How to use

## Prerequisites

Make sure you have installed [python3](https://www.python.org/downloads/), [pip](https://pip.pypa.io/en/stable/installation/) and [ansible](https://pypi.org/project/ansible/) on your host machine.

## Install Apache Pinot Cluster

In order to install Apache Pinot cluster on your nodes, it is required to do the following steps.
1. Set global environment variables which are located at `inventory/group_vars/all.yml` file. For example `pinot_installation_path` variable indicates that where to keep manifest of docker compose file for Apache Pinot components.

2. Create `inventory/inventory.yml` file from the `inventory/inventory.yml.sample` file and place the `IP` and `user` of the nodes there. You can easily create a new name and place it in inventory.yml‍ file.


3. Then go to the roles and set the values of each variable on `defaults` directory of each role. For example, you can change the port of controller, by changing the `controller_port` value located in `roles/controller/defaults/main.yml` file.

4. Execute the following command:
  ```bash
  ansible-playbook -i <path-to-inventory-file> cluster.yml --become --become-user=root --private-key=<path-to-private-key> -v -b
  # e.g.
  ansible-playbook -i inventory/inventory.yml cluster.yml --become --become-user=root --private-key=~/.ssh/ssh_pk -v -b
  ```

## Reset the files created by Ansible

# Jobs to be done

- [X] Setup new cluster
  - [ ] Add Docker image pull to prerequisites role
  - [ ] Add password vault 
  - [ ] Generalize group_vars file with all possible settings
- [X] Setup monitoring with Grafana and Prometheus
  - [X] Persist data of Grafana 
