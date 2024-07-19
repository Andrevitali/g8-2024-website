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


# **Our data**
#### A description of our dataset

<iframe src="{{site.baseurl}}/assets/charts/mappa_ristoranti.html" width="{{include.width  | default: '100%'  }}" height="{{include.height   | default: '400px'  }}" ></iframe>

<hr>

Descrizione veloce del dataset + introduzione al fatto che qui presentiamo i nostri dati e perché CraveIT è importante: dati descrivono fenomeni culturali

<hr>


### Number of reviews by month
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Total.json" style="width:100%"></vegachart>

<hr>

Andamento temporale reviews 
calo covid
ancora non si è ripreso
stagionalità  (minimi mesi invernali, massimo estivi)
<hr>


### Reviews by language

<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_N_ItalianvsNonItalian.json" style="width:100%"></vegachart>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_NForeignReviewsbyLanguage.json" style="width:100%"></vegachart>

<hr>
La maggior parte italiani, distribuzione di non italiani

<hr>

<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Italian_NonItalian.json" style="width:100%"></vegachart>

<hr>
andamento recensioni italiane e non ma vediamo il grafico dopo

<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_byItalian_NonItalian_Normalized.json" style="width:100%"></vegachart>

<hr>
normalizzando si vede un andamento prima covid regolare: mesi invernali più italiani fino ad un 50% nei mesi estivi. L'adamento è sperturbato dal covid, fino al 2022. Dal 2022 l'andamento si riprende completamente. Non tutte le lingue seguono lo stesso andamento.
<hr>
L'informazione interessante sono le recensioni in russo: è evidente che dal covid a causa della guerra
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_Russian.json" style="width:100%"></vegachart>

<hr>

Partendo da questi dati abbiamo deciso di considerare solo le recensioni in italiano, anche sotto consiglio di NOME,critico gastronomico.
<hr>
Dal grafico risulta evidente che la cultura, e dunque il gusto, influenza l'entusiasmo con cui vengono recensiti i vari ristoranti.
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1407Bar_Ratings_byLanguage.json" style="width:100%"></vegachart>
<hr>
Vediamo che i dati sono coerenti con ciò che ci aspettiamo, vedendo che persone che provengono da paesi più ricchi frequentano ristornati più cari e viceversa
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/PriceByLanguage.json" style="width: 100%"></vegachart>
<hr>
Inoltre, a conferma di quanto osservato i ristoranti più economici sono anche quelli con recensioni più positive. Una possibile spiegazione è il fatto che questi ristoranti sono frequentati da persone che vengono da paesi culturalmente simili al nostro.
Ovviamente, bisogna anche osservare che chi meno spende meno pretende.
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_ReviewbyStars.json" style="width: 100%"></vegachart>


### Reviews by type
L'andamento delle recensioni varia anche per tipologia, andamento generale:
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth&Party.json" style="width:100%"></vegachart>
<hr>

è interessante notare che le reviews per business hanno subito un forte decremento durante il covid ma non sono più tornate ai livelli precedenti.
<hr>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth_Business.json" style="width:100%"></vegachart>



<br>
### Esempio di inserimento di un chart realizzato con Altair 13 Luglio 
<hr>

<vegachart schema-url="{{site.baseurl}}/assets/charts/PriceByLanguage.json" style="width: 100%"></vegachart>

<hr>
- Il grafico è stato salvato come file `chart_responsive.json` e inserito nella cartella `assets/charts`.
- Se provassimo a visualizzare il grafico in una pagina web senza specificare la proprietà `width='container'`, il grafico non sarebbe responsive e verrebbe visualizzato con una larghezza fissa.
- Se porvassimo a visualizzare il grafico in un notebook Jupyter, il grafico non sarebbe visibile in quanto la proprietà `width='container'` non è supportata in questo ambiente. In tal caso, è possibile specificare una larghezza fissa in pixel e cambiare la proprietà width solo in fase di esportazione. 





<br>
### Geospatial Insights 
<hr>

{% include map-selector.html dataset="maps-selector" %}
