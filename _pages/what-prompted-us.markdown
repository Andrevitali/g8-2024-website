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
#### A description of our dataset and what promped us

From the late 1990s to the early 2000s, the emergence of successful social networks and review platforms marked the beginning of a new way of communicating, informing, and marketing.

<br>
The restaurant industry is also greatly marked by this phenomenon. We interviewed food critic **Carlo Passera**, editor-in-chief of [Identità Golose](https://www.identitagolose.it/)., who in this regard says:
<br>
 “The phenomenon of online reviews is part of a larger phenomenon that  can be called **disintermediation**. This phenomenon touches all of contemporary society. With e-commerce the intermediary skips the middleman and the customer is directly in contact with the producer.”
<br>
How has this new market dynamic affected the restaurant industry?
<br>
“Communication has changed a lot, now the trend is to have signatures, that are representative dishes that can describe the **brand** of the restaurant.
On social media, a very direct narrative around a specific type of dish works a lot, more so than a generalist restaurant that can tell its story simply as a restaurant.” 
<br>
The idea of CraveIT is to develop a platform that goes to recommend the best restaurants where to find a particular typical Italian dish. Do you think it makes sense to consider only feedback from Italian users?
<br>
“It tends to, for an almost anthropological question. For example, North American customers demand sweeter flavors. the Far East has a different relationship with salt than ours. There are really characteristics that develop in one's local gastronomic tradition, which make the perception of tastes also due to the area where the person comes from. So let's say that for Italian cuisine at least I would tend to trust a European user more, or even better from the Mediterranean area.”
<br>
In this new context, what role do industry experts play? We decided to use expert judgment for the construction of the CraveIT ranking.
<br>
“Too much information sometimes equals no information. Before, users referred to food guides because they did not know who to ask to figure out which restaurant to go to. Now it's the opposite, guides serve to discern, with some authority, among the too much information available online.”

<iframe src="{{site.baseurl}}/assets/charts/mappa_ristoranti.html" width="{{include.width  | default: '100%'  }}" height="{{include.height   | default: '400px'  }}" ></iframe>

<br>

Descrizione veloce del dataset + introduzione al fatto che qui presentiamo i nostri dati e perché CraveIT è importante: dati descrivono fenomeni culturali

<br>


### Number of reviews by month
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Total.json" style="width:100%"></vegachart>

<br>

Andamento temporale reviews 
calo covid
ancora non si è ripreso
stagionalità  (minimi mesi invernali, massimo estivi)
<br>


### Reviews by language

<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_N_ItalianvsNonItalian.json" style="width:100%"></vegachart>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_NForeignReviewsbyLanguage.json" style="width:100%"></vegachart>

<br>
La maggior parte italiani, distribuzione di non italiani

<br>

<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Italian_NonItalian.json" style="width:100%"></vegachart>

<br>
andamento recensioni italiane e non ma vediamo il grafico dopo

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
Dal grafico risulta evidente che la cultura, e dunque il gusto, influenza l'entusiasmo con cui vengono recensiti i vari ristoranti.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_Ratings_byLanguage.json" style="width:100%"></vegachart>
<br>
Vediamo che i dati sono coerenti con ciò che ci aspettiamo, vedendo che persone che provengono da paesi più ricchi frequentano ristornati più cari e viceversa
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_Price_byLanguage.json" style="width: 100%"></vegachart>
<br>
Inoltre, a conferma di quanto osservato i ristoranti più economici sono anche quelli con recensioni più positive. Una possibile spiegazione è il fatto che questi ristoranti sono frequentati da persone che vengono da paesi culturalmente simili al nostro.
Ovviamente, bisogna anche osservare che chi meno spende meno pretende.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_ReviewbyStars.json" style="width: 100%"></vegachart>


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
