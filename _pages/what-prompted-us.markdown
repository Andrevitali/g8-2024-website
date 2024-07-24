---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title:  "Data matters"
subtitle: "Our data and what promped us"
show_sidetoc: true
# header_type: hero #base, post, hero,image, splash
# header_img: assets/images/altair-gallery.png
# header_title: "Our Data"
vega: true
---


# **Data matters**
### The reasons behind our project

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
“Communication has changed massively. Now the trend is to have signature dishes that are representative of a restaurant and can embody its **brand**. These unique dishes become central to the restaurant's identity, making it easier to stand out in a crowded market.
<br>
Using the visual and the storytelling affordances of social media to create a compelling narratives around specific dishes can do wonders to generate positive buzz around a restaurant and therefore attract attention from customers. Something that non-specialty restaurants would struggle to match."
<br>
<br>
<i>Since the idea behind CraveIT is to develop a platform that recommends the best restaurants where a specific Italian dish can be eaten, do you believe it makes sense to consider only reviews written by Italian users?</i>
<br>
“I would say so, for cultural and anthropological reasons. For instance, North American customers tend to demand sweeter flavours, whereas those from the Far East have a significantly different relationship with salt than us. I think that **there are factors rooted in one's national gastronomic tradition that influence taste perception** based on the person's region of origin. Therefore, for Italian cuisine, I would tend to trust a European user more, or even better, someone from the Mediterranean area.”
<br>
<br>
<i>In the current restaurant environment, what is the role played by industry experts? 
Do you think including experts' opinions in CraveIT's ranking is a good idea?</i>
<br>
“In the past, customers used to depend on food guides as the only way to decide on which restaurant to go to.
<br>
Nowadays, we seem to have the opposite issue: **customers have too much information**, which at times it's like having no information. 
Since customers might find it difficult to negotiate the overwhelmingly vast amount of online information at their disposal, guides can serve to pinpoint the best options with some authority. Therefore, I reckon that including experts' opinion in CraveIT's score would make its ranking more robust and reliable”
<hr>

### Our data
To develop the proof of concept of CraveIT, we have decided to focus on Rome and collected information on traditional Roman restaurants. 
For improved **freshness** and therefore **reliability** of our results, we have opted to restrict our analysis to reviews written from January 2019 onward.
The map below shows the location and some information about the restaurants included in our dataset.
<br>
<iframe src="{{site.baseurl}}/assets/charts/mappa_ristoranti.html" width="{{include.width  | default: '100%'  }}" height="{{include.height   | default: '400px'  }}" ></iframe>
<br>


#### Number of reviews by month
It is often said that **big data are a proxy of our social lives**, capturing societal trends and behaviors.
Our dataset makes no exception and several interesting insights can be observed.
For instance, by analyzing the chart below, which illustrates the number of reviews by month, we can confidently say that:
- There is a clear **seasonal pattern** in the number of reviews, with significantly fewer reviews posted during the winter months.  
- The data distinctly reflects the impact of the **COVID-19 pandemic**, with trends mirroring the various lockdowns and restrictions that occurred in Italy between 2020 and 2021. During the initial lockdown in early 2020, there is a marked decline in the number of reviews, 
followed by fluctuations that correspond to subsequent waves of the pandemic and implementations of public health measures.
- The number of reviews does not seem to have recovered to pre-pandemic level.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Total.json" style="width:100%"></vegachart>
<br>
<br>

#### Reviews by language
Although CraveIT's ranking is based exclusively on **Italian reviews**, the original dataset includes both Italian and non-Italian reviews in a roughly 60:40 proportion.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/2207Bar_N_ItalianvsNonItalian.json" style="width:100%"></vegachart>
<br>
Among the non-Italian reviews there are many different languages, and consequently **cultures**. 
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_NForeignReviewsbyLanguage.json" style="width:100%"></vegachart>

<br>
Given the rich variety of languages and cultures in our dataset, we tried to extract some interesting insights on both tastes and behaviors. 
For instance, we expected people from high-income countries to go to more expensive restaurants and customers from less wealthy countries to cheaper ones. 
The data gathered and visualized in the chart below seem to confirm this expectation.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/2207Bar_Price_byLanguage.json" style="width: 100%"></vegachart>
<br>
It is also worth noting that there is a significant difference in **how different cultures rates Italian restaurants** and this is another 
factor that supports our decision to only include Italian reviews to calculate our ranking.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/2207Bar_Ratings_byLanguage.json" style="width:100%"></vegachart>
<br>
With regard to the previous chart, we need to remember that **not always correlation implies causation**.
In fact, it must be underlined that restaurants with lower prices tend to receive higher ratings (as shown in the chart below). 
Therefore, the link between languages and ratings might not be direct, but rather due to the fact that those who are willing to spend more might be more critical.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607Bar_ReviewbyStars.json" style="width: 100%"></vegachart>
Non-Italian reviews can serve as a reliable indicator of the presence of foreign tourists in Rome. By analyzing these reviews over time, we can therefore observe and **track touristic trends** in the city.
From the two graphs below, we can infer the following:
- There is a clear **seasonality in international tourism**, with a high season beginning approximately in April and ending in October.
- The **COVID-19 pandemic** had a huge impact on tourism from abroad due to the travel restrictions imposed. In June 2020 and between February 2021 and May 2021, the proportion of non-Italian reviews consistently fell below 8%, clearly indicating a collapse in international tourism. However, from 2022 the pandemic's disruptions began to recede and since 2023, a pre-pandemic trend seem to have resumed.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_Italian_NonItalian.json" style="width:100%"></vegachart>
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_Nreviews_bymonth_byItalian_NonItalian_Normalized.json" style="width:100%"></vegachart>

<br>
A final interesting piece of information that we have retrieved by analyzing our dataset is the evolution of reviews written in Russian over the last five years. 
As expected, they followed the COVID-related collapse seen in reviews written in any other language but Italian. However, differently from all the other foreign languages, **the number of reviews in Russian never recovered to pre-pandemic levels**. This unique behaviour is likely to be linked to the travel restrictions imposed by Western governments on Russian nationals after the invasion of Ukraine in February 2022.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_Russian.json" style="width:100%"></vegachart>

<br>



#### Reviews by type
Another valuable piece of information that our data can provide is the type of visit described in the reviews, such as whether they were made with family, as a couple, for business, alone, or with friends. 
By analyzing this detail and its evolution over time, we can infer important insights into **customers' social behaviours** and preferences when dining out.
The plots below seem to indicate the following:
- The vast majority of customers go out to eat with their partner, family, or friends.
- **The number of reviews written by customers dining out for business remains well below pre-pandemic levels**. This may suggest a shift in behaviour, with fewer business trips and an increase in online meetings and remote working.
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NormalizedReviews_byMonth&Party.json" style="width:100%"></vegachart>
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth&Party.json" style="width:100%"></vegachart>
<br>
<vegachart schema-url="{{site.baseurl}}/assets/charts/1607_NReviews_byMonth_Business.json" style="width:100%"></vegachart>
<br>

  
<br>
### Geospatial Insights 
<br>
In this section, several geospatial visualizations are displayed. It is particularly interesting to notice the **differences between the historic centre and the rest of the city**. The maps clearly illustrate the significant influence of tourism in the central areas of Rome. 
This insight helps us understand how tourist activity is concentrated in specific parts of the city and how this might impact the social and economic fabric of those areas.

{% include map-selector.html dataset="maps-selector" %}
