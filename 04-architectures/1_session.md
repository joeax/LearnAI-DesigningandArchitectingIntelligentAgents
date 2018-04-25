# 4.1: Reference Architectures and Common Patterns

We've talked about some things to consider when you're designing bots and designing their LUIS schema. But what about how your bot fits with other things? What's your bot's backend logical flow? More likely than not, you'll often develop bots that have multiple (probably many) components, depending on what you want your bot to accomplish.  

So, let's back up a bit. Let's talk about big picture things we want to think about when we're building the logical architecture of a bot. 

In principles of bot design, we covered a few key considerations for [designing a bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-principles):
* Does the bot easily solve the user's problem with the minimum number of steps?
* Does the bot solve the user's problem better/easier/faster than any of the alternative experiences?
* Does the bot run on the devices and platforms the user cares about?
* Is the bot discoverable? Do users naturally know what to do when using it?  

None of those questions directly relate to the architecture, but the answers to the questions have implications that do. So now that we have thought about our bot design and LUIS design, we ask "_How are we going to make this work?_"  

Well, the good news is that you're not alone in your quest to construct the architecture! At Microsoft, we've come up with a few key scenarios that we see customers implementing frequently. We've taken those scenarios and fleshed them out for you, so, depending on your scenario, you may be able to leverage some of the existing architectures. At the very least, you'll have full examples to see what we're doing and recommending, and that should help give you some ideas, along with a foundation in how bot logic is built.  

In the activity that follows this session, you'll get the opportunity to create the architecture for the key scenario we _aren't_ covering. This will give you the opportunity to practice what you've learned and get those creative juices flowing.  

There will be three main topics covered in this session:
1.  Key scenarios for bots
2.  Common patterns for bots
3.  Bot Framework v4 SDK

## Section 1: Key scenarios for bots
Let's dive in. There are four key scenarios we are going to cover in this session:
* Cortana skills bot
* Enterprise productivity bot
* Information bot
* IoT bot  

There is one more scenario, for a Commerce bot, but we will go over that after the activity that follows this session.
### Section 1.1: Cortana skills bot

The [Cortana skills bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-cortana-skill) extends Cortana and makes it easy for you to develop a bot to be used with Cortana. This way, users on Windows (or with the Cortana app) can make appointments, search the web, etc. via voice or text with the context from your calendar.  

For this architecture, we're going to talk about a scenario for an auto shop that wants to make a bot where you (and other customers) can make maintenance appointments. Using the natural interface of your voice and a custom Cortana skills bot, you can ask Cortana to speak to an organization, such as an auto shop, to help you make an appointment. The service may be able to provide a list of services, times available, duration, location, etc. Because Cortana can look at your calendar to see if you have something at a conflicting time, Cortana can suggest possible appointments and even add it to your calendar. Let's review the architecture below.
![Cortana skills bot architecture](./resources/assets/cortanabot.png)

Here is the logic flow of a Cortana skills bot for an auto shop:
1.  The user accesses Cortana from their PC or mobile device.
2.  Using either text or voice commands, the user asks for an automobile maintenance appointment.
3.  Because the bot is integrated with Cortana, it has access to the user's calendar and applies logic to the request.
4.  With that information, the bot can query the auto service for valid appointments.
5.  Presented with contextual options, the user can book the appointment.
6.  Application insights gathers runtime telemetry to help development with bot performance and usage.

