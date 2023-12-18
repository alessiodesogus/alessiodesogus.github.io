---
layout: page
title: Sentiment Analysis
subtitle:  
cover-img: /assets/img/header_2.png
thumbnail-img: /assets/img/header_2.png
share-img: /assets/img/header_2.png
---

## Sentiment Analysis

<div style="text-align: justify">Building on our previous analyses, which have meticulously dissected various aspects of mental health videos through time-series evaluations and an in-depth exploration of video metadata, we now turn our focus to a crucial and often underexplored facet: how these videos convey. 

This phase of our investigation seeks to bridge the gap between quantitative data and the qualitative essence of the content, through NLP analysis methodologies. By delving into the emotional undercurrents of these videos, we aim to paint a comprehensive picture, discovering out whether the top mental health videos are trying to use some tricks to become more popular - strong tone, engaging topics...
</div>



### Sentiment Analysis
<div style="text-align: justify">Sentiment analysis of video descriptions in the realm of mental health offers a unique and somewhat lighthearted lens to discern whether these videos are riding the wave of a trend or genuinely striving to address mental health issues. By scrutinizing the emotional tone embedded in these descriptions, we get a sneak peek into the creators' intentions. Are they upbeat and enthusiastic, hinting at a desire to genuinely uplift and educate about mental health? Or do they carry a more commercial, trend-following vibe?</div>

<div style="text-align: justify">
Let's use see how do the sentiments of mental health videos look like in an overall level. The sentiment score is provided by BERT model
</div>
{% include distribution_overall.html %}

The overwhelming majority of descriptions have been classified with high sentiment scores, indicating that we can see the intense nature of discussions and narratives around mental health topics on YouTube, where expressions of both support and struggle could be expected to elicit strong emotional responses. 

The stark contrast between the quantities of negative and positive sentiments may also point to a tendency for these videos to address challenging or problematic aspects of mental health more so than positive outcomes or support.

{% include distribution_time.html %}

The initial prevalence of positive sentiment might suggest an initial phase of aspirational content, where the intent was to motivate and instill positivity in the audience. As the years advance, the increasing proportion of negative sentiment becomes apparent, suggesting a shift towards a more candid exploration of mental health issues. This pivot could be interpreted as content creators moving away from solely uplifting content to incorporate a broader, more realistic range of mental health experiences, including the acknowledgment of struggles and the challenges faced by individuals.

The critical question arises as to whether this shift is a response to a growing demand for authenticity in mental health discussions or if it is merely a reflection of creators adapting to a trend. The steady rise in content with negative sentiment could point to an evolving public consciousness that favors a more holistic and truthful portrayal of mental health, countering earlier tendencies towards idealized portrayals. If this change were driven by trend-following alone, one might expect to see fluctuations that correlate with popular discourse at specific points in time. However, the sustained increase over a 14-year span suggests a more profound reorientation in how mental health is approached in digital media.


Now we take a deeper look into the sentiment scores, that how they evolve with popularity. We define a metrics for the popularity of YouTube videos here: `popularity_score` = `view_count` + `like_count`, considering the influence of both number of views and number of likes to the videos.

{% include distribution_popularity.html %}



<div style="text-align: justify">
As we ascend the popularity scale, there is an evident increase in the variability of sentiment scores. This variability suggests that more popular videos tend to polarize opinion, possibly due to their exposure to a broader and more diverse audience. The heightened emotional response in highly popular content could be attributed to several factors: the content might inherently provoke stronger emotional reactions due to its engaging nature, or the volume of views and likes might amplify the visibility and therefore the sentiment extremities. Alternatively, these videos could be subjects of controversy, which often engenders pronounced sentiment expressions.

At the lower end of the popularity spectrum, there is a notable stability in sentiment, indicating a consensus or uniformity in perception among a smaller audience. Yet, it is the middle popularity range where the sentiment begins to diverge, hinting at a more complex interplay of factors as content gains traction. To distill the underlying patterns in this mid-range, we can perform a linear regression analysis in the [10^2, 10^5] range.

{% include distribution_popularity_regression.html %}

There is a discernible downward trend in the average sentiment score of mental health video descriptions as they ascend in popularity, in the mid-range of the popularity spectrum. This trend suggests a nuanced shift in the tone of video descriptions: as videos garner more views and potentially reach a wider audience, their descriptions may increasingly reflect a more sober or realistic portrayal of mental health issues, which could be perceived as less positive.

