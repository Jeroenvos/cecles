# System Analysis
The system analysis chapter is dedicated to explaning the functionality of the CECLES system. This chapter is split in two mains sections, the keyword pipeline and the results pipeline. 

<!-- expand on this -->

##The keyword pipeline
This section provides information on how the keyword processing in CECLES is planned. Not all of the features presented here will be functional in the prototype that is presented with this report. However, for explanational purposes in this document it is assumed that all features are already present.

### Relevance
In this pipeline focuses on delivering keywords that represent the course contents best. Therefore, 'relevance' in this section is defined to be the 'measure' by which a keyword is representative of the course contents whilst being specific enough to have meaning.

###Keyword Processing Diagram

![Pipeline keywords](../Diagrammen/Pipeline keyword relevance.png "Keyword Pipeline Diagram")

###Sources
For the initial CECLES application the course data from the TUDelft API is used. To extend the course description and also for increasing the amount of keywords that are extracted, additional sources like the OCR data from the Colegerama slides should be used. This is intended to improve the relevance of the keywords that are used for querying.

Because even at the TU spelling errors are quite common, an initial spelling check on all course descriptions and goals is performed.

### AlchemyAPI
AlchemyAPI is a semantic analysis tool which supports a computer’s ability to understand human language and vision via an SaaS API. It integrates advanced text mining and computer vision functionality into Cecles' data-processing pipeline. [AlchemyAPI](http://www.alchemyapi.com/)

### Text analysis
Since Alchemy already does a large part of the analysis, stemming is the action most performed after the term extraction. Stemming is done because after testing several queries, overlap was found between several keywords (not yet in the results). 

The keywords are then compared to a blacklist. This list consists of insignificant of simplistic words. Also, since CECLES supports users' input, the blacklist holds inappropriate words.

### Score model
The score model consists of several techniques to obtain different factors for determining the relevance of the keywords. Currently the most important initial score factor is the check to keywords of all collected courses. Also the keywords can be used in a Google or Wikipedia search. Keywords that have too many results are seemly too generic. Containing too less results can indicate misguided terms. 
This score model has yet to be completed with additional techniques.

If a part of the keywords cannot be examined could be processed with the help of Crowdflower. If Crowdflower already has to be deployed in the process of keyword operations has still to be determined. 

### The User
When the keywords are extracted, scored on their relevance and sorted and filtered by eg. relevance they can be used for generating queries. Whether the right keywords are extracted is among others examined by the users' feedback. 

Relevance feedback is typically used for query expansion during short-term modeling of a user's immediate information need and for user profiling during long-term modeling of a user's persistent interests and preferences. Traditionally feedback methods require explicit feedback given by, for example, voting a plus or a minus. Such relevance feedback methods force users to engage in additional activities beyond their normal searching behavior [(Kelly, 	2003)](http://people.csail.mit.edu/teevan/work/publications/papers/sigir-forum03.pdf). To limit this 'costs' for the user in the keyword part, CECLES focuses primarily on implicit feedback. In this way in the parts that require explicit feedback most, the effectiveness of explicit techniques will remain well.

With implicit feedback click rates, conversions and bounce rates are used to re-rank the keywords in the score model  (or in the sort and filter step). With explicit feedback the user is asked to assess the keywords on their relevance. 
Also, when a user thinks a relevant keyword is missing he or she can submit additional keywords. These inputs will then be checked with the blacklist and put in the score model.

#### Implicit feedback
The implicit user feedback consists a.o. of the click behavior of the student. When a result is used a lot, the relevance score will increase. This results in the most 'popular issues' at the top of the page. The more specific issues or subjects will descend to the bottom or next pages. A model should determine the proper weights and a future feature could be to categorize the topics of the course so all the topics will still be significantly represented on the first result page.

#### Explicit feedback
Since the user interface has to be as clean as possible, not to burden the student with all kinds of feedback requests, the user will not be asked for feedback in this phase. This is as mentioned in the beginning of this paragraph. Instead of asking the student, an expert's feedback is used. Teachers can see the courses they teach and have the possibility to up vote and down vote the keywords of his/ her courses as well as other courses. Since they are experts it is assumed that they will not 'spam' or  misinterpret those keywords. Therefore this feedback will get a high weight factor.


## The result Pipeline
************** INTRO RESULT PIPELINE********
*************** Hier pipeline diagram********
**********BESCHRIJVING INTRO RESULT PIPELINE *************