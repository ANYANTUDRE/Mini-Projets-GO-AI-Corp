# Introduction au NLP & Rappels Deep Learning.md
This document goal is to provide a quick overview of Natural Language Processing.
I assume you already know most of theses concepts.


### Plan
**I. Le Traitement Automatique du Language Naturel (TALN ou NLP)**  
        1. Définition  
        2. Les Applications du NLP 
        3. Bibliothèques  pour le NLP
        4. Le Pipeline classique en NLP     
        5. Challenges  

**II. Le pipeline du NLP de plus près**
    1. Text Preprocessing
    2. Text Tokenization


**III. Rappels: Machine Learning pour le NLP**

   
**IV. Rappels: les Réseaux de Neurones pour le NLP**
        1. Brief history
        2. Le Perceptron    
        3. Le Perceptron Multi Couches (MLP ou PMC)    
        4. Couches denses : Transformation de la représentation des données   
        5. Les Réseaux de Neurones Convolutifs (CNN)
        6. Les Réseaux de Neurones Récurrents(RNNs) et LSTMs
        7. Exemple d'implémentation d'un PMC avec Keras.   

  
**IV. 1er Mini Projet: Analyse de sentiments**





# I. Le Traitement Automatique du Language Naturel (TALN ou NLP)

## 1. Définition
🗣️ 𝐍𝐚𝐭𝐮𝐫𝐚𝐥 𝐋𝐚𝐧𝐠𝐮𝐚𝐠𝐞 𝐏𝐫𝐨𝐜𝐞𝐬𝐬𝐢𝐧𝐠 (or NLP for short) is an engineering discipline that enables computers to understand, generate, and manipulate human language in the way that it is written, spoken, and organized.
NLP can be divided into two overlapping subfields: 
- **Natural Language Understanding (NLU)**, which focuses on semantic analysis (meaning of a text).
- **Natural Language Generation (NLG)**, which focuses on text generation.

