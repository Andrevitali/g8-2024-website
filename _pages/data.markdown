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
# vega: true
---


# **Our data**
#### A description of our dataset

Altair è una libreria di visualizzazione dei dati per Python, basata su Vega e Vega-Lite. Ciò significa che Altair genera specifiche Vega-Lite, che a loro volta vengono convertite in specifiche Vega e quindi in grafici visualizzabili in un browser web. Per incorporare un grafico Altair in una pagina web, è necessario convertire la specifica Vega-Lite in un oggetto JSON e salvarlo in un file `.json`.

La procedura in `altair` per salvare la specifica Vega-Lite in un file `.json` è la seguente:

Preso un `chart` di `altair` qualsiasi:
```python
# Esempio di dati
data = pd.DataFrame({
    'a': ['A', 'B', 'C', 'D', 'E'],
    'b': [28, 55, 43, 91, 81]
})
```
Nel caso in cui si voglia rendere il grafico responsive, al momento del salvataggio del file `.json` è possibile specificare la proprietà `width='container'`.
```python
# Creazione del grafico
chart = alt.Chart(data).mark_bar().encode(
    x='a:N',
    y='b:Q'
).properties(
    width='container',
    height=300 
)

# Salvataggio del grafico come file JSON
chart_json = chart.to_json()
with open('chart.json', 'w') as f:
    f.write(chart_json)
```
> [Link al Notebook Colab con l'esempio qui sopra](https://colab.research.google.com/drive/1ySTEzV2se1buHZ7X5p2fX5RlDUXyAfaX?usp=sharing)

Il file `chart.json` può essere poi utilizzato in una pagina web per visualizzare il grafico. Per fare ciò, è possibile utilizzare il tag `vegachart` di Jekyll, specificando il percorso del file `.json` come valore dell'attributo `schema-url`.

```html
<vegachart schema-url="{{site.baseurl}}/assets/charts/chart_responsive.json" style="width: 100%"></vegachart>
```
Questo tema è stato personalizzato per accogliere grafici vega senza grosse complicazioni: se nella pagina in cui si vuole visualizzare il grafico nel front matter è specificato `vega: true`, il tag `vegachart` verrà interpretato e il grafico verrà visualizzato correttamente.
`vega: true` è una variabile che indica di caricare il plugin Vega nella pagina.
In questo modo, il grafico verrà visualizzato in modo responsive, adattandosi alla larghezza del contenitore in cui è inserito.

<br>
### Esempio di inserimento di un chart realizzato con Altair 
<hr>
<br>
### Esempio di inserimento di un chart realizzato con Altair 13 Luglio 
<hr>

<vegachart schema-url="{{site.baseurl}}/assets/charts/PriceByLanguage.json" style="width: 100%"></vegachart>

<hr>
- Il grafico è stato salvato come file `chart_responsive.json` e inserito nella cartella `assets/charts`.
- Se provassimo a visualizzare il grafico in una pagina web senza specificare la proprietà `width='container'`, il grafico non sarebbe responsive e verrebbe visualizzato con una larghezza fissa.
- Se porvassimo a visualizzare il grafico in un notebook Jupyter, il grafico non sarebbe visibile in quanto la proprietà `width='container'` non è supportata in questo ambiente. In tal caso, è possibile specificare una larghezza fissa in pixel e cambiare la proprietà width solo in fase di esportazione. 

### Number of reviews by month
<vegachart schema-url="{{site.baseurl}}/assets/charts/NReviews_Month.json" style="width:100%"></vegachart>

### Esempio di inserimento di csv

<table>
  {% for row in site.data.PriceByLanguage %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}

    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
  {% endfor %}
</table>


### Mappa di Folium

### Where are our restaurants?
<iframe src="/assets/charts/mappa_ristoranti.html" width="100%" height="500px" ></iframe>

### Where do tourists go?
<iframe src="/assets/charts/mappa_ristoranti_ratio_italian.html" width="100%" height="500px" ></iframe>

### How much do the restaurants cost?
<iframe src="/assets/charts/mappa_ristoranti_prezzi.html" width="100%" height="500px" ></iframe>

### Where are the most reviewed restaurants?
<iframe src="/assets/charts/mappa_ristoranti_n_recensioni.html" width="100%" height="500px" ></iframe>

### Where are the best rated restaurants?
<iframe src="/assets/charts/mappa_ristoranti_stelle.html" width="100%" height="500px" ></iframe>

#### Where are the restaurants?
<iframe src="/assets/charts/mapchloropleth_nristoranti.html" width="100%" height="500px" ></iframe>

#### Where are the expensive restaurants?
<iframe src="/assets/charts/mapchloroplethcari.html" width="100%" height="500px" ></iframe>

#### Where are the cheap restaurants?
<iframe src="/assets/charts/mapchloropletheconomici.html" width="100%" height="500px" ></iframe>

#### Where are most highly rated restaurants?
<iframe src="/assets/charts/mapchloropleth_highlyrated.html" width="100%" height="500px" ></iframe>

#### Where are the restaurants with most Italian customers?
<iframe src="/assets/charts/Chloroplet_ItalianReviews_ratio.html" width="100%" height="500px" ></iframe>

#### Where are the restaurants with most Non-Italian customers?
<iframe src="/assets/charts/chloroplet_nonitalianreviews_ratio.html" width="100%" height="500px" ></iframe>

