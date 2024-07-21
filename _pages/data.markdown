---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title:  "data"
subtitle: "File di prova"
show_sidetoc: true
# header_type: hero #base, post, hero,image, splash
# header_img: assets/images/altair-gallery.png
# header_title: "Our Data"
vega: true
---


# **Our Pipeline**
### Data gathering and pre-processing

CraveIT is based on the analysis of Rome's restaurants reviews, aggregated from different sources. For our input data, we selected around 2.500 restaurants, on the grounds of their overall quality and popularity; moreover, all the gathered reviews were written in the past 5 years. To enrich the reviews’ context, and be later used in the ranking algorithm, we also collected several pieces of accessory information both about the review itself, and about the restaurant it was written for.
<br>
The pool of raw data has then entered a fine-grained pre-processing pipeline. All the reviews, and their contextual attributes, have been each checked for formal and semantic consistency. We dropped duplicate reviews and, where it was sensible to do so, replaced missing and null values according to the variable’s overall distributions; where it wasn’t, we discarded faulty entries.
<br>
As mentioned earlier, an important feature of our dataset is the diversity of its sources. After checking for consistency across these sources, each review, no matter where it was coming from, has been augmented with aggregate pieces of information coming from all the other sources as well, thus creating a rich, and so far unavailable, dataset.
<br>
The restaurants, and their respective reviews, have then been filtered to exclude non-italian types of cuisines; furthermore, we employed a pre-trained multi-class classifier to infer the review’s language, and restricted our data to the Italian ones. 

<hr>

### ElasticSearch
After the cleaning and filtering process, we were left with approximately 80% of the initial reviews; we then had to pinpoint the reviews that mentioned at least one of the 15 traditional Rome dishes that we selected for CraveIT’s proof of concept.
<br>
For this purpose, we chose to employ ElasticSearch. We set up a batching system to split up our corpus into more manageable bundles, indexed all the reviews’ bodies, together with their title if present, and paired them with a unique identifier.
After the indexing process, we built our queries; for each of our dishes, we asked the search engine to look for matches in either the body or the title of the reviews. These queries used two important ElasticSearch’s features: fuzziness and highlight. Fuzziness  allowed us to retrieve most of the reasonable variations of the search terms, especially plurals and typos; and there sure were many:

