---
layout: page
title: Is YouTube Riding the Mental Health Wave? 
subtitle: Deep dive into the YouTube Mental Health World 
cover-img: /assets/img/header_.png
thumbnail-img: /assets/img/header_.png
share-img: /assets/img/header_.png
---
<div style="text-align: justify"> 
Let us start with some simple questions: 

- Have you ever felt `pressure and depression` when there are so many deadlines?

- Have you ever seen any `videos talking about mental health` when surfring online on Youtube? 

- There are tons of discussions around mental health on Youtube. Have you ever wondered how they `shape the platform’s content and channel landscape`? 

In today's digital age, mental health has garnered paramount importance, and YouTube has emerged as a significant platform for individuals seeking information, support, and connection on this crucial topic. 

Follow our story today and delve into our analysis! Explore together with us to get the answers: Are mental health discussions on the rise on YouTube? Let us examine deeply the trends, categories, and  evolution of channels and videos. 

We invite you to join us on this journey of discovery, and we assure you that by the end you will unveil the platform's changing landscape and ave a better understanding of the ever-changing world of YouTube and the role mental health played within it.
 </div>


![invitation](assets/img/Accepting-the-Invitation.png)

&nbsp;
# The Dataset We Used
We are using the dataset `YouNiverse`, a large collection of channel and video metadata from English-language YouTube presented by _Dr.Ribeiro_ and _Dr.West_. It comprises metadata for over 136k channels and 72.9M videos published between May 2005 and October 2019, as well as channel-level time-series data of weekly subscriber and
view counts. 

For your reference, you can check the dataset [HERE](https://doi.org/10.5281/zenodo.46500463). 



&nbsp;
# Mental Health: Trendy Problem?
> RQ1: Is mental health a trend on YouTube?

We all know that `Mental Health` is not a new topic today. At the beginning of 21st Century, one in four adults in US suffered from some form of mental illness -— nearly 60 million Americans in any given year _(Agency for Healthcare Research and Quality, 2009)_. 

Then it comes to September 2021, the COVID-19 pandemic has significantly impacted mental health worldwide. The problem got much worse and went into the public sight again after the outbreak of the pandemic. According to the **World Health Organization (WHO)**, cases of anxiety and depression have `increased by 25%` globally since the pandemic began, with suicide the second leading cause of death among 15-29-year-olds. Approximately `one in five people` in post-conflict settings have a mental health condition.

**But, it is already a trend before the pandemic?** Internet reflects people's life within a certain period. We found many videos about mental health on Youtube even before the pandemic. Therefore, we would like to focus on the them to get the answers. 

&nbsp;

## 1.1 Filter the Videos

Before starting the analysis, we need to get videos about mental health. This is the core step in our data processing pipeline which target videos regarding `Mental Health` are retrieved for further processing and visualization. At the same time, we plan to retrieve videoes of other topics so that comparison can be made between different trends to further validate our hypothesis.

### 1.1.1 First Filter (keywords matching)

The method we use to retrieve relevent videos is based on the string matching of keywords. The idea is that:

1) We come up with a list of keywords  that is supposed to connect to the filed of mental health, including: `mental health`, `disorder`, `solitude`, `depress`, `stress`, `suicid`, etc.

2) Since the dataset is extremely large, we read the files line by line and process them in a batch size of 200000. Three attributes are taken into account during processing, namely `description`, `tags` and `title`. If **at least two out of three text fields** contain a word in our designed word list, we assume that video is relevent and be retrieved. We adopt the function `pd.Dataframe.str.contains` to check the existence of the keywords.

**Problem**: However, after the first filter and printing partial results, the problem is that many of them seems irrelevant to mental health like _The Lego Batman Movie: Batman's Lonely Life_. As a result, the first version of analysis results are not very satisfactory, and we get little information. To solve the problem, here comes to our second filter. 

![problem](assets/img/fixproblem.png)

### 1.1.2 Second Filter (snow ball sampling)
For the below block, we have done several additional filtering aiming for a more desired outcome.

1) After retrieving, we check the results manually and see if there is any insightful words that occur in the result but is not included in our designed keyword list. If such word exists, we `iteratively add them to the list` and `repeat the process` 1-3 times to update the results until no new words can be found.

2) We require that in the `title` of the video, at least one of keywords should exist, which is tighter than the `two out of three requirement` above.

3) We eliminate some videos belonging to categories like `Music`, `Movie` since we inspect the content of the videos and most of them are false positive. Till now, the categories we allow are included in the list `constrained_category`.

4) Specifically for `mental health` videos, we filter some of the undesired contents based on keywords like `monkey`, `malone`, for they show little relevance to the topic.

5) Finally, use a wordcloud figure and display our final results to validate the results we obtained so far.

![wordcloud](assets/img/wordcloud.png)
{% include samples.html %}

**Further Improvement**: It takes a long time to process through the data, so we cannot do the loop many times, further improvement on the topic may include improving keyword list quality, adopting stemming on words for better matching, etc.

### 1.1.3 Control Group
Aside from the target videos reagarding mental health, we also aim to retrieve videos of **three representative types**:

- Long-term trendy videos: This type of videos is the result of a long-term social trend, reflecting the raising awareness of some profound topics, e.g. `gender equality`, `climate change`. These topics enjoy a long-lasting attention and a steady increase in terms of YouTube videos. We hypothesize that `mental health` should belongs to such topic.

- Short-term trendy videos: This type of videos represents a very fashionable impulse on people posting same kind of videos just because other people are also doing it. The heat may be extreme at the moment but may not last long. Example such as `ice bucket challenge`, etc.

- Control group videos: This type of videos had not been brought to the spot of light during 2015-2019, but nonetheless we may still observe a growth in the number of videos on YouTube because the user growth and prevelant influence of digitilization.

We would like to compare the trend of the three types of videos and see if any interesting conclusion may be drawn from the results.

&nbsp;
## 1.2 Time Trend Analysis

Now everything is ready! It is time to look at the time trend -- how much videos about mental health are uploaded per month and their growth over the years.

### 1.2.1 Mental Health Trend
Now we display the number and the ratio of the mental health videos uploaded per month from 2006 to 2019. 

We display both video numbers and ratios throughout the year and applied a linear regression analysis to analyze if there is a trend. 

Although the p-value of the LR analysis indicates the relation is not statistically significant, we include it in our plot for reference.

To this end, we couldn't demonstrate any significant increase of the uploaded mental health videos. But we do see a mild upward trend and we need to further compare the results with other topics to further validate our ideas.

{% include ratio.html %}


[Interpretation]: It is intersting to see that although there is an increase in numbers of video uploaded..., the ratio with respect to all uploaded videos from the same category does not increase much. A mere 2.303e-06 coefficient can be estimated by linear regression, but again the results are not statistically significant.

Is this a common thing? We do not want to immdediately jump to a conclusion that there's no trend for the uploaded videos at all, so we filter severl videos from other socially important problems such as `climate change`, `gender discrimination`, etc. to compare their trend as well. And the comparison is illustrated below:


 {% include comparison.html %}






