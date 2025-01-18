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
9. [Azure SQL Database](#azure-sql-database)
10. [Azure Cosmos DB](#azure-cosmos-db)
11. [Azure Key Vault](#azure-key-vault)
12. [Azure Functions](#azure-functions)
13. [Azure Container Instances (ACI)](#azure-container-instances-aci)
14. [Azure Logic Apps](#azure-logic-apps)
15. [Azure Event Hubs](#azure-event-hubs)
16. [Azure Service Bus](#azure-service-bus)
17. [Azure Cognitive Services](#azure-cognitive-services)
18. [Azure IoT Hub](#azure-iot-hub)
19. [Azure Data Lake Storage](#azure-data-lake-storage)
20. [Azure Policy](#azure-policy)
21. [Azure Blueprints](#azure-blueprints)
22. [Azure Backup](#azure-backup)
23. [Scripting and Automation](#scripting-and-automation)

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

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

---

## Azure SQL Database

### Create a SQL Server
```bash
az sql server create \
  --name <server-name> \
  --resource-group <resource-group-name> \
  --location <location> \
  --admin-user <admin-username> \
  --admin-password <admin-password>
```

### Create a SQL Database
```bash
az sql db create \
  --resource-group <resource-group-name> \
  --server <server-name> \
  --name <database-name> \
  --service-objective S0
```

### List SQL Databases
```bash
az sql db list --resource-group <resource-group-name> --server <server-name> --output table
```

### Create a Firewall Rule for SQL Server
```bash
az sql server firewall-rule create \
  --resource-group <resource-group-name> \
  --server <server-name> \
  --name <rule-name> \
  --start-ip-address <start-ip> \
  --end-ip-address <end-ip>
```

---

## Azure Cosmos DB

### Create a Cosmos DB Account
```bash
az cosmosdb create \
  --name <account-name> \
  --resource-group <resource-group-name> \
  --locations regionName=<region> failoverPriority=0
```

### Create a Cosmos DB Database
```bash
az cosmosdb sql database create \
  --account-name <account-name> \
  --name <database-name> \
  --resource-group <resource-group-name>
```

### Create a Cosmos DB Container
```bash
az cosmosdb sql container create \
  --account-name <account-name> \
  --database-name <database-name> \
  --name <container-name> \
  --partition-key-path "/<partition-key>" \
  --resource-group <resource-group-name>
```

---

## Azure Key Vault

### Create a Key Vault
```bash
az keyvault create \
  --name <vault-name> \
  --resource-group <resource-group-name> \
  --location <location>
```

### Add a Secret to Key Vault
```bash
az keyvault secret set \
  --vault-name <vault-name> \
  --name <secret-name> \
  --value <secret-value>
```

### Retrieve a Secret from Key Vault
```bash
az keyvault secret show \
  --vault-name <vault-name> \
  --name <secret-name>
```

---

## Azure Functions

### Create a Function App with Custom Runtime
```bash
az functionapp create \
  --resource-group <resource-group-name> \
  --name <function-app-name> \
  --storage-account <storage-account-name> \
  --runtime <runtime> \
  --consumption-plan-location <location>
```

### Deploy a Function App from GitHub
```bash
az functionapp deployment source config \
  --resource-group <resource-group-name> \
  --name <function-app-name> \
  --repo-url <github-repo-url> \
  --branch <branch-name> \
  --manual-integration
```

---

## Azure Container Instances (ACI)

### Create a Container Instance
```bash
az container create \
  --resource-group <resource-group-name> \
  --name <container-name> \
  --image <docker-image> \
  --ports 80 \
  --dns-name-label <dns-label> \
  --location <location>
```

### List Container Instances
```bash
az container list --resource-group <resource-group-name> --output table
```

### Attach to a Running Container
```bash
az container attach \
  --resource-group <resource-group-name> \
  --name <container-name>
```

---

## Azure Logic Apps

### Create a Logic App
```bash
az logic workflow create \
  --resource-group <resource-group-name> \
  --name <logic-app-name> \
  --location <location>
```

### Trigger a Logic App
```bash
az logic workflow trigger \
  --resource-group <resource-group-name> \
  --name <logic-app-name> \
  --trigger-name <trigger-name>
```

---

## Azure Event Hubs

### Create an Event Hub Namespace
```bash
az eventhubs namespace create \
  --name <namespace-name> \
  --resource-group <resource-group-name> \
  --location <location>
```

### Create an Event Hub
```bash
az eventhubs eventhub create \
  --name <eventhub-name> \
  --resource-group <resource-group-name> \
  --namespace-name <namespace-name>
```

### List Event Hubs
```bash
az eventhubs eventhub list \
  --resource-group <resource-group-name> \
  --namespace-name <namespace-name> \
  --output table
```

---

## Azure Service Bus

### Create a Service Bus Namespace
```bash
az servicebus namespace create \
  --name <namespace-name> \
  --resource-group <resource-group-name> \
  --location <location>
```

### Create a Service Bus Queue
```bash
az servicebus queue create \
  --name <queue-name> \
  --resource-group <resource-group-name> \
  --namespace-name <namespace-name>
```

### Send a Message to a Queue
```bash
az servicebus queue send \
  --name <queue-name> \
  --resource-group <resource-group-name> \
  --namespace-name <namespace-name> \
  --message-body "Hello, Service Bus!"
```

---

## Azure Cognitive Services

### Create a Cognitive Services Account
```bash
az cognitiveservices account create \
  --name <account-name> \
  --resource-group <resource-group-name> \
  --kind <service-kind> \
  --sku <sku-name> \
  --location <location>
```

### List Cognitive Services Keys
```bash
az cognitiveservices account keys list \
  --name <account-name> \
  --resource-group <resource-group-name>
```

---

## Azure IoT Hub

### Create an IoT Hub
```bash
az iot hub create \
  --name <hub-name> \
  --resource-group <resource-group-name> \
  --sku S1
```

### Add a Device to IoT Hub
```bash
az iot hub device-identity create \
  --hub-name <hub-name> \
  --device-id <device-id>
```

### Send a Message to a Device
```bash
az iot device send-d2c-message \
  --hub-name <hub-name> \
  --device-id <device-id> \
  --data "Hello, IoT Device!"
```

---

## Azure Data Lake Storage

### Create a Data Lake Storage Account
```bash
az storage account create \
  --name <storage-account-name> \
  --resource-group <resource-group-name> \
  --location <location> \
  --sku Standard_LRS \
  --kind StorageV2 \
  --hierarchical-namespace true
```

### Create a File System (Container)
```bash
az storage fs create \
  --name <file-system-name> \
  --account-name <storage-account-name>
```

### Upload a File to Data Lake
```bash
az storage fs file upload \
  --file-system <file-system-name> \
  --source <local-file-path> \
  --path <destination-path> \
  --account-name <storage-account-name>
```

---

## Azure Policy

### Assign a Policy Definition
```bash
az policy assignment create \
  --name <assignment-name> \
  --policy <policy-definition-id> \
  --resource-group <resource-group-name>
```

### List Policy Assignments
```bash
az policy assignment list --resource-group <resource-group-name> --output table
```

---

## Azure Blueprints

### Create a Blueprint
```bash
az blueprint create \
  --name <blueprint-name> \
  --management-group <management-group-id>
```

### Publish a Blueprint
```bash
az blueprint publish \
  --blueprint-name <blueprint-name> \
  --version <version> \
  --management-group <management-group-id>
```

---

## Azure Backup

### Create a Backup Vault
```bash
az backup vault create \
  --name <vault-name> \
  --resource-group <resource-group-name> \
  --location <location>
```

### Enable Backup for a VM
```bash
az backup protection enable-for-vm \
  --resource-group <resource-group-name> \
  --vault-name <vault-name> \
  --vm <vm-name> \
  --policy-name <policy-name>
```

---

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
