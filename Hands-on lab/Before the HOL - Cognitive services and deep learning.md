![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Cognitive services and deep learning
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
January 2021
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2021 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Cognitive services and deep learning before the hands-on lab setup guide](#cognitive-services-and-deep-learning-before-the-hands-on-lab-setup-guide)
  - [Requirements](#requirements)
  - [Before the hands-on lab](#before-the-hands-on-lab)
    - [Task 1: Create a resource group](#task-1-create-a-resource-group)
    - [Task 2: Create a Computer Vision API](#task-2-create-a-computer-vision-api)
    - [Task 3: Provision a Text Analytics API](#task-3-provision-a-text-analytics-api)
    - [Task 4: Create an Azure Machine Learning workspace](#task-4-create-an-azure-machine-learning-workspace)
    - [Task 5: Create a Compute Instance](#task-5-create-a-compute-instance)
    - [Task 6: Import the Lab Notebooks](#task-6-import-the-lab-notebooks)

<!-- /TOC -->

# Cognitive services and deep learning before the hands-on lab setup guide

## Requirements

1. Microsoft Azure subscription must be pay-as-you-go or MSDN

   - Trial subscriptions will not work. You will run into issues with Azure resource quota limits.
   - Subscriptions with access limited to a single resource group will not work. You need the ability to deploy multiple resource groups.

## Before the hands-on lab

Duration: 25 minutes

In this exercise, you set up your environment for use in the rest of the hands-on lab. You should follow all steps provided _before_ attending the Hands-on lab.

> **Important**: Many Azure resources require globally unique names. Throughout these steps, the word "SUFFIX" appears as part of resource names. You should replace this with your Microsoft alias, initials, or other value to ensure uniquely named resources.

### Task 1: Create a resource group

1. In the [Azure portal](https://portal.azure.com), select **Resource groups** from the Azure services list.

   ![Resource groups is highlighted in the Azure services list.](media/azure-services-resource-groups.png "Azure services")

2. On the Resource groups blade, select **+Add**.

   ![+Add is highlighted in the toolbar on Resource groups blade.](media/resource-groups-add.png "Resource groups")

3. On the Create a resource group **Basics** tab, enter the following:

   - **Subscription**: Select the subscription you are using for this hands-on lab.
   - **Resource group**: Enter `hands-on-lab-SUFFIX` as the name of the new resource group, where SUFFIX is your Microsoft alias, initials, or other value to ensure uniquely named resources.
   - **Region**: Select the region you are using for this hands-on lab.

   ![The values specified above are entered into the Create a resource group Basics tab.](media/create-resource-group.png "Create resource group")

4. Select **Review + Create**.

5. On the **Review + create** tab, ensure the Validation passed message is displayed and then select **Create**.

### Task 2: Create a Computer Vision API

In this task, you provision a Computer Vision API, which will be integrated into your final POC.

1. In the [Azure portal](https://portal.azure.com/), select the **Show portal menu** icon and then choose **+Create a resource** from the menu.

   ![The Show portal menu icon is highlighted, and the portal menu is displayed. Create a resource is highlighted in the portal menu.](media/create-a-resource.png "Create a resource")

2. Select **AI + Machine Learning** in the Azure Marketplace list and then select **Computer Vision** from the featured services list.

    ![In the New resource blade, AI + Machine Learning is selected under the Azure Marketplace and Computer Vision is highlighted under the featured services.](media/create-resource-computer-vision.png "Computer Vision")

3. On the **Create** blade, provide the following:

    Project details:

    - **Subscription**: Select the subscription you are using for this hands-on lab.
    - **Resource group**: Select the hands-on-lab-SUFFIX resource group from the dropdown list.

    Instance Details:

    - **Region**: Select the region you used for the hands-on-lab-SUFFIX resource group.
    - **Name:** Provide a unique name for this instance, such as cv-SUFFIX.
    - **Pricing tier**: Select Standard S1.

    ![The Create Computer Vision Basics tab is populated with the values specified above.](media/create-computer-vision.png "Create Computer Vision")

4. Select **Review + create**.

5. Ensure validation passes and then select **Create** on the Review + create tab.

### Task 3: Provision a Text Analytics API

In this task, you create a Text Analytics API, which will be integrated into your final POC.

1. In the [Azure portal](https://portal.azure.com/), select the **Show portal menu** icon and then choose **+Create a resource** from the menu.

   ![The Show portal menu icon is highlighted, and the portal menu is displayed. Create a resource is highlighted in the portal menu.](media/create-a-resource.png "Create a resource")

2. Select **AI + Machine Learning** in the Azure Marketplace list and then select **Text Analytics** from the featured services list.

    ![In the New resource blade, AI + Machine Learning is selected under the Azure Marketplace and Text Analytics is highlighted under the featured services.](media/create-resource-text-analytics.png "Text Analytics")

3. On the **Basics** tab, provide the following:

    Project details:

    - **Subscription**: Select the subscription you are using for this hands-on lab.
    - **Resource group**: Select the hands-on-lab-SUFFIX resource group from the dropdown list.

    Instance Details:

    - **Region**: Select the region you used for the hands-on-lab-SUFFIX resource group.
    - **Name:** Provide a unique name for this instance, such as ta-SUFFIX.
    - **Pricing tier**: Select Standard S0.

    ![The Create Text Analytics Basics tab is populated with the values specified above.](media/create-text-analytics.png "Create Text Analytics")

4. Select **Review + create**.

5. Ensure validation passes and then select **Create** on the Review + create tab.

### Task 4: Create an Azure Machine Learning workspace

In this task, you provision the Azure Machine Learning workspace you will use throughout this hands-on lab.

1. In the [Azure portal](https://portal.azure.com/), select the **Show portal menu** icon and then choose **+Create a resource** from the menu.

   ![The Show portal menu icon is highlighted, and the portal menu is displayed. Create a resource is highlighted in the portal menu.](media/create-a-resource.png "Create a resource")

2. Enter "machine learning" into the Search the Marketplace box, and then select **Machine Learning** from the results.

   ![Machine learning is entered into the Search the Marketplace box, and Machine Learning is highlighted in the results.](media/marketplace-results-machine-learning.png "Create Machine Learning service")

3. On the Machine Learning blade, select **Create**.

   ![The Create button is highlighted on the Machine Learning blade.](media/machine-learning-create.png "Create Machine Learning resource")

4. On the Create a machine learning workspace blade, provide the following information to configure the new workspace:

   Project details:

   - **Subscription**: Select the subscription you are using for this hands-on lab.
   - **Resource group**: Select the hands-on-lab-SUFFIX resource group from the dropdown list.

   Workspace details:

   - **Workspace name**: Enter **ml-wksp-SUFFIX**, where SUFFIX is your Microsoft alias, initials, or other value to ensure uniquely named resources. Names must be unique across the resource group. Use one that is easy to recall and differentiate from workspaces created by others.
   - **Region**: Select the region you used for the hands-on-lab-SUFFIX resource group.
   - **Storage account**: Accept the generated storage account name.
   - **Key vault**: Accept the generated key vault name.
   - **Application insights**: Accepted the generated application insights name.
   - **Container registry**: Leave set to None.

   ![The Create Machine Learning workspace Basics tab is displayed populated with the values specified above entered into the form.](media/machine-learning-basics-tab.png 'Create Azure Machine Learning Workspace page')

5. Select **Review + create**. The default values will be used for the remaining screens.

6. Ensure the **Validation passed** message is displayed at the top of the Review + create tab and then select **Create**.

   ![A validation passed message is displayed on the Review + create tab, and the Create button is highlighted.](media/machine-learning-review-create.png)

7. It may take several minutes to provision a new Machine Learning workspace. When the deployment completes, select **Go to resource** on the deployment screen.

   ![The Go to resource button is highlighted on the Machine Learning workspace deployment screen.](media/machine-learning-deployment.png "Machine Learning workspace deployment")

### Task 5: Create a Compute Instance

In this task, you add a compute resource to your Azure Machine Learning workspace.

1. On the Machine Learning blade in the [Azure portal](https://portal.azure.com/), open Azure Machine Learning studio by selecting **Launch studio** from the center section of the screen.

   ![The Launch studio button is highlighted on the Machine Learning blade.](media/machine-learning-launch-studio.png "Launch Azure Machine Learning studio")

2. In the new Azure Machine Learning studio window, select **Create new** and then select **Compute instance** from the context menu.

   ![Within Azure Machine Learning studio, Create new is selected and highlighted, and Compute instance is highlighted in the context menu.](media/machine-learning-studio-create-new-compute-instance.png "Create new compute instance")

3. On the create compute instance screen, enter the following information:

   - **Virtual machine type**: Select `CPU`.
   - **Virtual machine size**: Select `Select from recommended options` and then select `Standard_DS3_v2`.

   ![On the create compute instance dialog, CPU is selected for the virtual machine type. Select from recommended options is selected under virtual machine size, and Standard_DS3_v2 is selected and highlighted in the recommended virtual machine sizes.](media/machine-learning-studio-create-compute-instance-select-virtual-machine.png "Select virtual machine")

4. Select **Next** to move to the virtual machine settings tab.

5. On the **Configure Settings** tab, configure the following:

   - **Compute name**: Enter `csdl-compute-SUFFIX`, where SUFFIX is your Microsoft alias, initials, or other value to ensure uniquely named resources.

   ![On the configure settings dialog, csdl-compute-SUFFIX is entered into the compute name box.](media/machine-learning-studio-create-compute-instance-configure-settings.png "Configure compute instance settings")

6. Select **Create** and wait for the Compute Instance to be ready. It takes approximately 3-5 minutes for the compute provisioning to complete.

### Task 6: Import the Lab Notebooks

In this task, you import Jupyter notebooks from GitHub that you will use to complete the exercises in this hands-on lab.

1. Select the Compute Instance, **csdl-compute-SUFFIX**, and then select **Jupyter** link to open Jupyter Notebooks interface.

   ![The Jupyter link is highlighted next to the csdl-compute-SUFFIX compute instance.](media/ml-workspace-compute-instances.png "Compute instances")

2. Check **Yes, I understand** and select **Continue** in the trusted code dialog.

   ![In the Always use trusted code dialog, Yes, I understand is checked, and the continue button is highlighted.](media/trusted-code-dialog.png "Always use trusted code")

3. In the new Jupyter window, select **New** and then select **Terminal** from the context menu.

   ![In the Jupyter notebooks interface, the New dropdown is selected, and Terminal is highlighted in the context menu.](media/jupyter-new-terminal.png "Open new terminal window")
  
4. Run the following commands in order in the terminal window:

   - `mkdir mcw-csdl`
   - `cd mcw-csdl`
   - `git clone https://github.com/microsoft/MCW-Cognitive-services-and-deep-learning.git`

   ![In the Jupyter terminal window, the commands listed above are displayed.](media/jupyter-terminal.png "Import repository")

5. Wait for the `clone` command to finish importing the repo.

You should follow all these steps provided *before* attending the Hands-on lab.
