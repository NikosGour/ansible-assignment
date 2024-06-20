# Distributed Systems Deployment
## Author : Nikos Gournakis
## Roles
- `ansible-galaxy role install geerlingguy.mysql`
- `ansible-galaxy role install geerlingguy.docker`

## Note on running the playbooks
Some of the playbooks copy over an ssh key to the remote host, this is done to get the git repositories. You need to do one of two things for them to work:
- Either change the instances of `id_distributed_systems_rsa` with your own key (not recommended)
- Or create a key with the name `id_distributed_systems_rsa`, add it on github, and add it on `~/.ssh/id_distributed_systems_rsa`

## Hosts
- jenkins_hosts: All the hosts that are running Jenkins
- backend_hosts: All the hosts that are running the backend services
- frontend_hosts: All the hosts that are running the frontend
- azure_hosts: All the hosts that are running on Azure

### For common use the first three groups are used

## Playbooks
- `ping.yaml`: Pings all the hosts
- `install_docker.yaml`: Installs docker on any host. This should be used with the `-l` flag to specify the host
- `mysql.yaml`: Installs MySQL on the backend hosts
- `spring.yaml`: Installs the spring boot application on the backend hosts
- `react.yaml`: Installs the react application on the frontend hosts
- `main.yaml`: Runs the playbooks in the correct order to deploy the application
- `main_docker_compose.yaml`: The playbook for the docker-compose Jenkins deployment

## Templates
these are templates to create services on the remote hosts, they are used in the playbooks. For now they are the same, but they are separated for future use.