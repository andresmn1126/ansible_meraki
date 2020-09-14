# Meraki Deplyment Automation

Ansible playbooks to be used for deployments using the Meraki API

### Prerequisites

If working in Windows, install WSL and your favorite Linux distro.

https://docs.microsoft.com/en-us/windows/wsl/install-win10

Once WSL is installed, you will need to install ansible.

### Installing

Ansible can beinstalled via your distro package manager

```
sudo apt install ansible
```

Or via Python's pip package manager

```
pip install ansible
```
or in the case of running Python3

```
pip3 install ansible
```

Ansible does not come pre installed with the lastes meraki modules, make sure to install the latest version of the modules by running.

```
ansible-galaxy install collection cisco.meraki
```

ALl the playbooks utlizie the json_query ansible filter, please make sure to install the jmespath python query language by running

```
pip install jmespath
```
### Running Playbooks

Playbook use variables in order to not expose sensitive information such as your meraki api key, playbooks will either expect the variablees to be passed at runtime using the -e or --extra-vars switch
```
ansible-playbook meraki-ap-reboot -e "meraki_api_key=<your_api_key>, organization_id=<org_id>
```

If the playbook calls for a vars_file, simply create a file in your working directory called vars.yml and enter the information within it

```
---
meraki_api_key: <you key>
organization_id: <org id>
organization_name: <Name of organization as it appears in the meraki portal>
template_org_id: <org id of template organization>
```