---
layout: post
---

<p style="text-align:center;">
<img src="https://images.pexels.com/photos/708440/pexels-photo-708440.jpeg?auto=compress&cs=tinysrgb&dpr=2&h=750&w=1260" alt="young people">
<figcaption style="text-align:center;font-size:small;font-style:italic">Photo by <a href="https://www.pexels.com/@wildlittlethingsphoto">Helena Lopes</a> from <a href="https://www.pexels.com/photo/men-s-white-button-up-dress-shirt-708440/">Pexels</a>
</figcaption>
</p>

Hey there! Do you also find yourself scrolling through interesting datasets on [kaggle](https://www.kaggle.com/datasets) from time to time?

Well, I do! And I recently stumbled upon an extremely interesting one: the [young people survey](https://www.kaggle.com/miroslavsabo/young-people-survey)! Even though it's from already quite old (it's from 2013), it contains more than one thousand survey answers of young people concerning their hobbies, interests, political and philosophical views and more!

In particular, I personally am interested in the answers related to spending money, or "spending habits". I guess everyone remembers that, at a young age, when you're going to school, college or university, the amount of money you have at your disposal is typically not that great. At least I remember being afraid to look at the account balance at the end of the month more often than not.

This is why I find it very interesting what young people *do* spend their scarce money on in particular, and if there are any features telling us if a person had more luxorious - or a more economical lifestyle. Let's dive in!

---


### What young people like to spend their money on?

The survey dataset contains six categories about spending money:
- Spending on entertainment
- Spending on looks
- Spending on gadgets
- Spending on healthy eating
- Spending on branded clothing
- Spending in shopping centres

For each of these, participants had to answer with preference values between 1 to 5, where 1 means spending a low amount and 5 a high amount of money. We also created a *total spending* feature, simply summing all the spending values. Here are the results:

<p style="text-align:center;">
<img src="/images/2022-02-22-what-makes-young-people-spend-money/spending_overview.png" alt="spending habits overview">
</p>


As we can see, most survey participants chose the middle value, 3, which means they neither spend a large, nor a super small amount of money. People also tend to spend a bit more on healthy eating and in shopping centers and a bit less on "gadgets". When summing up the answers, we see the distribution is centered on a slightly higher value than the central one.

### Does gender and education have an impact on spending habits?

To answer this question, let's look at the total spending distributions for female and male participants first:

![Spending habits of female and male participants](/images/2022-02-22-what-makes-young-people-spend-money/gender_histogram.png)

Looking at the result, it seems that male participants are trending towards higher spending, while female participants seem to be more economical. A quick hypothesis test revealed that the difference between the two populations is indeed significant! So we can say that female participants tend to spend lower amounts of money overall than male participants.

For the educational background, things look a bit less different. Here I divided the participants in two groups: participants with "higher education" have a bachelor degree or higher, while people with "lower education" have a secondary school degree or lower. Let's have a look at this distribution:

![Spending habits of participants with high and low education](/images/2022-02-22-what-makes-young-people-spend-money/education_histogram.png)

Simply looking at the plot by eye does not really tell us anything, since the distributions look rather similar. There is a high bin for higher education at a total spending score of 12 for unknown reasons, but doing the same hypothesis test as before revealed that the difference between the two populations is *not* significant.

This is interesting, since I would have expected people with higher education to be wealthier and thus being able to afford a more luxorious lifestyle than people with lower education. However, let's keep in mind that this is a *young* people survey, which means that most of the participants are probably still in the beginning of their career and have not earned that much just yet.

### Which hobbies/interests/views of young people are most strongly correlated with their spending habits?

Since the amount of different hobbies and interests in this survey is huge, I only plotted the 5 most positively and most negatively correlated categories here:

![Feature importance](/images/2022-02-22-what-makes-young-people-spend-money/correlation_full.png)

The most strognly correlated feature is rather obvious: Having shopping as a hobby has a high correlation with total spending.

The second feature is "*knowing the right people*", which is interesting: I guess that people who do a lot of networking also need to spend more money to do others a favour to get into the "right circles". Also it could just be that people who are better known also get better job offers and thus can afford a more luxorious lifestyle.

The "appearance and gestures" feature corresponds to the score towards the statement "*I am well mannered and I look after my appearance.*". Again, I think it is expected to have a high correlation with spending habits, since people with a high score here will probably spend a lot of money for adequate clothing and other fashion and beauty-related products.

Doing adrenaline sports is expensive and also here we shouldn't be too surprised to see it highly correlated with spending habits. Having a lot of friends is also highly correlated, probably because spending a lot of time with friends often includes fun activities that cost money (e.g. hanging out in bars or clubs).

The most negatively correlated features are decision making, interests in documentaries, listening to metal or hardrock and folk music as well as being interested in finances.

The latter I found especially interesting, since one would expect an interest in finances to be positively correlated with spending. If someone is an intelligent investor, I would have expected they have more money and thus can afford a mor luxorious lifesteyle.

However, it could also be that in order to invest, people interested in finance need to save up more money, which is why they also need to spend less and the correlation gets negative.

### Predicting spending habits

To see if I can predict the spending habits from the data given in this survey, I created a machine learning-based regression model. The overall score of the model was rather bad, which means that it is - as we would expect - rather hard to forecast the spending habits of young people using hobbies and interests. Looking at the most important features for the model, we get this plot:

![Feature importance](/images/2022-02-22-what-makes-young-people-spend-money/importance_mlp.png)

Some of the results are the same as we saw from our correlation study: Shopping and knowing the right people, being interested in finances and looking after one's appearance show up again. 

Interestingly, the belief in final judgement seems to also be a very predictive feature for this model, too! Maybe this is a remnant of the [protestant work ethic](https://en.wikipedia.org/wiki/Protestant_work_ethic)? Who knows.

The least important features seem to be: punctuality, liking animated movies, looking after stuff that was borrowed from others, interest in mathematics and socializing. The latter I also find quite interesting, since being social often also comes with higher costs, like hanging out with people in bars, clubs, cinemas etc. 


### Wrapping it up

In this article, we looked at what young people spend their money on and if we can identify any particular habits, hobbies or views that influence their spending. Here are the key findings:

1. When looking at what young people spend their money on, most chose a "medium" value for the different categories, which means they neither spend an awful lot, nor an extremely low amount on these things. We also saw people were spending a bit more on healthy eating and in shopping centers than for things like gadgets.

2. When looking how gender and education affected spending habits, we found out that there is a significant difference for gender, showing that male participants tend to spend more money than their female counterparts, while no such difference was observed for education.

3. Most of the habits that are most strongly correlated to the spending are also connected to money: being interested in shopping, networking, finances, looking after ones appearance etc. Interestingly, the interest in finances is negatively correlated with spending.

4. Most of the habits that are strongly correlated with the spending habits also seem to be good predictors. A quite unexpected feature that now also shows up is the belief in final judgement.

5. Overall, it is quite hard to predict spending habits from the questionary inputs. Even with advanced tools like machine learning models, we could not get to a very high predictive score.

So, what do **you** think? Which hobbies, views or habits might have an influence on how you spend your money? Are there any? Or is such a prediction just not possible at all?

To check out the full analysis code, see the link to the respective Github repo [here](https://github.com/loeschet/fsev-youth-analysis).
