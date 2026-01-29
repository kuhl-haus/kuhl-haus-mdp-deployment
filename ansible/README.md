
> WORK-IN-PROGRESS: I know, this README totally sucks.  These are rough notes while I am working on a more formal write-up. I will update this soon! I promise! :)


Set the following environment variables before running the scripts.

```
# Needed for Ansible playbook scripts
APP_ENV=dev

# Needed for all scripts
BASE_WORKING_DIR=/mnt/c/Users/tom/Documents/GitHub/kuhl-haus/

# Needed for smoke test scripts
APP_DOMAIN=mdp.kuhl.haus
MDC_SERVER_DOMAIN=mdp-cache.kuhl.haus
MDL_SERVER_DOMAIN=mdp-listener.kuhl.haus
MDP_SERVER_DOMAIN=mdp-processor.kuhl.haus
MDQ_SERVER_DOMAIN=mdp-queues.kuhl.haus
WDS_SERVER_DOMAIN=wds.kuhl.haus
```

```
# Part 1 - Install prerequisites on Ansible host
./scripts/01-run-prereq-playbook.sh

# Part 2 - Kubernetes Infrastructure
./scripts/02-run-k8s-infra-playbook.sh

# Part 3 - Application
./scripts/03-run-app-playbook.sh
./scripts/smoke-test-app.sh

# Part 4 - Data Plane
# Part 4.1 - Data Plane: Certificate Manager
./scripts/04-run-data-plane-playbook.sh deploy-dp-cm.yml

# Part 4.2 - Data Plane: Market Data Cache
./scripts/04-run-data-plane-playbook.sh deploy-mdc.yml
./scripts/smoke-test-mdc.sh

# Part 4.3 - Data Plane: Market Data Queues
./scripts/04-run-data-plane-playbook.sh deploy-mdq.yml
./scripts/smoke-test-mdq.sh

# Part 4.4 - Data Plane: Widget Data Service
./scripts/04-run-data-plane-playbook.sh deploy-wds.yml
./scripts/smoke-test-wds.sh

# Part 4.5 - Data Plane: Market Data Processors
./scripts/04-run-data-plane-playbook.sh deploy-mdp.yml
./scripts/smoke-test-mdp.sh

# Part 4.6 - Data Plane: Market Data Listener
./scripts/04-run-data-plane-playbook.sh deploy-mdl.yml
./scripts/smoke-test-mdl.sh

```