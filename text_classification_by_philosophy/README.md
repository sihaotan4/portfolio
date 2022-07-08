# Classifying Text by Philosophical Inclination
#### by Si Hao Tan

<br/>

# Executive Summary

The project is for a new wellness app where users are invited to write a short journal entry. The app will then analyze the journal entry and provide a personalized message for the user. Therefore, a key component of the app is to classify the user's philosophical inclinations based on the text entry. The project deliverable is a text classifier pipeline which has an accuracy of 0.83. The pipeline includes feature engineering, NLP preprocessing, and the lightGBM classifier. Additionally, with the use of Shapley values, feature importance can also be extracted from the lightGBM blackbox for model explainability.


# Problem Statement 

The team is working on a new wellness app called "Daily Mind Journal" where users are invited to write a short journal entry everyday. The app will then analyze the journal entry and provide a personalized message for the user based on the philosophical inclinations of the user's entry.

Therefore, a key component of the app is to **classify the user's philosophical inclinations based on the text entry**. In this early prototype, we attempt to classify the user's entry into only two philosophical inclinations - Buddhism or Stoicism. In the future, we will expand the app to include more philosophical inclinations.

To this end, the project deliverable is a classifier model that can distinguish philosophical inclinations solely based on text.

The trained model can then be deployed within the app as an initial model, to be improved over time with real user data after launch.

# Business context

The proliferation of wellness apps has been exacerbated by pandemic fatigue around the globe. [The New York Times](https://www.nytimes.com/2021/02/17/magazine/wellness-apps.html) reports that "_Mindfulness apps like Calm, Headspace, Fabulous, Rootd and Liberate all surged over the past year, downloaded by people in search of reprieve from the crushing anxiety of the virus."_

Pair this idea with the [findings](https://www.webmd.com/mental-health/mental-health-benefits-of-journaling#:~:text=Journaling%20is%20the%20act%20of,of%20improving%20your%20mental%20health.) that daily journaling has been shown to reduce anxiety, regulate emotions, and even benefit physical health. 

This sets the stage for a new app that can act as an interactive digital journal by returning a positive thought of the day based on the user's journal input. The [mechanism](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4760272/) of replacing usual forms of worry with positive stimuli has been effective in helping with Generalized Anxiety Disorder (GAD). 

We think that the approach of daily journaling and the interactivity of being returned a curated message forms a powerful and positive feedback mechanism to help users alleviate worries. 

Part of the approach hinges on accurately profiling the user's philosophical inclination, so the message returned is appropriate to the user's outlook on existence. 

# Model Results 

The project deliverable is a tuned lightGBM classifier, which can be deployed on the app after some refinements. The classifier delivers a respectable classification accuracy of 0.83 on a balanced dataset and is able to discern the originating subreddit of a post, simply by using the text within the post. 

The model has two strengths over similar approaches:

1. For the purpose of reducing variance on real app data, the model is trained on the modified corpus where obvious keywords words are omitted. This is to avoid the model overfitting to the obvious keywords words present in Reddit posts but **unlikely to be used in a user's journal entry**. 

2. The model leverages new features engineered from the original text (measures of verbosity, pronoun usage, and frequency of question statements). Such data is not always used in a NLP pre-processing workflow and are sometimes missed out entirely due to stop word removal.

# Limitations

1. Most glaringly, the training data may not be representative of the journal entries on the app. Reddit posts have a different tone, objective, and vocabulary from what might be written in a private journal. For example, posts on both subreddits have a high frequency of question statements, which is something that is not usually observed in a journal reflection. 

2. Biases in data collection are definitely present. The model is trained on a modified corpus of Reddit posts. According to [sources](https://www.statista.com/statistics/325144/reddit-global-active-user-distribution/#:~:text=Reddit%20use%20in%20the%20United,platform%20strongly%20declines%20with%20age.), users from the USA account for almost 47.1% of the traffic on the site, with most users between the age of 18-49 and predominantly male. This can have significant effects on overall text patterns on the site leading to the model being unable to effectively generalize on the actual app user base. 

3. Lack of a feedback loop. In this early prototype, the model does not have capabilities to learn from misclassifications. 

4. Possible poor performance on translated text and other languages. The model is trained on the text written on Reddit with mostly native English speakers.

# Possible extensions

1. More data can be collected through other social media sources like blogs, twitter, or facebook for model training. However, these sources do not come with the convenience of clear labels. Perhaps hashtags could serve that purpose for other media sources.

2. Transformer deep learning models have had great success in NLP tasks and are more likely to identify patterns in syntax, semantics, and structure. Some of these patterns could be effective in identifying philosophical inclination from text. 

## Changelog
- Si Hao Tan, 30 June 2022