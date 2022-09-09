Sections:
1. Background:
	-Start by writing what do we know about the topic
Then write about what do we NOT know about the topic and what are the challenges. Then write about what about the unknowns that you are going to address

2. Goals and Objectives
You insert a separate section here and write about the goal(s) of your project and the objectives that will meet the goal. Typically, the way to write this is something like, "The goal of this research is to ...", and then continue with something like, "Goal 1 will be met by achieving the following objectives ...", and so on. The goal is a broad based statement, and the objectives are very specific, achievable series of statements that will show how you will achieve the goal you set out. 


# Amara
## Background:
### What we know about the topic: 
Indic epigraphy deals with inscriptions and manuscripts that date back several hundreds to thousands of years. An additional challenge is that Indic epigraphy is an umbrella term for manuscripts and inscriptions of several different dialects and languages. These can be divided broadly into Sanskritic and Dravidian languages, what is roughly north and south indian today. While studying the development of writing in ancient India, one can roughly divide the attempt into the following categories - The Indus Script, The Brahmi script, and The Kharoshthi script. The ancient indian writing epigraphists deal with comes in three major formats - 
1) Inscriptions on stones, stone-tablets in monuments  
2) Inscriptions as found in palm manuscripts and other similar organic medium like parched paper etc  
3) Inscriptions  on copper and similar metal plates as well as metal artifacts like vigrahas

Challenges that an Epigraphist faces when coming across the above are:  
a) Lack of good Photographs of the artefact  
b) Character challenges - can be faded or disfigured or partially damaged or malformed with additional unnecessary or accidental signages  etc  
c) Word challenges - a word is composed of characters with one or more characters having damaged character challenges as listed above  
d) Sentences Challenges - a sequence of words forming a sentence having damaged word challenges  
  
What an Epigraphist needs is:  
a) A tool that will help give plausible predictions on what could be the right options in repairing a damaged character or a damaged word or a broken sentence.  
b) With an ability to intrinsically understand the underlying patterns of usage of the symbols of the characters and words in predicting the missing or damaged characters or words after learning from what is available - either from that family of artefacts or from similar ones.  
c)And an ability to come up with statistics and meta-information predictions so more details about the family of artefact so as to formulate and populate an epidoc document for it.

Example:

Consider the stone inscriptions found in a temple. Typically these are slabs with several tens of lines of text carved on the slab. Perhaps there are some thirty such slabs. Of these thirty, really good inscriptions could be there on 12 of them and can be the training dataset. In this 12 slab photographs each core and complex character is marked and bounded using via. Next, perhaps there are 7 such slabs that pass the grade for recognisable characters. These 7 slab photographs can be used as the validation dataset. If successfully validated, the rest of 11 slabs have  all kinds of damages and defects can be processed using this application to predict the damaged character or damaged words or perhaps the sentence.  
In the context of say Bakshali manuscripts, the 70 odd palmscripts can be processed using these neural networks and all the damaged parts of the manuscript can be predicted and validated against what experts have come up with in order to make that manuscript complete. Part of the training could also mean that the domain knowledge is fed into the neural network appropriately.



## Goals and Objectives
The goal of this project is to 
  
Amara is an intelligent machine learning based epigraphist tool that enables the following:  
a) That allows the uploading and archival of images of a family of artefacts along with their meta-information from a physical archeological entity  
b) Allows the tool to apply machines learning techniques on the good resolution photographs for predicting parts which have possible problematic situations like damaged characters or words or sentences.  
c) Interactively allow the epigrahists to collaborate with team members in marking and identifying  individual characters and their associated diacritical markings so as to formulate the basic character set along with their composite formulations (like complex sandhi characters in samskrit)  
d) Allow Applying and gather statistics for clustering classification  
e) Allow applying a variety of deeplearning neural network libraries (like pytorch or tensorflow) to learn and finetune a multilayered deep neural network to recognise the characters and output recognised digital textual characters (equivalent of OCR)  
f) Generating options with probabilities of what the damaged character or word could be where needed. Additionally, it could also mean that domain knowledge oriented predictions are also attempted.  
g) Keep continuously augmenting and finetuning the database of artefacts, neural networks etc


# Nahautl
