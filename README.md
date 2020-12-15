
# BIG-IP VE dynamic onboarding

## Purpose

This repo does the DO and AS3 provisioning and uses a dynamically built inventory (by vRA - but it could be from AWS or any other cloud as well)

## Pre-req's

Docker

## Steps

* ### clone the repo


* ### build and run the container

``` docker-compose run onboard```

If you get the following error

``` 

 docker.credentials.errors.InitializationError: docker-credential-gcloud not installed or not available in PATH
[75654] Failed to execute script docker-compose 

```
run the following command and then run docker compose again

```
rm  ~/.docker/config.json

```

* ### You are inside the container now
* ### Edit the vault and modify bigip password (vault pass is default bigip pass)

``` ansible-vault edit group_vars/virtualDataCenter/vault.yml ``

* ### Run the playbook using the following command.

``` ansible-playbook playbooks/build_infra.yaml -i inventory-vmware.yml -vvv --ask-vault-pass ```