This gradual decline in sentiment with rising popularity could indicate that creators with a larger audience may feel a responsibility to present a more multifaceted and perhaps less idealized view of mental health, aligning with a broader societal trend towards authenticity and acknowledgment of mental health complexities. 

Connecting this observation to the previous analysis, the shift in sentiment could be indicative of content creators' response to audience expectations, suggesting a deliberate move away from simply uplifting content towards material that engages with the nuanced realities of mental health. This pattern could be driven by a genuine desire to contribute to the destigmatization of mental health issues, rather than a mere pursuit of popularity or trend-following. The challenge remains to discern whether this shift is motivated by a trend or a collective move towards greater awareness and understanding of mental health.

</div>




### Topic Detection
To explore what are the popular videos trying to deliver with such polarized sentiment score distributions, we can detect what are the main topics they are related to. We perform topic detection analysis based on LDA model, a type of statistical model used for discovering the abstract "topics" that occur in a collection of documents. It's a form of unsupervised machine learning that organizes a corpus of text documents into topics, which are distributions of words that capture the essence of thematic subjects.
We define "top videos" as the 1000 videos with highest popularity score (view number + like number) we use above, and perform topic detection analysis on their titles only, as titles can concretely summarize the topics of the videos, while description can include some minor texts like channel websites or previous video links.

{% include lda_topic.html %}

Topics such as "psychological," "tips," "love," "signs," and "disorders" (found in Topics 2 and 6) suggest a serious exploration of mental health issues. These topics likely cover psychological advice, tips for well-being, and discussions about mental health disorders, indicating a genuine concern for mental health education and support.

Conversely, Topics 0, 1, 3, 5, 7, and 8 seem to veer towards entertainment or lifestyle content. Words like "funny," "prank," "hacks," "giant," "experiment," and "sneak" imply content that is more about engaging viewers with amusing or intriguing activities rather than focusing on mental health issues. This might indicate a trend-following approach among some content creators, possibly aiming to capitalize on popular themes to attract viewership.

Topic 4, featuring words like "brain," "big," "old," and "traits," presents a mix that could be interpreted in multiple ways. It might indicate content that blends entertainment with educational elements, possibly using engaging methods to discuss serious topics like brain health or psychological traits.

A unique observation is the repeated occurrence of words like "open," "store," "bought," and "girls," across various topics. This repetition might suggest a common style or thematic element in these videos, possibly indicating a specific trend or a commonly adopted format among content creators.

Finally, the presence of words like "desk," "zen," "garden," and "relieving" in Topic 9 hints at content focused on stress relief and relaxation techniques, which is relevant to mental health but in a more indirect, lifestyle-oriented manner.


When we look deeper into the topic detection analysis of mental health video titles, the narrative begins to unfold even further. The LDA model has surfaced topics that underscore a serious and substantive engagement with mental health issues. For example, terms like "psychological," "tips," "love," "signs," and "disorders" are indicative of content that is not just skimming the surface for views or likes. Instead, these topics suggest a deeper dive into the intricacies of mental health, offering educational content and advice that could genuinely aid viewers in understanding and managing their mental well-being.

This inclination towards substantial content is crucial in our assessment of whether mental health videos are merely trend-following or revealing real social issues. While some topics may seem to align with popular culture or entertainment, they could very well be strategic choices by content creators to engage a broader audience before delving into the more serious discussions suggested by other prevalent themes.

**Our findings show that while there is some content that may appear to follow viewing trends with lighter themes, there is a significant portion of mental health videos that commit to more profound topics**. This balance indicates that the space for mental health content on digital platforms is not monolithic and trend-driven but is instead a complex landscape where serious social issues are given the spotlight alongside more engaging, viewer-friendly content.

As we consider the overarching trends in sentiment and topic popularity, the coherence in the message becomes apparent. The gradual shift towards a more sober tone in descriptions and the emergence of weightier topics in video titles both point towards a digital environment that is increasingly reflective of the real societal dialogue on mental health. Far from simply riding the waves of transient trends, it appears that the mental health conversation on platforms like YouTube is evolving into a space where real issues are confronted, discussed, and destigmatized.

In conclusion, the data from sentiment analysis and topic detection when considered together, weave a narrative that affirms the growing maturity of discourse around mental health in digital media. This maturation reflects a conscious shift by content creators to acknowledge and address the complex realities of mental health, indicating a broader cultural movement towards openness and authenticity in the portrayal of mental health issues.