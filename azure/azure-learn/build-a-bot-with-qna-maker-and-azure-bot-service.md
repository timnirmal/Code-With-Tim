# Build a bot with QnA Maker and Azure Bot Service



## Introduction

100 XP

* 3 minutes

In today's connected world, people use a variety of technologies to communicate. For example:

* Voice calls
* Messaging services
* Online chat applications
* Email
* Social media platforms
* Collaborative workplace tools

We've become so used to ubiquitous connectivity, that we expect the organizations we deal with to be easily contactable and immediately responsive through the channels we already use. Additionally, we expect these organizations to engage with us individually, and be able to answer complex questions at a personal level.

### Conversational AI <a id="conversational-ai"></a>

While many organizations publish support information and answers to frequently asked questions \(FAQs\) that can be accessed through a web browser or dedicated app. The complexity of the systems and services they offer means that answers to specific questions are hard to find. Often, these organizations find their support personnel being overloaded with requests for help through phone calls, email, text messages, social media, and other channels.

Increasingly, organizations are turning to artificial intelligence \(AI\) solutions that make use of AI agents, commonly known as _bots_ to provide a first-line of automated support through the full range of channels that we use to communicate. Bots are designed to interact with users in a conversational manner, as shown in this example of a chat interface:

![A chat interface showing user input and responses from a bot](https://docs.microsoft.com/en-us/learn/wwl-data-ai/build-faq-chatbot-qna-maker-azure-bot-service/media/bot.png)

 Note

The example shown here is a chat interface, such as you might find on a web site; but bots can be designed to work across multiple channels, including email, social media platforms, and even voice calls. Regardless of the channel used, bots typically manage conversation flows using a combination of natural language and constrained option responses that guide the user to a resolution.

Conversations typically take the form of messages exchanged in turns; and one of the most common kinds of conversational exchange is a question followed by an answer. This pattern forms the basis for many user support bots, and can often be based on existing FAQ documentation. To implement this kind of solution, you need:

* A _knowledge base_ of question and answer pairs - usually with some built-in natural language processing model to enable questions that can be phrased in multiple ways to be understood with the same semantic meaning.
* A _bot service_ that provides an interface to the knowledge base through one or more channels.

## Get started with QnA Maker and Azure Bot Service

100 XP

* 3 minutes

You can easily create a user support bot solution on Microsoft Azure using a combination of two core technologies:

* **QnA Maker**. This cognitive service enables you to create and publish a knowledge base with built-in natural language processing capabilities.
* **Azure Bot Service**. This service provides a framework for developing, publishing, and managing bots on Azure.

### Creating a QnA Maker knowledge base <a id="creating-a-qna-maker-knowledge-base"></a>

The first challenge in creating a user support bot is to use the QnA Maker service to create a knowledge base. The service provides a dedicated _QnA Maker portal_ web-based interface that you can use to create, train, publish, and manage knowledge bases.

 Note

You can write code to create and manage knowledge bases using the QnA Maker REST API or SDK. However, in most scenarios it is easier to use the QnA Maker portal.

#### Provision a QnA Maker Azure resource <a id="provision-a-qna-maker-azure-resource"></a>

To create a knowledge base, you must first provision a **QnA Maker** resource in your Azure subscription. You can do this directly in the Azure portal before you start creating your knowledge base, or you can start developing your knowledge base in the QnA Maker portal and provision the resource when prompted.

#### Define questions and answers <a id="define-questions-and-answers"></a>

After provisioning a QnA Maker resource, you can use the QnA Maker portal to create a knowledge base that consists of question-and-answer pairs. These questions and answers can be:

* Generated from an existing FAQ document or web page.
* Imported from a pre-defined _chit-chat_ data source.
* Entered and edited manually.

In many cases, a knowledge base is created using a combination of all of these techniques; starting with a base dataset of questions and answers from an existing FAQ document, adding common conversational exchanges from a chit-chat source, and extending the knowledge base with additional manual entries.

Questions in the knowledge base can be assigned _alternative phrasing_ to help consolidate questions with the same meaning. For example, you might include a question like:

> _What is your head office location?_

You can anticipate different ways this question could be asked by adding an alternative phrasing such as:

> _Where is your head office located?_

#### Train and test the knowledge base <a id="train-and-test-the-knowledge-base"></a>

After creating a set of question-and-answer pairs, you must train your knowledge base. This process analyzes your literal questions and answers and applies a built-in natural language processing model to match appropriate answers to questions, even when they are not phrased exactly as specified in your question definitions.

After training, you can use the built-in test interface in the QnA Maker portal to test your knowledge base by submitting questions and reviewing the answers that are returned.

#### Publish the knowledge base <a id="publish-the-knowledge-base"></a>

When you're satisfied with your trained knowledge base, you can publish it so that client applications can use it over its REST interface. To access the knowledge base, client applications require:

* The knowledge base ID
* The knowledge base endpoint
* The knowledge base authorization key

### Build a bot with the Azure Bot Service <a id="build-a-bot-with-the-azure-bot-service"></a>

After you've created and published a knowledge base, you can deliver it to users through a bot.

#### Create a bot for your knowledge base <a id="create-a-bot-for-your-knowledge-base"></a>

You can create a custom bot by using the Microsoft Bot Framework SDK to write code that controls conversation flow and integrates with your QnA Maker knowledge base. However, an easier approach is to use the automatic bot creation functionality of QnA Maker, which enables you create a bot for your published knowledge base and publish it as an Azure Bot Service application with just a few clicks.

#### Extend and configure the bot <a id="extend-and-configure-the-bot"></a>

After creating your bot, you can manage it in the Azure portal, where you can:

* Extend the bot's functionality by adding custom code.
* Test the bot in an interactive test interface.
* Configure logging, analytics, and integration with other services.

For simple updates, you can edit bot code directly in the Azure portal. However, for more comprehensive customization, you can download the source code and edit it locally; republishing the bot directly to Azure when you're ready.

#### Connect channels <a id="connect-channels"></a>

When your bot is ready to be delivered to users, you can connect it to multiple _channels_; making it possible for users to interact with it through web chat, email, Microsoft Teams, and other common communication media.

![A chat interface showing user input and responses from a bot](https://docs.microsoft.com/en-us/learn/wwl-data-ai/build-faq-chatbot-qna-maker-azure-bot-service/media/bot-solution.png)

Users can submit questions to the bot through any of its channels, and receive an appropriate answer from the knowledge base on which the bot is based.  




