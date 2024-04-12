Note: Much of the material in this chapter is expanded upon in the book *The Art of Data Science* by Peng and Matsui, which is [available from Leanpub](https://leanpub.com/artofdatascience/).

# The Data Analysis Iteration

Watch a video: [Data Analysis Iteration](https://www.youtube.com/watch?v=xOomNicqbkk) | [Stages of Data Analysis](https://www.youtube.com/watch?v=kiQ6LwefUb4)

To the uninitiated, a data analysis may appear to follow a linear, one-step-after-the-other process which at the end, arrives at a nicely packaged and coherent result.  In reality, data analysis is a highly iterative and non-linear process, better reflected by a series of epicycles (see Figure), in which information is learned at each step, which then informs whether (and how) to refine, and redo, the step that was just performed, or whether (and how) to proceed to the next step. 

An epicycle is a small circle whose center moves around the
circumference of a larger circle. In data analysis, the iterative
process that is applied to all steps of the data analysis can be
conceived of as an epicycle that is repeated for each step along the
circumference of the entire data analysis process.  Some data analyses
appear to be fixed and linear, such as algorithms embedded into
various software platforms, including apps.  However, these algorithms
are final data analysis products that have emerged from the very
non-linear work of developing and refining a data analysis so that it
can be algorithmized.

## Epicycle of Analysis

There are 5 core activities of data analysis: 

1. Stating and refining the question

2. Exploring the data

3. Building formal statistical models

4. Interpreting the results

5. Communicating the results  

These 5 activities can occur at different time scales: for example, you might go through all 5 in the course of a day, but also deal with each, for a large project, over the course of many months.  Before discussing these core activities, which will occur in later chapters, it will be important to first understand the overall framework used to approach each of these activities.

Although there are many different types of activities that you might engage in while doing data analysis, every aspect of the entire process can be approached through an interative process that we call the *epicycle of data analysis*. More specifically, for each of the five core activities, it is critical that you engage in the following steps:

1. Setting Expectations, 

2. Collecting information (data), comparing the data to your expectations, and if the expectations don’t match, 
 
3. Revising your expectations or fixing the data so your data and your expectations match. 

As you go through every stage of an analysis, you will need to go through the epicycle to continuously refine your question, your exploratory data analysis, your formal models, your interpretation, and your communication. 

The repeated cycling through each of these five core activities that is done to complete a data analysis forms the larger circle of data analysis.  In this chapter we go into detail about what this 3-step epicyclic process is and give examples of how you can apply it to your data analysis.

Developing expectations is the process of deliberately thinking about what you expect before you do anything, such as inspect your data, perform a procedure, or enter a command.  For experienced data analysts, in some circumstances, developing expectations may be an automatic, almost subconscious process, but it’s an important activity to cultivate and be deliberate about.  

For example, you may be going out to dinner with friends at a cash-only establishment and need to stop by the ATM to withdraw money before meeting up.  To make a decision about the amount of money you’re going to withdraw, you have to have developed some expectation of the cost of dinner.   This may be an automatic expectation because you dine at this establishment regularly so you know what the typical cost of a meal is there, which would be an example of *a priori* knowledge.  Another example of *a priori* knowledge would be knowing what a typical meal costs at a restaurant in your city, or knowing what a meal at the most expensive restaurants in your city costs. Using that information, you could perhaps place an upper and lower bound on how much the meal will cost.

You may have also sought out external information to develop your expectations, which could include asking your friends who will be joining you or who have eaten at the restaurant before and/or Googling the restaurant to find general cost information online or a menu with prices.   This same process, in which you use any a priori information you have and/or external sources to determine what you expect when you inspect your data or execute an analysis procedure, applies to each core activity of the data analysis process.

Collecting information entails collecting information about your question or your data.  For your question, you collect information by performing a literature search or asking experts in order to ensure that your question is a good one. In the next chapter, we will discuss characteristics of a good question.  For your data, after you have some expectations about what the result will be when you inspect your data or perform the analysis procedure, you then perform the operation. The results of that operation are the data you need to collect, and then you determine if the data you collected matches your expectations.  To extend the restaurant metaphor, when you go to the restaurant, getting the check is collecting the data.   

Now that you have data in hand (the check at the restaurant), the next step is to compare your expectations to the data.  There are two possible outcomes:  either your expectations of the cost matches the amount on the check, or they do not.  If your expectations and the data match, terrific, you can move onto the next activity.  If, on the other hand, your expectations were a cost of 30 dollars, but the check was 40 dollars, your expectations and the data do not match.  There are two possible explanations for the discordance: first, your expectations were wrong and need to be revised, or second, the check was wrong and contains an error.  You review the check and find that you were charged for two desserts instead of the one that you had, and conclude that there is an error in the data, so ask for the check to be corrected.

One key indicator of how well your data analysis is going is how easy or difficult it is to match the data you collected to your original expectations. You want to setup your expectations and your data so that matching the two up is easy. In the restaurant example, your expectation was $30 and the data said the meal cost $40, so it’s easy to see that (a) your expectation was off by $10 and that (b) the meal was more expensive than you thought. When you come back to this place, you might bring an extra $10. If our original expectation was that the meal would be between $0 and $1,000, then it’s true that our data fall into that range, but it’s not clear how much more we’ve learned. For example, would you change your behavior the next time you came back? The expectation of a $30 meal is sometimes referred to as a sharp hypothesis because it states something very specific that can be verified with the data.




# Asking the Question

Watch a video: [Characteristics of a Good Question](https://www.youtube.com/watch?v=cJYgCI4inU0) | [Types of Questions](https://www.youtube.com/watch?v=GRNyEzQ26Ww)

Doing data analysis requires quite a bit of thinking and we believe that when you’ve completed a good data analysis, you’ve spent more time thinking than doing. The thinking begins before you even look at a dataset, and it’s well worth devoting careful thought to your question.  This point cannot be over-emphasized as many of the “fatal” pitfalls of a data analysis can be avoided by expending the mental energy to get your question right.  In this chapter, we will discuss the characteristics of a good question, the types of questions that can be asked, and how to apply the iterative epicyclic process to stating and refining your question so that when you start looking at data, you have a sharp, answerable question.

## Types of Questions

Before we delve into stating the question, it's helpful to consider what the different types of questions are. There are six basic types of questions and much of the discussion that follows comes from a [paper](http://www.sciencemag.org/content/347/6228/1314.short) published in *Science* by [Roger Peng](http://www.biostat.jhsph.edu/~rpeng) and [Jeff Leek](http://jtleek.com).  Understanding the type of question you are asking may be the most fundamental step you can take to ensure that, in the end, your interpretation of the results is correct.  The six types of questions are:

1.  Descriptive
2.  Exploratory
3.  Inferential
4.  Predictive
5.  Causal
6.  Mechanistic

And the type of question you are asking directly informs how you interpret your results.

An *exploratory* question is one in which you analyze the data to see if there are patterns, trends, or relationships between variables.  These types of analyses are also called “hypothesis-generating” analyses because rather than testing a hypothesis as would be done with an inferential, causal, or mechanistic question, you are looking for patterns that would support proposing a hypothesis.  If you had a general thought that diet was linked somehow to viral illnesses, you might explore this idea by examining relationships between a range of dietary factors and viral illnesses.  You find in your exploratory analysis that individuals who ate a diet high in certain foods had fewer viral illnesses than those whose diet was not enriched for these foods, so you propose the hypothesis that among adults, eating at least 5 servings a day of fresh fruit and vegetables is associated with fewer viral illnesses per year.

An *inferential* question would be a restatement of this proposed hypothesis as a question and would be answered by analyzing a different set of data, which in this example, is a representative sample of adults in the US.  By analyzing this different set of data you are both determining if the association you observed in your exploratory analysis holds in a different sample and whether it holds in a sample that is representative of the adult US population, which would suggest that the association is applicable to all adults in the US.  In other words, you will be able to infer what is true, on average, for the adult population in the US from the analysis you perform on the representative sample.  

A *predictive* question would be one where you ask what types of people will eat a diet high in fresh fruits and vegetables during the next year.  In this type of question you are less interested in what causes someone to eat a certain diet, just what predicts whether someone will eat this certain diet.  For example, higher income may be one of the final set of predictors, and you may not know (or even care) why people with higher incomes are more likely to eat a diet high in fresh fruits and vegetables, but what is most important is that income is a factor that predicts this behavior.  
 
Although an inferential question might tell us that people who eat a certain type of foods tend to have fewer viral illnesses, the answer to this question does not tell us if eating these foods causes a reduction in the number of viral illnesses, which would be the case for a *causal* question.  A causal question asks about whether changing one factor will change another factor, on average, in a population.  Sometimes the underlying design of the data collection, by default, allows for the question that you ask to be causal.  An example of this would be data collected in the context of a randomized trial, in which people were randomly assigned to eat a diet high in fresh fruits and vegetables or one that was low in fresh fruits and vegetables.  In other instances, even if your data are not from a randomized trial, you can take an analytic approach designed to answer a causal question. 

Finally, none of the questions described so far will lead to an answer that will tell us, if the diet does, indeed, cause a reduction in the number of viral illnesses, *how* the diet leads to a reduction in the number of viral illnesses.  A question that asks how a diet high in fresh fruits and vegetables leads to a reduction in the number of viral illnesses would be a *mechanistic* question.

There are a couple of additional points about the types of questions that are important.  First, by necessity, many data analyses answer multiple types of questions. For example, if a data analysis aims to answer an inferential question, descriptive and exploratory questions must also be answered during the process of answering the inferential question.  To continue our example of diet and viral illnesses, you would not jump straight to a statistical model of the relationship between a diet high in fresh fruits and vegetables and the number of viral illnesses without having determined the frequency of this type of diet and viral illnesses and their relationship to one another in this sample.  A second point is that the type of question you ask is determined in part by the data available to you (unless you plan to conduct a study and collect the data needed to do the analysis).   For example, you may want to ask a causal question about diet and viral illnesses to know whether eating a diet high in fresh fruits and vegetables causes a decrease in the number of viral illnesses, and the best type of data to answer this causal question is one in which people’s diets change from one that is high in fresh fruits and vegetables to one that is not, or vice versa.  If this type of data set does not exist, then the best you may be able to do is either apply causal analysis methods to observational data or instead answer an inferential question about diet and viral illnesses.

# Exploratory Data Analysis

Watch a video: [EDA Part 1](https://www.youtube.com/watch?v=NvxbGsfPirE) | [EDA Part 2](https://www.youtube.com/watch?v=GXRss4EvHqU) | [EDA Part 3](https://www.youtube.com/watch?v=14-9plHpFdw) | [EDA Part 4](https://www.youtube.com/watch?v=9gJ8lSfhNrs)

Exploratory data analysis is the process of exploring your data, and it typically includes examining the structure and components of your dataset, the distributions of individual variables, and the relationships between two or more variables.  The most heavily relied upon tool for exploratory data analysis is visualizing data using a graphical representation of the data.  Data visualization is arguably the most important tool for exploratory data analysis because the information conveyed by graphical display can be very quickly absorbed and because it is generally easy to recognize patterns in a graphical display. 

There are several goals of exploratory data analysis, which are:

1. To determine if there are any problems with your dataset.

2. To determine whether the question you are asking can be answered by the data that you have.

3. To develop a sketch of the answer to your question.

Your application of exploratory data analysis will be guided by your question.  The example question used in this chapter is: "Do counties in the eastern United States have higher ozone levels than counties in the western United States?"  In this instance, you will explore the data to determine if there are problems with the dataset, and to determine if you can answer your question with this dataset.  

To answer the question of course, you need ozone, county, and US region data.  The next step is to use exploratory data analysis to begin to answer your question, which could include displaying boxplots of ozone by region of the US.  At the end of exploratory data analysis, you should have a good sense of what the answer to your question is and be armed with sufficient information to move onto the next steps of data analysis.

It's important to note that here, again, the concept of the epicycle of analysis applies.  You should have an expectation of what your dataset will look like and whether your question can be answered by the data you have.  If the content and structure of the dataset doesn't match your expectation, then you will need to go back and figure out if your expectation was correct (but there was a problem with the data) or alternatively, your expectation was incorrect, so you cannot use the dataset to answer the question and will need to find another dataset.  

You should also have some expectation of what the ozone levels will be as well as whether one region's ozone should be higher (or lower) than another's.  As you move to step 3 of beginning to answer your question, you will again apply the epicycle of analysis so that if, for example, the ozone levels in the dataset are lower than what you expected from looking at previously published data, you will need to pause and figure out if there is an issue with your data or if your expectation was incorrect.  Your expectation could be incorrect, for example, if your source of information for setting your expectation about ozone levels was data collected from 20 years ago (when levels were likely higher) or from only a single city in the U.S.  We will go into more detail with the case study below, but this should give you an overview about the approach and goals of exploratory data analysis.

In this section we will run through an informal "checklist" of things to do when embarking on an exploratory data analysis. The elements of the checklist are

1. *Formulate your question*. We have discussed the importance of properly formulating a question. Formulating a question can be a useful way to guide the exploratory data analysis process and to limit the exponential number of paths that can be taken with any sizeable dataset. In particular, a *sharp* question or hypothesis can serve as a dimension reduction tool that can eliminate variables that are not immediately relevant to the question. It's usually a good idea to spend a few minutes to figure out what is the question you're *really* interested in, and narrow it down to be as specific as possible (without becoming uninteresting).

2. *Read in your data*. This part is obvious--without data there's no analysis. Sometimes the data will come in a very messy format and you'll need to do some cleaning. Other times, someone else will have cleaned up that data for you so you'll be spared the pain of having to do the cleaning. 

3. *Check the packaging*. Assuming you don't get any warnings or errors when reading in the dataset, it's usually a good idea to poke the data a little bit before you break open the wrapping paper. For example, you should check the number of rows and columns. Often, with just a few simple maneuvers that perhaps don't qualify as real data analysis, you can nevertheless identify potential problems with the data before plunging in head first into a complicated data analysis.

5. *Look at the top and the bottom of your data*. It's often useful to look at the "beginning" and "end" of a dataset right after you check the packaging. This lets you know if the data were read in properly, things are properly formatted, and that everthing is there. If your data are time series data, then make sure the dates at the beginning and end of the dataset match what you expect the beginning and ending time period to be. Looking at the last few rows of a dataset can be particularly useful because often there will be some problem reading the end of a dataset and if you don't check that specifically you'd never know. 

6. *Check your "n"s*. In general, counting things is usually a good way to figure out if anything is wrong or not. In the simplest case, if you're expecting there to be 1,000 observations and it turns out there's only 20, you know something must have gone wrong somewhere. But there are other areas that you can check depending on your application. To do this properly, you need to identify some *landmarks* that can be used to check against your data. For example, if you are collecting data on people, such as in a survey or clinical trial, then you should know how many people there are in your study.

7. *Validate with at least one external data source*. Making sure your data matches something outside of the dataset is very important. It allows you to ensure that the measurements are roughly in line with what they should be and it serves as a check on what *other* things might be wrong in your dataset. External validation can often be as simple as checking your data against a single number.

7. *Make a plot*. Making a plot to visualize your data is a good way to further your understanding of your question and your data. There are two key reasons for making a plot of your data. They are *creating expectations* and *checking deviations from expectations*. At the early stages of analysis, you may be equipped with a question/hypothesis, but you may have little sense of what is going on in the data. You may have peeked at some of it for sake of doing some sanity checks, but if your dataset is big enough, it will be difficult to simply look at all the data. Making some sort of plot, which serves as a summary, will be a useful tool for *setting expectations for what the data should look like*. Making a plot can also be a useful tool to see how well the data match your expectations. Plots are particularly good at letting you see *deviations* from what you might expect. Tables typically are good at *summarizing* data by presenting things like means, medians, or other statistics. Plots, however, can show you those things, as well as show you things that are far from the mean or median, so you can check to see if something is *supposed* to be that far away. Often, what is obvious in a plot can be hidden away in a table.

8. *Try the easy solution first*. What's the simplest answer you could provide to answer your question? For the moment, don't worry about whether the answer is 100% correct, but the point is how could you provide *prima facie* evidence for your hypothesis or question. You may refute that evidence later with deeper analysis, but this is the first pass. Importantly, if you do not find evidence of a signal in the data using just a simple plot or analysis, then often it is unlikely that you will find something using a more sophisticated analysis. 

In this section we've presented some simple steps to take when starting off on an exploratory analysis. The point of this is to get you thinking about the data and the question of interest. It should also give you a number of things to follow up on in case you continue to be interested in this question. At this point it's useful to consider a few followup questions.

1. *Do you have the right data?* Sometimes at the conclusion of an exploratory data analysis, the conclusion is that the dataset is not really appropriate for this question. In that case you may need to go and get completely different data for your question.
2. *Do you need other data?* Sometimes you need to go out and get more data in order to make a stronger argument or to check your preliminary findings.
3. *Do you have the right question?* After looking at the data, is it clear that the question you tried to answer has immediate relevance. It may be more important to refine your question a bit or focus on something different. However, it the data appear appropriate for your question you can press on to the subsequent stages of the process.

# Modeling

Watch a video: [Framework](https://www.youtube.com/watch?v=rb4vzF5NhQc) | [Associational Analyses](https://www.youtube.com/watch?v=vzXiLld8kZI) | [Prediction](https://www.youtube.com/watch?v=RVl1W3Fc4xs)

## What Are the Goals of Formal Modeling?

One key goal of formal modeling is to develop a precise specification of your question and how your data can be used to answer that question. Formal models allow you to identify clearly what you are trying to infer from data and what form the relationships between features of the population take. It can be difficult to achieve this kind of precision using words alone.

Parameters play an important role in many formal statistical models (in statistical language, these are known as *parametric statistical models*). These are numbers that we use to represent features or associations that exist in the population. Because they represent population features, parameters are generally considered unknown, and our goal is to estimate them from the data we collect. 

For example, suppose we want to assess the relationship between the number of ounces of soda consumed by a person per day and that person's BMI. The slope of a line that you might plot visualizing this relationship is the parameter you want to estimate to answer your question: "How much would BMI be expected to increase per each additional ounce of soda consumed?" More specifically, you are using a *linear regression model* to formulate this problem.

Another goal of formal modeling is to develop a rigorous framework with which you can challenge and test your primary results. At this point in your data analysis, you've stated and refined your question, you've explored the data visually and maybe conducted some exploratory modeling. The key thing is that you likely have a pretty good sense of what the answer to your question is, but maybe have some doubts about whether your findings will hold up under intense scrutiny. Assuming you are still interested in moving forward with your results, this is where formal modeling can play an important role.

We can apply the basic epicycle of analysis to the formal modeling portion of data analysis. We still want to set expectations, collect information, and refine our expectations based on the data. In this setting, these three phases look as follows.

1. **Setting expectations**. Setting expectations comes in the form of developing a *primary model* that represents your best sense of what provides the answer to your question. This model is chosen based on whatever information you have currently available.

2. **Collecting Information**. Once the primary model is set, we will want to create a set of secondary models that challenge the primary model in some way. We will discuss examples of what this means below.

3. **Revising expectations**. If our secondary models are successful in challenging our primary model and put the primary model's conclusions in some doubt, then we may need to adjust or modify the primary model to better reflect what we have learned from the secondary models.

It's often useful to start with a *primary model*. This model will likely be derived from any exploratory analyses that you have already conducted and will serve as the lead candidate for something that succinctly summarizes your results and matches your expectations. It's important to realize that at any given moment in a data analysis, the primary model is *not necessarily the final model*. It is simply the model against which you will compare other secondary models. The process of comparing your model to other secondary models is often referred to as *sensitivity analyses*, because you are interested in seeing how sensitive your model is to changes, such as adding or deleting predictors or removing outliers in the data. 

Through the iterative process of formal modeling, you may decide that a different model is better suited as the primary model. This is okay, and is all part of the process of setting expectations, collecting information, and refining expectations based on the data. 

Once you have decided on a primary model, you will then typically develop a series of secondary models. The purpose of these models is to test the legitimacy and robustness of your primary model and potentially generate evidence against your primary model. If the secondary models are successful in generating evidence that refutes the conclusions of your primary model, then you may need to revisit the primary model and whether its conclusions are still reasonable.


## Associational Analyses

Associational analyses are ones where we are looking at an association between two or more features in the presence of other potentially confounding factors. There are three classes of variables that are important to think about in an associational analysis.

1. **Outcome**. The outcome is the feature of your dataset that is thought to change along with your **key predictor**. Even if you are not asking a causal or mechanistic question, so you don't necessarily believe that the outcome *responds* to changes in the key predictor, an outcome still needs to be defined for most formal modeling approaches.

2. **Key predictor**. Often for associational analyses there is one key predictor of interest (there may be a few of them). We want to know how the outcome changes with this key predictor. However, our understanding of that relationship may be challenged by the presence of potential confounders.

3. **Potential confounders**. This is a large class of predictors that are both related to the key predictor and the outcome. It's important to have a good understanding what these are and whether they are available in your dataset. If a key confounder is not available in the dataset, sometimes there will be a proxy that is related to that key confounder that can be substituted instead.

Once you have identified these three classes of variables in your dataset, you can start to think about formal modeling in an associational setting.

This is a linear model is a common approach to quantifying the relationship between the key predictor and the outcome while adjusting for any potential confounders. In many cases linear model can be used as the primary model (or at least as a reasonable approximation). Typically you would include the key predictor and one or a few confounders in the model where it is perhaps well known that you should adjust for those confounders. This model may produce sensible results and follows what is generally known in the area. 

Secondary models for associational analyses will typically include more or more complex confounder information. Often this is because we do not know for sure whether we actually observe all of the factors that potentially confound the relationship between our outcome and key predictor. Therefore, it's sometimes helpful to include a number of additional factors tha ttest whether our primary association is very sensitive to the inclusion of those factors.

Determining where to go from here may depend on factors outside of the dataset. Some typical considerations are

1. *Effect size*.  Different models may present a range of estimates. Is this a large range? It's possible that for your organization a range of this magnitude is not large enough to really make a difference and so all of the models might be considered equivalent. Or you might consider the different estimates to be significantly different from each other, in which case you might put more weight on one model over another. Another factor might be cost, in which case you would be interested in the return on your investment for whatever decision you plan to make based on this analysis.

2. *Plausibility*. Although you may fit a series of models for the purposes of challenging your primary model, it may be the case that some models are more plausible than others, in terms of being close to whatever the "truth" about the population is. Whether a model could be considered more or less plausible will depend on your knowledge of the subject matter and your ability to map real-world events to the mathematical formulation of the model. You may need to consult with other experts in this area to assess the plausibility of various models. 

3. *Parsimony*. In the case where the different models all tell the same story it's often preferable to choose the model that is simplest. There are two reasons for this. First, with a simpler model it can be easier to tell a story about what is going on in the data via the various parameters in the model. For example, it's easier to explain a linear trend than it is to explain an exponential trend. Second, simpler models, from a statistical perspective, are more "efficient", so that they make better use of the data per parameter that is being estimated. Complexity in a statistical model generally refers to the number of parameters in the model. If the primary and secondary models produce significant differences, then you still might choose a parsimonious model over a more complex model, but not if the more complex model tells a more compelling story. 



## Prediction Analyses

In the previous section we described associational analyses, where the goal is to see if a key predictor and an outcome are associated. But sometimes the goal is to use all of the information available to you to predict the outcome.  Furthermore, it doesn't matter if the variables would be considered unrelated in a causal way to the outcome you want to predict because the objective is prediction, not developing an understanding about the relationships between features.

With prediction models, we have outcome variables--features about which we would like to make predictions--but we typically do not make a distinction between "key predictors" and other predictors. In most cases, any predictor that might be of use in predicting the outcome would be considered in an analysis and might, *a priori*, be given equal weight in terms of its importance in predicting the outcome. Prediction analyses will often leave it to the prediction algorithm to determine the importance of each predictor and to determine the functional form of the model.

For many prediction analyses it is not possible to literally write down the model that is being used to predict because it cannot be represented using standard mathematical notation. Many modern prediction routines are structured as algorithms or procedures that take inputs and transform them into outputs. The path that the inputs take to be transformed into outputs may be highly nonlinear and predictors may interact with other predictors on the way. Typically, there are no parameters of interest that we try to estimate--in fact many algorithmic procedures do not have any estimable parameters at all.

The key thing to remember with prediction analyses is that we usually do not care about the specific details of the model. In most cases, as long as the method "works", is reproducible, and produces good predictions with minimal error, then we have achieved our goals.

For prediction problems, deciding on the next step after initial model fitting can depend on a few factors.

1. *Prediction quality*. Is the model's accuracy good enough for your purposes? This depends on the ultimate goal and the risks associated with subsequent actions. For medical applications, where the outcome might be the presence of a disease, we may want to have a high sensitivity, so that if you genuinely have the disease, the algorithm will detect it. That way we can get you into treatment quickly. However, if the treatment is very painful, perhaps with many side effects, then we might actually prefer a high specificity, which would ensure that we don't mistakenly treat someone who *doesn't* have the disease. For financial applications, like the credit worthiness example used here, there may be asymmetric costs associated with mistaking good credit for bad versus mistaking bad credit for good.

2. *Model tuning*. A hallmark of prediction algorithms is their many tuning parameters. Sometimes these parameters can have large effects on prediction quality if they are changed and so it is important to be informed of the impact of tuning parameters for whatever algorithm you use. There is no prediction algorithm for which a single set of tuning parameters works well for all problems. Most likely, for the initial model fit, you will use "default" parameters, but these defaults may not be sufficient for your purposes. Fiddling with the tuning parameters may greatly change the quality of your predictions. It's very important that you document the values of these tuning parameters so that the analysis can be reproduced in the future. 

3. *Availability of Other Data*. Many prediction algorithms are quite good at exploring the structure of large and complex datasets and identifying a structure that can best predict your outcome. If you find that your model is not working well, even after some adjustment of tuning parameters, it is likely that you need additional data to improve your prediction. 

Formal modeling is typically the most technical aspect of data analysis, and its purpose is to precisely lay out what is the goal of the analysis and to provide a rigorous framework for challenging your findings and for testing your assumptions. The approach that you take can vary depending primarily on whether your question is fundamentally about estimating an association develoing a good prediction. 



# Interpretation

Watch a video: [Interpretation](https://www.youtube.com/watch?v=JKP-yVcL_Y4≈)

There are several principles of interpreting results that we will illustrate in this chapter.  These principles are: 

1. *Revisit your original question*. This may seem like a flippant statement, but it is not uncommon for people to lose their way as they go through the process of exploratory analysis and formal modeling.  This typically happens when a data analyst wanders too far off course pursuing an incidental finding that appears in the process of exploratory data analysis or formal modeling.  Then the final model(s) provide an answer to another question that popped up during the analyses rather than the original question. Revisiting your question also provides a framework for interpreting your results because you can remind yourself of the type of question that you asked.

2. Start with the primary statistical model to get your bearings and focus on the nature of the result rather than on a binary assessment of the result (e.g. statistically significant or not). The nature of the result includes three characteristics: its directionality, magnitude, and uncertainty.  Uncertainty is an assessment of how likely the result was obtained by chance.  eting your results will be missed if you zoom in on a single feature of your result, so that you either ignore or gloss over other important information provided by the model. Although your interpretation isn't complete until you consider the results in totality, it is often most helpful to first focus on interpreting the results of the model that you believe best answers your question and reflects (or "fits") your data, which is your primary model.  Don't spend a lot of time worrying about which single model to start with, because in the end you will consider all of your results and this initial interpretation exercise serves to orient you and provide a framework for your final interpretation.

3. *Develop an overall interpretation* based on (a) the totality of your analysis and (b) the context of what is already known about the subject matter.  The interpretation of the results from your primary model serves to set the expectation for your overall interpretation when you consider all of your analyses. Recall that this primary model was constructed after gathering information through exploratory analyses and that you may have refined this model when you were going through the process of interpreting its results by evaluating the directionality, magnitude and uncertainty of the model's results. External information is both general knowledge that you or your team members have about the topic, results from similar analyses, and information about the target population. 

4. Consider the implications, which will guide you in determining what action(s), if any, should be taken as a result of the answer to your question. After all, the point of doing an analysis is usually to inform a decision or to take an action.  Sometimes the implications are straightforward, but other times the implications take some thought.  An example of a straightforward implication is if you performed an analysis to determine if purchasing ads increased sales, and if so, did the investment in ads result in a net profit.  You may learn that either there was a net profit or not, and if there were a net profit, this finding would support continuing the ads.  




# Communication

Watch a video: [Routine Communication](https://www.youtube.com/watch?v=IcrqPxH9rVk) | [Presentations](https://www.youtube.com/watch?v=vHZhKTqTsiE)

Communication is fundamental to good data analysis. Data analysis is an inherently verbal process that requires constant discussion. What we aim to address in this chapter is the role of routine communication in the process of doing your data analysis and in disseminating your final results in a more formal setting, often to an external, larger audience.  There are lots of good books that address the "how-to" of giving formal presentations, either in the form of a talk or a written piece, such as a white paper or scientific paper.  In this section we will focus on how to use routine communication as one of the tools needed to perform a good data analysis how to convey the key points of your data analysis when communicating informally and formally.  

Communication is both one of the tools of data analysis, and also the final product of data analysis: there is no point in doing a data analysis if you're not going to communicate your process and results to an audience. A good data analyst communicates informally multiple times during the data analysis process and also gives careful thought to communicating the final results so that the analysis is as useful and informative as possible to the wider audience it was intended for.

The main purpose of routine communication is to gather data, which is part of the epicyclic process for each core activity.  You gather data by communicating your results and the responses you receive from your audience should inform the next steps in your data analysis.  The types of responses you receive include not only answers to specific questions, but also commentary and questions your audience has in response to your report (either written or oral). The form that your routine communication takes depends on what the goal of the communication is. If your goal, for example, is to get clarity on how a variable is coded because when you explore the dataset it appears to be an ordinal variable, but you had understood that it was a continous variable, your communication is brief and to the point.  

If, on the other hand, some results from your exploratory data analysis are not what you expected, your communication may take the form of a small, informal meeting that includes displaying tables and/or figures pertinent to your issue.  A third type of informal communication is one in which you may not have specific questions to ask of your audience, but instead are seeking feedback on the data analysis process and/or results to help you refine the process and/or to inform your next steps.  

In sum, there are three main types of informal communication and they are classified based on the objectives you have for the communication: (1) to answer a very focused question, which is often a technical question or a question aimed at gathering a fact, (2) to help you work through some results that are puzzling or not quite what you expected, and (3) to get general impressions and feedback as a means of identifying issues that had not occurred to you so that you can refine your data analysis. 

Focusing on a few core concepts will help you achieve your objectives when planning routine communication.  These concepts are:

1. **Audience**: Know your audience and when you have control over who the audience is, select the right audience for the kind of feedback you are looking for.  In some cases, such as when you are delivering an interim report to your boss or your team, the audience may be pre-determined. Your audience may be composed of other data analysts, the individual(s) who initiated the question, your boss and/or other managers or executive team members, non-data analysts who are content experts, and/or someone representing the general public.  

2. **Content**: Be focused and concise, but provide sufficient information for the audience to understand the information you are presenting and question(s) you are asking.

3. **Style**: Avoid jargon. Unless you are communicating about a focused highly technical issue to a highly technical audience, it is best to use language and figures and tables that can be understood by a more general audience. 

4. **Attitude**: Have an open, collaborative attitude so that you are ready to fully engage in a dialogue and so that your audience gets the message that your goal is not to "defend" your question or work, but rather to get their input so that you can do your best work.
