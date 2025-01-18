# Azure CLI Commands
The Azure CLI is a powerful tool for managing Azure resources from the command line.

## Table of Contents
1. [Installation and Setup](#installation-and-setup)
2. [Basic Commands](#basic-commands)
3. [Resource Management](#resource-management)
4. [Virtual Machines](#virtual-machines)
5. [Networking](#networking)
6. [Storage](#storage)
7. [Identity and Access Management](#identity-and-access-management)
8. [Monitoring and Diagnostics](#monitoring-and-diagnostics)
9. [Advanced Commands](#advanced-commands)
10. [Scripting and Automation](#scripting-and-automation)

## Installation and Setup

### Install Azure CLI
```bash
# For Windows
Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'

# For macOS
brew install azure-cli

# For Linux (Ubuntu/Debian)
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash
```

### Login to Azure
```bash
az login
```

### Set Default Subscription
```bash
az account set --subscription <subscription-id>
```

### List Subscriptions
```bash
az account list --output table
```

## Basic Commands

### Get Help
```bash
az --help
```

### List Available Locations
```bash
az account list-locations --output table
```

### List Resource Providers
```bash
az provider list --output table
```

### Show Azure CLI Version
```bash
az --version
```

## Resource Management

### Create a Resource Group
```bash
az group create --name <resource-group-name> --location <location>
```

### List Resource Groups
```bash
az group list --output table
```

### Delete a Resource Group
```bash
az group delete --name <resource-group-name> --yes
```

### List Resources in a Resource Group
```bash
az resource list --resource-group <resource-group-name> --output table
```

## Virtual Machines

### Create a Virtual Machine
```bash
az vm create \
  --resource-group <resource-group-name> \
  --name <vm-name> \
  --image UbuntuLTS \
  --admin-username <username> \
  --generate-ssh-keys
```

### List Virtual Machines
```bash
az vm list --output table
```

### Start a Virtual Machine
```bash
az vm start --resource-group <resource-group-name> --name <vm-name>
```

### Stop a Virtual Machine
```bash
az vm stop --resource-group <resource-group-name> --name <vm-name>
```

### Delete a Virtual Machine
```bash
az vm delete --resource-group <resource-group-name> --name <vm-name> --yes
```

### Get VM Details
```bash
az vm show --resource-group <resource-group-name> --name <vm-name>
```

## Networking

### Create a Virtual Network
```bash
az network vnet create \
  --resource-group <resource-group-name> \
  --name <vnet-name> \
  --address-prefix 10.0.0.0/16 \
  --subnet-name <subnet-name> \
  --subnet-prefix 10.0.0.0/24
```

### List Virtual Networks
```bash
az network vnet list --output table
```

### Create a Public IP Address
```bash
az network public-ip create \
  --resource-group <resource-group-name> \
  --name <public-ip-name> \
  --allocation-method Static
```

### Create a Network Security Group (NSG)
```bash
az network nsg create \
  --resource-group <resource-group-name> \
  --name <nsg-name>
```

### Add NSG Rule
```bash
az network nsg rule create \
  --resource-group <resource-group-name> \
  --nsg-name <nsg-name> \
  --name <rule-name> \
  --priority 100 \
  --access Allow \
  --protocol Tcp \
  --direction Inbound \
  --source-address-prefix '*' \
  --source-port-range '*' \
  --destination-address-prefix '*' \
  --destination-port-range 22
```

## Storage

### Create a Storage Account
```bash
az storage account create \
  --name <storage-account-name> \
  --resource-group <resource-group-name> \
  --location <location> \
  --sku Standard_LRS
```

### List Storage Accounts
```bash
az storage account list --output table
```

### Create a Blob Container
```bash
az storage container create \
  --account-name <storage-account-name> \
  --name <container-name> \
  --public-access blob
```

### Upload a File to Blob Storage
```bash
az storage blob upload \
  --account-name <storage-account-name> \
  --container-name <container-name> \
  --name <blob-name> \
  --file <local-file-path>
```

## Identity and Access Management

### Create a Service Principal
```bash
az ad sp create-for-rbac --name <service-principal-name>
```

### List Service Principals
```bash
az ad sp list --output table
```

### Assign Role to a Service Principal
```bash
az role assignment create \
  --assignee <service-principal-id> \
  --role Contributor \
  --resource-group <resource-group-name>
```

### Create a User
```bash
az ad user create \
  --display-name <display-name> \
  --password <password> \
  --user-principal-name <upn>
```

## Monitoring and Diagnostics

### Enable Diagnostics on a VM
```bash
az vm diagnostics set \
  --resource-group <resource-group-name> \
  --vm-name <vm-name> \
  --settings <diagnostics-settings-json>
```

### List Activity Logs
```bash
az monitor activity-log list --output table
```

### Create an Alert Rule
```bash
az monitor metrics alert create \
  --name <alert-name> \
  --resource-group <resource-group-name> \
  --condition "avg Percentage CPU > 80" \
  --action email <email-address>
```

## Advanced Commands

### Deploy an ARM Template
```bash
az deployment group create \
  --resource-group <resource-group-name> \
  --template-file <template-file.json> \
  --parameters <parameters-file.json>
```

### Create a Kubernetes Cluster (AKS)
```bash
az aks create \
  --resource-group <resource-group-name> \
  --name <cluster-name> \
  --node-count 3 \
  --generate-ssh-keys
```

### Deploy a Web App
```bash
az webapp up \
  --resource-group <resource-group-name> \
  --name <app-name> \
  --location <location> \
  --sku F1
```

### Create a Function App
```bash
az functionapp create \
  --resource-group <resource-group-name> \
  --name <function-app-name> \
  --storage-account <storage-account-name> \
  --consumption-plan-location <location>
```

## Scripting and Automation

### Run a CLI Script
```bash
az login
az group create --name MyResourceGroup --location eastus
az vm create --resource-group MyResourceGroup --name MyVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
```

### Export Resource Group to ARM Template
```bash
az group export --name <resource-group-name> > template.json
```

### Import ARM Template
```bash
az deployment group create --resource-group <resource-group-name> --template-file template.json
```

### Automate with Azure CLI in CI/CD
```bash
# Example: Azure DevOps Pipeline
- script: |
    az login --service-principal -u <service-principal-id> -p <password> --tenant <tenant-id>
    az group create --name MyResourceGroup --location eastus
    az vm create --resource-group MyResourceGroup --name MyVM --image UbuntuLTS --admin-username azureuser --generate-ssh-keys
  displayName: 'Create VM with Azure CLI'
```
