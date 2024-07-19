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

Altair è una libreria di visualizzazione dei dati per Python, basata su Vega e Vega-Lite. Ciò significa che Altair genera specifiche Vega-Lite, che a loro volta vengono convertite in specifiche Vega e quindi in grafici visualizzabili in un browser web. Per incorporare un grafico Altair in una pagina web, è necessario convertire la specifica Vega-Lite in un oggetto JSON e salvarlo in un file `.json`.


### Number of reviews by month
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Total.json" style="width:100%"></vegachart>

Andamento temporale reviews 
calo covid
ancora non si è ripreso
stagionalità  (minimi mesi invernali, massimo estivi)

### Reviews by language
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_N_ItalianvsNonItalian.json" style="width:100%"></vegachart>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_NForeignReviewsbyLanguage.json" style="width:100%"></vegachart>
La maggior parte italiani, distribuzione di non italiani

<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Italian_NonItalian.json" style="width:100%"></vegachart>
andamento recensioni italiane e non ma vediamo il grafico dopo
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_byItalian_NonItalian_Normalized.json" style="width:100%"></vegachart>
normalizzando si vede un andamento prima covid regolare: mesi invernali più italiani fino ad un 50% nei mesi estivi. L'adamento è sperturbato dal covid, fino al 2022. Dal 2022 l'andamento si riprende completamente. Non tutte le lingue seguono lo stesso andamento.

L'informazione interessante sono le recensioni in russo: è evidente che dal covid a causa della guerra
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_Russian.json" style="width:100%"></vegachart>

### Reviews by type
L'andamento delle recensioni varia anche per tipologia, andamento generale:
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth&Party.json" style="width:100%"></vegachart>

è interessante notare che le reviews per business hanno subito un forte decremento durante il covid ma non sono più tornate ai livelli precedenti.
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
