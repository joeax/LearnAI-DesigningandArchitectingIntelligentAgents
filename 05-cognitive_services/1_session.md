# 5.1: Integration with Cognitive Services (and more)

In this session, we will break up **making bots smarter** into three sections:
1.  Cognitive Services
2.  Adding Cognitive Services to bots
3.  Other ways to make bots smarter

## Section 1: Cognitive Services 
Cognitive Services can be used to infuse your apps, websites and [bots with algorithms](https://docs.microsoft.com/en-us/azure/bot-service/bot-service-concept-intelligence) to see, hear, speak, understand, and interpret your user needs through natural methods of communication. 

There are five main categories for the available Cognitive Services:
- **Language understanding**: Allow your apps to process natural language with pre-built scripts, evaluate sentiment and learn how to recognize what users want
- **Knowledge extraction**: Map complex information and data to solve tasks such as intelligent recommendations and semantic search
- **Speech recognition and conversion**: Convert spoken audio into text, use voice for verification, or add speaker recognition to your app
- **Web search**: Add Bing Search APIs to your apps and harness the ability to comb billions of webpages, images, videos, and news with a single API call
- **Image and video understanding**: Image-processing algorithms to identify, caption and moderate your pictures and videos  

There are also [Cognitive Services Labs](https://labs.cognitive.microsoft.com/), and we'll talk through what's on the horizon with them.


You can browse all the specific APIs in the [Services Directory](https://azure.microsoft.com/en-us/services/cognitive-services/directory/). 

Next, we're going to dive a bit deeper (but still relatively on the surface - check out the [documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/Welcome) for technical details) - and provide something similar to a "cheat sheet" that includes a very brief each of the Cognitive Services. We'll tell you the main things they do and what to look out for (i.e. are they going away, only projects at the moment, etc.).

### Section 1.1: Language understanding
- [Language Understanding Intelligent Service (LUIS)](https://azure.microsoft.com/en-us/services/cognitive-services/language-understanding-intelligent-service/)
    - Extract intents and entities from natural language
- [Text Analytics](https://azure.microsoft.com/en-us/services/cognitive-services/text-analytics/)
    - Determine language, key phrases, and sentiment
- [Bing Spell Check](https://azure.microsoft.com/en-us/services/cognitive-services/spell-check/)
    - Correct spelling errors, recognize name differences, brands, slang, and homonyms
- [Translator Text](https://azure.microsoft.com/en-us/services/cognitive-services/translator-text-api/)
    - Real-time text translation
- [Content Moderator](https://azure.microsoft.com/en-us/services/cognitive-services/content-moderator/)
    - Explicit or offensive content moderation for images and videos

### Section 1.2: Knowledge extraction
- [QnA Maker](https://qnamaker.ai/)
    - Quickly and easily create simple question and answer bots based on FAQ URLs, structured documents, or editorial content

### Section 1.3: Speech recognition and conversion
- [Speech](https://azure.microsoft.com/en-us/services/cognitive-services/speech/)
    - Convert speech-to-text and text-to-speech, understand intent
        - [Speech to Text](https://azure.microsoft.com/en-us/services/cognitive-services/speech-to-text/)
            - Convert audio to text
        - [Text to Speech](https://azure.microsoft.com/en-us/services/cognitive-services/text-to-speech/)
            - Convert text to speech
        - [Speech Translation](https://azure.microsoft.com/en-us/services/cognitive-services/speech-translation/)
            - Easily add real-time speech translation to your bot
        - [Custom Speech Service (CRIS) (preview)](https://azure.microsoft.com/en-us/services/cognitive-services/custom-speech-service/)
            - Overcome speech recognition barriers such as speaking style, vocabulary, and background noise
- [Speaker Recognition API (preview)](https://azure.microsoft.com/en-us/services/cognitive-services/speaker-recognition/)
    - Identify individual speakers or use speech as a means of authentication


### Section 1.4: Web search
- [Bing Web Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-web-search-api/)
    - Conduct web searches within bots
- [Bing Image Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-image-search-api/)
    - Conduct image searches within bots
- [Bing Video Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-video-search-api/)
    - Conduct video searches within bots
- [Bing News Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-news-search-api/)
    - Conduct news searches within bots
- [Bing Autosuggest](https://azure.microsoft.com/en-us/services/cognitive-services/autosuggest/)
    - Automated search suggestions – _probably not applicable for a standard bot_
- [Bing Entity Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-entity-search-api/)
    - Bring rich context about entities (like people, places, things, etc.)
- [Bing Custom Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-custom-search/)
    - Easy-to-use, ad-free, commercial-grade search tool that lets you deliver the results you want
- [Bing Visual Search](https://azure.microsoft.com/en-us/services/cognitive-services/bing-visual-search/)
    - Enable users to search with images and gain insights in new ways

### Section 1.5: Image and video understanding
- [Computer Vision API](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/)
    - Obtain tags, descriptions, adult/racy scores, text, hand writing, celebrities, and more from images
- [Face API](https://azure.microsoft.com/en-us/services/cognitive-services/face/)
    - Detect faces and compare similar ones, organize similar images in groups, identify previously tagged people in images and their emotions
- [Video indexer](https://azure.microsoft.com/en-us/services/cognitive-services/video-indexer/)
    - Unlock video insights – _Video API ended, Video Indexer replaced it_
- [Custom Vision Service (preview)](https://azure.microsoft.com/en-us/services/cognitive-services/custom-vision-service/)
    - Custom image classification models made easy, also object detection is in preview
- [Content Moderator](https://azure.microsoft.com/en-us/services/cognitive-services/content-moderator/)  
    - Machine-assisted moderation of text and images

### Section 1.6: Cognitive Services Labs
- [Project Gesture](https://labs.cognitive.microsoft.com/en-us/project-gesture)
    - Incorporate gesture-based controls into your apps 
- [Project Local Insights](https://labs.cognitive.microsoft.com/en-us/project-local-insights)
    - Score the attractiveness of a location 
- [Project Event Tracking](https://labs.cognitive.microsoft.com/en-us/project-event-tracking)
    - Find events associated with Wikipedia entities 
- [Project Entity Linking](https://labs.cognitive.microsoft.com/en-us/project-entity-linking)
    - Disambiguates entities from context and links text from your bot to additional information 
- [Project Knowledge Exploration](https://labs.cognitive.microsoft.com/en-us/project-knowledge-exploration)
    - Quickly add interactive search to structured data 
- [Project Academic Knowledge](https://labs.cognitive.microsoft.com/en-us/project-academic-knowledge)
    - Help users find the academic resources they’re looking for
- [Project Ink Analysis](https://labs.cognitive.microsoft.com/en-us/project-ink-analysis)
    - Recognize digital handwriting and common shapes as well as layouts
- [Project Answer Search](https://labs.cognitive.microsoft.com/en-us/project-answer-search)
    - Instead of providing users with a list of ten blue links, the service sifts through millions of web documents and presents the relevant results
- [Project URL Preview](https://labs.cognitive.microsoft.com/en-us/project-url-preview)
    - Quickly provide a webpage preview of a URL's page title, description and relevant image
- [Project Conversation Learner](https://labs.cognitive.microsoft.com/en-us/project-conversation-learner)
    - Teach new behaviors to task-oriented conversational interfaces through example interactions
- [Project Personality Chat](https://labs.cognitive.microsoft.com/en-us/project-personality-chat)
    - Choose from multiple default personas to enhance chat conversations and easily add curated small talk responses
- [Project Anomaly Finder](https://labs.cognitive.microsoft.com/en-us/project-anomaly-finder)
    - Use ML to help understand abnormal events in data
- [Project Custom Decision](https://labs.cognitive.microsoft.com/en-us/project-custom-decision)
    - Use reinforcement learning in a new approach for personalizing content

## Section 2: Adding Cognitive Services to Bots

Let's assume you've completed all the recommended steps in the course up until now for a project you're working on. You've designed your bot, determined your LUIS schema, created an architecture, and picked Cognitive Services to include. Your next task is going to be to put it all together and actually build the bot.  

This is not a coding course, so we will not spend time getting deep into the code. We do want to share a few samples showing how you _might_ integrate some of the various services into a bot. The samples we reference will show code written with the Microsoft Bot Framework SDK [V4 for .NET](https://github.com/Microsoft/botbuilder-dotnet), from the [samples repository for .NET Core](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore).

The examples we will point you to walk through integrating QnA Maker, LUIS, and Azure Search (note: it is not a Cognitive Service, but it's been mentioned several times), and the Text Translator API. For each of the following samples, if you want a deeper understanding, we recommend reviewing the `BotServices.cs`, `Startup.cs`, and `<samplename>Bot.cs` files **later** and examining the related code for that service. This section is really a list of resources for POC/development of your future bot endeavors.

1. QnA Maker:
    * [Sample 1: Basic QnA Bot](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/11.qnamaker)
    * [Sample 2: QnA with AppInsights](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/20.qna-with-appinsights)
    * [Documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0)
2. LUIS:
    * [Sample 1: Basic LUIS Bot](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/12.nlp-with-luis)
    * [Sample 2: LUIS with AppInsights](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/21.luis-with-appinsights)
    * [Documentation](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0)
3. Text Translator API:
    * [Sample 1: Multilingual Bot](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/17.multilingual-bot)
    * [Documentation](https://github.com/Microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/17.multilingual-bot/readme.md)


In addition, we wanted to provide a list of samples that integrate multiple:
1. [LearnAI-Bootcamp for Emerging AI Developers](https://github.com/Azure/LearnAI-Bootcamp/blob/master/emergingaidev_bootcamp.md)
    * Step-by-step instructions for building a V4 SDK bot that incorporates the Computer Vision API, LUIS, Azure Search, and the Bing Image Search API.
2. [Conference Buddy Bot](https://github.com/Azure/ConferenceBuddy)
    * While this sample is currently still in the V3 SDK, it's a great sample that shows how you might integrate Cognitive Services (Text Analytics, Bing Search, QnA Maker, and Video Indexer) into a bot.
2. More samples from the BotBuilder-Samples repository
    * Check out the [Samples list](https://github.com/Microsoft/BotBuilder-Samples#samples-list) to see what other samples are available in your language of choice.
    * If you're looking for a sample that will get you on your way to creating an enterprise bot, we recommend checking out [the enterprise-bot template](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/52.enterprise-bot).

> Side Note: If you want to combine multiple LUIS apps and QnAMaker services, there's a tool within [botbuilder-tools](https://github.com/Microsoft/botbuilder-tools) called Dispatch that can assist. You can read the [documentation here](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-tutorial-dispatch?view=azure-bot-service-4.0&tabs=csaddref%2Ccsbotconfig) and check out the [dispatch sample](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/14.nlp-with-dispatch) if you're interested in learning more about it.


## Section 3: Other ways to make bots smarter

In this section, we'll talk about some other ways to make bots smarter. The main topics we'll touch on are managing data and organizing conversations.

### Section 3.1: Managing data

#### Managing state data
The [Bot Builder Framework enables your bot to store and retrieve state data](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-storage-concept?view=azure-bot-service-4.0) that is associated with a user, a conversation, or a specific user within the context of a specific conversation. State data can be used for many purposes, such as determining where the prior conversation left off or simply greeting a returning user by name. If you store a user's preferences, you can use that information to customize the conversation the next time you chat. For example, you might alert the user to a news article about a topic that interests her or alert a user when an appointment becomes available.

In the Bot Builder v4 SDK, for each activity that your application receives, the adapter creates a [new turn context object](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-activity-processing?view=azure-bot-service-4.0) that includes information about the channel, the sender, the conversation, and the received activity. This context object exists only for the processing of that one activity (also referred to as one turn). Your bot is otherwise stateless. So, for testing and prototyping purposes, this may be enough. For production bots, you can implement your own storage adapter or use one of the Azure extensions. The Azure extensions allow you to store your bot's state data in either Table Storage, CosmosDB, or SQL.

#### Managing historical data

For many reasons, you may choose to log or store different conversation aspects. One reason might be to determine what kinds of things users are actually using the bot, and another reason might be to collect data about users to generate machine learning models (e.g. a recommendation engine based on what users typically search for in a retail bot). The V4 SDK makes it easier for you to do this, by building in sample code around `LoggerFactory` (which is an extension within the `Microsoft.Extensions.Logging` library) to most of the `Startup.cs` files in the samples. You can see logging being implemented in [this sample](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/22.conversation-history), and the storage being set up in [this sample](https://github.com/Microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/13.basic-bot/Startup.cs).

**Want to dive deeper?** 

We're really just making you aware that these are things you need to consider as your bot projects progress. We have resources for you to learn more:  

* [Write directly to storage](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-howto-v4-storage?view=azure-bot-service-4.0)
* [Manage conversation and user state](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-howto-v4-state?view=azure-bot-service-4.0)
* [Persist data in dialogs](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-tutorial-persist-user-inputs?view=azure-bot-service-4.0)
* Learn how [Dialogs state](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-dialog-state?view=azure-bot-service-4.0) relates to the overall conversation state.
* Understand how [Middleware](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-middleware?view=azure-bot-service-4.0) functions in the V4 SDK.
* [Botbuilder-utils-js](https://github.com/Microsoft/botbuilder-utils-js): This repository contains sample packages you can use to log transcripts (with CosmosDB or AppInsights) and store feedback from users during conversations.


### Section 3.2: Managing dialogs

Getting into exactly how dialogs function or are formed is beyond the scope of this design and architecture course. **However**, it is crucial to have a good conversation design (refer to modules 02 and 03) to develop an effective and smooth dialog stack. We recommend reviewing the following resources as you get further down the path in your bot projects in creating conversation flows:
* [How bots work](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0)
* [Dialogs library](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-concept-dialog?view=azure-bot-service-4.0)
* [Use dialog library to gather user input](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-prompts?view=azure-bot-service-4.0)
* Use dialogs to manage [simple conversation flow](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-dialog-manage-conversation-flow?view=azure-bot-service-4.0) and [complex conversation flow](https://docs.microsoft.com/en-us/azure/bot-service/bot-builder-dialog-manage-complex-conversation-flow?view=azure-bot-service-4.0)
* This sample focused on [message routing](https://github.com/Microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/09.message-routing)

### Continue to [2_activity](./2_activity.md)
Back to [README](./readme.md)  


