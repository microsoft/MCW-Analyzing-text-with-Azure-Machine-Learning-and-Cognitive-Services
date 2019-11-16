![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Cognitive services and deep learning
</div>

<div class="MCWHeader2">
Whiteboard design session student guide
</div>

<div class="MCWHeader3">
September 2019
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only, and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third-party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2019 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are the property of their respective owners.

**Contents**

<!-- TOC -->

- [Cognitive services and deep learning whiteboard design session student guide](#cognitive-services-and-deep-learning-whiteboard-design-session-student-guide)
  - [Abstract and learning objectives](#abstract-and-learning-objectives)
  - [Step 1: Review the customer case study](#step-1-review-the-customer-case-study)
    - [Customer situation](#customer-situation)
    - [Customer needs](#customer-needs)
    - [Customer objections](#customer-objections)
    - [Infographic for common scenarios](#infographic-for-common-scenarios)
  - [Step 2: Design a proof of concept solution](#step-2-design-a-proof-of-concept-solution)
  - [Step 3: Present the solution](#step-3-present-the-solution)
  - [Wrap-up](#wrap-up)
  - [Additional references](#additional-references)

<!-- /TOC -->

#  Cognitive services and deep learning whiteboard design session student guide

## Abstract and learning objectives 

In this whiteboard design session, you will work with a group to design a solution which combines both pre-built artificial intelligence (AI) in the form of various Cognitive Services, with custom AI in the form of services built and deployed with Azure Machine Learning service. You will learn to create intelligent solutions atop unstructured text data by designing and implementing a text analytics pipeline. You will discover how to build a binary classifier using a simple neural network that can be used to classify the textual data, as well as how to deploy multiple kinds of predictive services using Azure Machine Learning service and learn to integrate with the Computer Vision API and the Text Analytics API from Cognitive Services.

At the end of this whiteboard design session, you will be better able to design solutions leveraging the Azure Machine Learning service and Cognitive Services.

## Step 1: Review the customer case study 

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions: With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1.  Meet your table participants and trainer.

2.  Read all of the directions for steps 1-3 in the student guide.

3.  As a table team, review the following customer case study.

### Customer situation

Contoso Ltd is a large corporation, headquartered in the United States that provides insurance packages for U.S. consumers. Its products include accident and health insurance, life insurance, travel, home, and auto coverage.

Contoso is looking to build a next-generation platform for its insurance products and had identified claims processing as the first area in which they would like to focus their efforts. Currently customers submit a claim using either the website, their mobile app or by speaking with a live agent.

A claim includes the following information:

-   Information about the insured (contact information, policy number, etc.)

-   Free text responses describing the claim (details of what happened, what was affected, the conditions in which it occurred)

-   Photographs that support the claim (photos of the insured object before the event, photos of the damage or stolen items, etc.)

When an agent (an employee or contractor of Contoso) is processing a claim, there are multiple challenges that add significantly to the cost, including the significant time it takes for an agent to read through and process the content submitted with each claim, as well as the difficulty they have in finding particular claim artifacts when returning to a claim after a while. While each claim is stored in a database, the details about the claim, including the free text responses and supporting photos, are stored as opaque attachments that are not searchable - meaning agents typically pull up the claim by the claim number or the insured's contact information and then must manually read through the attachments.

Also, there are some common challenges that Contoso is hoping they could automate away. According to Francine Fischer, CIO, there are two sets of issues where they envision amplifying the capabilities of their agents with AI.

One set of such issues deals with the free text responses. The first issue Contoso identified is that each claim detail should be automatically classified as either home or auto based on the text. This classification would be displayed in the claim summary, so an agent can quickly assess whether they are dealing with purely a home claim, an auto claim or a claim that has a mixture of the two.

The second issue is Contoso would like to experiment applying sentiment analysis to the claim text. They know most customers are either  factual in their description (a neutral sentiment) or slightly unhappy (a more negative sentiment), but believe that a negative sentiment can be an indicator to claim text that involves a more severe situation, which might warrant an expedited review by an agent.

The third issue with the free text is that some of the responses are long. When agents are shifting between claims, it can be hard for them to recall which response had the details for which they are looking. Contoso would like to experiment with an automatic summarization of long claims that produces a summary of about 30 words in length. This summarization would enable the agent to get the gist before having to read the full claim and can quickly remind themselves of the claim when revisiting it.

The next set of issues where they would like to amplify the capabilities of their agents have to deal with extracting information from the photos submitted to increase their searchability. The first item they would like to address is providing automatic captions describing the contents of the photo. Second, they would like to automatically apply tags that describe the content of the photo. Third, the solution should try to pull out any text that appears in the image. Taken together, solving these items can reduce the amount of data entry an agent has to do, while simultaneously increasing the searchability for content present in photos.

As a final step, they would like to organize the information extracted from photos, tying it together with the results of processing the free text responses into a solution that is easily searchable and stays up to date as new claim information surfaces.

As a first step towards their bigger goals, Contoso would like to build a proof of concept (PoC) for an intelligent solution that could automate all the above. They would like to build this PoC to build upon their claims submission solution they already have running in Azure (which consists of a Web App for claims submission and a SQL Database for claim storage). They believe this might be possible using AI, machine learning or deep learning and would like to build a proof of concept to understand just how far they can go using these technologies.

### Customer needs 

1.  We receive a lot of useful information in the free text responses, but because they can be long, agents sometimes skip over them and miss vital details or spend too much time looking for a particular detail when returning to a claim. We aren't certain this can be automated, but we would like to have a standardized process that identifies the key entities in a claim and pulls them out into a separate list that agents can more easily review, and then click to view the entity in the context of the claim.

2.  We need a solution that can "look" at a photo and give us a description of the photos contents and tag the photos with keywords, so agents can more easily find and refer to the photo later

3.  We are looking to amplify the capabilities of our agents and improve their claims processing capabilities - not replace them. We want a solution that does the same.


### Customer objections 

1.  We are skeptical about all the hype surrounding these "AI" solutions. It's hard to know what is feasible versus what is not possible with today's technology and Azure.

2.  We know that are both pre-built AI and custom AI options available. We are confused as to when to choose one over the other.

3.  We expect some part of our solution would require deep learning. Do you have any prescriptive guidance on how we might choose between investing in learning and using TensorFlow or the Microsoft Cognitive Toolkit (CNTK)?


### Infographic for common scenarios

![In the Traning a classification model with text diagram, Document labels points to Supervised ML or DL Algorithm, which points to Classification Model. Documents points to Text Normalization, which points to Feature Extraction, which points to Supervised ML or DL Algorithm. Vectors points to a table of words and percentages.](images/Whiteboarddesignsessiontrainerguide-CognitiveServicesanddeeplearningimages/media/image2.png "Traning a classification model with text diagram")

![The Predicting a classification from text diagram has Documents, which points to Text Normalization, which points to Feature Extraction, which points to Classification Model, which points to Document Labels. Vectors points to a table of words and percentages.](images/Whiteboarddesignsessiontrainerguide-CognitiveServicesanddeeplearningimages/media/image3.png "Predicting a classification from text diagram")

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions:  With all participants at your table, answer the following questions and list the answers on a flip chart:

1.  Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2.  What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

_High-level architecture_

1.  Without getting into the details (the following sections will address the details), diagram your initial vision for handling the top-level requirements for processing the claims textual data, photos, and enabling search. You will refine this diagram as you proceed.

_Classifying claim-text data_

1.  What is the general pipeline for approaching the training of text analytic models such as this? What are the general steps you need to take to prepare the text data for performing tasks like classification?

2.  What data would they need to train the model?

3.  Contoso want to understand some of the common approaches to handle texts for machine learning? Is there a recommended approach to dealing with long descriptive texts that are typically found in claims data?

4.  Contoso understands they should use a classification algorithm for this problem. They have asked if a Deep Neural Network could be trained against the text to recognize home or auto classifications. Could they use a DNN for this?

5.  For this scenario, Contoso has indicated an interest in using TensorFlow, but is concerned about the complexity of jumping right in. They are wondering if Keras would provide an easier framework they could use as a stepping stone to the full blown TensorFlow, that would enable them to build TensorFlow compatible models so that they can "graduate" to using TensorFlow when the team is ready?

6.  What would a very simple DNN that performs this classification look like? Sketch the graph of input nodes, hidden layer nodes, and output nodes.

7.  Assuming they will be using a fully connected DNN with a sigmoid activation function to train the classifier using Keras, pseudo code the code you would write to construct the network you just illustrated.

8.  Next, pseudo code how they would construct the DNN from the network and fit the model to the data

9.  With the trained model in hand, pseudo code how the model would be used to predict the class of a given claim text. What would the output of the prediction be? How would you interpret the value?

10.  Describe at a high level, how you would deploy this trained model, so it is available as a web service that can be integrated with the rest of the solution.

_Identifying free-text sentiment_

1.  How would you recommend Contoso identify the sentiment in the free-response text provided associated with a claim? Would this require you to build a custom AI model? Is there a pre-built AI service you could use?

2.  For the solution you propose, what is the range of value of the sentiment score and how would you interpret that value?

_Summarizing claim text_

1.  The team at Contoso has heard about a Python library called gensim that has a summarize function. Given an input of text, it can extract a summary of the desired length. Contoso would like their PoC to implement its summarization functionality initially using gensim. However, the process they follow to deploy the summarization capability should also enable them to replace the use of gensim with another library or with the use of their own custom trained models if desired down the road. Describe how Contoso should deploy the summarization service to meet these requirements?

2.  Can they deploy a predictive web service to Azure Machine Learning service that does not utilize an external model (as in the case with gensim) or would support an unsupervised approach?

_Captions, tags and "reading" images_

1.  How would you recommend Contoso implement support for automatically creating captions for the claim photos? Similarly, how would they automatically generate tags? Would this require you to build a custom AI model? Is there a pre-built AI service you could use?

2.  Describe the flow of processing of an image as input; what value is returned by each component in your proposed solution for captioning and tagging images?

3.  How would you recommend Contoso implement support for "reading" any text that appears within an image, so that it could be searched later? Would this require you to build a custom AI model? Is there a pre-built AI service you could use?

4.  Describe the flow of processing of an image as input; what value is returned by each component in your proposed solution for "reading" images?

_Enabling search_

1.  What service would you recommend Contoso leverage to enable greater searchability over the claim data, inclusive of the new data fields created by your text processing and image processing components?

2.  Would they be able to keep their claims data in the existing database and layer in this search capability? If so, explain how.

**Prepare**

Directions: With all participants at your table:

1.  Identify any customer needs that are not addressed with the proposed solution.

2.  Identify the benefits of your solution.

3.  Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

**Presentation**

Directions:

1.  Pair with another table.

2.  One table is the Microsoft team and the other table is the customer.

3.  The Microsoft team presents their proposed solution to the customer.

4.  The customer makes one of the objections from the list of objections.

5.  The Microsoft team responds to the objection.

6.  The customer team gives feedback to the Microsoft team.

7.  Tables switch roles and repeat Steps 2-6.

##  Wrap-up 

Timeframe: 15 minutes

Directions: Tables reconvene with the larger group to hear the facilitator/SME share the preferred solution for the case study.

##  Additional references


|                                                       |                                                                                                   |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Description**                                       | **Links**                                                                                         |
| Azure Machine Learning service                        | <https://docs.microsoft.com/en-us/azure/machine-learning/service/overview-what-is-azure-ml>       |  |
| Deploying Web Services                                | <https://docs.microsoft.com/en-us/azure/machine-learning/preview/model-management-service-deploy> |
| Overview of Keras                                   | <https://keras.io/> |
| Overview of TensorFlow                                | <https://www.tensorflow.org/> |
| GloVe: Global Vectors for Word Representation | <https://nlp.stanford.edu/projects/glove/>  |
| Research Paper: "GloVe: Global Vectors for Word Representation" | <https://nlp.stanford.edu/pubs/glove.pdf>  |
| Word2vec | <https://en.wikipedia.org/wiki/Word2vec>  |
| Overview of the Computer Vision API Cognitive Service | <https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/home>                  |
| Overview of the Text Analytics API Cognitive Service  | <https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/overview>               |
