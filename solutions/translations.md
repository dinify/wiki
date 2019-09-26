### Intro
This page documents how the translations are solved form an architecural standpoint. 

### Aspects  
#### Problem scope  
Design goals include, being able to switch between languages on the frontend and deliver the menu content, as well as all other restaurant services in multiple languages based on user's preference. It is initially determined by detecting it in the User App, and users should be able to modify that initial setting in the interface. On the restaurant side, they have to choose a default language, when the menu gets created. We recommend restaurants to use English as their default language becase that yields better results.

#### Limitations
Using Google Translate API has a cost, and this cost should be minimized.
Translation quality is better with language pairs that translate between English and another language.

### Proposal
Translations should be done in real time, as the restaurant is creating their menu in the Dashboard. 
We support 96 languages in total, which is the intersection of the list of supported languages by Unicode CLDR data and Google Translate API. However, according to to UN WTO statistics, only a subset of these languages are relevant for our target, the relevance of which are dependent on the locality of the market. For example, in Japan, about 80% of tourists only consist of Asians, but this statistic is different for another country.   
See data:  
[artifacts/i18n/supported-languages](https://gitlab.com/dinify/artifacts/blob/master/i18n/supported-languages.json)  
[artifacts/i18n/default-languages](https://gitlab.com/dinify/artifacts/blob/master/i18n/default-languages.json)

### Strategy
Using cloud techonolgies to automatically translate existing text content into a range of supported languages. Then based on this data, we are able to collect a list of ingredients and other related culinary vocabulary, and translate it manually via hiring freelance work. The proofreader role on the platform would allow us to scale this by not having to put in manual work to find freelancers to do the job at some point. 

### Conclusions
In the UI, the most relevant languages should be made more accessible by either hiding irrelevant languages to the bottom of the list or hiding them.
On the backend, translations have to be designed in a way that is easy to interface with from the controller that deals with the translations all at once, as well as separately from each model.