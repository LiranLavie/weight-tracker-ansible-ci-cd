# Weight Tracker Ansible CI-CD


 This project demonstrate the provision of infrastructure as code project  [**weight-tracker-inftastructure**](https://github.com/LiranLavie/weight-tracker-inftastructure-ci-cd) with Ansible .

The requested infrastructure:

![project6](doc/project6.png)


## Configuration
Two identical environments created except for the number of web servers:
1. Production -3 web servers 
2. Staging - 2 web servers


A variable file added for each of the environments.

From the Terraform project I exported variable files for hosts, variable file for Postgres details, and hosts details for host file to use with Ansible.

* For the Infrastructure CI-CD  i created a playbook file named **webserver_playbook.yml** for installing configuration on the servers

* For the weight tracker app CI-CD i created a playbook file named **app_deploy_playbook.yml** for installing necessary configuration after the app deployment.

* The playbook files will start automatically by the release pipeline.

* Variable files are encrypted with Ansible Vault.


```
weight-tracker-ansible-ci-cd
│   ├── README.md
│   ├── ansible.cfg
│   ├── app_deploy_playbook.yml
│   ├── doc
│   │   └── project6.png
│   ├── inventory
│   │   ├── production
│   │   │   ├── host
│   │   │   └── host_vars
│   │   │       ├── web-server-1-production.yml
│   │   │       ├── web-server-2-production.yml
│   │   │       └── web-server-3-production.yml
│   │   ├── staging
│   │   │   ├── host
│   │   │   └── host_vars
│   │   │       ├── web-server-1-staging.yml
│   │   │       └── web-server-2-staging.yml
│   │   └── webservers_vars
│   │       └── webservers_vars.yml
│   ├── roles
│   │   ├── app_deploy
│   │   │   ├── tasks
│   │   │   │   └── main.yml
│   │   │   └── templates
│   │   │       └── env.j2
│   │   └── webserver_conf
│   │       ├── tasks
│   │       │   └── main.yml
│   │       └── templates
│   │           ├── app_startup_service.j2
│   │           └── start_app_script.j2
│   └── webserver_playbook.yml
```