<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            display: flex;
            flex-wrap: wrap;
        }
        .column {
            flex: 50%;
            padding: 10px;
        }
        pre {
            background: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            white-space: pre-wrap;
            word-wrap: break-word;
        }
        .soft-pink {
            color: #FF69B4; /* Soft pink color */
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="column">
            <pre><code class="soft-pink">{
    "amatriciana": 15034,
    "amatriciano": 69,
    "l'amatriciana": 271,
    "l’amatriciana": 162,
    "matriciana": 209,
    "amatriciane": 372,
    "amtatriciana": 2,
    "amatricia": 1,
    "amaticiana": 4,
    "amatricina": 5,
    "amitriciana": 11,
    "amatriciata": 2,
    "matriciano": 13,
    "amatrciana": 5,
    "matriciane": 5,
    "amatricciana": 15,
    "amatritiana": 1,
    "amatrisciana": 2,
    "amatriciani": 22,
    "lamatriciana": 7,
    "amatraciana": 5,
    "amatriciama": 3,
    "a’matriciana": 2,
    "amayriciana": 1,
    "ammatriciana": 10,
    "amatriciqna": 1,
    "amarticiana": 3,
    "1amatriciana": 1,
    "amatoriciana": 2,
    "amattriciana": 1,
    "a'matriciana": 1,
}</code></pre>
        </div>
        <div class="column">
            <pre><code class="soft-pink">{
    "amantriciana": 2,
    "amatriziana": 1,
    "amatricisna": 1,
    "amatticiana": 2,
    "amatricaina": 1,
    "umatriciana": 1,
    "amartriciana": 2,
    "amatriviana": 1,
    "amatrigiana": 1,
    "amatruciana": 2,
    "amateiciana": 1,
    "amamtriciana": 1,
    "1matriciana": 1,
    "amatriciara": 1,
    "anatriciana": 3,
    "amatrichana": 1,
    "amariciana": 2,
    "amatritciana": 1,
    "ametriciana": 1,
    "amatrichiana": 1,
    "amatrriciana": 1,
    "amatricianna": 1,
    "amatreciana": 2,
    "amatriaciana": 1,
    "amatricinana": 2,
    "amstriciana": 1,
    "amatrician": 1,
    "amtriciana": 1,
    "amatricianan": 1,
    "maticiana": 1,
    "amatriciaba": 1
}</code></pre>
        </div>
    </div>
</body>
</html>



 


<br>
The fuzziness parameter had of course to be tailored on the specific dish, depending on the length of the search term and on the presence of similar,  meaningful but semantically different, words in the italian vocabulary (e.g."trippa", “troppa”, “troppe”).  We also built custom solutions for the phrase dishes (“cacio e pepe”, “carciofi alla giudia”, “carciofi alla romana”); the queries retrieved fuzzy variations of the single words, provided that they were preceded or followed by the appropriate terms (e.g. it retrieved hits for “giuria” only if preceded by “carciofi alla”).
<br>
The highlighting function tells ElasticSearch to mark the matching term in the document with a <em></em> tag; this feature was particularly helpful to check for unintended and unforeseen matches. Moreover, we set it up so that ES would not return the entire matching document, but only a snippet that included the sentence where it found the highlighted term, and some bordering text. Finally, we passes its results into nltk’s sentence tokenizer, in order to retrieve only the sentence that was actually mentioning our specified dish. This was necessary for moving to the next step, sentiment analysis.
<br>

<hr>

### Sentiment Analysis
At the end of the ElasticSearch process, we were left with just short of 20% of the initial reviews, each of which mentions at least one of our selected dishes; as expected, some dishes were more popular than others: for instance “carbonara” had four times the hits of“amatriciana”.
<br>
As mentioned, CraveIT is dish-specific, so we wanted the models to associate a sentiment score specifically associated with the dish we were evaluating. 
We tested BERT for this task, we used a multilingual model pre-trained on product reviews, that would return a score from 0 to 5, where 0 meant a negative sentiment, 5 a positive one, and 3 a neutral one. Since we could not direct BERT into giving us the sentiment associated with a particular item (our selected dish), we couldn’t feed it the entire review, as users often mention multiple dishes, and express opinions on the restaurant's general atmosphere, its value and service. Therefore, we had to feed it the already tokenized sentences returned by ES. Evaluating the results on a sample of reviews, we found that BERT’s accuracy was surprisingly high, and that the model was able to pick up on somewhat subtle differences. For instance:
<br>

<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
        }
        .container {
            padding: 10px;
        }
        pre {
            background: #f4f4f4;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            white-space: pre-wrap;
            word-wrap: break-word;
            color: #FF69B4; /* Soft pink color */
        }
    </style>
</head>
<body>
    <div class="container">
        <pre>"Ho ordinato una carbonara pensando di mangiare quella migliore di Roma, invece hanno usato la panna!"
Tensor(1)</pre>
    </div>
</body>
</html>


BERT didn’t get fooled by the mention of “quella migliore di Roma”, and correctly assigned a low sentiment score to the review. However, BERT was of course failing on reviews that were mentioning multiple dishes in the highlighted sentence, conflating opinions; more importantly, it could not succeed on reviews that were mentioning our target dish in a sentence, but expressing the related sentiment in another, as it was only reading parts of them.

<hr>

### Ranking Algorithm
After cleaning the results provided by the  sentiment analysis, we moved to defining our ranking function. The function uses 3 parameters; as opposed to traditional apps, all of them are dish-specific. For each restaurant, we calculated:
<br>

