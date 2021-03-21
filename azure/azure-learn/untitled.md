# Get started with AI on Azure

## Introduction to AI

100 XP

* 3 minutes

AI enables us to build amazing software that can improve health care, enable people to overcome physical disadvantages, empower smart infrastructure, create incredible entertainment experiences, and even save the planet!

Watch the following video to see some ways that AI can be used.

### What is AI? <a id="what-is-ai"></a>

Simply put, AI is the creation of software that imitates human behaviors and capabilities. Key elements include:

* **Machine learning** - This is often the foundation for an AI system, and is the way we "teach" a computer model to make prediction and draw conclusions from data.
* **Anomaly detection** - The capability to automatically detect errors or unusual activity in a system.
* **Computer vision** - The capability of software to interpret the world visually through cameras, video, and images.
* **Natural language processing** - The capability for a computer to interpret written or spoken language, and respond in kind.
* **Conversational AI** - The capability of a software "agent" to participate in a conversation.

## Understand machine learning

100 XP

* 3 minutes

Machine Learning is the foundation for most AI solutions.

Let's start by looking at a real-world example of how machine learning can be used to solve a difficult problem.

Sustainable farming techniques are essential to maximize food production while protecting a fragile environment. _The Yield_, an agricultural technology company based in Australia, uses sensors, data and machine learning to help farmers make informed decisions related to weather, soil and plant conditions.

View the following video to learn more.

