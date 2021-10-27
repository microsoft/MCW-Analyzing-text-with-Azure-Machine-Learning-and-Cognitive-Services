![Microsoft Cloud Workshops](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/main/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Cognitive services and deep learning
</div>

<div class="MCWHeader2">
Whiteboard design session student guide
</div>

<div class="MCWHeader3">
November 2021
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only, and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third-party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2021 Microsoft Corporation. All rights reserved.

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

# Cognitive services and deep learning whiteboard design session student guide

## Abstract and learning objectives

In this whiteboard design session, you work with a group to design a solution that combines both pre-built artificial intelligence (AI) in the form of Text Analytics API from Cognitive Services with custom AI in the form of services built and deployed with Azure Machine Learning services. You will learn to create intelligent solutions atop unstructured text data by designing and implementing a text analytics pipeline. You will discover how to build a binary classifier that can be used to classify the textual data. You will also learn how to deploy multiple kinds of predictive services using Azure Machine Learning and learn to integrate with the Text Analytics API from Cognitive Services.

At the end of this whiteboard design session, you will be better able to design solutions leveraging Azure Machine Learning services and Cognitive Services.

## Step 1: Review the customer case study

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions:  With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1. Meet your table participants and trainer.

2. Read all of the directions for steps 1-3 in the student guide.

3. As a table team, review the following customer case study.

### Customer situation

Contoso Ltd is a large corporation headquartered in the United States that provides insurance packages for U.S. consumers. Its products include accident and health insurance, life insurance, travel, home, and auto coverage.

Contoso is looking to build a next-generation platform for its insurance products and has identified claims processing as the first area in which they would like to focus its efforts. Currently, customers submit a claim using either the website, their mobile app, or by speaking with a live agent.

A claim includes the following information:

- Information about the insured (contact information, policy number, etc.)

- Free text responses describing the claim (details of what happened, what was affected, the conditions in which the incident occurred)

When processing a claim, agents face multiple challenges that add significantly to Contoso's costs. These challenges include the time it takes for an agent to read through and process the content submitted with each claim. While each claim is stored in a database, the details about the claim, including the free-text responses are stored as opaque attachments. Agents typically have to pull up the claim by the claim number or the insured's contact information and manually read through the attachments.

Also, there are some common challenges that Contoso is hoping they could automate away. According to Francine Fischer, CIO, there are two sets of issues where they envision amplifying their agents' capabilities with AI.

One set of such issues deals with the free-text responses. The first issue Contoso identified is that each claim detail should be automatically classified as either home or auto based on the text. This classification should be displayed within the claim summary, so agents can quickly assess whether they are dealing with a home claim, an auto claim, or a claim with a mixture of the two.

The second issue is Contoso would like to experiment with applying text analysis to the claim text. They know most customers are either factual in their description (a neutral sentiment) or slightly unhappy (a more negative sentiment). They believe that negative sentiment can be an indicator to claim text that involves a more severe situation, which might warrant an agent's expedited review. Furthermore, they would like to understand any positive or negative opinions the customers have expressed in their responses, and quickly identify key concepts in the claims text. They would also like to detect the language of the claims and identify any personal information included by customers in their responses.

The third issue with the free text is that some of the responses are long. When agents are shifting between claims, it can be difficult for them to recall which response had the details they need. Contoso would like to experiment with an automatic summarization of long claims that produces a summary of about 30 words in length. This summarization would enable the agent to get the gist before reading the full claim and quickly remind themselves of the claim when revisiting it.

As a final step, they would like to organize the information generated from text classification, text analysis and text summarization that can be then fed into their Agent portal.

As a first step towards their bigger goals, Contoso would like to build a proof of concept (PoC) for an intelligent solution that could automate all the above. They would like to develop this PoC to build upon the claims submission solution they already have running in Azure. The existing solution consists of a Web App for claims submission and a SQL Database for claim storage. Contoso Ltd. believes this might be possible using AI, machine learning, or deep learning and would like to build a proof of concept to understand how far they can go using these technologies.

### Customer needs

1. We receive a lot of useful information in the free-text responses. However, because the free-text responses can be lengthy, agents sometimes skip over them and miss vital details or spend too much time looking for a particular point when returning to a claim. We aren't confident we can automate this step. Still, we would like to have a standardized process that identifies the key units of actionable information in a claim and pulls these units of information out into a separate sections that agents can more easily review and then be able to view and read both the summary and the entire text of the claims.

2. We are looking to amplify our agents' capabilities and improve their claims processing capabilities - not replace them. We want a solution that does the same.

### Customer objections

1. We are skeptical about all the hype surrounding these "AI" solutions. It's hard to know what is feasible versus what is not possible with today's technology and Azure.

2. We know that there are pre-built AI, Automated ML, and custom AI options available. We are confused as to when to choose one over the other.

3. We expect some part of our solution would require deep learning. Do you have any prescriptive guidance on how we might choose between investing in understanding and using TensorFlow or the Microsoft Cognitive Toolkit (CNTK)?

### Infographic for common scenarios

![In the Training a classification model with text diagram, Document labels points to Supervised ML or DL Algorithm, which points to Classification Model. Documents points to Text Normalization, which points to Feature Extraction, which points to Supervised ML or DL Algorithm. Vectors points to a table of words and percentages.](media/image2.png "Training a classification model with text diagram")

![The Predicting a classification from text diagram has Documents, which points to Text Normalization, which points to Feature Extraction, which points to Classification Model, which points to Document Labels. Vectors points to a table of words and percentages.](media/image3.png "Predicting a classification from text diagram")

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions: With all participants at your table, answer the following questions and list the answers on a flip chart:

1. Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2. What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

_High-level architecture_

1. Without getting into the details (the following sections will address the details), diagram your initial vision for handling the top-level requirements for processing the claims textual data, photos, and enabling search. You will refine this diagram as you proceed.

_Classifying claim-text data_

1. What is the general pipeline for approaching the training of text analytic models such as this? What are the general steps you need to take to prepare the text data for performing tasks like classification?

2. What data would they need to train the model?

3. Contoso wants to understand some of the common approaches to handle texts for machine learning. Is there a recommended approach to dealing with long descriptive texts that are typically found in claims data?

4. Contoso understands they should use a classification algorithm for this problem. They have asked if a Deep Neural Network could be trained against the text to recognize home or auto classifications. Could they use a DNN for this?

5. For this scenario, Contoso has indicated an interest in using TensorFlow but is concerned about the complexity of jumping right in. They wonder if Keras would provide an easier framework they could use as a steppingstone to the full-blown TensorFlow, which would enable them to build TensorFlow compatible models so that they can "graduate" to using TensorFlow when the team is ready?

6. What would a Long Short-Term Memory (LSTM) recurrent neural network that performs this classification look like? Show a snippet of a single layer of an unrolled LSTM network and the binary classification output at the network's last step.

7. Assuming they will be using an LSTM recurrent neural network to train the classifier using Keras, pseudo code the code you would write to construct the network you just illustrated.

8. Next, pseudo code how they would define the optimizer, loss function and fit the model to the vectorized data and the labels.

9. With the trained model in hand, pseudo code how the model would predict the class of a given claim text. What would the output of the prediction be? How would you interpret the value?

10. Describe how you would deploy this trained model at a high level to be available as a web service integrated with the rest of the solution.

_Automated machine learning_

1. Can Contoso apply automated machine learning for text classification?

2. Can they really expect a non-data scientist to create performant models using automated machine learning?

_Free-text Analytics_

1. How would you recommend Contoso identify the sentiment, opinions, and key phrases in the free-response text provided associated with a claim? Would this require you to build a custom AI model? Is there a pre-built AI service you could use?

2. For the solution you propose, what is the range of value of the sentiment score, and how would you interpret that value?

3. Next, pseudo code on how to use the Text Analytics Python APIs for their text analytics use cases.

_Summarizing claim text_

1. The team at Contoso has heard about a Python library called Gensim, which has a summarize function. Given an input of text, it can extract a summary of the desired length. Contoso would like their PoC to implement its summarization functionality initially using Gensim. However, the process they follow to deploy the summarization capability should also enable them to replace Gensim with another library or with the use of their own custom trained models if desired down the road. Describe how Contoso should deploy the summarization service to meet these requirements?

2. Discuss with Contoso team the Text Analytics extractive summarization capability that is currently in preview and how that can be used in place of Gensim when it becomes generally available.

**Prepare**

Directions: With all participants at your table:

1. Identify any customer needs that are not addressed with the proposed solution.

2. Identify the benefits of your solution.

3. Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

1. Pair with another table.

2. One table is the Microsoft team and the other table is the customer.

3. The Microsoft team presents their proposed solution to the customer.

4. The customer makes one of the objections from the list of objections.

5. The Microsoft team responds to the objection.

6. The customer team gives feedback to the Microsoft team.

7. Tables switch roles and repeat Steps 2-6.

## Wrap-up

Timeframe: 15 minutes

Directions: Tables reconvene with the larger group to hear the facilitator/SME share the preferred solution for the case study.

## Additional references

|                                                       |                                                                                                   |
| ----------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Description**                                       | **Links**                                                                                         |
| Azure Machine Learning service                        | <https://docs.microsoft.com/en-us/azure/machine-learning/service/overview-what-is-azure-ml>       |  |
| Deploying Web Services                                | <https://docs.microsoft.com/en-us/azure/machine-learning/service/how-to-deploy-and-where> |
| Overview of Keras                                   | <https://keras.io/> |
| Overview of TensorFlow                                | <https://www.tensorflow.org/> |
| Term Frequency-Inverse Document Frequency (TF-IDF) vectorization | <https://en.wikipedia.org/wiki/Tf-idf> |
| GloVe: Global Vectors for Word Representation | <https://nlp.stanford.edu/projects/glove/>  |
| Research Paper: "GloVe: Global Vectors for Word Representation" | <https://nlp.stanford.edu/pubs/glove.pdf>  |
| Word2vec word embeddings | <https://en.wikipedia.org/wiki/Word2vec>  |
| Overview of the Text Analytics API Cognitive Service  | <https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/overview>               |
| Text Analytics Extractive Summarization | <https://docs.microsoft.com/en-us/azure/cognitive-services/text-analytics/how-tos/extractive-summarization>               |
