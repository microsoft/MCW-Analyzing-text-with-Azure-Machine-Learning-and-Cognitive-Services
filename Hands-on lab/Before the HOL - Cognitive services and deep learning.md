![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png 'Microsoft Cloud Workshops')

<div class="MCWHeader1">
Cognitive services and deep learning
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
June 2020
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2020 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Cognitive services and deep learning before the hands-on lab setup guide](#cognitive-services-and-deep-learning-before-the-hands-on-lab-setup-guide)
  - [Requirements](#requirements)
  - [Before the hands-on lab](#before-the-hands-on-lab)

<!-- /TOC -->

# Cognitive services and deep learning before the hands-on lab setup guide

## Requirements

1. Microsoft Azure subscription must be pay-as-you-go or MSDN

   - Trial subscriptions will not work. You will run into issues with Azure resource quota limits.

   - Subscriptions with access limited to a single resource group will not work. You will need the ability to deploy multiple resource groups.

## Before the hands-on lab

Duration: 25 minutes

### Task 1: Create an Azure Machine Learning workspace

1. Sign in to [Azure portal](https://portal.azure.com) by using the credentials for your Azure subscription.

2. In the upper-left corner of Azure portal, select **+ Create a resource**.

3. Select **AI + Machine Learning, Machine Learning**.

      ![The Create a resource page displays AI + Machine Learning and Machine Learning selected.](images/01.png 'Open Create Azure Machine Learning Workspace')

4. Provide the following information to configure your new workspace:

   - **Subscription**: Select the Azure subscription that you want to use.

   - **Resource group**: Use an existing resource group in your subscription or enter a name to create a new resource group. A resource group holds related resources for an Azure solution. In this example, we use **mcwailab**.
  
   - **Workspace name**: Enter a unique name that identifies your workspace. In this example, we use **mcw-csdl**. Names must be unique across the resource group. Use a name that's easy to recall and to differentiate from workspaces created by others.

   - **Location**: Select the location closest to your users and the data resources to create your workspace.

   - **Workspace edition**: **Basic**. The workspace type (Basic & Enterprise) determines the features to which you’ll have access and pricing. Exercises in this tutorial works on either Basic or Enterprise editions.

   ![The Machine Learning Create form is displayed populated with the aforementioned values. The Review + Create button is highlighted.](images/02.png 'Create Azure Machine Learning Workspace page')

5. After you are finished configuring the workspace, select **Review + Create**. Select **Create** after you review the fields you just entered.

    > **Note**: It can take several minutes to create your workspace in the cloud. When the process is finished, a deployment success message appears.

6. To view the new workspace, select **Go to resource**.

   ![The overview page shows your deployment is complete message and go to resource button highlighted.](images/03.png 'Go to Azure Machine Learning workspace')

### Task 2: Create a Compute Instance

1. From within your Azure Machine Learning workspace, select **Compute, Compute instances** in the left navigation and then select **Create new compute instance**.

   ![The Compute section of the Azure Machine Learning workspace showing create new compute instance button selected.](images/04.png 'Create New Compute Instance')

2. Provide the following information and then select **Create**:

    a. Compute name: `csdl-compute`

    b. Virtual machine type: `CPU (Central Processing Unit)`

    c. VM machine size: `Standard_DS3_V2`

   ![The new compute instance form is displayed populated with the aforementioned values. The Create button is highlighted.](images/05.png 'Create New Compute Instance')

   >**Note**: If the Compute Instance names should be unique within an Azure Region notification appears, choose a different name that is unique to your environment.
  
3. Wait for the Compute Instance to be ready, it will take around 3-5 minutes.

### Task 3: Import the Lab Notebooks

1. Select the Compute Instance: **csdl-compute** and then select **Jupyter** open icon, to open Jupyter Notebooks interface.

   ![The Compute section of the Azure Machine Learning workspace showing the Jupyter link selected for the compute instance csdl-compute.](images/06.png 'Open Jupyter Notebooks')

2. Select **New, Terminal** as shown to open the terminal page.

   ![Jupyter Notebooks interface showing how to open a new terminal window.](images/07.png 'Open Terminal Window')
  
3. Run the following commands in order in the terminal window:

   a. `mkdir mcw-csdl`

   b. `cd mcw-csdl`

   c. `git clone https://github.com/microsoft/MCW-Cognitive-services-and-deep-learning.git`

      ![Jupyter terminal window showing aforementioned commands to clone the github repository.](images/08.png 'Import Repository')

   d. Wait for the import to complete.

You should follow all these steps provided *before* attending the Hands-on lab.
