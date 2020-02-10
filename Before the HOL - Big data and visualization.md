![Microsoft Cloud Workshop](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshop')

<div class="MCWHeader1">
Big data and visualization
</div>
    
<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
Feb 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Big data and visualization before the hands-on lab setup guide](#big-data-and-visualization-before-the-hands-on-lab-setup-guide)
  - [Requirements](#requirements)
  - [Before the hands-on lab](#before-the-hands-on-lab)
    - [Task 1: Provision Azure Databricks](#task-1-provision-azure-databricks)
    - [Task 2: Create Azure Storage account](#task-2-create-azure-storage-account)
    - [Task 3: Create storage container](#task-3-create-storage-container)
    - [Task 4: Provision Azure Data Factory](#task-4-provision-azure-data-factory)
    - [Task 5: Download and install Power BI Desktop](#task-5-download-and-install-power-bi-desktop)
    - [Task 6: Download Azure Storage Explorer](#task-6-download-and-install-azure-storage-explorer)
    - [Task 7: Provision SnowFlake](#task-7-provision-snow-flake)

<!-- /TOC -->

# Big data and visualization before the hands-on lab setup guide

## Requirements

1.  Microsoft Azure subscription must be pay-as-you-go or MSDN.

    a. Trial subscriptions will not work.

## Before the hands-on lab

Duration: 30 minutes

In this exercise, you will set up your environment for use in the rest of the hands-on lab. You should follow all the steps provided in the Before the Hands-on Lab section to prepare your environment _before_ attending the hands-on lab.

### Task 1: Provision Azure Databricks

Azure Databricks is an Apache Spark-based analytics platform optimized for Azure. It will be used in this lab to build and train a machine learning model used to predict flight delays.

> **Note**: To view the Azure portal menu, select the menu icon in the upper left-hand corner.

![The Azure portal menu is highlighted.](media/portal-menu.png 'Azure portal menu')

1. In the [Azure Portal](https://portal.azure.com) (https://portal.azure.com), select **+ Create a resource** within the portal menu, then type "Azure Databricks" into the search bar. Select Azure Databricks from the results.

   ![Select create a resource, type in Azure Databricks, then select it from the results list](media/create-azure-databricks-resource.png)

2. Select Create on the bottom of the blade that follows.

3. Set the following configuration on the Azure Databricks Service creation form:

   - **Name**: Enter a unique name as indicated by a green checkmark.

   - **Subscription**: Select the subscription you are using for this hands-on lab.

   - **Resource Group**: Select **Create new** and enter a unique name, such as "hands-on-lab-bigdata".

   - **Location**: Select a region close to you. **_(If you are using an Azure Pass, select South Central US.)_**

   - **Pricing**: Select Premium.

   - **Deploy Azure Databricks workspace in your Virtual Network**: Select No.

   ![Complete the Azure Databricks Service creation form with the options as outlined above.](media/azure-databricks-create-blade.png)

4. Select **Create** to finish and submit.

### Task 2: Create Azure Storage account

Create a new Azure Storage account that will be used to store Shopify and Magento data.

1. In the [Azure Portal](https://portal.azure.com) (<https://portal.azure.com>), select **+ Create a resource**, then type "storage" into the search bar. Select **Storage account** from the results.

   ![Select create a resource, type in storage, then select Storage account... from the results list](media/create-azure-storage-resource.png)

2. Select Create on the bottom of the blade that follows.

3. Set the following configuration on the Azure Storage account creation form:

   - **Subscription**: Select the subscription you are using for this hands-on lab.

   - **Resource group**: Select the same resource group you created at the beginning of this lab.

   - **Storage account name**: Enter a unique name as indicated by a green checkmark.

   - **Location**: Select the same region you used for Azure Databricks.

   - **Performance**: Standard

   - **Account kind**: StorageV2(general purpose v2)

   - **Replication**: Read-access geo-redundant storage (RA-GRS)

   - **Access tier**: Hot
   
   Navigate to Advanced Tab 
   
   - **Hierarchical namespace**: Enabled
   

   

   ![Complete the Azure storage account creation form with the options as outlined above.](media/StorageAccountCreation.png)

4. Select **Create** to finish and submit.

### Task 3: Create storage container

In this task, you will create a storage container in which you will store your Magento and Shopify data files.

1. From the side menu in the Azure portal, choose **Resource groups**, then enter your resource group name into the filter box, and select it from the list.

2. Next, select your lab Azure Storage account from the list.

   ![Select the lab Azure Storage account from within your lab resource group](media/select-azure-storage-account.png)

3. Select **Containers** (1) from the menu. Select **+ Container** (2) enter **analytics** for the name (3), leaving the public access level set to Private. Select **OK** (4) to create the container.

   ![Screenshot showing the steps to create a new storage container](media/azure-storage-create-container.png)
   

### Task 4: Provision Azure Data Factory

Create a new Azure Data Factory instance that will be used to orchestrate data transfers for analysis.

1. In the [Azure Portal](https://portal.azure.com) (<https://portal.azure.com>), select **+ Create a resource**, then type "Data Factory" into the search bar. Select **Data Factory** from the results.

   ![Select create a resource, type in Data Factory, then select Data Factory from the results list](media/create-azure-data-factory.png)

2. Select Create on the bottom of the blade that follows.

3. Set the following configuration on the Data Factory creation form:

   - **Name**: Enter a unique name as indicated by a green checkmark.

   - **Subscription**: Select the subscription you are using for this hands-on lab.

   - **Resource Group**: Select the same resource group you created at the beginning of this lab.

   - **Version**: Select V2.

   - **Location**: Select any region close to you.

   - **Enable GIT**: Unchecked.

   **_Understanding Data Factory Location:_**
   The Data Factory location is where the metadata of the data factory is stored and where the triggering of the pipeline is initiated from. Meanwhile, a data factory can access data stores and compute services in other Azure regions to move data between data stores or process data using compute services. This behavior is realized through the [globally available IR](https://azure.microsoft.com/en-us/global-infrastructure/services/?products=data-factory) to ensure data compliance, efficiency, and reduced network egress costs.

   The IR Location defines the location of its back-end compute, and essentially the location where the data movement, activity dispatching, and SSIS package execution are performed. The IR location can be different from the location of the data factory it belongs to.

   ![Complete the Azure Data Factory creation form with the options as outlined above.](media/azure-data-factory-create-blade.png)

4. Select **Create** to finish and submit.

### Task 5: Download and install Power BI Desktop

Power BI desktop is required to make a connection to your Azure Databricks environment when creating the Power BI dashboard.

1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/).


### Task 6: Download Azure Storage Explorer

Azure Storage Explorer is required to upload/ view data in Data Lake Gen 2.

1. Download and install [Storage Explorer] (https://azure.microsoft.com/en-us/features/storage-explorer/).

You should follow all these steps provided _before_ attending the Hands-on lab.
