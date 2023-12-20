---
layout: page
title: Video Content Analysis
subtitle:  
cover-img: /assets/img/header_2.png
thumbnail-img: /assets/img/header_2.png
share-img: /assets/img/header_2.png
---

## Video Content Analysis

<div style="text-align: justify">Building on our in-depth exploration of mental health videos through time-series evaluations and video metadata analysis, we now venture into a critical yet often overlooked dimension: the sentiments these videos express. 

In this phase, we employ NLP methodologies to blend quantitative data with the qualitative essence of the content. We're diving into the emotional nuances of these videos to explore an intriguing question: are top mental health videos using certain strategies, like impactful tones or engaging topics, to increase their popularity? Let's delve deeper and find out.</div>



### Sentiment Analysis
<div style="text-align: justify">Our sentiment analysis of video descriptions in the mental health genre offers a unique window into whether these videos are trend-focused or genuinely addressing mental health concerns. By examining the emotional tones in these descriptions, we get insights into the creators' intentions. Are they striving to uplift and educate about mental health, or are they more commercially driven, chasing trends?</div>

<div style="text-align: justify">
Let's examine the overall sentiment landscape of mental health videos. What do the sentiment scores, determined by the BERT model, reveal about these conversations? Are they more about delving into the complexities of mental health, or celebrating positive support and outcomes?
</div>
{% include distribution_overall.html %}

The prevalence of high sentiment scores suggests that mental health discussions on YouTube are emotionally charged. This raises a question: does this intensity focus more on the complexities of mental health rather than just positive outcomes or support?

{% include distribution_time.html %}

The initial dominance of positive sentiment might point to a phase of inspiring and uplifting content. However, as time progresses, we notice a shift towards negative sentiment. What does this shift signify? Could it indicate a more honest and profound discussion about mental health issues?

This evolving sentiment pattern might be a response to a growing demand for authenticity in mental health discussions, rather than a mere adaptation to trends. The consistent increase in negative sentiment over 14 years suggests a deeper, more meaningful change in how mental health is portrayed in digital media.

Now, let's consider how sentiment scores correlate with popularity, defined by a `popularity_score` combining `view_count` and `like_count`. 

{% include distribution_popularity.html %}

We have two interesting discoveries:
1. At the lower end of the popularity spectrum, there is a notable stability in sentiment, with a subtle decreasing trend overall. (specifically in the [10^2, 10^5] range)
2. As videos become more popular, their sentiment scores become more varied. (specifically in the [10^6, 10^8] range)

For the first observation, we can perform a linear regression analysis in the middle range.

{% include distribution_popularity_regression.html %}


There is a discernible downward trend in the average sentiment score. This trend suggests a nuanced shift in the tone of video descriptions: as videos garner more views and potentially reach a wider audience, their descriptions may increasingly reflect a more sober or realistic portrayal of mental health issues, which could be perceived as less positive.

This gradual decline in sentiment with rising popularity could indicate that creators with a larger audience may feel a responsibility to present a more multifaceted and perhaps less idealized view of mental health, aligning with a broader societal trend towards authenticity and acknowledgment of mental health complexities. 

This pattern could be driven by **a genuine desire to contribute to the destigmatization of mental health issues, rather than a mere pursuit of popularity or trend-following**. The challenge remains to discern whether this shift is motivated by a trend or a collective move towards greater awareness and understanding of mental health.


For the second observation, this variability in top videos suggests that more popular videos tend to polarize opinion. 

This pattern could be driven by a genuine desire to contribute to the destigmatization of mental health issues or a pursuit of popularity or trend-following. Let's have a deeper look in what topics those top videos are talking about.





### Topic Detection
To understand what the popular videos are trying to deliver with such polarized sentiment score distributions, we turn to topic detection analysis based on the LDA model, a statistical model that uncovers abstract "topics" in a collection of documents. 

We focus on the top 1000 videos with the highest popularity scores, analyzing their titles to grasp the core topics, as titles can concisely summarize the videos' themes.

{% include lda_topic.html %}

The analysis uncovers a range of topics. "Psychological," "tips," "love," "signs," and "disorders," found in Topics 2 and 6, suggest a serious exploration of mental health issues. These topics likely cover psychological advice, well-being tips, and discussions about mental health disorders, indicating a commitment to mental health education and support.

Conversely, Topics 0, 1, 3, 5, 7, and 8 lean towards entertainment or lifestyle content. Words like "funny," "prank," "hacks," "giant," "experiment," and "sneak" imply a focus on engaging viewers with amusing or intriguing activities rather than mental health discussions. This could indicate a trend-following approach among some content creators, aiming to capitalize on popular themes to attract viewership.

Topic 4, with words like "brain," "big," "old," and "traits," presents a mix of entertainment and education, suggesting content that blends engaging methods with serious topics like brain health or psychological traits.

The repeated occurrence of words like "open," "store," "bought," and "girls" across various topics might suggest a common style or thematic element, possibly reflecting specific trends or formats adopted by content creators.

Finally, words like "desk," "zen," "garden," and "relieving" in Topic 9 hint at content focused on stress relief and relaxation techniques, relevant to mental health but in a more indirect, lifestyle-oriented manner.

As we delve deeper into the topic detection analysis, the narrative becomes more intricate. The LDA model has revealed topics that underscore a serious and substantive engagement with mental health issues. Terms like "psychological," "tips," "love," "signs," and "disorders" suggest a deeper dive into the intricacies of mental health, offering educational content and advice that could genuinely aid viewers in understanding and managing their mental well-being.

This inclination towards substantial content is crucial in our assessment of whether mental health videos are merely trend-following or revealing real social issues. While some topics may align with popular culture or entertainment, they could be strategic choices by content creators to engage a broader audience before delving into more serious discussions suggested by other prevalent themes.

**Our findings show that while there is some content that may follow viewing trends with lighter themes, a significant portion of mental health videos is committed to more profound topics**. 

As we consider the overarching trends in sentiment and topic popularity, we may see a coherent message. 
* The gradual shift towards a more sober tone in descriptions
* The emergence of weightier topics in video titles 
    => both point towards a digital environment that is increasingly reflective of the real societal dialogue on mental health. 

Far from simply riding the waves of transient trends, the mental health conversation on platforms like YouTube is evolving into a space where real issues are confronted and discussed.

In conclusion, the data from sentiment analysis and topic detection when considered together, weave a narrative that affirms the growing maturity of discourse around mental health in digital media. This maturation reflects a conscious shift by content creators to acknowledge and address the complex realities of mental health, indicating a broader cultural movement towards openness and authenticity in the portrayal of mental health issues.