![Image](https://media.licdn.com/dms/image/D4E22AQE9-Pd-_7wSGA/feedshare-shrink_800/0/1711320661393?e=1715817600&v=beta&t=XoT-fL1M57T30LvVYM8PtfBwNvfKLxIfpnAPmc6ADEk)

**Voir Référence:**  [Natural Language Processing](https://www.linkedin.com/posts/anyantudre_nlp-ai-llm-activity-7177929763972362240-2S8b?utm_source=share&utm_medium=member_desktop).


## 2. Les Applications du NLP
NLP is used for a wide variety of language-related tasks:
- 𝐓𝐞𝐱𝐭 𝐜𝐥𝐚𝐬𝐬𝐢𝐟𝐢𝐜𝐚𝐭𝐢𝐨𝐧: the process of automatically categorizing or labeling text data into predefined categories or classes based on its content and context. Sub-tasks include:
     o  Sentiment Analysis: identifying emotional intent in text, which aids in customer review classification for example.
     o  Toxicty detection: detecting hate speech or defamation in online content.
     o  Spam Detection: flagging unsolicited emails for removal.

- **Neural** 𝐌𝐚𝐜𝐡𝐢𝐧𝐞 𝐭𝐫𝐚𝐧𝐬𝐥𝐚𝐭𝐢𝐨𝐧: that allows to automate translation between different languages. Google Translate and DeepL are probably the most famous mainstream applications.

- 𝐓𝐞𝐱𝐭 𝐠𝐞𝐧𝐞𝐫𝐚𝐭𝐢𝐨𝐧: probably the most popular application of NLP right now with Generative AI. It aims to produce text similar to human-written text, including:
     o  Conversation agents and virtual assistants (Chatbots) for questions answering,
     o  Autocompletion, predicting the next word,
     o  Masked words filling etc.

- 𝐍𝐄𝐑 (Named Entity Recognition): identifying and extracting useful entities such as personal names, organizations and locations in text.

- 𝐓𝐨𝐩𝐢𝐜 𝐦𝐨𝐝𝐞𝐥𝐢𝐧𝐠: an unsupervised text mining task that discovers abstract topics within a corpus of documents.

- 𝐒𝐮𝐦𝐦𝐚𝐫𝐢𝐳𝐚𝐭𝐢𝐨𝐧: task of shortening or condensing text to highlight the most relevant information.

Moreover, NLP isn’t limited to written text though; it also tackles complex challenges in 𝐬𝐩𝐞𝐞𝐜𝐡 𝐫𝐞𝐜𝐨𝐠𝐧𝐢𝐭𝐢𝐨𝐧 and 𝐜𝐨𝐦𝐩𝐮𝐭𝐞𝐫 𝐯𝐢𝐬𝐢𝐨𝐧, such as generating transcripts of audio samples or descriptions of images.

![](https://alvinntnu.github.io/NTNU_ENC2045_LECTURES/_images/nlp-apps.png).

**Voir Référence:**  [Natural Language Processing](https://www.linkedin.com/posts/anyantudre_nlp-ai-llm-activity-7177929763972362240-2S8b?utm_source=share&utm_medium=member_desktop).



## 3. Bibliothèques

NLTK and spaCy are probably the two most popular and widely used tools/libraries for NLP (in Python of course), although there are many other interesting tools.
What are their specific features?

- 𝐬𝐩𝐚𝐂𝐲: at the top of my list, this is my favorite NLP library to date. spaCy is versatile, open-source, object-oriented and comes with pre-trained statistical models (like the famous BERT) and word vectors. It supports over 66 languages and can be used to build production-ready systems for NER, sentence segmentation, text classification, lemmatization etc. 
Recently, spacy-llm was released to enable the integration of Large Language Models (LLMs) into spaCy.

- 𝐍𝐋𝐓𝐊 (Natural Language Toolkit): one of the oldest NLP libraries, written in Python and used in both academia and industry. It provides easy-to-use interfaces to corpora and lexical resources such as WordNet. 
It also provides a suite of text processing libraries for classification, tagging, tokenization, stemming, parsing and semantic reasoning. 
Apparently, NLTK, which by the way is **string-based**, is preferred by many for its comprehensive documentation and educational resources. 

In addition, other notable libraries purely for NLP are :
- 𝐅𝐚𝐬𝐭𝐓𝐞𝐱𝐭: developed by Facebook AI, it enables users to learn text representations and classifiers with fast training speed and scalability using supervised and unsupervised learning algorithms.
- 𝐆𝐞𝐧𝐬𝐢𝐦: useful for unsupervised learning tasks such as document similarity analysis, topic modeling and word embedding techniques.

Last but not least on the list is 𝐇𝐮𝐠𝐠𝐢𝐧𝐠 𝐅𝐚𝐜𝐞🤗 and its 𝐓𝐫𝐚𝐧𝐬𝐟𝐨𝐫𝐦𝐞𝐫𝐬 library. It provides thousands of state-of-the-art pre-trained models for a variety of NLP tasks, including BERT, GPT, RoBERTa, and many others. 
The platform makes it easy to customize and train the models.

![Image](https://media.licdn.com/dms/image/D4E22AQFLlcaoz2A6Kg/feedshare-shrink_800/0/1711512337238?e=1715817600&v=beta&t=yfELOSkRXI3eWlcmX6LwT5pGZkUrqvmc96NYOUyeZzo)   

**Voir Référence:**  [NLP Tools](https://www.linkedin.com/posts/anyantudre_nlp-ai-llm-activity-7178654528462802944-vlWZ?utm_source=share&utm_medium=member_desktop).


## 4. Le pipeline classique en NLP

NLP pipeline refers to the sequence of steps involved in analyzing, understanding and transforming raw text data into a desired output.
There are 8 main stages (not exhaustive of course):

- 𝐃𝐚𝐭𝐚 𝐂𝐨𝐥𝐥𝐞𝐜𝐭𝐢𝐨𝐧: it's obvious - no data, no ML, no NLP. Data acquisition is the heart of any ML system and the ideal setting is having everything needed, the data labeled and annotated correctly. 
Some of the techniques people use to get data are web scraping, APIs, public datasets, data augmentation, synthetic data generation etc.

- 𝐓𝐞𝐱𝐭 𝐞𝐱𝐭𝐫𝐚𝐜𝐭𝐢𝐨𝐧 𝐚𝐧𝐝 𝐂𝐥𝐞𝐚𝐧𝐮𝐩: initially consists of extracting raw text from input data such as web pages (HTML) and scanned PDFs.
Cleanup, also called 𝐩𝐫𝐞𝐩𝐫𝐨𝐜𝐞𝐬𝐬𝐢𝐧𝐠, evolves removing irrelevant, non-textual information from the data and then prepare it for further analysis by applying fundamental transformations:
          o  Segmentation & tokenization
          o  Lowercasing & encoding
          o  Removing stopwords, punctuations, digits...
          o  Stemming and/or lemmatization

- 𝐅𝐞𝐚𝐭𝐮𝐫𝐞 𝐄𝐧𝐠𝐢𝐧𝐞𝐞𝐫𝐢𝐧𝐠: the process of transforming raw data into informative numerical features that are suitable for ML algorithms. The goal here is to represent text in a format that captures semantic meaning, contextual information, and relationships between words.     
Some techniques include:
          o One-Hot Encoding
          o Bag of Words (BoW) & TF-IDF
          o Word Embeddings

- 𝐌𝐨𝐝𝐞𝐥𝐢𝐧𝐠: we arrived at the favorite part of each ML practitioner: builing models.

- 𝐄𝐯𝐚𝐥𝐮𝐚𝐭𝐢𝐨𝐧: after taking some time to build, tune and finally find the “BEST” model for our task, we need to know how good it is or let's say, how it really performs – “Goodness”. 

- 𝐏𝐨𝐬𝐭-𝐦𝐨𝐝𝐞𝐥𝐢𝐧𝐠 𝐩𝐡𝐚𝐬𝐞𝐬: the final stage consists in deploying the model in a production environment (e.g., web service), monitor the system performance on a regular basis, and update it with new-coming data (if any).
Another thing to consider maybe 𝐦𝐨𝐝𝐞𝐥 𝐢𝐧𝐭𝐞𝐫𝐩𝐫𝐞𝐭𝐚𝐛𝐢𝐥𝐢𝐭𝐲 which, briefly, aims to understanding and explaining how a ML model makes predictions or decisions.

Note that this NLP pipeline may not always be linear since there are loops in between and it may depend on specific task at hand.

![Image]()  
Voir Référence: [🧩 𝐆𝐞𝐧𝐞𝐫𝐚𝐥 𝐍𝐋𝐏 𝐏𝐢𝐩𝐞𝐥𝐢𝐧𝐞.](https://www.linkedin.com/posts/anyantudre_nlp-ai-llm-activity-7179703891511382016-xm-A?utm_source=share&utm_medium=member_desktop)

## 5. 𝐖𝐡𝐲 𝐢𝐬 𝐢𝐭 𝐬𝐨 𝐜𝐡𝐚𝐥𝐥𝐞𝐧𝐠𝐢𝐧𝐠?
Computers interpret information differently from humans. 
We can easily understand a sentence meaning or determine how similar two sentences are. But unlike us, machines don’t understand characters or sentences. They can only deal with numbers.

The text needs to be processed in a way that enables the machine to learn from it.
And because language is extremely complex, we need to think carefully about how this processing must be done.  
 
- **Ambiguity & Context**
- **Creativity & Diversity**



## II. Bref rappel sur l'histoire des Réseaux de Neurones

### 1. Bref historique

![](https://miro.medium.com/v2/resize:fit:720/format:webp/0*eoUYQD-k28K5Cu3r.png)


## Le Perceptron

![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*30YDnisanIYRHpC-L2Br-g.png)

[Voir Article](https://anyantudre.medium.com/from-biological-to-artificial-neurons-theory-behind-perceptrons-d0ccc5bcf1eb)


## Simple Dense Layer

Imagine you're an high school teacher and after end-of-year evaluations you stored the grades of your students in a table like the following one:

![Image 2](visuals/1.Mathematics-&-Gradients-everywhere/2.png)

Each row is for students and each columns for a specific course taken.

About variables in this table:

|French         | English             |
| ------------- | ------------------- |
| Mathematiques | Mathematics         |
| Physique      | Physics             |
| Informatique  | Computer Science    |
| LV1           | Modern Language 1  |
| LV2           | Modern Language 2  |
| Biologie      | Biology             |
| Chimie        | Chemistry           |


Well, so basically the problematic is 
> **Question 1: How do you highlight features or let's say extract meaningful information from this table(data)?**

- An intuive solution that schools and teachers often use is **calculating the mean of all the grades** for each student. In other words, we sum up all the grades for each student and then divide by the total number of subjects (7 here). This operation simplifies the information since we have now at hand only one column showing ...
In this case we'll got something like that:
![Image 3](visuals/1.Mathematics-&-Gradients-everywhere/3.png)

- A more general solution to the previous one is **calculating a weighted sum of the grades** in order to extract specific features/tendences for each student.  
The **general formula** is the following one, where the w_j represent the weights and the x_i_j the j_th grade of the i_th student :    
<center><img src="visuals/1.Mathematics-&-Gradients-everywhere/3.1.png" alt="Image 3.1" height="200" width="400"></center> 


    - For example, if we want to know which students are very **strong only in Modern Languages**, we can take the weight vector as follows: `w = (0.0, 0.0, 0.0, 0.5, 0.5, 0.0, 0.0)`.  
It simply **calculates the average of the marks obtained in the two language subjects**!  
![Image 4](visuals/1.Mathematics-&-Gradients-everywhere/4.png)

    - A second illustration comes when we want to **compare students who are excellent in mathematics and those who are excellent in physics*. Taking a weight vector `w = (1.0, 0.0, − 1.0, 0.0, 0.0, 0.0, 0.0)`, we simply calculate **the difference between the two scores**: 
![Image 5](visuals/1.Mathematics-&-Gradients-everywhere/5.png)

    - Now let's say we want to know how each student performs in **scientific subjects**. Like in the first example we can simply compute **a weighted sum of the scientific subjects** with a weight vector given as `w = (0.2, 0.2, 0.2, 0.0, 0.0, 0.2, 0.2)`.
**The average performance in scientific subjects.**  
![Image 6](visuals/1.Mathematics-&-Gradients-everywhere/6.png)

Well you noticed that it's interesting to see in a more informative way how our students performs generally in all the subjects, and particularly in Modern Languages and in Scientific subjects... That's great, but too easy. Yes indeed, we need some more and specific information.


> **Question 2: How can we keep only the information that interests us?**


### Dense layer with bias, followed by ReLU (Rectified Linear Unit)

If the previous question is not yet clear to you, imagine from the third(last) illustration we only want to know exactly who are the students that are above the average to pass (10 in our case) in science subjects and discard the remaining ones (others that are below the passing average).  
A simple solution would be to subtract 10 from the weighted sum and keep only those students whose results are positive (above zero).

Here is an illustration:
![Image 7](visuals/1.Mathematics-&-Gradients-everywhere/7.png)

So basically, what is done here is substracting 10 to the result of the weighted sum of scientific subjects and using the ReLU function we test if the global result is greater than zero (0) then we keep it as it is but if it's negative we replace it by zero (0).  

In Deep Learning, b (value 10 here) is called **the bias term** and the function **y_i = max(0, s_i)** is the **Rectified Linear Unit called ReLU** for short.  
**Simply put, ReLU allows you to set unnecessary information to zero** (of course depending on the weightings chosen).

Let's apply same principles to Languages subjects and see which students performs well on both scientific and Languages:

![Image 8](visuals/1.Mathematics-&-Gradients-everywhere/8.png)  
You noticed we passed **from a 7 columns raw table to a 2 columns meaningful table** showing us exactly what we wanted to know i.e., the best students in Sciences and Languages. We can even go futher by repeating this process again and again with different weights and different subjects.
I think at this stage, you got the point: **this process is exactly what Dense layers in Neural Networks do.**

So to sum up, what Dense layers i.e., **several weighted sums with bias, followed by ReLU** do is:
- **Data dimension reduction** 
- **Feature extraction**
- **Information selection**


![](https://miro.medium.com/v2/resize:fit:720/format:webp/1*ub-ifcgdi9xgryqvo0_GRA.png)



## 4. Les CNN
Another fundamental building blocks in Neural Networks that allows to recognize patterns within data (typically images but not only) are **Convolutional layers**.


### Convolution 
Convolution is simply a mathematical operation used to process images or other multidimensional data. It involves **sliding a small matrix also called "kernel" or "filter" over the image**. This kernel is typically a square matrix with numbers. 
At each position, the kernel multiplies element-wise with the overlapping part of the image, and then adds up all the results to produce a single number. This process is repeated across the entire image and as the filter moves, it detects features such as edges, textures, or shapes at different positions.
Here is a simple illustration:
![Image 9](visuals/1.Mathematics-&-Gradients-everywhere/9.png)  

The mathematical formula is the follwing one
![Image 9.1](visuals/1.Mathematics-&-Gradients-everywhere/9.1.png)  

I'm sure you're asking yourself, what if we use a different kernel on the same image? 
Well, by applying multiple filters to an image, Convolutional layers can learn to detect various features at different scales and orientations.

For example, a kernel might detect vertical edges by responding strongly to transitions from dark to light or light to dark in a vertical direction. 
After convolution, the resulting image will typically have highlighted features that the kernel was designed to detect.

![Image 10](visuals/1.Mathematics-&-Gradients-everywhere/10.png)  



### Assembling building blocks: Neural network architecture


> **How does the Neural Network modify the image layer by layer?**
Well an image is worth thousand words:

![Image 15](visuals/1.Mathematics-&-Gradients-everywhere/15.png)  


### Summury

![Image 16](visuals/1.Mathematics-&-Gradients-everywhere/16.png)  

CNN learning: Optimization of [convolution filters], [bias] and [last layer matrices layers] so that they lead to the best possible predictions on a training set. 
- Filters highlight relevant properties in the image 
- Mixing different channels can create advanced representations of information 
- Using biases, ReLU functions can remove unnecessary information 
- Max-pooling selects the most relevant information from each image region



# II- Gradient Descent





# III. Le Pipeline de plus près

### 1. Text Preprocessing

#### Text Normalisation:
    - HTML tags
    - Stemming
    - Lemmatization
    - Accented Characters & Special Characters
    - Redundant Whitespaces
    - Stopwords


#### Text Tokenization:

Tokenizers are one of the core components of NLP pipeline. 𝐓𝐨𝐤𝐞𝐧𝐢𝐳𝐚𝐭𝐢𝐨𝐧 is the process of splitting raw text into smaller units called "tokens", which are often more linguistically meaningful. These tokens are easier to deal with and can be numerically encoded and given as input to NLP models.

There are three main tokenization algorithms:
- 𝐖𝐨𝐫𝐝-𝐛𝐚𝐬𝐞𝐝 tokenization: the most straightforward method, consisting in splitting text into words.
Example: "Let's do tokenization" --> ["Let's", "do", "tokenization"]

Pros:
  o Easy to implement. By considering whitespaces, using the good old Python 'split()' function, and you're done.
  o Often yields decent results and is useful for most NLP tasks as words are the basic units of meaning in language.
Cons:
  o Large “vocabularies”(total number of tokens in a corpus) problem due to punctuations, special characters or word variants. 
For instance, words like “run” and “running” may be identified as unrelated.
  o Similarly, how to deal with slang and abbreviations such as "lol", "tl;dr" or imagine for a second this kind of tokenizer used for a language like Chinese, which doesn't use spaces to separate words.

Well, let's go one level deeper.

- 𝐂𝐡𝐚𝐫𝐚𝐜𝐭𝐞𝐫-𝐛𝐚𝐬𝐞𝐝 tokenization: the goal here is to split the text into characters, rather than words.
Exple: "word" --> ["w", "o", "r", "d"]

Pros:
  o Much smaller vocabulary, and fewer out-of-vocabulary (unknown) tokens, since each word can be constructed from characters.
  o Seems useful for tasks like spelling correction and works well for languages where words are not clearly separated.

Cons:
  o Intuitively, it’s less meaningful: unlike words each character doesn’t mean a lot on its own.
  o We may end up with a very large amount of tokens. For a 5-word long sentence, you may need to process 30 tokens instead of 5 word-based tokens. It's computationally expensive.
  o Finally, it narrows down the number of NLP tasks. With long sequences of characters, wecan only use a certain types of neural network architecture.

Fortunetly, we can get the best of both worlds.

- 𝐒𝐮𝐛𝐰𝐨𝐫𝐝 tokenization: this algorithm rely on the principle that frequently used words should not be decomposed, but rare words should. 
So basically, it splits some words into smaller units, such as prefixes, suffixes, or roots.These subwords end up providing a lot of semantic meaning while being space-saving.  
Exple:“tokenization” --> [“token”, “ization”]

Pros:
  o Good coverage with small vocabulary.
  o Handles out-of-vocabulary words well.
  
Cons:
  o Requires pre-trained models or algorithms to learn subword units, which can be resource-intensive.


![](https://media.licdn.com/dms/image/D4E22AQH3IRHf4ZguzQ/feedshare-shrink_800/0/1712046668667?e=1715817600&v=beta&t=0l7-ghxyml9uNQL5XnXRaTIrJR9CXehMuq1QrvVV9VQ)


And many more!
Unsurprisingly, there are many more techniques out there. To name a few:
- Byte-level 𝐁𝐏𝐄, as used in GPT-2.
- 𝐖𝐨𝐫𝐝𝐏𝐢𝐞𝐜𝐞, as used in BERT.
- 𝐒𝐞𝐧𝐭𝐞𝐧𝐜𝐞𝐏𝐢𝐞𝐜𝐞 or Unigram, as used in several multilingual models.


    
    2. TF-IDF
