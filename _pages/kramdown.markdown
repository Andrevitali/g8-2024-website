---


layout: default
title:  "How it works"
subtitle: "File di prova"
show_sidetoc: true
# header_type: hero #base, post, hero,image, splash
# header_img: assets/images/altair-gallery.png
# header_title: "Our Data"
vega: true
---


# **UNDER THE HOOD**

<br>

Currently, CraveIT is a **proof-of-concept**: it focuses on the city of Rome, and on a selection of 15 traditional dishes. Obviously it could, and we hope soon will, be extended to any town and any list of dishes.

CraveIT’s PoC is based on the analysis of over **1.000.000** reviews, gathered from the most important informative hubs of the food industry; this pool of reviews spans around **2.500** of the best (top 20%) and more visited (top 10%) restaurants of Rome. For each of these restaurants, we collected all the reviews written in the past **5 years**, together with a rich set of **contextual information** regarding both the review (title, score, date, <i>etc.</i>) and the restaurant itself (price range, location, contact info, opening hours, features, <i>etc.</i>).

The pool of raw data has then entered a fine-grained **pre-processing pipeline**. All the reviews, and their contextual attributes, have been each checked for formal and semantic consistency; furthermore, duplicates, missing and null values have been handled through solutions tailored on the importance of the variable.
The different sources have then been merged: each review, no matter where it was collected from, has been augmented with aggregate pieces of information coming from all the other sources as well, thus creating a **rich, and so far unavailable, dataset**.
Finally, the results have been **filtered** to include only reviews written in Italian, and about Italian restaurants.

We then needed an efficient and scalable mechanism to **locate the texts mentioning at least one of our 15 target dishes**. The reviews’ bodies, together with their respective titles where present, have hence been indexed in batches. We then built the queries so that the search engine would also retrieve misspellings and morphological variants of the target terms, and devised custom solutions for the phrase ones (<i>e.g.</i> “cacio e pepe”). 

Having identified, for each of our target dishes, the set of all and only reviews that were mentioning that dish, we were ready to move to **sentiment analysis**. This phase was particularly crucial: the novelty and peculiarity of CraveIT lies in the fact that its analysis, and hence the recommendations it provides, are **dish-specific**; users, however, frequently mention multiple dishes in the same review, and express opinions on the restaurant's general features, such as its atmosphere, value and service. For our sentiment analysis we thus employed **different state-of-the-art models**, variously tailoring the format of the input data. For each review, and for each dish, the models were fed either the whole body or chunks of it, and outputted a sentiment value between 1 (very negative) and 5 (very positive).

The **results were great**, and far exceeded expectations: even if unprompted to do so, the models would automatically recognize reviews that were not including a specific sentiment for the dish at hand (as, for instance, the users only mentioned that the dish was on the menu, but hadn’t tried it themselves); more importantly, they picked up on **subtle nuances of meaning and distant dependencies**. This becomes particularly clear if we merge together the results the models got, in different iterations, on reviews that were mentioning multiple dishes in our selection:

<br>
<center>
<img  width="800px" style="margin: 0px 0px 0px 0px;" src="assets/images/Under_The_Hood_02.png">
</center>
<br>
<br>

The models were able to **pinpoint the sentiment associated with the target dish**, disregarding what else was said about other dishes, the service, or the restaurant in general. Notice that, crucially, the **overall stars** assigned by the users, on which traditional apps base their rankings, **lack the necessary granularity** in order to pick up on all the opinions expressed in the text; this, we argue, means that current platforms lose a lot of prime information along the way. The dish-specific sentiment will, on the other hand, give CraveIT a much more precise base for the ranking algorithm.

CraveIT’s ranking algorithm uses **3 main parameters**, all of which are **dish-specific**:

- **mean sentiment**: for every restaurant, for every dish, the mean of the sentiment scores associated with each review, as returned by the models; the various models' results have also been weighted on the basis of their accuracy and the breadth of the context they were fed;
- **popularity**: the ratio of the reviews that were mentioning that specific dish in that restaurant to the total of the reviews that were mentioning that specific dish.
- **freshness**: the ratio of the reviews mentioning that dish in that restaurant that were written in the past two years, to the total of reviews mentioning that dish in that restaurant.

Popularity and freshness ensure that CraveIT’s **ranking is reliable**: the sentiment it associates to that dish for that particular restaurant is weighed by number of reviews on which the score is grounded, and by how recent they are as, of course, we wouldn’t want to recommend a restaurant on the basis of just a handful of reviews, or on reviews that were written years ago and might no longer reflect the quality of the food served. Finally, we incorporated the **expert’s opinions** by adding a flat score for every guide (Michelin, Gambero Rosso, Identià Golose) the restaurant appears in. 

We aggregated all of these parameters with a normalized weighted sum that returned, for each restaurant-dish pair, a number between 0 and 10: our **CraveIT score**.

<br>