You can follow [this tutorial](https://docs.microsoft.com/en-us/azure/bot-service/dotnet/bot-builder-dotnet-cortana-skill) learn how to build a speech-enabled bot with Cortana skills. You should also check out the [Cortana skills kit documentation](https://docs.microsoft.com/en-us/cortana/skills/overview) and the [Cortana skills samples](https://docs.microsoft.com/en-us/cortana/skills/cortana-samples).



### Section 1.2: Enterprise productivity bot 

The [Enterprise productivity bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-enterprise-productivity) shows how you can increase productivity of organizations by integrating bots with productivity services like Office 365 and Dynamics CRM. 

For this architecture, we're going to focus on a scenario where employees in the sales organization of a company need to access customer information. The beauty of this bot is it makes it so employees can quickly access customer information, without having to open a bunch of windows. Using simple chat commands, a sales rep can look up a customer and check their next appointment via the Graph API and Office 365. From there they can access customer specific information stored in Dynamics CRM such as get a case or create a new one. Review the architecture:
![Enterprise productivity architecture](./resources/assets/enterprisebot.png)
Here is the logic flow for our enterprise productivity bot:
1.  The employee accesses the Enterprise Productivity bot.
2.  Azure Active Directory validates the employee's identity.
3.  The Enterprise Productivity bot can query the employee's Office 365 calendar via the [Microsoft Graph](https://graph.microsoft.com/).
4.  Using data gathered from the calendar, the bot accesses case information in Dynamics CRM.
5.  The information is returned to the employee who can filter down the data without leaving the bot.
6.  Application insights gathers runtime telemetry to help development with bot performance and usage.  

You can find some sample code for the scenario described [here](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Enterprise/src).

While we're on the topic of enterprise productivity, it's important to provide a little warning. Many times, organizations will see productivity gains of utilizing bots across the enterprise. In many cases, a department will create a bot that turns out to be a success. Other departments quickly see the value and apply the bot technology to their domain. Fast forward several months, and there are many bots floating around with different architectures. When developing bots, as an enterprise, [there needs to be a cohesive enterprise bot strategy and architecture in place](https://blogs.msdn.microsoft.com/pragdev/2018/02/10/enterprise-bot-architecture/) so the following concerns are addressed effectively and consistently:
* User experience
* Discovery
* Bot maintainability and creation
* Managed security
* Inconsistent API access  

We **highly recommend** you read [this article](https://blogs.msdn.microsoft.com/pragdev/2018/02/10/enterprise-bot-architecture/) that explains the scenario, the problem, and a solution.


### Section 1.3: Information bot

The [Information bot scenario](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-informational) may be the one you've heard the most about. There are lots of use-cases for a bot like this, including: FAQ, IT support, store location and information, open-ended search, retail/inventory...the list goes on. An information bot could be used to answer questions defined in a knowledge set or even more open-ended questions.  

Often information is buried in structured data stores like SQL Server that can be easily surfaced via search. Using [Cognitive Services QnA Maker](https://qnamaker.ai/) or [Azure Search](https://docs.microsoft.com/en-us/azure/search/), you can make those searches possible with conversational commands.

For this architecture, a user may be looking for specific information related to specific customers. Using QnA Maker, the user is presented with a set of valid search options like, lookup a customer, review a customer's most recent order, etc. With the QnA format defined the user can easily ask questions that are backed by Azure Search which can look up data stored in a SQL Database. Let's review the architecture:

![Information bot architecture](./resources/assets/infobot.png)

Here is the logic flow of this Information bot:
1.  The employee starts the information bot.
2.  AAD validates the employee's identity.
3.  The employee can ask what type of queries are supported.
4.  Using LUIS or QnA Maker, the bot processes the request and gives an answer.
5.  The employee responds with a valid query
6.  The bot submits the query to Azure Search which returns information from SQL to the user.
7.   Application insights gathers runtime telemetry to help development with bot performance and usage.

You can find some sample code for the scenario described [here](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Informational/src).  

An example of a real-world information bot comes from a navigation technology company [NAVITIME JAPAN](http://corporate.navitime.co.jp/en/index.html). NAVITIME JAPAN recognized the need to help visitors find tourist attractions without having to understand Japanese. To help travelers find their way, the Tokyo-based company used Microsoft Bot Framework to incorporate a bot into its tourist software app - allowing visitors to obtain real-time answers to their travel questions while they explore Japan. You can read the full story [here](https://customers.microsoft.com/en-us/story/navitime-japan-travel-hospitality-microsoft-cognitive-services).

[Fiducia & GAD IT AG](https://www.fiduciagad.de/) is a German company that really embraced the Microsoft AI Platform to quickly develop a support system surfaced as a bot for its employees. Within five weeks, they were able to release a Minimum Viable Product (MVP) that used many of the existing knowledge databases. They were able to lighten the load of the call center, keep track of issues and resolutions, and provide overall better customer service. Read more about Fiducia & GAD IT AG's [bot transformation](https://customers.microsoft.com/en-us/story/fiducia-gad-cortana-azure-powerbi-services-bot-framework-banking-germany-en).

The final example we'll talk about for information bot - there are so many we could not cover them all - is [UST Global](http://www.ust-global.com/). UST Global needed a more streamlined approach to help their employees find information over the intranet and internal applications. Employees were greatly impressed by the bot's ability to find relevant applications and information from the internal network and to automate some of their IT operation activities. Because of the success, UST is now working on evolving the bot from an information bot to and information bot and enterprise productivity bot that integrates with Azure ML, ERP systems, ServiceNow, Dynamics CRM, and more. [Read their story](https://customers.microsoft.com/en-us/story/ust-global-professional-services-microsoft-bot-framework-en).


### Section 1.4: IoT Bot
People love to talk to their things. That's a nice way of saying it right? We can be lazy. We want something, and we want it now! And, by the way, we want to be able to access things without moving, or when we aren't them, or maybe even just by speaking.  

That may not be exactly the world we live in - but it's becoming more and more possible! Internet of Things (IoT) allows us to manage our things with our devices, no matter where we are. So why not have a bot, that we can tell to manage our things?

The [IoT bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-internet-things) makes it easy for you to control devices using voice or interactive chat controls. For this architecture, we'll be using the example of the Philips Hue light. This bot allows a person to manage a Philips Hue by simple chat commands or voice. In addition, when using chat, a person can be given visual choices related to colors to pick. See the architecture below:
![IoT bot architecture](./resources/assets/iotbot.png)
Here is the logic flow for this sample IoT bot:
1. The user logs into Skype to access the IoT bot.
2. Using voice or IM, the user asks the bot to turn on the lights via the IoT device.
3. The request is relayed to a third party service that has access to the IoT device network.
4. The results of the command are returned to the user.
5. Application insights gathers runtime telemetry to help development with bot performance and usage.

You can review some sample code for this scenario [here](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Iot/src).

When we talk about [Microsoft Azure and IoT](https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-what-is-azure-iot), we've really opened the doors to what scenarios we could be dealing with. [IoT Solutions](https://www.microsoft.com/en-us/internet-of-things/solutions) can be tailored for any need, to help employees make informed decisions, optimize operations, reduce costs, and create new revenue streams. But how does this surface in a bot? Here are a few ideas:  
* For [Connected Factory](https://www.microsoft.com/en-us/internet-of-things/connected-factory), maybe you use a bot to receive proactive messages containing insights generated by connected equipment or to request the status of various machines.
* For [Remote Monitoring](https://www.microsoft.com/en-us/internet-of-things/remote-monitoring), maybe you have a bot that provides the experts responsible for specific projects regular updates into operating conditions, increasing visibility for higher efficiency. 
* For [Predictive Maintenance](https://www.microsoft.com/en-us/internet-of-things/predictive-maintenance), perhaps you use a bot that takes insights from data (which has been analyzed with machine-learning algorithms) and allows the supervisor or line managers to understand the results and modifications needed via conversation.
* For [Connected Field Service](https://www.microsoft.com/en-us/internet-of-things/connected-field-service), maybe you have a bot that a field expert authenticates to, and then the field expert can ask the bot what their schedule for the day should be, using schedule optimization and performance indicators.

The answer: Almost all IoT scenarios _could_ have a bot. While it will depend on the situation if a bot is the best way, using bots should definitely be considered.

## Section 2: Common patterns for bots
Now that we're clear on some of the key scenarios and have learned about plenty of real-world scenarios as well, let's shift gears slightly to talk about patterns.  

When we talk about common patterns for bots, we're referring to the set of tasks that bots commonly must do. The patterns that we'll dive into for this section include:
* Task automation
* Access to knowledge and other content
* Bot to human handoff
* Bot to web browser and back
* Bots in websites
* Bots in apps

### Section 2.1: Task automation

A [task automation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-task-automation) bot enables a user to complete a specific task or set of tasks without any assistance from a human. This type of bot often closely resembles a typical app or website, communicating with the user primarily via rich user controls and text. It may have natural language understanding capabilities to enrich conversations with users.

To better understand the nature of a task bot, read about an [example use case: password-reset](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-task-automation#example-use-case-password-reset), and check out the sample code ([C# v3 SDK](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/capability-SimpleTaskAutomation) and [Node.js v3 SDK](https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/capability-SimpleTaskAutomation)).

![Password Reset Flow](./resources/assets/pwreset.png)
![Password reset chat](./resources/assets/pwresetchat.png)


### Section 2.2: Access to knowledge and other content
A [knowledge bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-knowledge-base) can be designed to provide information about virtually any topic. For example, one knowledge bot might answer questions about events such as, "What bot events are there at this conference?", "When is the next Reggae show?", or "Who is Tame Impala?" Another might answer IT-related questions such as "How do I update my operating system?" or "Where do I go to reset my password?" Yet another might answer questions about contacts such as "Who is John Doe?" or "What is Jane Doe's email address?"

Regardless of the use case for which a knowledge bot is designed, its basic objective is always the same: find and return the information that the user has requested by leveraging a body of data, such as relational data in a SQL database, JSON data in a non-relational store, or PDFs in a document store.

You can provide access to other knowledge and content by incorporating things like search with [Azure Search](https://azure.microsoft.com/en-us/services/search/), FAQ with [QnA maker](https://www.microsoft.com/cognitive-services/en-us/qnamaker), language understanding with [LUIS](https://www.luis.ai/), other resources' information with [Microsoft Graph](https://developer.microsoft.com/en-us/graph/docs/concepts/overview),or a combination of the above. Read more about adding search, QnA Maker, and LUIS to provide access to knowledge [here](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-knowledge-base#search).   

You can obtain hands on experience for integrating Azure Search and LUIS together in a bot (Bot Framework v3 or v4 SDK) by completing the labs found [here](https://github.com/Azure/LearnAI-Bootcamp/blob/master/emergingaidev_bootcamp.md). There are also several samples for the Bot Framework v3 SDK if you want to get more hands-on experience with [Search-powered bots](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/demo-Search) or [Knowledge bots](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/sample-KnowledgeBot).  

You can also provide access to other content via the use of the [Bing Search APIs](https://azure.microsoft.com/en-us/services/cognitive-services/directory/search/) which we'll cover in 05-cognitive_services.

We'll also walk through some examples when we talk about integration of services in 05-cognitive_services.
   
### Section 2.3: Bot to human handoff
Regardless of how much artificial intelligence a bot possesses, there may still be times when it needs to hand off the conversation to a human being. The bot should recognize when it needs to hand off and provide the user with a clear, smooth transition.  

A wide variety of scenarios may require that a bot transition control of the conversation to a human. A few of those scenarios are [triage, escalation, and supervision](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-handoff-human#scenarios-that-require-human-involvement).  

Let's explore those scenarios by using the common help desk bot example:
* **Triage**: Using a bot to triage incoming requests and collect basic information (name, phone number, reason for calling) allows agents to devote their time to solving the problem instead of collecting information.  
* **Escalation**: A bot may be able to answer basic questions and resolve simple issues (e.g. password-reset). If the issue is complex, the bot will need to escalate to a human agent. To implement this type of scenario, a bot must be capable of differentiating between issues it can resolve independently and issues that must be escalated to a human.
* **Supervision**: Sometimes, the human agents will want to monitor multiple conversations instead of taking control. The bot will use a machine learning model to determine the probable issue. If it's confidence is low, the bot can privately confirm the diagnosis and remedy with the human agent and request authorization to proceed.

How and when you decide to transfer the user from a bot to a human needs to be handled carefully. Read more about [transitioning control of the conversation and routing messages between user and agent](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-handoff-human#transitioning-control-of-the-conversation). 

If you want to dive deeper into what information gets handed-off, when the decision to handoff occurs, or how to implement this (code), we recommend you check out this [awesome blog article](https://www.microsoft.com/developerblog/2017/06/30/bot-to-human-handover-in-node-js/) and its associated [GitHub repository](https://github.com/palindromed/Bot-HandOff) and [npm module](https://www.npmjs.com/package/botbuilder-handoff). After that, you'll probably want to read [the follow-up blog post](https://www.microsoft.com/developerblog/2018/02/05/human-handoff-dashboard/) about how to develop a bot analytics dashboard that analyzes your bot to human handoff interactions.

     
### Section 2.4: Bot to web browser and back

> **Warning**: Transitioning from chat to web browser and back is not ideal, as switching between applications can easily confuse a user. To provide a better experience, many channels offer built-in HTML windows that a bot can use to present applications would otherwise appear in a web browser. This technique allows the user to remain within the conversation while still accessing external resources. This approach is conceptually similar to mobile applications managing authorization flows using OAuth within embedded web views.

Some scenarios require more than just a bot to fulfill a requirement. A bot may need to send the [user to a web browser to complete a task and then resume the conversation with the user](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-integrate-browser) after the task has been completed. The two most common reasons for this are:
* Authentication and authorization
    * If a bot wants the ability to access the user's calendar in Office 365, the user must first authenticate with Microsoft Azure Active Directory by being redirected to a browser to complete authentication/authorization tasks, and then resume the conversation.
* Security and compliance
    * Security and compliance requirements often restrict the type of information that a bot can exchange with a user. For example, if the user wants to execute a payment with a third-party, a credit card number should not be specified in the conversation. The bot will direct the user to a web browser to complete the payment process and then resume the conversation.

OK. So how do we go from the bot to the web browser and back again?

Here's a high-level flow with a brief explanation for each step. You should refer [here](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-integrate-browser#bot-to-web-browser-and-back-again) for more details:

![Bot to web browser and back again](./resources/assets/b2w2b.png)

1. The bot generates and displays a hyperlink (with the conversation context) that redirects the user to a website.
2. The user clicks the hyperlink and is redirected to the target URL.
3. The bot enters a state awaiting communication from the website.
4. The user completes the necessary task(s) via the web browser.
5. When the user is done, the website generates a [magic number](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-integrate-browser#verify-identity) and instructs the user to send it in the conversation with the bot.
6. The website [signals to the bot](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-integrate-browser#website-signal-to-bot) that the user has completed the website flow and provides the magic number and any relevant data.
7. The user provides the magic number to the bot, and the bot validates that it matches the expected value.  

If you want to get into the code, we recommend checking out these samples for bot authentication with the [Bot Framework v3 SDK](https://github.com/MicrosoftDX/botauth). You can also see what's been added to the Bot Framework v4 SDK authentication libraries for [.NET](https://github.com/Microsoft/botbuilder-dotnet/tree/master/libraries/Microsoft.Bot.Connector/Authentication) and [Node.js](https://github.com/Microsoft/botbuilder-js/tree/master/libraries/botframework-connector/lib/auth). 

[This blog](https://blogs.msdn.microsoft.com/uk_faculty_connection/2016/06/17/developing-a-microsoft-health-bot-based-on-data-captured-from-the-microsoft-band/) also provides a nice end-to-end example for how you might incorporate bot to web browser and back into a Health Bot with data from the Microsoft Band ([RIP](www.businessinsider.com/microsoft-fitness-band-discontinued-2016-10)).
   
### Section 2.5: Bots in websites
Although bots commonly exist outside of websites, they can also be embedded within a website. For example, you may embed a knowledge bot within a website to enable users to quickly find information that might otherwise be challenging to locate within complex website structures. Or you might embed a bot within a help desk website to act as the first responder to incoming user requests. The bot could independently resolve simple issues and handoff more complex issues to a human agent.

Microsoft provides two ways to integrate a bot in a website: the Skype web control (essentially a Skype client in a web-enabled control) and an open source web control.

The [open source web chat control](https://github.com/Microsoft/BotFramework-WebChat) is based upon [ReactJS](https://reactjs.org/) and uses the [Direct Line API](https://docs.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts) to communicate with the Bot Framework. The web chat control provides a blank canvas for implementing the web chat, giving you full control over its behaviors and the user experience that it delivers.

The [backchannel](https://docs.microsoft.com/en-us/azure/bot-service/nodejs/bot-builder-nodejs-backchannel) mechanism enables the web page that is hosting the control to communicate directly with the bot in a manner that is entirely invisible to the user. This capability enables several useful scenarios:

* The web page can send relevant data to the bot (e.g., GPS location).
* The web page can advise the bot about user actions (e.g., "user just selected Option A from the dropdown").
* The web page can send the bot the auth token for a logged-in user.
* The bot can send relevant data to the web page (e.g., current value of user's portfolio).
* The bot can send "commands" to the web page (e.g., change background color).


### Section 2.6: Bots in apps
Although bots most commonly exist outside of apps, they can also be integrated with apps. For example, and similarly to bots in websites, you could embed a knowledge bot within an app to help users find information that might otherwise be challenging to locate within complex app structures. You could embed a bot within a help desk app to act as the first responder to incoming user requests. The bot could independently resolve simple issues and hand off more complex issues to a human agent.

Unless you're dealing with a web-based mobile app, use the [Direct Line API](https://docs.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts) to integrate a bot with an app (Native mobile, IoT, other types of apps/games). If it is a web-based mobile app, you can communicate with the Bot Framework using the same components that a bot embedded in a website would use, just encapsulated within the native app's shell.

Check out the [documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-embed-app) and this [bot in apps sample](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/capability-BotInApps) for more information.


## Section 3: Bot Framework v4 SDK

As you've probably noticed by now, there are two Bot Framework SDK versions in circulation at the moment. The Bot Framework v4 SDK is actively being developed (officially announced at //build on May 7) and you can access them here (depending on language):

- [SDK for Node.js](https://github.com/Microsoft/botbuilder-js)
- [SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet)
- [SDK for Python](https://github.com/Microsoft/botbuilder-python)
- [SDK for Java](https://github.com/Microsoft/botbuilder-java)  

Why?  

There are two main reasons:
1. C#/Node.js SDKs in v3 are vastly different. There are different names for the same concepts, different concepts, different architectures, no common extensibility points, and complex dependency trees.
2. Both SDKs are too opinionated, regarding conversation management and state management.

So, as you might've guessed, the Bot Framework v4 SDK had four related goals:
1. Simplify
2. Unify programming models across languages
3. Allow developers to pick components and services
4. Break monolithic stack into a la carte libraries to enable more innovation

The v4 SDK architecture:
![v4 SDK Architecture](./resources/assets/v4sdk.png)

Each GitHub repository should have a "Wiki" tab with documentation information to help you get started. Additionally, we've created a lab for you (to complete later) as part of the [LearnAI-Bootcamp](https://azure.github.io/LearnAI-Bootcamp/) that integrates Azure Search and LUIS into a bot built with the Bot Framework v4 SDK. You can find the [building bots lab here](https://github.com/Azure/LearnAI-Bootcamp/tree/master/lab02.2-building_bots).

In 05-cognitive_services, we'll talk more about some of the differences between v3 and v4, and we'll walk through integrating services into the v3 and v4 SDK.


### Continue to [2_activity](./2_activity.md)
Back to [README](./readme.md)  



## References

- Key scenarios for bots  
      
    Cortana skills bot
    - [Cortana skills scenario](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-cortana-skill)
    - [Build a speech-enabled bot with Cortana skills](https://docs.microsoft.com/en-us/azure/bot-service/dotnet/bot-builder-dotnet-cortana-skill)
    - [Cortana skills kit](https://docs.microsoft.com/en-us/cortana/skills/overview)
    - [Cortana skills samples](https://docs.microsoft.com/en-us/cortana/skills/cortana-samples)  
      
    Enterprise productivity bot
    - [Enterprise productivity scenario](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-enterprise-productivity)
    - [Enterprise productivity sample (v3 SDK)](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Enterprise/src)
    - [Microsoft Graph](https://graph.microsoft.com/)
    - [Another Enterprise bot architecture](https://blogs.msdn.microsoft.com/pragdev/2018/02/10/enterprise-bot-architecture/)
    - [UST Global’s Bot Journey](https://customers.microsoft.com/en-us/story/ust-global-professional-services-microsoft-bot-framework-en)  
      
    Information bot
    - [Information scenario](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-informational)
    - [Information sample (v3 SDK)](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Informational/src)
    - [Navitime chatbot to help tourists get around Japan](https://customers.microsoft.com/en-us/story/navitime-japan-travel-hospitality-microsoft-cognitive-services)
    - [Fiducia & GAD IT AG using bots for customer services and support](https://customers.microsoft.com/en-us/story/fiducia-gad-cortana-azure-powerbi-services-bot-framework-banking-germany-en)  
      
    IoT bot
    - [IoT scenario](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-scenario-internet-things)
    - [IoT sample (v3 SDK)](https://github.com/Microsoft/AzureBotServices-scenarios/tree/master/CSharp/Iot/src)
    - [IoT solutions](https://www.microsoft.com/en-us/internet-of-things/solutions)  
      
- Common patterns  
  
    Task Automation
    - [Task automation documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-task-automation)
    - [Simple task automation sample (C# v3 SDK)](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/capability-SimpleTaskAutomation)
    - [Simple task automation sample (Node.js v3 SDK)](https://github.com/Microsoft/BotBuilder-Samples/tree/master/Node/capability-SimpleTaskAutomation)  
      
    Access to knowledge and other content
    - [Azure search]( https://azure.microsoft.com/en-us/services/search/)
    - [QnA maker](https://www.microsoft.com/cognitive-services/en-us/qnamaker)
    - [Bootcamp Materials - Combing LUIS and Azure Search in Microsoft Bot Framework SDK v4 for .NET](https://github.com/Azure/LearnAI-Bootcamp/blob/master/emergingaidev_bootcamp.md)
    - [Search-powered bots sample (v3 SDK)](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/demo-Search)
    - [Knowledge bot sample (v3 SDK)](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/sample-KnowledgeBot)
    - [QnA maker library for v4 SDK (.NET)](https://github.com/Microsoft/botbuilder-dotnet/tree/master/libraries/Microsoft.Bot.Builder.Ai)
    - [Using LUIS and QnA maker with the v4 SDK](https://github.com/Microsoft/botbuilder-dotnet/wiki/Using-LUIS-and-QnA-Maker)
    - [Bing Search APIs](https://azure.microsoft.com/en-us/services/cognitive-services/directory/search/)
    - [Microsoft Graph](https://developer.microsoft.com/en-us/graph)  
      
    Bot to human handoff
    - [Transition conversations from bot to human](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-handoff-human)
    - [Bot to human handoff in Node.js](https://www.microsoft.com/developerblog/2017/06/30/bot-to-human-handover-in-node-js/)
    - [Analyzing bot to human handoff interactions](https://www.microsoft.com/developerblog/2018/02/05/human-handoff-dashboard/)
    - [Bot handoff sample code and implementation instructions (Node.js)](https://github.com/palindromed/Bot-HandOff)
    - [Botbuilder-handoff npm module](https://www.npmjs.com/package/botbuilder-handoff)  
      
    Bot to web browser and back:
    - [Bot to web documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-integrate-browser)
    - [Bot Authentication samples (v3 SDK)](https://github.com/MicrosoftDX/botauth)
    - [Example of bot to web browser for authentication](https://blogs.msdn.microsoft.com/uk_faculty_connection/2016/06/17/developing-a-microsoft-health-bot-based-on-data-captured-from-the-microsoft-band/)
    - [Authentication library for the v4 SDK (.NET)](https://github.com/Microsoft/botbuilder-dotnet/tree/master/libraries/Microsoft.Bot.Connector/Authentication)
    - [Authentication library for the v4 SDK (Node.js)](https://github.com/Microsoft/botbuilder-js/tree/master/libraries/botframework-connector/lib/auth)  
      
    Bots in websites
    - [Bots in websites documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-embed-web-site)
    - [Open source web chat](https://github.com/Microsoft/BotFramework-WebChat)
    - [Using the backchannel mechanism (Node.js)](https://docs.microsoft.com/en-us/azure/bot-service/nodejs/bot-builder-nodejs-backchannel)
    - [Connect directly to bots with the Direct Line API](https://docs.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts)
    - [How to enable bots for Direct Line](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-channel-connect-directline)  
      
    Bots in apps
    - [Bots in apps documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-design-pattern-embed-app)
    - [Bots in apps sample (v3 SDK)](https://github.com/Microsoft/BotBuilder-Samples/tree/master/CSharp/capability-BotInApps)
    - [Use open source web chat control](https://github.com/Microsoft/BotFramework-WebChat)
    - [For native mobile apps, IoT apps, and other types of apps/games use the Direct Line API](https://docs.microsoft.com/en-us/azure/bot-service/rest-api/bot-framework-rest-direct-line-3-0-concepts)  

- Bot Framework v4 SDK
    - [SDK for Node.js](https://github.com/Microsoft/botbuilder-js)
    - [SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet)
    - [SDK for Python](https://github.com/Microsoft/botbuilder-python)
    - [SDK for Java](https://github.com/Microsoft/botbuilder-java)  
      
- Additional resources
    - [LearnAI-Bootcamp](https://github.com/Azure/LearnAI-Bootcamp)
    - [LearnAnalytics Website](http://learnanalytics.microsoft.com/)
    - [AI Learning Paths](https://aischool.microsoft.com/learning-paths)
  
### Continue to [2_activity](./2_activity.md)
Back to [README](./readme.md)