# 20231940 - DEVELOPING A UNIFIED DATA PRODUCT MODEL AND INTEGRATING DATA GOVERNANCE AND DATA SECURITY BEST PRACTICES FOR CUSTOMER CARE USE-CASES IN THE BANKING SECTOR REFERENCING BIAN FRAMEWORK

This is the source code repository for the implementation of the physical architecture for the research.

![PhysicalArchitecture](https://github.com/user-attachments/assets/1e39e086-6477-4e20-a414-e621defce53e)

# Introduction
This research addresses a critical challenge faced across various industries, with a focused application in the banking sector: integrating disparate data sources into a unified, accessible format. By targeting customer, transaction, and service data, the study emphasizes how a Customer Data Product (CDP) can serve as a central, standardized repository. The research solves the problem of isolated data sources by aligning them under a common data model within the BIAN Service Landscape. This alignment ensures that the data is not only centrally available but also standardized for seamless consumption across business, AI, and machine processes.
Key achievements include demonstrating how the common data model simplifies data accessibility and usability, eliminating the need to search for diverse integration points or develop expertise in multiple systems. Instead, users—whether business analysts or automated systems—can directly leverage data from a single, well-defined source, fostering efficiency and scalability. The modular nature of BIAN is integral to this approach, as it allows data consumers to know exactly where and how to access customer data for specific service models.
The logical and physical architecture designed in this research validates the practicality of the concept. By employing Microsoft Azure-based cloud architecture for implementation, the study demonstrates real-world feasibility. A core emphasis of the architecture was modularity, ensuring that it aligns with the BIAN framework while securely centralizing data.
Given the sensitivity of customer data, compliance with privacy laws, including New Zealand’s regulations, GDPR, and internal frameworks like NIST, was a critical challenge addressed by embedding DMBOK and NIST principles into the research. This approach ensures that the CDP not only meets governance and security standards but also instills trust in its implementation.

# Objective
The research of data products completed with an aim to implement it with a real world architecture implementation. It provides a prescriptive data platform design coupled with Azure best practices and design principles. These principles serve as a compass for subsequent design decisions across critical technical domains. The architecture will continue to evolve alongside the Azure platform and is ultimately driven by the various design decisions that organizations must make to define their Azure data journey.

The architecture of data products implementation in typical bankking eniviroment for customer, consists of two core building blocks:

Data Governance consist of data security and data governance capabilities of a bank.
Data Product Enabler which is a data architecture that enables data product using the data from silos implemented using the Azure components.

The architecture is modular by design and allows organizations to start small with a single Data Product for customer and implement data architecture using Azure. 

## Deploy Data Product End to End Implementation

Following are the ARM templates
1- Deploy Resouce Template [CreateResource.zip](https://github.com/user-attachments/files/17916880/CreateResource.zip)
2- Deploy Account Template [CreateAccount.zip](https://github.com/user-attachments/files/17916887/CreateAccount.zip)
3- Deploy Azure Database Template [CreateDatabase.zip](https://github.com/user-attachments/files/17916891/CreateDatabase.zip)
4- Deploy Azure Datalake Template [DataLake.zip](https://github.com/user-attachments/files/17916899/DataLake.zip)
5- Deploy Data Factory Template [DataFactory.zip](https://github.com/user-attachments/files/17916903/DataFactory.zip)
6- Deploy Synapse Template [SnapseAnalytics.zip](https://github.com/user-attachments/files/17916910/SnapseAnalytics.zip)
7- Deploy Stream Template[AzureStream.zip](https://github.com/user-attachments/files/17916911/AzureStream.zip)
8- Deploy Montoring Template[MonitoringBencmarkSQL.zip](https://github.com/user-attachments/files/17916917/MonitoringBencmarkSQL.zip)

Following can be created using CLI command in Azure
9- Create App Service
# Create an app service plan
az appservice plan create -n <plan_name> --g <resource_group>

# Create an App Service Web app
az webapp create -n <app_name> -g <resource_group> -p <plan_name> 

# Create an App Service Web app with docker container
az webapp create -n <app_name> -g <group> -p <plan_name> -i <docker_img>

# Create an App Service Web App for static html
az webapp up -l <region> -n <app_name> --html

# Configure a deployment user
az webapp deployment user set --user-name <username> --password <pwd>

# Get web app deploymetn URL
az webapp deployment source config-local-git -n <app_name> -g <resource_group> -o tsv

# Delete an App Service Web App 
az webapp delete -n <app_name>

# Set App Service Configuration
az webapp config appsettings set -n <name> --settings <setting>
10-# Create an API Management Instance
az apim create -n <apim_name> -l <location> `
    --publisher-email <email>  `
    -g <rescource_group_name> `
    --publisher-name <publisher_name> `
    --sku-name Consumption
    
    
# create apim api
az apim api create -api-id <name> -g <group> --display-name <name> --path <path> --service-name <service_name>

##Following is the visual implementation of the code 

#Resouce group snapshot 
Following is the snapshot of the resource group after implementing all the key components of the architecture
![image](https://github.com/user-attachments/assets/3d72ac3f-9818-46f5-b210-97cdfe6782d0)

#Azure Purview of Governance 
![image](https://github.com/user-attachments/assets/1a1404bc-9a38-4799-9780-354d0f0b18a4)

#Azure Data Factory reponsible to bring data from Azure Data base siloed tables into lake into common data product model of customer
![image](https://github.com/user-attachments/assets/1bf5dfae-58ba-4c1d-846b-f6b70d32bade)

#Azure Data Product
![image](https://github.com/user-attachments/assets/0fcc90d3-da68-4f76-917d-d5e794ebc4c3)







