Overview
Network Manager is a tool designed to simplify the creation, management, and deployment of Azure Virtual Networks (VNets). It helps users automate the provisioning of VNets, subnets, and associated resources using Azure CLI and ARM templates. For information about the scenario please check the diagram in the main repository. 


Prerequisites

  Before deploying Network Manager, ensure you have:
      
      Azure CLI installed (az --version to check).
      Azure subscription with necessary permissions.
      Resource Group created (az group create --name <ResourceGroup> --location <Region>).


Deployment Steps

  Follow these steps to deploy the resoures depicts in the diagram using Azure CLI:
  
  Step 1: Clone the Repository

    git clone https://github.com/ovahedvakhshori/azure-templates/tree/main/AzureNetworkManager-FullScenario.git

 Step 2: Authenticate to Azure
    
      az login
      az account set --subscription <your-subscription-id>

Step 3: Deploy VNet Using Azure CLI


T01-S01-R1 --------------------------------------------T01-S01-R1------------------------------------------T01-S01-R1

    az login --tenan Tenant01ID 
    
    az account set --subscription S01ID
    
    az group create --name T01-S01-R1 --location westeurope
    
    az deployment group create  -g T01-S01-R1 -f T01-S01-R1-template.json -p T01-S01-R1-parameters.json

T01-S02-R2 ------------------------------------------- T01-S02-R2------------------------------------------T01-S02-R2

    az account set --subscription S02ID
    
    az group create --name T01-S02-R2 --location swedencentral
    
    az deployment group create  -g T01-S02-R2 -f T01-S02-R2-template.json -p T01-S02-R2-parameters.json


T02-S01-R1 ------------------------------------------- T02-S01-R1------------------------------------------T02-S01-R1

    az login --tenant Tenant02ID 

    az account set --subscription S01ID

    az group create --name T02-S01-R1 --location eastus


    az deployment group create  -g T02-S01-R1 -f T02-S01-R1-template.json -p T02-S01-R1-parameters.json