1)   the mean sentiment associated with the dish.
2)   the popularity of the restaurant with respect to that dish
3)   the recency of the reviews
<br>
Parameters 2 and 3 ensure that our ranking is reliable: the sentiment it associates to that dish for that particular restaurant is weighed by the number of reviews on which we’re grounding our score, and on how recent they are as, of course, we wouldn’t want to recommend a restaurant on the basis of just a handful of reviews, or on reviews that were written years ago and might no longer reflect the quality of the food served.
<br>
Finally, we included the expert’s opinions. We combined all of these parameters with a normalized weighted sum that returned, for each restaurant-dish pair, a float between 0 and 10: our CraveIT score.

<hr>


### Validation
Simply sorting the restaurants by descending CraveIT score, we got our top 10s back.
<br>
CraveIT does something that no other app does: a restaurant ranking that is specifically based on the quality of a particular dish; this, of course, is a result we cherish. On the other hand it poses a problem: it’s an unsupervised process for the validation of which we have no obvious label. We don’t know what is the correct result that our ranking is supposed to return.
<br>
We therefore picked the carbonara, which is by far the most popular of the dishes we selected, and looked for newspapers and food blogs articles that had compiled a specific list of “The best places to eat a carbonara in Rome”.
<br>
Il Messaggero:
<br>
<https://www.ilmessaggero.it/ristoranti/carbonara_le_dieci_migliori_di_roma_da_roscioli_pipero_al_rex-186966.html>
<br>
la Repubblica:
<br>
<https://roma.repubblica.it/cronaca/2021/04/06/news/carbonara_day_mappa_piu_buone_roma_secondo_lettori-295264786/ >
<br>
SkyTG24:
<br>
<https://tg24.sky.it/lifestyle/2024/04/06/carbonara-migliori-ristoranti-italia >
<br>
Puntarella Rossa:
<br>
<https://www.puntarellarossa.it/2016/04/18/la-migliore-carbonara-di-roma/#:~:text=TRASTEVERE-,Eggs,prime%2C%20ma%20anche%20le%20varianti.>
<br>
Gambero Rosso:
<br>
https://www.gamberorosso.it/notizie/classifiche/la-migliore-carbonara-di-roma-la-classifica-dopo-21-test-in-4-giorni/

<br>

Three restaurants consistently appear in the top 5s of the articles, Roscioli, Luciano and Eggs: all of them are in CraveIT’s top 5s.
As for the other restaurants appearing in CraveIT’s carbonara top 10s, they are all extremely popular places, variously mentioned on social media and YouTube videos (e.g. La Fraschetta, Tonnarello, Osteria da Fortunata).
<br>
The online articles are not as detailed about other, less popular, dishes; however, the results are definitely promising: CraveIT’s results are extremely diverse as they vary deeply based on the selected dish and they seem overall more than sensible: CraveIT top results for cacio e pepe are Felice a Testaccio and Flavio al Velavevodetto, both places variously mentioned in newspapers and food blog articles specifically addressing that particular dish; the same goes for saltimbocca (Armando al Pantheon), coda alla vaccinara (SantoPalato, Checchino dal 1887), trippa (Osteria La Sol Fa), abbacchio (Matricianella), supplì (Supplizio, 180g Pizzeria Romana, Trapizzino Trilussa), pajata (Trattoria Pennestri, Sora Lella), gricia (Osteria Bonelli, da Enzo al 29), baccalà (Dar Filettaro, Grappolo d’oro), puntarelle (da Gino al Parlamento); a peculiarly encouraging result is that the top 2 places among CraveIT’s “carciofi alla giudia” results are restaurants located at the Jewish ghetto, an area where no restaurants recommended for other dishes appear.
<br>
What’s more important, and somewhat surprising, about these results is that virtually none of the above-mentioned restaurants are highly rated on the generic online sources, proving that CraveIT’s sentiment analysis and ranking algorithm are the ones doing most of the work. 
