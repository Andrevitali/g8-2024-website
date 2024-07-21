---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title:  "Why it matters"
subtitle: "Our data and what promped us"
show_sidetoc: true
# header_type: hero #base, post, hero,image, splash
# header_img: assets/images/altair-gallery.png
# header_title: "Our Data"
vega: true
---


# **Why it matters**
#### Our data and the reasons behind our project

Between the late 1990s and the early 2000s, the emergence of successful social networks and review platforms marked the beginning of a new era in communication, information sharing, and marketing.

<br>
The restaurant industry has been no exception and has been hugely impacted by this phenomenon as well. 
To gain more insights on this, we have interviewed food critic **Carlo Passera**, editor-in-chief of [Identità Golose](https://www.identitagolose.it/), who observed:
<div style="background-color: #f9f9f9; padding: 10px; margin: 10px 0;">
    “The phenomenon of online reviews is part of a larger trend known as <strong>disintermediation</strong>. This trend seems to affect all aspects of contemporary society. In e-commerce, for instance, disintermediation cuts out the middleman and allows customers to communicate directly with producers.”
</div>
<br>
<i>How have these new dynamics affected the restaurant industry?</i> 
<br>
<div style="background-color: #f9f9f9; padding: 10px; margin: 10px 0;">
“Communication has changed massively. Now the trend is to have signature dishes that are representative of a restaurant and can embody its **brand**. These unique dishes become central to the restaurant's identity, making it easier to stand out in a crowded market.
Using the visual and the storytelling affordances of social media to create a compelling narratives around specific dishes can do wonders to generate positive buzz around a restaurant and therefore attract attention from customers. Something that non-specialty restaurants would struggle to match."
</div>
<br>
<br>
<i>Since the idea behind CraveIT is to develop a platform that recommends the best restaurants where a specific Italian dish can be eaten, do you believe it makes sense to consider only reviews written by Italian users?</i>
<br>
<div style="background-color: #f9f9f9; padding: 10px; margin: 10px 0;">
“I would say so, for cultural and anthropological reasons. For instance, North American customers tend to demand sweeter flavors, whereas those from the Far East have a significantly different relationship with salt than us. I think that there are factors rooted in one's national gastronomic tradition that influence taste perception based on the person's region of origin. Therefore, for Italian cuisine, I would tend to trust a European user more, or even better, someone from the Mediterranean area.”
</div>
<br>
<br>
<i>In the current restaurant environment, what is the role played by industry experts? Do you think including experts' opinions in CraveIT's ranking is a good idea?</i>
<br>
<div style="background-color: #f9f9f9; padding: 10px; margin: 10px 0;">
“In the past, customers used to depend on food guides as the only way to decide on which restaurant to go to. Nowadays, we seem to have the opposite issue: customers have too much information, which at times it's like having no information. Since customers might find it difficult to negotiate the overwhelmingly vast amount of online information at their disposal, guides can serve to pinpoint the best options with some authority. Therefore, I reckon that including experts' opinion in CraveIT's score would make its ranking more robust and reliable”
</div>

<hr>

## Our data
In order to develop CraveIT we focus our interest on Rome and gather the information about traditional roman restaurants. In the map below it's possibile to explore all the restaurants we analyzed.
 <br>
<iframe src="{{site.baseurl}}/assets/charts/mappa_ristoranti.html" width="{{include.width  | default: '100%'  }}" height="{{include.height   | default: '400px'  }}" ></iframe>

<br>


### Number of reviews by month
To make the results reliable, we decided to consider only relatively recent information; in fact, the reviews analyzed start from 2019.
As noted, the data perfectly describe the covid phenomenon, and the various closures and reopenings had in Italy during 2020 and 2021. 
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Total.json" style="width:100%"></vegachart>
<br>
From what has been analyzed, the number of reviews has not yet returned to the pre-covid periods, but the seasonality of the time series is evident: the highest peak periods are in summer, the lowest peak periods in winter. It must be remembered that Rome is a tourist city, so it is logical to expect such behavior.
<br>

### Reviews by language
As mentioned before our aim was to discrover the best restaurant for a particular italian dish, so we chose to focus on italin reviews only, constituting more than 50% of the total reviews.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_N_ItalianvsNonItalian.json" style="width:100%"></vegachart>
<br>
In fact, among the non-italian reviews there are a lot of different languages,therefore also different cultures. 
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_NForeignReviewsbyLanguage.json" style="width:100%"></vegachart>

<br>
It makes sense to expect not only different taste, associated with different cultures, but also different behavior.
In particular, we can assume that people from wealthier countries frequent more expensive locales. Conversely, countries with lower average incomes will frequent cheaper restaurants.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_Ratings_byLanguage.json" style="width:100%"></vegachart>
<br>
From the chart above we can observe how people from different cultures react to italian cusine. In addition, confirming what we expect it seems that people from wealthier countries prefer restaurants with a higher price range.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_Price_byLanguage.json" style="width: 100%"></vegachart>
<br>
Finally, restaurants with lower price ranges receive higher ratings than more expensive restaurants. We can infer from this that those who are willing to spend more will be more critical , we might also assume that positive reviews come from people of similar culture to those in Italy.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_ReviewbyStars.json" style="width: 100%"></vegachart>

Going back to analyze the time trend of reviews, we can observe again how tourism in the city of Rome changed before and after the covid. This information can also be used as a validation of the reliability of the data considered.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Italian_NonItalian.json" style="width:100%"></vegachart>
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_byItalian_NonItalian_Normalized.json" style="width:100%"></vegachart>

<br>
normalizzando si vede un andamento prima covid regolare: mesi invernali più italiani fino ad un 50% nei mesi estivi. L'adamento è sperturbato dal covid, fino al 2022. Dal 2022 l'andamento si riprende completamente. Non tutte le lingue seguono lo stesso andamento.
<br>
L'informazione interessante sono le recensioni in russo: è evidente che dal covid a causa della guerra
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_Russian.json" style="width:100%"></vegachart>

<br>

Partendo da questi dati abbiamo deciso di considerare solo le recensioni in italiano, anche sotto consiglio di NOME,critico gastronomico.
<br>



### Reviews by type
L'andamento delle recensioni varia anche per tipologia, andamento generale:
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth&Party.json" style="width:100%"></vegachart>
<br>

è interessante notare che le reviews per business hanno subito un forte decremento durante il covid ma non sono più tornate ai livelli precedenti.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth_Business.json" style="width:100%"></vegachart>



<br>
### Esempio di inserimento di un chart realizzato con Altair 13 Luglio 
<br>

<vegachart schema-url="{{site.baseurl}}/assets/charts/PriceByLanguage.json" style="width: 100%"></vegachart>

<br>
- Il grafico è stato salvato come file `chart_responsive.json` e inserito nella cartella `assets/charts`.
- Se provassimo a visualizzare il grafico in una pagina web senza specificare la proprietà `width='container'`, il grafico non sarebbe responsive e verrebbe visualizzato con una larghezza fissa.
- Se porvassimo a visualizzare il grafico in un notebook Jupyter, il grafico non sarebbe visibile in quanto la proprietà `width='container'` non è supportata in questo ambiente. In tal caso, è possibile specificare una larghezza fissa in pixel e cambiare la proprietà width solo in fase di esportazione. 





<br>
### Geospatial Insights 
<br>

{% include map-selector.html dataset="maps-selector" %}