You can find out more about how the Yield is using machine learning to feed the world without wrecking the planet [here](https://news.microsoft.com/transform/videos/yield-feed-world-without-wrecking-planet/).

### How machine learning works <a id="how-machine-learning-works"></a>

So how do machines learn?

The answer is, from data. In today's world, we create huge volumes of data as we go about our everyday lives. From the text messages, emails, and social media posts we send to the photographs and videos we take on our phones, we generate massive amounts of information. More data still is created by millions of sensors in our homes, cars, cities, public transport infrastructure, and factories.

Data scientists can use all of that data to train machine learning models that can make predictions and inferences based on the relationships they find in the data.

For example, suppose an environmental conservation organization wants volunteers to identify and catalog different species of wildflower using a phone app. The following animation shows how machine learning can be used to enable this scenario.

![Machine Learning](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/machine-learn.gif)

1. A team of botanists and data scientists collects samples of wildflowers.
2. The team labels the samples with the correct species.
3. The labeled data is processed using an algorithm that finds relationships between the features of the samples and the labeled species.
4. The results of the algorithm are encapsulated in a model.
5. When new samples are found by volunteers, the model can identify the correct species label.

### Machine learning in Microsoft Azure <a id="machine-learning-in-microsoft-azure"></a>

Microsoft Azure provides the **Azure Machine Learning** service - a cloud-based platform for creating, managing, and publishing machine learning models. Azure Machine Learning provides the following features and capabilities:

| MACHINE LEARNING IN MICROSOFT AZURE |  |
| :--- | :--- |
| Feature | Capability |
| Automated machine learning | This feature enables non-experts to quickly create an effective machine learning model from data. |
| Azure Machine Learning designer | A graphical interface enabling no-code development of machine learning solutions. |
| Data and compute management | Cloud-based data storage and compute resources that professional data scientists can use to run data experiment code at scale. |
| Pipelines | Data scientists, software engineers, and IT operations professionals can define pipelines to orchestrate model training, deployment, and management tasks. |

## Understand anomaly detection

100 XP

* 3 minutes

Imagine you're creating a software system to monitor credit card transactions and detect unusual usage patterns that might indicate fraud. Or an application that tracks activity in an automated production line and identifies failures. Or a racing car telemetry system that uses sensors to proactively warn engineers about potential mechanical failures before they happen.

These kinds of scenario can be addressed by using _anomaly detection_ - a machine learning based technique that analyzes data over time and identifies unusual changes.

Let's explore how anomaly detection might help in the racing car scenario.

![A race car drives past and an instrument panel shows telemetry values, which vary over time. When an anomaly occurs, a warning is displayed and the car stops.](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/anomaly-detection.gif)

1. Sensors in the car collect telemetry, such as engine revolutions, brake temperature, and so on.
2. An anomaly detection model is trained to understand expected fluctuations in the telemetry measurements over time.
3. If a measurement occurs outside of the normal expected range, the model reports an anomaly that can be used to alert the race engineer to call the driver in for a pit stop to fix the issue before it forces retirement from the race.

### Anomaly detection in Microsoft Azure <a id="anomaly-detection-in-microsoft-azure"></a>

In Microsoft Azure, the **Anomaly Detector** service provides an application programming interface \(API\) that developers can use to create anomaly detection solutions.

To learn more, view the [Anomaly Detector service web site](https://azure.microsoft.com/services/cognitive-services/anomaly-detector/).

## Understand computer vision

100 XP

* 3 minutes

Computer Vision is an area of AI that deals with visual processing. Let's explore some of the possibilities that computer vision brings.

The **Seeing AI** app is a great example of the power of computer vision. Designed for the blind and low vision community, the Seeing AI app harnesses the power of AI to open up the visual world and describe nearby people, text and objects.

View the following video to learn more about Seeing AI.

To find out more, check out the [Seeing AI web page](https://www.microsoft.com/ai/seeing-ai).

### Computer Vision models and capabilities <a id="computer-vision-models-and-capabilities"></a>

Most computer vision solutions are based on machine learning models that can be applied to visual input from cameras, videos, or images. The following table describes common computer vision tasks.

| COMPUTER VISION MODELS AND CAPABILITIES |  |
| :--- | :--- |
| Task | Description |
| Image classification | ![An image of a taxi with the label &quot;Taxi&quot;](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/image-classification.png) Image classification involves training a machine learning model to classify images based on their contents. For example, in a traffic monitoring solution you might use an image classification model to classify images based on the type of vehicle they contain, such as taxis, buses, cyclists, and so on. |
| Object detection | ![An image of a street with buses, cars, and cyclists identified and highlighted with a bounding box](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/object-detection.png) Object detection machine learning models are trained to classify individual objects within an image, and identify their location with a bounding box. For example, a traffic monitoring solution might use object detection to identify the location of different classes of vehicle. |
| Semantic segmentation | ![An image of a street with the pixels belonging to buses, cars, and cyclists identified](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/semantic-segmentation.png) Semantic segmentation is an advanced machine learning technique in which individual pixels in the image are classified according to the object to which they belong. For example, a traffic monitoring solution might overlay traffic images with "mask" layers to highlight different vehicles using specific colors. |
| Image analysis | ![An image of a person with a dog on a street and the caption &quot;A person with a dog on a street&quot;](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/image-analysis.png) You can create solutions that combine machine learning models with advanced image analysis techniques to extract information from images, including "tags" that could help catalog the image or even descriptive captions that summarize the scene shown in the image. |
| Face detection, analysis, and recognition | ![An image of multiple people on a city street with their faces highlighted](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/face-analysis.png) Face detection is a specialized form of object detection that locates human faces in an image. This can be combined with classification and facial geometry analysis techniques to infer details such as age and emotional state; and even recognize individuals based on their facial features. |
| Optical character recognition \(OCR\) | ![An image of a building with the sign &quot;Toronto Dominion Bank&quot;, which is highlighted](https://docs.microsoft.com/en-us/learn/wwl-data-ai/get-started-ai-fundamentals/media/ocr.png) Optical character recognition is a technique used to detect and read text in images. You can use OCR to read text in photographs \(for example, road signs or store fronts\) or to extract information from scanned documents such as letters, invoices, or forms. |

### Computer vision services in Microsoft Azure <a id="computer-vision-services-in-microsoft-azure"></a>

Microsoft Azure provides the following cognitive services to help you create computer vision solutions:

| COMPUTER VISION SERVICES IN MICROSOFT AZURE |  |
| :--- | :--- |
| Service | Capabilities |
| **Computer Vision** | You can use this service to analyze images and video, and extract descriptions, tags, objects, and text. |
| **Custom Vision** | Use this service to train custom image classification and object detection models using your own images. |
| **Face** | The Face service enables you to build face detection and facial recognition solutions. |
| **Form Recognizer** | Use this service to extract information from scanned forms and invoices. |

### Try this <a id="try-this"></a>

To see an example of a how computer vision can be used to analyze images, follow these steps:

1. Open another browser tab and go to [https://aidemos.microsoft.com/computer-vision](https://aidemos.microsoft.com/computer-vision).
2. Use the demo interface to try each of the steps. For each step, you can select images and review the information returned by the Computer Vision service.

## Understand natural language processing

100 XP

* 3 minutes

Natural language processing \(NLP\) is the area of AI that deals with creating software that understands written and spoken language.

NLP enables you to create software that can:

* Analyze and interpret text in documents, email messages, and other sources.
* Interpret spoken language, and synthesize speech responses.
* Automatically translate spoken or written phrases between languages.
* Interpret commands and determine appropriate actions.

For example, _Starship Commander_, is a virtual reality \(VR\) game from Human Interact, that takes place in a science fiction world. The game uses natural language processing to enable players to control the narrative and interact with in-game characters and starship systems.

Watch the following video to learn more.

### Natural language processing in Microsoft Azure <a id="natural-language-processing-in-microsoft-azure"></a>

In Microsoft Azure, you can use the following cognitive services to build natural language processing solutions:

| NATURAL LANGUAGE PROCESSING IN MICROSOFT AZURE |  |
| :--- | :--- |
| Service | Capabilities |
| **Text Analytics** | Use this service to analyze text documents and extract key phrases, detect entities \(such as places, dates, and people\), and evaluate sentiment \(how positive or negative a document is\). |
| **Translator Text** | Use this service to translate text between more than 60 languages. |
| **Speech** | Use this service to recognize and synthesize speech, and to translate spoken languages. |
| **Language Understanding Intelligent Service \(LUIS**\) | Use this service to train a language model that can understand spoken or text-based commands. |

### Try this <a id="try-this"></a>

To see an example of a how you can use natural language to interact with an AI system, follow these steps:

1. Open another browser tab and go to [https://aidemos.microsoft.com/luis/demo](https://aidemos.microsoft.com/luis/demo).
2. Use the demo interface to control the lighting in the virtual home. You can type instructions, use the microphone button to speak commands, or select any of the suggested phrases to see how the system responds.

## Understand conversational AI

100 XP

* 3 minutes

Conversational AI is the term used to describe solutions where AI agents participate in conversations with humans. Most commonly, conversational AI solutions use _bots_ to manage dialogs with users. These dialogs can take place through web site interfaces, email, social media platforms, messaging systems, phone calls, and other channels.

Bots can be the basis of AI solutions for:

* Customer support for products or services.
* Reservation systems for restaurants, airlines, cinemas, and other appointment based businesses.
* Health care consultations and self-diagnosis.
* Home automation and personal digital assistants.

View the following video for some examples of how organizations are using bots to enable conversational AI.

### Conversational AI in Microsoft Azure <a id="conversational-ai-in-microsoft-azure"></a>

To create conversational AI solutions on Microsoft Azure, you can use the following services:

| CONVERSATIONAL AI IN MICROSOFT AZURE |  |
| :--- | :--- |
| Service | Capabilities |
| **QnA Maker** | This cognitive service enables you to quickly build a _knowledge base_ of questions and answers that can form the basis of a dialog between a human and an AI agent. |
| **Azure Bot Service** | This service provides a platform for creating, publishing, and managing bots. Developers can use the _Bot Framework_ to create a bot and manage it with Azure Bot Service - integrating back-end services like QnA Maker and LUIS, and connecting to channels for web chat, email, Microsoft Teams, and others. |

### Try this <a id="try-this"></a>

The Microsoft healthcare bot is built on Azure Bot Service and enables developers to quickly create conversational AI solutions for health care. To see an example of the healthcare bot:

1. Open another browser tab and go to [https://www.microsoft.com/research/project/health-bot/](https://www.microsoft.com/research/project/health-bot/).
2. Select the option to _Try a demo of an example end-user experience_.
3. Use the web chat interface to interact with the bot.

## Understand responsible AI

100 XP

* 10 minutes

Artificial Intelligence is a powerful tool that can be used to greatly benefit the world. However, like any tool, it must be used responsibly.

At Microsoft, AI software development is guided by a set of six principles, designed to ensure that AI applications provide amazing solutions to difficult problems without any unintended negative consequences.

### Fairness <a id="fairness"></a>

AI systems should treat all people fairly. For example, suppose you create a machine learning model to support a loan approval application for a bank. The model should make predictions of whether or not the loan should be approved without incorporating any bias based on gender, ethnicity, or other factors that might result in an unfair advantage or disadvantage to specific groups of applicants.

Azure Machine Learning includes the capability to interpret models and quantify the extent to which each feature of the data influences the model's prediction. This capability helps data scientists and developers identify and mitigate bias in the model.

For more details about considerations for fairness, watch the following video.

### Reliability and safety <a id="reliability-and-safety"></a>

AI systems should perform reliably and safely. For example, consider an AI-based software system for an autonomous vehicle; or a machine learning model that diagnoses patient symptoms and recommends prescriptions. Unreliability in these kinds of system can result in substantial risk to human life.

AI-based software application development must be subjected to rigorous testing and deployment management processes to ensure that they work as expected before release.

For more information about considerations for reliability and safety, watch the following video.

### Privacy and security <a id="privacy-and-security"></a>

AI systems should be secure and respect privacy. The machine learning models on which AI systems are based rely on large volumes of data, which may contain personal details that must be kept private. Even after the models are trained and the system is in production, it uses new data to make predictions or take action that may be subject to privacy or security concerns.

For more details about considerations for privacy and security, watch the following video.

### Inclusiveness <a id="inclusiveness"></a>

AI systems should empower everyone and engage people. AI should bring benefits to all parts of society, regardless of physical ability, gender, sexual orientation, ethnicity, or other factors.

For more details about considerations for inclusiveness, watch the following video.

### Transparency <a id="transparency"></a>

AI systems should be understandable. Users should be made fully aware of the purpose of the system, how it works, and what limitations may be expected.

For more details about considerations for transparency, watch the following video.

### Accountability <a id="accountability"></a>

People should be accountable for AI systems. Designers and developers of AI-based solution should work within a framework of governance and organizational principles that ensure the solution meets ethical and legal standards that are clearly defined.

For more details about considerations for accountability, watch the following video.

## Explore responsible AI in practice

100 XP

* 3 minutes

The principles of responsible AI can help you understand some of the challenges facing developers as they try to create ethical AI solutions. It's easy to read about the principles, or watch a video; but it's much harder to put the principles into practice.

### Try this <a id="try-this"></a>

Here's an activity to help you learn more about how principles apply to an AI system that interacts with human users.

1. Open another browser tab and go to [https://aidemos.microsoft.com/guidelines-for-human-ai-interaction/demo](https://aidemos.microsoft.com/guidelines-for-human-ai-interaction/demo).
2. Select cards from each of the decks, which represent four phases in a Human-AI interaction:
   * Initially
   * During the interaction
   * When something goes wrong
   * Over time
3. For each card, view the examples provided.
4. Try to identify which of the six principles the examples reflect \(an example might reflect more than one principle\).

### Further resources <a id="further-resources"></a>

For more resources to help you put the responsible AI principles into practice, see [https://www.microsoft.com/ai/responsible-ai-resources](https://www.microsoft.com/ai/responsible-ai-resources).

## Summary

100 XP

* 1 minute

Artificial Intelligence enables the creation of powerful solutions to many kinds of problems. AI systems can exhibit human characteristics to analyze the world around them, make predictions or inferences, and act on them in ways that we could only imagine a short time ago.

With this power, comes responsibility. As developers of AI solutions, we must apply principles that ensure that everyone benefits from AI without disadvantaging any individual or section of society.

