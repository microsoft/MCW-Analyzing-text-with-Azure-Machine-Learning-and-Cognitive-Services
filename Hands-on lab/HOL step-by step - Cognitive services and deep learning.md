![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Cognitive services and deep learning
</div>

<div class="MCWHeader2">
Hands-on lab step-by-step
</div>

<div class="MCWHeader3">
June 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only, and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third-party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

©  2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are the property of their respective owners.

# Cognitive services and deep learning hands-on lab step-by-step

## Contents

- [Abstract and learning objectives](#abstract-and-learning-objectives)
- [Overview](#overview)
- [Solution architecture](#solution-architecture)
- [Requirements](#requirements)
- [Exercise 1: Setup Azure Machine Learning accounts](#exercise-1-setup-azure-machine-learning-accounts)
  - [Task 1: Provision Azure Machine Learning Experimentation service](#task-1-provision-azure-machine-learning-experimentation-service)
  - [Task 2: Create the Azure Machine Learning project](#task-2-create-the-azure-machine-learning-project)
- [Exercise 2: Create and Deploy an Unsupervised Model](#exercise-2-create-and-deploy-an-unsupervised-model)
  - [Task 1: Deploy your ACS cluster](#task-1-deploy-your-acs-cluster)
  - [Task 2: Install dependencies](#task-2-install-dependencies)
  - [Task 3: Set Visual Studio Code as the project IDE in Workbench](#task-3-set-visual-studio-code-as-the-project-ide-in-workbench)
  - [Task 4: Create the Summarization service](#task-4-create-the-summarization-service)
  - [Task 5: Deploy the Summarization service](#task-5-deploy-the-summarization-service)
- [Exercise 3: Applying TensorFlow](#exercise-3-applying-tensorflow)
  - [Task 1: Prepare TensorFlow](#task-1-prepare-tensorflow)
  - [Task 2: Train and deploy the TensorFlow model](#task-2-train-and-deploy-the-tensorflow-model)
- [Exercise 4: Completing the solution](#exercise-4-completing-the-solution)
  - [Task 1: Deploy the Computer Vision API](#task-1-deploy-the-computer-vision-api)
  - [Task 2: Deploy the Text Analytics API](#task-2-deploy-the-text-analytics-api)
  - [Task 3: Completing the solution](#task-3-completing-the-solution)
- [After the hands-on lab](#after-the-hands-on-lab)
  - [Task 1: Clean up lab resources](#task-1-clean-up-lab-resources)

## Abstract and learning objectives

In this hands-on lab, you will implement a solution which combines both pre-built artificial intelligence (AI) in the form of various Cognitive Services, with custom AI in the form of services built and deployed with Azure Machine Learning services. You will learn to create intelligent solutions atop unstructured text data by designing and implementing a text analytics pipeline. You will discover how to build a binary classifier using a simple neural network that can be used to classify the textual data, as well as how to deploy multiple kinds of predictive services using Azure Machine Learning and learn to integrate with the Computer Vision API and the Text Analytics API from Cognitive Services.

At the end of this hands-on lab, you will be better able to implement solutions leveraging Azure Machine Learning services and Cognitive Services.

## Overview

In this workshop, you will help Contoso Ltd. build a proof of concept that shows how they can build a solution that amplifies the claims processing capabilities of their agents.

## Solution architecture

The high-level architecture of the solution is illustrated in the diagram. The lab is performed within the context of a Jupyter Notebook running within a VM on Azure. Various notebooks are built to test the integration with the Cognitive Services listed, to train customer ML services, and to integrate the results in a simple user interface that shows the result of processing the claim with all of the AI services involved.

![The High-level architectural solution begins with a Claim, which points to Jupyter notebook. Jupyter then points to Computer Vision, Text Analytics, and Containerized Services, which includes a Classification Service and a Summary Service that both process claim text.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image2.png "High-level architectural solution")

## Requirements

1.  Microsoft Azure subscription must be pay-as-you-go or MSDN

    a.  Trial subscriptions will not work. You will run into issues with Azure resource quota limits.

    b.  Subscriptions with access limited to a single resource group will not work. You will need the ability to deploy multiple resource groups.

## Exercise 1: Setup Azure Machine Learning accounts

Duration: 45 minutes

In this exercise, you will setup your Azure Machine Learning Experimentation and Model Management Accounts and get your project environment setup.

### Task 1: Provision Azure Machine Learning Experimentation service

1.  Navigate to the Azure Portal

2.  Select **Create a resource**

    ![Screenshot of the Create a resource button.](media/azure-portal-create-a-resource.png "Create a resource button")

3.  Select **AI + Machine Learning** and then select **Machine Learning Experimentation**

    ![In the New blade, AI + Machine Learning is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image19.png "New blade")

4.  On the **ML Experimentation** blade, provide the following:

    a.  **Experimentation account name**: provide a name for your experimentation account

    b.  **Subscription:** select your Azure subscription

    c.  **Resource group**: select the mcw-ai-lab resource group you previously created

    d.  **Location**: select the region nearest to where you deployed your lab VM. It's OK if they are not exactly in the same region, but try to select a region that is close to minimize latency.

    e.  **Number of seats**: leave at 2

    f.  **Storage account**: select create new and provide a unique name for the new storage account

    g.  **Workspace for Experimentation account**: provide a unique name for the workspace

    h.  **Assign owner for the workspace**: leave the owner assigned to you

    i.  **Create Model Management account**: leave checked

    j.  **Account name**: provide a name for your model management account

    k.  **Model Management pricing tier**: select the S1 pricing tier

    ![The ML Experimentation blade fields are set to the previously defined settings.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image20.png "ML Experimentation blade")

5.  Select **Create** to provision the Experimentation and Model Management Service. The deployment should take about 2 minutes.

6.  When the deployment completes, navigate to your mcw-ai-lab resource group and confirm that you see an instance of Machine Learning Experimentation and Machine Learning Model Management

    ![Both Machine Learning Experimentation and Machine Learning Model Management are called out in the Resource group list.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image21.png "Resource group")

### Task 2: Create the Azure Machine Learning project

1.  Connect to the labvm via RDP. If you stopped the VM, remember to Start it up again before attempting to connect.

2.  From the **Start** menu, launch **Azure Machine Learning Workbench**

3.  Select **Sign in with Microsoft**\
    ![Screenshot of the Azure Machine Learning Workbench Start menu icon.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image22.png "Azure Machine Learning Workbench Start menu icon")

4.  Sign in with the credentials you used when creating the Experimentation Service in the Azure Portal\
    ![Screenshot of the Microsoft Azure sign in screen.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image23.png "Microsoft Azure sign in screen")

5.  After successfully signing in, the Workbench interface should appear and list the experimentation workspace that you created\
    ![Screenshot of the Workbench window.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image24.png "Workbench window")

6.  From the **File** Menu, select **New Project...**\
    ![In the Workbench File menu, New Project is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image25.png "Workbench File menu")

7.  In the **New Project** blade that appears, provide the following:

    a.  **Project name**: mcw-ai-lab

    b.  **Project directory**: C:\HOL

    c.  **Project description**: leave blank

    d.  **Vistualstudio.com GIT Repository URL**: leave blank

    e.  **Selected workspace**: select the ML Experimentation Workspace you created\
        ![Fields in the New Project blade display the previously defined settings.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image26.png "New Project blade")

8.  In the Search Project Templates, enter **TDSP** and select the item called **TDSP Template**\
    ![Screenshot of the TDSP Tile.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image27.png "TDSP Tile")

9.  Select **Create**

10. The template will download and in a few moments you should see the TDSP project dashboard\
    ![Screenshot of the TDSP project dashboard.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image28.png "TDSP project dashboard")

## Exercise 2: Create and Deploy an Unsupervised Model

Duration: 60 minutes

In this exercise, you will create and deploy a web service that uses a pre-trained model to summarize long paragraphs of text. 

### Task 1: Deploy your ACS cluster

1.	Navigate to the Azure Portal

2.	Select All Services, Subscriptions and then select your subscription from the list

3.	Under the Settings grouping, select Resource Providers\
    ![Screenshot of the Settings tabs for a selected subscription in the Azure Portal](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image74.png "Settings")
 
4.	Search for “container,” and in the list that appears, verify that all resource providers related to containers are registered. If not, select the Register link next to the items that are not registered.
    ![Screenshot showing the search results for providers with the name container](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image75.png "Search resource providers")
 
5.  Within Workbench, from the **File** menu, select **Open Command Prompt**

6.  Create the cluster environment by running the following command and replace the values indicated in angle brackets with the appropriate values. This will create new resources groups for the cluster.

    a.  For \<environment name\> enter mcwailabenv, or something similar. This value can only contain lowercase alphanumeric characters.

    b.  For location, use eastus2, westcentralus, australiaeast, westeurope, or southeastasia, as those are the only acceptable values at this time

    ```sh
    az ml env setup -c -n <environment name> --location <e.g. eastus2>
    ```

7.  If prompted, copy the URL presented and sign in using your web browser

8.  Enter the code provided in the command prompt
    ![Screenshot of the Device Login page](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image34.png "Device Login page")

9.  Select **Continue**\
    ![The Device Login page now displays the code.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image35.png "Device Login page")

10.  Sign in with your Azure Credentials\
    ![The Microsoft Azure sign in page displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image36.png "Microsoft Azure sign in page")

11.  Return to the command prompt, which should automatically update after you log in

12.  At the "Subscription set to <subscription name>" prompt, enter **Y** if the subscription name is correct, or **N** to select the subscription to use from a list
    ![In the Command Prompt window, the updates display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image37.png "Command prompt window")

9.  It will take 10-20 minutes for your ACS cluster to be ready. You can periodically check on the status by running the command shown in the output to the previous step, which is of the form:

    ```sh
    az ml env show -g <resourceGroupName> -n <clusterName>
    ```

10. **Continue on with the lab while your ACS cluster provisions**



### Task 2: Install dependencies

The tasks that follow depend on Python libraries, like nltk and gensim. The following steps ensure you have these installed in your environment.

1.  From the **File** menu of Workbench, select **Open Command Prompt**

2.  Run the following command to install nltk:

    ```sh
    pip install nltk
    ```

1.  NLTK should install, with a message similar to the following:
    ![In the Command Prompt window, the previous commands and their output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image29.png "Command Prompt window")

4.  NLTK is a rich toolkit with modular components, many of which are not installed by default. To install all the components, run the python shell by entering **python** at the command prompt:

    ```sh
    python
    ```

5.  Within the python shell, run the following two lines:

    ```sh
    import nltk
    nltk.download('all')
    ```

6.  The downloader will take about 5 minutes to complete. Once it is finished, exit the python shell by entering:

    ```sh
    exit()
    ```

7.  Run the following command to install gensim:

    ```sh
    pip install gensim
    ```
    
    ![In the Command Prompt window, the previous command and its output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image30.png "Command Prompt window")

8.  Next, download a pre-built Jupyter Notebook that you will step through to understand the process used to summarize the text of the claims documents. In the browser on your VM, navigate to the following (note that the URL is case sensitive). Note, if using IE, you will need to modify the default security settings, which prevent files from being downloaded.

    <http://bit.ly/2G4hAQz>

9.  In the command prompt, enter the following and press enter to launch the Jupyter Notebook:

    ```sh
    jupyter notebook
    ```

    ![In the Command Prompt window, the command to launch the Jupyter Notebook displays. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image31.png "Command Prompt window")

10. In a few moments, you should be prompted for which browser to use to open the link

11. The Jupyter Notebook interface should appear in the browser, listing the contents of your project folder\
    ![The Jupyter Notebook interface displays the contents of the project folder.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image32.png "Jupyter Notebook interface")

12. Select the **code** folder

13. Select **01\_data\_acquisition\_and\_understanding**\
    ![Screenshot of the Code folder contents.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image33.png "Code folder")

14. Select the **Upload** button

15. Open the **Summarize.ipynb** notebook and follow the instructions within it

### Task 3: Set Visual Studio Code as the project IDE in Workbench

1.  Within Workbench, from the **File** menu, select **Configure Project IDE**\
    ![In the Workbench File menu, Configure Project IDE is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image39.png "Workbench, File menu")

2.  In the **Configure IDE** blade that appears, set the following properties:

    a.  **Name**: Visual Studio Code

    b.  **Executable Path**: C:\\Program Files\\Microsoft VS Code\\Code.exe\
        ![The Configure IDE blade displays the previously defined settings.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image40.png "Configure IDE blade")

3.  Select **OK**

4.  Launch Visual Studio Code for the project by selecting **Open Project (Visual Studio Code)** from the **File** menu\
    ![In the File menu, Open Project (Visual Studio Code) is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image41.png "File menu")

5.  You are now ready to author service script

### Task 4: Create the Summarization service

1.  Visual Studio Code will open against the project directory

2.  In the tree view, expand **code** and then right-click **03\_deployment** and select **New File**\
    ![The previously defined options are selected in the Visual Studio Code tree view.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image42.png "Visual Studio Code tree view")

3.  For the file name, enter summarizer\_service.py and press **Enter**

4.  In a browser, navigate to <http://bit.ly/2FLJn8Y> and copy the contents of the file

5.  Paste the contents of this script into your summarizer\_service.py. Take a moment to review the script, as it is effectively the same code you were running in the Jupyter notebook, except that is has been modified to follow the format required by services in Azure Machine Learning. The init method is called once per container by the Azure Machine Learning infrastructure when the service is deployed. It is here that we need to load all of the modules required by NLTK in the call to nltk.download. The run method is where any scoring (or in our case summarization) activity takes place.\
    ![In the Command Prompt window, the script that you copied displays. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image43.png "Command Prompt window")

6.  Next, we need to capture the dependencies for the modules used by the script. These are declared in a conda environment file, which you can generate from an environment or create by hand. In this case, we will edit the default conda environment provided by the TDSP project by hand, and add a configuration that will pip install gensim as required by our script. To do this, in Visual Studio Code, expand, aml\_config and open conda\_dependencies.yml.\
    ![In Visual Studio Code, MCW-AI-LAB is expanded, aml\_config is expanded, and conda\_dependencies.yml is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image44.png "Visual Studio Code")

7.  At the last line, under azure-ml-api-sdk add another line with -gensim to the pip configuration. You should also add entries for tensorflow and tflearn, which we will need later in the lab. Your final configuration should look as follows:

    ```yaml
    name: project_environment

    dependencies:
    - python=3.5.2
    - scikit-learn
    - pip:
      # The API for Azure Machine Learning Model Management Service.
      # Details: https://github.com/Azure/Machine-Learning-Operationalization
      - azure-ml-api-sdk==0.1.0a11
      - azureml.datacollector==0.1.0a13
      - gensim
      - tensorflow
      - tflearn
    ```

8.  Save the file. When we go to create the image in a later step, this file will be included with command.

9.  Next, create an empty file called dummy\_model.bin in the 03\_deployment folder. In this case, we don't have a model to deploy with this service, but we still need to provide one to the CLI as we will see in a moment. An empty file will do.

### Task 5: Deploy the Summarization service

1. Return to the Workbench and use the File menu to open another command prompt.

2. Wait for your ACS cluster to be ready. You can periodically check on the status by running the command shown in the output to the previous step, which is of the form:

    ```sh
    az ml env show -g <resourceGroupName> -n <clusterName>
    ```

3. Once the environment has successfully provisioned (the Provisioning State in the above command will read "Succeeded"), set your default environment with a command of the form:

    ```sh
    az ml env set -g \<resourceGroupName\> -n \<clusterName\>
    ```
    
    ![In the Command Prompt window, the previous commands and their output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image38.png "Command prompt window")

4. This will set the context of the command line to target this environment.

5. Finally, set the model management account, to be used by the command line, to be the one you created previously (mcw-ai-lab-model-mgmt). Run the following command, replacing the values indicated in angle brackets with appropriate values:

    a.  For \<acctname\>, enter the name of the Machine Learning Model Management resource in your mcw-ai-lab resource group.

    b.  For \<resourcegroupname\>, use your mcw-ai-lab resource group name.

    ```sh
    az ml account modelmanagement set -n <acctname> -g <resourcegroupname>
    ```

6.  At the command prompt, change directories to the code\\03\_deployment directory by executing the following command:

    ```sh
    cd code\03_deployment
    ```

7.  You can deploy the service using a single command (which orchestrates the multiple steps of creating a docker manifest, creating a docker image, and deploying a container instance from the image). The command needs to refer to all the components required for the service, including the dummy model file, the service script, the conda dependencies, and the runtime to use (python in this case). Run the following command to deploy the summarizer service:

    ```sh
    az ml service create realtime -n summarizer -c ..\..\aml_config\conda_dependencies.yml -m dummy_model.bin -f summarizer_service.py -r python
    ```

    ![In the Command Prompt window, the previous command and its output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image45.png "Command Prompt window")

8.  Notice in the output of the preceding command, you are provided with instructions (third line from last) on how you can invoke the deployed service using the CLI. Try executing the following command (modify the Service ID of you service as indicated in the previous command output):

    ```sh
    az ml service run realtime -i summarizer.[mcwailab-xyz.location] -d "I was driving down El Camino and stopped at a red light. It was about 3pm in the afternoon. The sun was bright and shining just behind the stoplight. This made it hard to see the lights. There was a car on my left in the left turn lane. A few moments later another car, a black sedan pulled up behind me. When the left turn light changed green, the black sedan hit me thinking that the light had changed for us, but I had not moved because the light was still red. After hitting my car, the black sedan backed up and then sped past me. I did manage to catch its license plate. The license plate of the black sedan was ABC123."
    ```

    ![In the Command Prompt window, the previous text displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image46.png "Command Prompt window")

9.  If you get a summary back, your service is working! Try calling the service with other text and observe the summary returned. Note that the service tries to build a summary of about 30 words, so if you provide too short a text, an empty summary will be returned.

10.  Finally, in a notepad or other location take note of the full Service ID (e.g., summarizer.mcwailab-xyz.location) and the authorization key, which you will need later in the lab. To get the authorization key for your deployed service, run the following command and take note of the PrimaryKey value in the output:

        ```sh
        az ml service keys realtime -i summarizer.[mcwailab-xyz.location]
        ```

        ![In the Command Prompt window, the previous command and its output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image47.png "Command Prompt window")

## Exercise 3: Applying TensorFlow

Duration: 60 minutes

In this exercise, you will use TensorFlow to construct and train a simple deep neural network classification model that will classify claim text as belonging to a home insurance claim or an automobile claim. You will then deploy this trained model as a web service.

### Task 1: Prepare TensorFlow

1.  Return to your RDP session to the Lab VM

2.  Switch to the command prompt that is running the Jupyter Notebook command and press **Control + Break**. This will stop the Jupyter Notebook process while you update TensorFlow.

3.  From the command line run:

    ```sh
    pip install tensorflow
    ```

4.  In a few moments, the install should complete, and you should see output ending similar to the following:\
    \
    ![In the Command Prompt window, output indicates that the file was successfully installed. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image48.png "Command Prompt window")

5.  We will be using the TFLearn library which sits atop TensorFlow. To install it run:

    ```sh
    pip install tflearn
    ```

    ![In the Command Prompt window, the installation progress and the success message displays. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image49.png "Command Prompt window")

6.  Run "Jupyter Notebook" to re-start the process

7.  You should now be ready to use TensorFlow on your lab VM

### Task 2: Train and deploy the TensorFlow model

1.  Return to your RDP session to the lab VM

2.  Download the TensorFlow notebook, text analytics helper module and sample data from the following link:

    <http://bit.ly/2pucpje>

3.  Extract this zip and copy the contents to C:\\HOL\\mcw-ai-lab\\code\\02\_modeling

4.  Return to the instance of the Jupyter Notebook home that should be open in your browser

    ![The Jupyter Notebook interface displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image50.png "Jupyter Notebook")

5.  Select the code folder**, 02\_modeling**. You should see a folder listing similar to the following. Select **Claim Classification.ipynb**.

    ![The 02\_modeling code folder contents display.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image51.png "Code folder contents")

6.  The Claim Classification notebook will appear. Step through this notebook to read how the data is prepared and the neural network model is trained. Be sure to execute each cell as you get to it.

7.  When you have finished executing the notebook, some model files will have been produced. Using File Explorer, navigate to **C:\\HOL\\mcw-ai-lab\\code\\02\_modeling**, you should see the three new files (each beginning with claim\_classifier.tfl).

    ![In File Explorer, three claim\_classifier files are selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image52.png "File Explorer")

8.  Copy these three files and paste them under C:\\HOL\\mcw-ai-lab\\code\\03\_deployment\\claim\_class\_service. You are copying these over so they can be used by the predictive web service we will deploy.

    ![In File Explorer, the same three claim\_classifier files display in the previously defined address.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image53.png "File Explorer ")

9.  Next, download the supporting files for the claim\_class\_service from:

    <http://bit.ly/2u5DoGH>

10. Extract the files and copy them into C:\\HOL\\mcw-ai-lab\\code\\03\_deployment\\claim\_class\_service

11. Return to the instance of the Jupyter Notebook home that should be open in your browser

12. Select the code folder, **03\_deployment** and then **claim\_class\_service**

13. Open **claim\_class\_service.py**. Observe that the code it uses is like what you ran in the Claim Classification notebook, only formatted to fit the structure of an Azure Machine Learning web service (with init and run methods).

    ![Screenshot of the Jupyter code window. At this time, we are unable to capture all of the information in the Jupyter code window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image54.png "Jupyter code window")

14. Next, you will deploy this service. Switch to your command line window and navigate to **C:\\HOL\\mcw-ai-lab\\code\\03\_deployment\\claim\_class\_service**.

15. Run the following command in the context of the claim\_class\_service folder to deploy the service:

    ```sh
    az ml service create realtime -n claimclassifier -c ..\..\..\aml_config\conda_dependencies.yml -m claim_classifier.tfl.meta -f claim_class_service.py -r python -d claim_classifier.tfl.data-00000-of-00001 -d claim_classifier.tfl.index -d claims_text.txt -d textanalytics.py -d contractions.py
    ```

> ![In the Command Prompt window, the previous command and its output displays. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image55.png "Command Prompt window")

16. Next, test the deployed service by running the following command (substitute the values of the Service ID as indicated in the last line of the previous):

    ```sh
    az ml service run realtime -i claimclassifier.[mcwailab-xyz.location] -d "A tornado ripped through my home."
    ```

    ![In the Command Prompt window, the previous command and its output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image56.png "Command Prompt window")

17. Recall the classifier will return 1 if the text is classified as related to a car insurance claim and 0 if the claim pertains to a home insurance claim. Try submitting a few different sentences to the service.

18. Next, in a notepad or other location take note of the full Service ID (e.g., claimclassifier.mcwailab-xyz.location) and the authorization key which you will need later in the lab. To get the authorization key for your deployed service, run the following command and take note of the PrimaryKey value in the output:

    ```sh
    az ml service keys realtime -i claimclassifier.[mcwailab-xyz.location]
    ```

    ![In the Command Prompt window, the previous command and its output display. At this time, we are unable to capture all of the information in the command prompt window. Future versions of this course should address this.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image57.png "Command Prompt window")

19. Finally, run the following command to retrieve the IP address of your claimclassifier and summarizer services, and note the value in notepad or other location for use later in the lab. The IP address will be the same for both services.

    ```sh
    az ml service usage realtime -i claimclassifier.[mcwailab-xyz.location]
    ```

    ![In the Command Prompt window, the IP address displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image58.png "Command Prompt window")

## Exercise 4: Completing the solution

Duration: 45 minutes

In this exercise, you will perform the final integration with the Computer Vision API and the Text Analytics API along with the Azure Machine Learning Services you previously deployed, to deliver the completed proof of concept solution.

### Task 1: Deploy the Computer Vision API

1.  Navigate to the Azure Portal in your browser

2.  Select **Create a resource**

3.  Select **AI + Machine Learning** and then **Computer Vision API.**\
    ![In the New blade, the AI + Machine Learning option is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image19.png "New blade")

4.  On the **Create** blade, provide the following:

    a.  **Name:** provide a unique name for this instance.

    b.  **Subscription:** select your Azure subscription.

    c.  **Location**: select a location nearest your other deployed services.

    d.  **Pricing tier**: select S1.

    e.  **Resource group**: select the existing mcw-ai-lab resource group\
        ![The Create blade fields display the previously defined settings.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image60.png "Create blade")

5.  Select **Create**

6.  When the notification appears that the deployment succeeded, select **Go to resource**

    ![A Deployment succeeded notification displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image61.png "Notification")

7.  Select **Keys** and then copy the value of Key 1 into notepad or something similar as you will need this value later in the lab

    ![In the Cognitive Services blade, under Resource Management, Keys is selected. ](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image62.png "Cognitive Services blade")

8.  Select **Overview** and copy the value of Endpoint from the Essentials panel. Store this value in notepad or something similar as you will need this value later in the lab.

    ![In the Cognitive Services blade, the Endpoint URL is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image63.png "Cognitive Services blade")

### Task 2: Deploy the Text Analytics API

1.  Navigate to the Azure Portal in your browser

2.  Select **Create a resource**

3.  Select **AI + Cognitive Services** and then **Text Analytics API**

    ![In the New blade, both AI + Cognitive Services and Text Analytics API are selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image64.png "New blade")

4.  On the **Create** blade, provide the following:

    a.  **Name**: provide a unique name for this instance

    b.  **Subscription**: select your Azure subscription

    c.  **Location**: select a location nearest your other deployed services

    d.  **Pricing tier**: select S0

    e.  **Resource group**: select the existing mcw-ai-lab resource group\
        ![The Create blade fields are set to the previously defined settings.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image65.png "Create blade")

5.  Select **Create**

6.  When the notification appears that the deployment succeeded, select **Go to resource**

    ![A Deployment succeeded notification displays.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image66.png "Notification")

7.  Select **Keys**, and then copy the value of Key 1 into notepad or something similar as you will need this value later in the lab.

    ![In the Cognitive Services blade, under Resource Management, Keys is selected. ](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image67.png "Cognitive Services blade")

8.  Select **Overview** and copy the value of Endpoint from the Essentials panel. Store this value in notepad or something similar as you will need this value later in the lab.

    ![In the Cognitive Services blade, the Endpoint URL is selected.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image68.png "Cognitive Services blade")

### Task 3: Completing the solution

1.  Return to your RDP session to the lab VM

2.  Download the starter files for this task from:

    <http://bit.ly/2puj7oL>

3.  Extract the contents of this zip file to C:\\HOL\\mcw-ai-lab\\code\\03\_deployment

4.  Return to the instance of the Jupyter Notebook home that should be open in your browser

    ![The Jupyter Notebook home page displays in a browser window.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image50.png "Jupyter Notebook")

5.  Select the code folder, **03\_deployment**. You should see a folder listing like the following. Select **Cognitive Services.ipynb**.

    ![In the Jupyter notebook, the 03\_deployment folder contents display.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image69.png "Jupyter notebook")

6.  Follow the steps within the notebook to complete the lab and view the result of combining Cognitive Services with your Azure Machine Learning Services.

    ![The Claim Summary results display.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image70.png "Claim Summary results")

## After the hands-on lab

Duration: 5 minutes

To avoid unexpected charges, it is recommended that you clean up all of your lab resources when you complete the lab.

### Task 1: Clean up lab resources

1.  Navigate to the Azure Portal and locate the Resource Groups you created for this lab

    a.  mcw-ai-lab

    b.  mcwailabenv (note there are two resources groups starting with this name, so delete both)

2.  Select **Delete resource group** from the command bar

    ![Screenshot of the Delete resource group button.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image71.png "Delete resource group button")

3.  In the confirmation dialog that appears, enter the name of the resource group and select **Delete**

4.  Wait for the confirmation that the Resource Group has been successfully deleted. If you don't wait, and the delete fails for some reason, you may be left with resources running that were not expected. You can monitor using the Notifications dialog, which is accessible from the Alarm icon.

    ![The Notifications dialog box has a message stating that the resource group is being deleted.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image72.png "Notifications dialog box")

5.  When the Notification indicates success, the cleanup is complete

    ![The Notifications dialog box has a message stating that the resource group has been deleted.](images/Hands-onlabstep-bystep-CognitiveServicesanddeeplearningimages/media/image73.png "Notifications dialog box")

You should follow all steps provided *after* attending the Hands-on lab.
