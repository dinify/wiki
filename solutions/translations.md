### Intro
This page documents how the translations are solved form an architecural standpoint. 

### Aspects  
#### Problem scope  
Design goals include, being able to switch between languages on the frontend and deliver the menu content, as well as all other restaurant services in multiple languages based on user's preference. It is initially determined by detecting it in the User App, and users should be able to modify that initial setting in the interface. On the restaurant side, they have to choose a default language, when the menu gets created. We recommend restaurants to use English as their default language becase that yields better results.

#### Limitations
Using Google Translate API has a cost, and this cost should be minimized.
Translation quality is better with language pairs that translate between English and another language.
The cost of the Translate API isn't the only important factor to consider, it's also the API's response speed to our translation service backend.

## Proposal
### Design goals
Translations should be done in real time, as the restaurant is creating their menu in the Dashboard. 
We support 96 languages in total, which is the intersection of the list of supported languages by Unicode CLDR data and Google Translate API. However, according to to UN WTO statistics, only a subset of these languages are relevant for our target, the relevance of which are dependent on the locality of the market. For example, in Japan, about 80% of tourists only consist of Asians, but this statistic is different for another country. This data should be used for suggestive UI.   
So for the European market, this list is narrowed down to _40 default languages_, that are a subset of all supported languages. Using the the restaurant's default language as the source menu data, the realtime translations will be done to these target languages from  without any extra configuration by the user (by default).
See data:  
[artifacts/i18n/supported-languages](https://gitlab.com/dinify/artifacts/blob/master/i18n/supported-languages.json)  
[artifacts/i18n/default-languages](https://gitlab.com/dinify/artifacts/blob/master/i18n/default-languages.json)

### Glossary
Design goals:
 - save on cloud costs
 - get overall better performance out of the system by saving on API request time
 - store and retrieve existing translations to avoid re-translating the same term
 - record the time at which the translation function was executed and transformed the original string into a string in the new language

Each time a translate function is executed a new localized term is created in the graph, where each term is a node in the graph. The accuracy of the translation function can be represented by a weight between each node. The weight is updated by the number of verifications of a given translation input - output pair. The reason this is a complex problem is because the translation function is a [one-way function](https://en.wikipedia.org/wiki/One-way_function).
By making a distinction between an "input" to the translation function, and the "output" of that function, it's possible to limit the problem scope. Defining two types of terms in the glossary:
- **Content String**: static terms that make up the frontends; the dynamic terms that were input by users. In other words, textual data that make up our content. What language this content happens to be in is determined by the user at the time of creating the content string by posting the value of an input in a form on the frontend, having selected their default language to create the content in. There are also ways to detect language for an arbirary input string using the Translation API.  
- **Translation String**: terms that were an output of an automatic (or manual) translation, using a **Content String**. The language of these strings are determined by the target languages a given restaurant wants to deliver their menu content in. There should be a setting in the Dashboard to modify this, otherwise 40 target languages by default in the European market.

### **Translation** 
An execution of a one way tranformation function, given an input string and target language(s).
- content string (input text, input language)
- translation string (output text, output language)
- number of verifications by proofreaders
- translated at (datetime)
- context of the function: Cloud API request ID and metadata, user ID in case of manual translation by a translato role, etc

In NoSQL terms, a unique constraint should be enforced on the language - string pair. It is important to have control over when the translated strings get promoted to being part of the content that the user app provides.
#### Stage 1.
We treat translation strings as content strings automatically, because we have no resources to process translations by users with proofreader roles. So the "threshold" for including translations in our content is 0 verifications. 
#### Stage 2.
The mechanism that includes the translation strings into the content should sort avaiable translations for a given input (content string), by the amount of verifications the translation has. 

### Strategy
Using cloud techonolgies to automatically translate existing text content into a range of supported languages. Then based on this data, we are able to collect a list of ingredients and other related culinary vocabulary, and translate it manually via hiring freelance work. The proofreader role on the platform would allow us to scale this by not having to put in manual work to find freelancers to do the job at some point. 

### Conclusions
In the UI, the most relevant languages should be made more accessible by either hiding irrelevant languages to the bottom of the list or hiding them.
On the backend, translations have to be designed in a way that is easy to interface with from the controller that deals with the translations all at once, as well as separately from each model.