
> WORK-IN-PROGRESS: I know, this README totally sucks.  These are rough notes while I am working on a more formal write-up. I will update this soon! I promise! :)

# Prerequisites
## Kubernetes

To standardize on a platform for the purposes of providing a working example, this tutorial uses Kubernetes on Docker Desktop. However, translating that to a production k8s cluster should be straightforward.


## Ansible Setup

### 1. Install Ansible

[Follow the official installation instructions for your OS.](https://docs.ansible.com/projects/ansible/latest/installation_guide/index.html)

### 2. Clone the repositories

The project is split across three repos:
* kuhl-haus-mdp-servers - Backend services (listener, processor, widget service)
* kuhl-haus-mdp-app - Frontend application and web server
* kuhl-haus-mdp-deployment - Example code for development and production deployment strategies

Create a folder to contain them all and clone them using the GitHub CLI:

```
mkdir ~/kuhl-haus
cd ~/kuhl-haus
gh repo clone kuhl-haus/kuhl-haus-mdp-servers
gh repo clone kuhl-haus/kuhl-haus-mdp-app
gh repo clone kuhl-haus/kuhl-haus-mdp-deployment

```

### 3. Configure Ansible Vault

Create a `secrets.yml` file under `~/kuhl-haus/kuhl-haus-mdp-deployment/ansible/group_vars` using the `ansible-vault` command.

Refer to the official ansible vault documentation.

TL;DR version:

```
# Create new encrypted file
ansible-vault create ansible/group_vars/secrets.yml

# Edit existing encrypted file
ansible-vault edit ansible/group_vars/secrets.yml

# View encrypted file contents
ansible-vault view ansible/group_vars/secrets.yml
```

Add the following contents while in `edit` mode:

```
acme_prod_route53_access_key_id: ""
acme_prod_route53_secret_access_key: ""

aws_ses_smtp_username: ""
aws_ses_smtp_password: ""

cloudflare_prod_dns_api_token: ""
cloudflare_prod_global_api_key: ""

google_oauth_client_id: ""
google_oauth_client_secret: ""

# Stock Market Data
prod_massive_api_key: ""
prod_massive_s3_access_key: ""
prod_massive_s3_secret_key: ""

admin_name: ""
admin_email: ""

# MDP
dev_admin_password: ""
dev_wds_api_token: ""

dev_postgres_password: ""
dev_replication_password: ""
dev_rabbitmq_password: ""
dev_redis_password: ""

# PY4WEB
py4web_session_secret_key: ""
```

Fill in the appropriate values for your environment and save the file.

# Deployment

## Prepare the workspace

Set the following environment variables before running the scripts.

```
# Needed for Ansible playbook scripts
APP_ENV=example

# Needed for all scripts
BASE_WORKING_DIR=~/kuhl-haus

# Needed for smoke test scripts
APP_DOMAIN=mdp.example.com
MDC_SERVER_DOMAIN=mdp-cache.example.com
MDL_SERVER_DOMAIN=mdp-listener.example.com
MDP_SERVER_DOMAIN=mdp-processor.example.com
MDQ_SERVER_DOMAIN=mdp-queues.example.com
WDS_SERVER_DOMAIN=wds.example.com
```

## Part 1 - Install prerequisites on Ansible host

```
./scripts/01-run-prereq-playbook.sh

```

## Part 2 - Kubernetes Infrastructure

```
./scripts/02-run-k8s-infra-playbook.sh
```

## Part 3 - Application

```
./scripts/03-run-app-playbook.sh
./scripts/smoke-test-app.sh
```

## Part 4 - Data Plane
### Part 4.1 - Data Plane: Certificate Manager

```
./scripts/04-run-data-plane-playbook.sh deploy-dp-cm.yml
```


### Part 4.2 - Data Plane: Market Data Cache

```
./scripts/04-run-data-plane-playbook.sh deploy-mdc.yml
./scripts/smoke-test-mdc.sh
```

### Part 4.3 - Data Plane: Market Data Queues

```
./scripts/04-run-data-plane-playbook.sh deploy-mdq.yml
./scripts/smoke-test-mdq.sh
```

### Part 4.4 - Data Plane: Widget Data Service

```
./scripts/04-run-data-plane-playbook.sh deploy-wds.yml
./scripts/smoke-test-wds.sh
```

### Part 4.5 - Data Plane: Market Data Processors

```
./scripts/04-run-data-plane-playbook.sh deploy-mdp.yml
./scripts/smoke-test-mdp.sh
```


### Part 4.6 - Data Plane: Market Data Listener

```
./scripts/04-run-data-plane-playbook.sh deploy-mdl.yml
./scripts/smoke-test-mdl.sh
```
