If you want a condensed and fun version of this Part, you can watch this [short cartoon](https://www.youtube.com/watch?v=9BIYmw5wnBI&list=PLpl-gQkQivXjFkaLGmWRKYs4KUgCzmSxv).

# What You've Gotten Yourself Into

Have you ever had the perfect data science experiment?
In the perfect data science experiment,

1.  You have clearly defined hypotheses that are specified a priori.
2. You're able to carefully design the experiment.  For example, you can use randomization
across the treatment of interest and
you are aware of, can measure and can block on important confounding variables.
3. Your sample is a random sample from a population of interests so
you know that your results will be generalizable.
4. The data that you have are directly
able to interrogate the hypothesis that you're interested in.
5.  All the data set creation and merging and data pulls from the larger data set goes smoothly.
6. There's no missing data or dropout.
7. Your analyses are robust without the need for any sort of advance modeling.
8. Your conclusions are clear and parsimonious of knowledge is gained via the experiment.
9. The decision is obvious given the data and analysis.
10. The results are communicated clearly with a nice report or data product.

Has this ever happened in real life? Probably not. (Certainly not to your authors.)
In real life, often the data is needed to both inform the
hypotheses and interrogate the hypotheses. Multiple comparisons are an issue
because you've tried several different hypotheses or
you're looking at multiple things at once.

Your access to experimental design is limited or nonexistent and you must
take what you can get.  The data is often completely observational with nothing
intervened on or randomized.  Take, for example, studying a behavior like smoking
or a trait, like height. Your ability to randomize or on intervene on these factors
is either not ethical or not possible.

In the terms of generalizability, the population being studied rarely is
the population that you're actually interested in. In clinical trials, for example,
professional "Guinea pigs" (people who frequently get paid to participate as subjects in clinical trials) are often the sample.
These folks have good adherence to treatments, stay in the study the whole time and
have a whole host of other behaviors unlike the real population.[^f1]

[^f1]: See this article [http://www.newyorker.com/magazine/2008/01/07/guinea-pigging](http://www.newyorker.com/magazine/2008/01/07/guinea-pigging)

The data often don't have the exact measurements
that you need to evaluate the hypothesis.
For example, in nutrition, it's often of interest to study caloric intake.
However, instead all you have are so called food frequency questionnaires
where you ask people how many calories they ate last week.

Another issue arises when the data set itself is problematic. For example,
 merging has multiple matches, when matching should be unique or there
 are missing matches when every record should have a match.
There can be data entry errors or errors in pulling the data from its
original source. In short, the reality of building the analytic
data set is a challenging process.

A frequent problem with experimental and observational
data is missingness, which often requires advanced modeling
to address. And then because you need advanced
modeling, advanced computing is needed to
fit the model, which raises
issues with robustness and bugs.

When you're all done with this messy process,
often your conclusions wind up
being indeterminate and the decision is not substantially
further informed by the data and
the models that you've fit.

Maybe all of these things don't happen at once, but
at least some of them or others do in most data science experiments.


Let's go through some examples of these problems that we've seen recently.

## Data double duty

As an example, our colleagues wrote
this wonderful paper about, exactly about the issue of using your
data to come up with your hypotheses. They work in the area
of multiple sclerosis (MS). A common problem in the area of
MS brain research with magnetic resonance imaging is actually defining what it means for
a lesion to be so-called "enhancing", which is an imaging indicator of a progessively
worsening lesion. However, there was no clear way to quantitatively define a
lesion as enhancing and they were usually diagnosed by having a radiologist look at it.
They put forward a framework that
both quantitatively identified the hypotheses and interrogated the hypotheses
with the same data set. Such analyses are tremendously
prone to errors of getting biased results comparing the hypotheses. Since
they're statistical researchers so their emphasis was on doing
this in a rigorous fashion to avoid such errors. However, it's an example
of a setting where the hypotheses wasn't specified ahead of time and
the data had to perform double duty where a great deal of sophistication
is necessary to avoid spurious conclusions.  

## Multiplicity

 Multiple comparisons. Since we're on the subject
of brain imaging, which is the area that I work on,
multiple comparisons is often an issue. And in one particularly famous example,
some people put a dead salmon in an fMRI machine
to detect brain activation. Of course, there's no brain
activation in a dead salmon. What they've found is that if you
do lots and lots and lots of tests, and you don't account for that correctly, you
can see brain activation in a dead salmon.

## Randomization versus observational studies

A very famous example of randomization
was from the Women's Health Initiative. The Women's Health initiative
conducted a study, a randomized trial of
hormone replacement therapy, which at the time, was a fairly standard
treatment for post menopausal women. The results of these randomized trials
contradicted what was thought of as common knowledge for the advocacy of hormone
replacement therapy and the safety of it. And so it brought about a lot of
soul searching about the value of a randomized trial versus the value
of a lot of observational data. And I think it's maybe not necessary
to go into the weeds of this study for the purposes of this chapter. However, suffice it to say, the randomized
trial carried a lot of weight with it because of the randomization. All the previous observational trials
where they just saw whether or not women were on hormone replacement
therapy and watched them over time. The multitude of those studies
was not deemed as rigorous as the one study that had
randomization where women were actually randomized to hormone
replacement therapy or not. And as a side note, if you're interested about reading
up on hormone replacement therapy. I put a website here from
the Women's Health Initiative where you can actually go and
look on the frequently asked questions relating to some of
the studies that have done since then. There's been a decade of
work since then that further refine the science on
this particular issue. The main point for
this lecture is the importance, how important randomization was
in this particular setting.


In this chapter, we'll contrast data
science in the ideal versus data science
in real life. We'll discuss
different variations
of experimental design versus
observational studies and how you can
 check for errant data and
other tools to make data analysis in
real life a little bit more manageable.

# The Data Pull is Clean

[Lecture slides](https://docs.google.com/presentation/d/106TF1VtIrS3Ze09_9kgPZY14vPrc9wlMNg9E5XWVDo4/edit?usp=sharing)

In real life, data can be very messy. In this chapter, when we talk about the data pull,
we're talking about all the different components that go into going from raw
data into an analytic data set. In this process, several intermediate
steps are required.

First, one typically has to arrange
the analytic data set from a larger more complex data source (data pull).
In addition, it is often required to merge disparate sorts
of data, resulting in matching errors. For example, in a analysis that I (Brian)
worked on, I had to connect insurance claims with individual data. There were
claims with no matching individual, individuals with no claims, and presumably mismatches
of other sorts. Presumably there were also errant claim IDs that resulted
in apparent correct matches with indidividuals, with no fullproof way to diagnose
such matching errors.


Another frequent issue in creating an analytic data set is in summarizing complex data
types. For example, you might have recorded voice data or text data that you
need to convert into meaningful summaries. In the area that I work in,
interest lies in large, complex, brain imaging data. Summarizing those down
into a handful of numbers that represent
certain regions of the brain is a complex process that is frought with errors
and complexities.

Another very common problem is going
from data that is convenient for one purpose into a convenient form for
analysis. In other words, the way we
might store the data for archival purposes is generally not
what's right for analysis purposes. This can be as simple as compressed data, but
is often more complicated. The brain imaging data mentioned earlier
is often stored in 3D or 4D (fourth dimension
being time) arrays, which typically not the best format for analysis. Other examples include:
language data being converted into n-grams, fine scale (minute, second, nanosecond)
stock values converted into
coarser (daily or monthly) values and so on. This process of converting often introduces errors
or unanticipated loss of information.

As a manager, you're probably not
going to actually execute any of the necessary coding. Maybe you did that in your past, but
now you're managing groups of people or individuals that are doing this for you.
While there's tons of generic tools to protect coders from errors, there aren't that many
tools to help managers help the people they're managing.
So we give
some simple tools that can help ensure data quality in real life.

The first thing worth mentioning is the
simple act of creating what I like to call Table 1. Table 1. is basically
a summary table of interest and, surprisingly, these are a great way to catch errors.
The phrase Table 1. comes from scientific papers where the first table is almost always
just a summary table of demographics and basic information.


These basic summary tables are a great way to catch errors. A group of people with fresh eyes
thinking high level about basic summaries spot odd things that easily get lost for the analyst
that is neck deep in the weeds of data analysis.
An important consideration is to get standard deviations along with means,
medians and quantiles.  Also refer back to old tables as you meet with your team
recurrently. Jumps in
quantities that should be stable are a great way to catch data errors.
Another important one is to check your units. By this, I mean your scientific
units (inches, pounds, hits). It's a good habit to attach units to everything and actively
discuss the units.
As an example, if you have errant data that would suggest too many clicks per second,
but everyone assumes the data are in clicks per minute, an obvious
error might go unnoticed. Force the discussion by requiring units to be explicit.


After you've done some
regression modeling, regression diagnostics are an extremely
useful way to detect data errors. My favorite examples of regression
diagnostics are from Len Stefansky from North Carolina State. He
creates data for students
where scatter plots appear normal, but residual plots show
interesting pictures, like Homer Simpson or text that says "check your residuals".
This is his way of showing
how residual plots can highlight hidden systematic patterns in our data.
[http://www4.stat.ncsu.edu/~stefanski/NSF_Supported/Hidden_Images/stat_res_plots.html](See more examples here.)

Of course, residual plots are only useful
after you've done your modeling. Given that this is the case, there's
a few other regression diagnostics you might consider. We'll give
some basic definitions:

**Residuals** are the difference between the response (the outcome that you're studying)
and the fitted value (what your model predicts it would be).
When looking at residuals make sure that there aren't any systematic
patterns or extremely large values that are well outside
the general pattern.

**hat values** or **hat diagonals**, and they consider how variable a data row of explanatory variable is
among its space of fellow predictors. So hat values help you
tell how outside of the normal range of variability,
this particular row of data is.

**dffits**, **dfbetas**, and **Cook's distance** are all related statistical measures.
These measures all compare some aspect of the model from the
fit the model with a point deleted and the model
with that point included.  For example, if you compare the fitted values with the data point
deleted and included in the fit, you get the dffits. If you compare the slope estimates then
you get what are called the dfbetas. If you compare the slope estimates
aggregated into one single number, one single metric
called Cook's distance (named after its inventor).
All of these are influence measures. They're trying to do is tell
you how much did things change when a data
row is deleted from model fitting.
They're almost always introduced primarily for considering model fit.
However, not only do they help you evaluate
things about your regression model, they also help you perform data quality control.

Another fascinating way to consider data quality is Benford's law. This is a
phenomenological law about leading digits. It can sometimes help with data
entry errors. For example, if those doing the data entry like to systematically
round down when they shouldn't.

The final thing you might want to
try is actually checking specific rows of your data through so-called
data quality queries, DQQs. Of course you can't check every single
point; however, you can check some. And you can use statistical procedures,
like random sampling, to get a random sample of rows of your data, check those
rows individually. Because it's a nice random sample, you can get an estimate of
the proportion of bad rows in your data.

# The Experiment is Carefully Designed: Principles

Lecture notes for this chapter:

* [Introductory video](https://docs.google.com/presentation/d/16CTB8spdjaz3xy4PZ7cvB4f28XKNduvANuesITypvbU/edit?usp=sharing)
* [Causality](https://docs.google.com/presentation/d/1DqxwVDvV5JRdzlGdEB9FKcK2UnZ9j1YANlgxwVbCbV8/edit?usp=sharing)

In this chapter consider the difference between statistically designed and observational studies.

An experimentally designed study is the case where you have tight control over several aspects of the experiment.
Good experimental design can do things like account for known important factors through things like blocking and
stratification.
In addition, it can account for unknown confounding factors through randomization.
Experimental design can help in the terms of bias by random sampling.
If you execute good experimental design and everything goes well, often it eliminates
the need for complex analyses. Simple analysis usually suffice, and are better in these settings.
Carfully designed experiments help us isolate the effects of interest.

More often we have an observational experiment. This is the opposite setting, where you don't have tight control
over the experiment or sample. In an observational experiment,  
you're collecting it as or after it occurs without interventions. This has some benefits as well.
For example, it's often feasible when designed experiments are not. You can't, for example,
ethically randomize people in a study of smoking behaviors.
In addition, observational studies often have very large sample sizes since passive monitoring or
retrospective  data collection is typically much cheaper than active intervention.

On the negative side, in order to get things out of observational data analysis,
you often need much more complex modeling and assumptions, because you haven't been able to do things,
like control for known important factors as part of the design.
Thus, it's almost always the case that an observational study needs larger sample sizes to accommodate
the much more complex analysis that you have to do to study them.

In the next few sections, we'll cover some of the key aspects and considerations of designed and
observational experiments.


## Causality

"Correlation isn't causation" is one of the most famous phrases about statistics. However, why
collect the data or do the study if we can never figure out cause? For most people, the
combination of iterating over the empirical evidence, the scientific basis, face validity
and the assumptions evetually establishes causality. Relatively recent efforts from
statisticians, economists, epidemiologists and others have formalized this process quite a bit.
One aspect is that good experimental design can get us closer to a causal interpretation
with fewer assumptions.

However, to make any headway on this problem, we have to define causation, which we will do
with so-called counterfactuals.
The philosopher David Hume codified this way of thinking about causality, which is the only one we
consider in this book. There are many others.

In a statistical sense, a **counterfactual** is an outcome that would have occurred a
different set of conditions than actually happened (i.e. counter to the facts of what
actually occurred). For example, if a subject receives an experimental medication, their
counterfactual would be their outcome had they not received the treatment, with all
else being held the same. For a subject that didn't receive the treatment, the counterfactual
would be the their outcome had they received it. The counterfactual difference (also
often just referred to as the counterfactual) is the difference between the two.
In our example, it's the difference between the outcome that was observed and
the outcome that would have been observed if the subject received the opposite treatment.

This difference define the counterfactual causal effect of the treatment on a subject:
the change in the outcome from the treatment that the subject actually received and what
would've occurred had she or he received the other treatment.

Thus our causal effect requires something observe with something we *cannot* observe.

Let's go through a conceptual example. Just to frame an example that everyone would have
familiarity with, let's discuss an exercise regimen. In the video lectures, I consider
a silly exercise called the Twist and Tone. A person can
only either be using the Twist and Tone or not.
Let's assume that the outcome of interest
was weight loss. The causal effect would be difference in weight loss or gain between
from the subject using the Twist and Tone program to not using it, with all else
being the same.

We cannot observe, at the same time, a person who has both used the Twist and Tone
and not used the Twist and Tone. We could, however, look at a person before they used
it, then afterwards. This would not be at the same time and any effect we saw could be
aliased with time. For example, if the subject was measured before the holidays not
using the Twist and Tone, the counterfactual difference in weight gain/loss could just be
due to holiday weight gain. We'll come back to designs like this later. Suffice it to
say that we can't actually get at the causal effect for an individual, without untestable and unreasonable
assumptions.  However we can get at, we can estimate the average causal effect, the average of
counterfactual differences across individuals, under some reasonable assumptions under certain study designs.

The average causal effect (ACE) isn't itself a counterfactual difference, it's an estimate of the
average of counterfactual differences obtained when you only get to see subjects under one
treatment. The simplest way to obtain this estimate is with randomziation. So, for example,
if we were to randomize the Twist and Tone to half of our subjects and a control regimen to
the other half, the average difference in weight loss would be thought of as the ACE.

You can think of the ACE as a "policy effect". It estimates what the impact of enacting the
Twist and Tone exercise regimen as a matter of policy across subjects similar to the ones in our study would be.
It does not say that the Twist and Tone will have a good counterfactual difference for every
subject. In other words, causal thinking in this way is not "mechanistic thinking". If you
want to understand mechanisms, you have to take a different approach. However, thinking
causally this way is incredibly useful for fields like public health, where many of the issues
are policies. For example: "Would the hosptial infection rate decline after the introduction of a hand
washing program?", "Would childhood obesity decline if laws were enacted to prevent soda beverage
machines in lunchrooms?", "Would heart attacks decline if indoor smoking bans were enacted?".

There are some important considerations when thinking about causality. Use of randomization
is the best way to get at the ACE. However, generalizability is separate issue. Even with randomization,
if your subjects are fundamentally different than the ones you'd like to generalize to, your
ACE estimator isn't very useful. We'll talk more about this in the bias section.

Another consideration is that your treatment has to be conceptually assignable to think about
causal inference in this way. For example, your eye color isn't assignable (can't be randomized).
The treatments have to be stable in the sense that a subject's treatment status doesn't impact
another's outcome. You can think of things like vaccine trials and transmission where this would
fail to be true.

A final consideration. Without explicit randomization,
one must make more assumptions to estimate the ACE that are beyond the scope of this book.
Students interested in causal inference should consider reading one of the many introductory
books devoted to the topic.


**Crossover trials**

For example, consider crossover trials. In these experiments, a subject is given a treatment, then
there's a washout period, then they're given the control (or vice versa). Usually which they receive
first is randomized. What assumptions would be necessary for the subject differences to look like a
counterfactual difference? Would this design work for a trial of teaching methods? Would it
work for a headache medication? Try to think about these questions now with some of the causal
ideas in mind!

**Natural experiments**

Let's consider another way of analyzing and thinking about analysis using natural experiments.
Again, I'd like you to use your new knowledge of thinking in the terms of causal effects when
thinking about these kinds of analyses.

A great example of natural experiments is where smoking bans were enacted.
You can't randomize smoking status to see whether smoking is a causal factor
in heart attacks.  What you can look at are places that put in smoking bans before and after the ban went
into effect and look at hosptialization records for heart attacs at the same times. However,
if that same election cycle had other policies that also impacted things, those other policies could
also be the cause of whatever decline in cardiac issues that you saw from your hospital records. The
same can be said for anything else that is similarly aliased with timing of the bans.

Naturalized natural experiments study the impact of an external manipulation, like a ban going into effect,
to try to get at causality, with a lot of assumptions.

**Matching**

Matching is this idea of finding dopplegangers.  
If I have a collection of subjects that received the treatment, for each one
I find a control subjects who is very close in every other respect (dopplegangers). Then I analyze these
pairs of dopplegangers.
This is very commonly done in medical studies. A classic example is lung cancer studies of smoking.
If you have historical smoking status and other information
of a collection of subjects who were diagnosed with lung cancer, you could find a set of similar
in all relevant aspects subjects without lung cancer then comparing the smoking rates between the groups.
Hopefully, you see how the matching connects to our idea of trying to get at counterfactual differences
and how looking backward is certainly going to be a lot easier than following smokers up for decades
to see if they eventually get cancer.f
Hopefully you also see the many flaws in this study design. A big one is the issue that you may have
forgotten to match on an important variable, or matched on one that was unimportant, but highly correlated
with smoking status. The retrospective design has issues as well, such as with generalizability and
the necessary assumptions.

Randomization is our best tool for finding average causal effects.
We'll discuss more in the lecture on randomization in AB testing.
So what are some other examples of things we can do when don't have randomization?
Perhaps the most common way is to use some sort of modeling. Methods such
as propensity scores and others rely on developing accurate models of
treatment assignment. Others, like natural experiments and instrumental variables
require a degree of luck and cleverness that doesn't lend itself well to
general application. However, every method will come with its
assumptions and limitations. The modern study of causal inference focuses
on elucidating the assumptions and limitations and making as robust inferences
as possible.  I hope that this chapter has inspired enough of an interest in causal inference ideas
for further reading and hopefully use in your data science management.

## Confounding

One aspect of analysis is so persistent that it deserves repeated mention throughout this chapter
and that is of confounding. If you want a simple rule to remember confounding by it's this:
*The apparent relationship or lack of relationship between A and B may be due to their joint
relationship with C*. Many examples of controversial or hotly argued statistical relationships boil down to
this statement. To mention some famous ones:
*The apparent relationship between lung cancer and smoking may be due to their
joint relationship in genetics* (a historically famous example). *The apparent relationship between
man made carbon emissions and global average temperature is due to their joint relationship with
natural carbon emissions.* *The apparent relationship between the race of murder trial defendants
and a death penalty sentence is due to their joint relationship with the race of the victims*.

Let's go through a simple exam that Jeff concocted just to illustrate the principle of confounding.
Here we see a picture of Jeff playing with his son. Jeff points out that he has big shoes,
and he's literate. His son has little shoes and is not literate. If you were to collect a large
dataset of fathers and sons, you would find the relationship was statistically significant.
Of course, we would all agree that the confounding variable in this case is age. In other words,
*the apparent relationship between literacy and shoe size is due to their joint relationship with
age*.


Addressing known confounders is at least conceptually easy.
For example, if one were to account for age in the analysis, such as looking within age groups,
you would find no apparent relationship between shoe size and literacy rate. However, common issues are
the existence of too many confounders to address or
unobserved or unknown confounders that should be addressed.

One can also adress confounders at the design phase. We'll discuss this more in the next section on
A/B testing.

# The Experiment is Carefully Designed: Things to Do

Lecture ntoes for this section:

* [A/B Testing](https://docs.google.com/presentation/d/1sdFDud2Wrv8PmmY2_XDknkg1tgvpheNMD_9Old9IA8c/edit?usp=sharing)

* [Sampling](https://docs.google.com/presentation/d/133bBtOQHPaBYSu7RBmbGuu8PN0UUxt278qTqOWSuJIQ/edit?usp=sharing)

* [Adjustment / blocking](https://docs.google.com/presentation/d/1xDY7Qh_ip4HA01unq8mxLF7M0ti8AGA0xmKeOihkqjg/edit?usp=sharing)

## A/B testing

A/B testing is the use of randomized trials in data science settings. To put this in context,
let's consider two ad campaigns that Jeff is using to sell books. Let's say campaign A and B,
respectively. How would one evaluate the campaigns?

One could run the ads serially; he could run ad A for a couple of weeks then ad B for a couple of weeks,
and then compare the conversion rate during the time periods of the two ads. Under this approach,
anything relationship found could be attributed to whatever's aliased with the time periods that
he was studying. For example, imagine if the first ad ran during Christmas or a major holiday.
Then, of course people's purchasing patterns are different during that time of year. So any observed
difference could be attributed to the unlucky timing of the ads.

If he were to run the ads at the same time, but ran the ads on sites with different audience demographics,
one wouldn't be able to differentiate ad type and audience characteristics. Ideally, he would be able
to randomize across time and/or sites. This of course, doesn't guarantee that the timing or sites the
ads appeared on are well balanced on all potential lurking or confounding variables. An argument could
be made that better strategies exist for known confounders that would force balance.
However, randomization is certainly the best strategy for trying to acheive such balance for unknown
lurking variables.

Our discussion of A/B testing focuses on randomization. However, the eventual analysis can get
quite challenging despite the help of randomization.
As an example, how can we be sure that Jeff's ads aren't be viewed by the same
people who visit different sites? If enough such people were contributing to the converion rates,
indepence assumptions usually made during analyses would be incorrect. Missing or incomplete data
often plague trials and A/B tests.

## Sampling

It's important not to confuse randomization, a strategy used to combat lurking and confounding
variables and random sampling, a stategy used to help with generalizability.
In many respects generalizability is the core of what statistics is trying to accomplish,
making inferences about a population from a sample.
In general, it's not enough to just say things about our sample. We want to
generalize that knowledge beyond our sample; a process called statistical inference.

A famous example of bias came from the so-called Kinsey Report of human sexuality.
The study subjects involved many more people with
psychological disorders and prisoners than were represented in the broader population.
Thus, the main criticism of the work was that it wasn't generalizable because of the importance
differences between the sample and the group inferences would like to be drawn on.
It's interesting to note that Kinsey's response was to simply collect more of the same kind ofsubjects,
which, of course doesn't solve the problem. Simply getting a larger biased sample doesn't correct the bias.

In the terms of solutions, three strategies should be considered first.
The first is random sampling where we try to draw subjects randomly from the population that
we're interested in. This can often be quite hard to do.
For example, in election polling, there's an entire science devoted to getting accurate polling data.

What if random sampling isn't available?  Weighting is another strategy that has many positive aspects, though
also some down sides. The idea of weighting is multiply observations in your sample so that they represent
the population you're interested in. Imagine you wanted to estimate the average height. However,
in your sample you have twice as many men as you have women.
In the population that you're interested in,
there's equal numbers of men and women. In weighting, you would upweight the collection of women that you had
or downweight the collection of men. Thus, as far as the weighted inferences were concerned,
the women and men had equal numbers.
Weighting requires that you know the weights, usually based on population demographics.
Moreover, certain weighting strategies can result in huge increases in the variability of estimates.

The last strategy  is modeling. That is to build up a statistical model
hoping that the model relationship holds
outside of where you have data.
This approach has the problem of actually having to build the model and
whether or not our conclusions are robust to this model building.
A careful design with random sampling results in analyses that are robust to assumptions,
whereas modeling can often be fraught with errors from assumption.

## Blocking and Adjustment

Imagine if you're interested in improving mobility among the elderly using fitness tracker, say FitBit.
You plan on doing a clinical trial where you randomize half of your subjects to receive a Fitbit, while
the others get nothing. (Side note, control subjects often get the treatment at the end of the trial to
reward them for participation.)

You are concerned that age confounds the relationship between fitness tracker usage and mobility.
It's likely that the age groups would be distributed In roughly equal proportions among the treated and the controls due to the randomization. However, if you have a smaller study, chance imbalances could occur.
Because you know age is such an important factor, you might wanna force it to be balanced between your
treated and control groups. To do this you might want to randomize within age blocks; this is called blocking.
In other words, if you hvae a factor that you know is important, why randomize and hope for the best?

Let's consider the same issue when you don't have control over the experiment, or you've conducted
the experiment and realize that there was an imbalance of ages between the treated and control groups.
Focus on the observational case where you don't have control over the experiment. Consider studying elderly
subjects comparing the use of fitness trackers with mobility. But, you are just observing the collection of people who self-select into using fitness trackers versus the controls. Because it's an observation study, you're worried about lots of factors that might confound the relationship between mobility and use of a fitness tracker. However, you're very concerned about age in specific, so let's focus on that one variable. (In a typical observational study, we'd be concerned about lots of things of course.) The younger subjects are
going to be more likely to use and directly engage with the features of a fitness tracker, just because of familiarity with technology. A direct comparison between fitness tracker users and controls would clearly
be inappropriate. The most common solution to this problem is adjustment.

Adjustment is the idea of looking at the relationship within levels of the confounder held fixed. Consider dividing age into say five categories. A simple adjustment strategy would compare the mobility within each age category, so we're more probably comparing like with like. We may not have equal or consistent numbers of fitness tracker users and non-users within or across age groups. But, by comparing within age groups, we
wouldn't be worried that our results were due to age.

There's lots of different ways to do adjustment. Perhaps the most common and easiest one is regression adjustment. In this form of adjustment we would add age into a regression model that included fitness tracker
useage. The estimate with age in the model would be the adjusted estimate. This performs a model
based adjustment that requires some assumptions to be effective.


# Results of the Analysis Are Clear

Lecture notes:

* [Multiple comparisons](https://docs.google.com/presentation/d/1TcDBpbMHh1dmL9Jwq_51S6U-PyMy-jkBjJGPMsaZrCQ/edit?usp=sharing)

* [Effect sizes](https://docs.google.com/presentation/d/1alJNwPcJLUBwLnMsrF1bmSIaqm_MCDpq0nYX-L5NHS4/edit?usp=sharing)

* [Comparing to known effects](https://docs.google.com/presentation/d/1ubNBV_EXiHvv-TP3iY4qYaxiPbjFtz2rqu5HkVbTGuQ/edit?usp=sharing)

* [Negative controls](https://docs.google.com/presentation/d/1-TgW9W_lazs9Jx6mZM0CYQBoJWzxU2-8wJOqvgRqbsA/edit?usp=sharing)

## Multiple comparisons

One way results can appear unclear is if results don't paint a compelling narative. This can happen
if spurious effects are detected or too many effects are significant. A common reason for this to
happen is from multiplicity.

Multiplicity is the concern of repeatedly doing hypothesis tests until one comes up significant by chance.
This sounds nefarious, and it can be, but it can be often done with the best of intentions, especially in
modern problems. Moreover, multiple comparisons issues can creep into analyses in unexpected ways.
For example, multiple testing issues can arise from fitting too many models or from looking at too many
quantities of interest within a model. The worst version of multiple comparisons is if an
unscrupulous researcher keeps looking at effects until he or she finds one that is signficant then presents
results as if that was the only test performed. (One could consider this less of a multiplicity problem
than an ethics problem.) Of course, most data scientists don't approach their work so poorly.
In many cases large numbers of tests are done as part of a legitimate and honest hypothesis
generating exercise. Or, large numbers of models are fit as part of a legitimate model building exercise.

There is a vast literature on multiple comparisons, but the easiest fix uses an inequality that's named after the mathematician, Bonferroni. Because it's named after his inequality, it's called the "Bonferroni correction".
The easiest way to execute a Bonferroni correction is to simply multiply your P-values by the number of tests that you're performing. So, for example, if you perform 10 tests and one of the P-values is 0.01, then that P-value is now 0.10. You then perform your inference as usual. This method shows you the impact of performing more tests. If you double your number of tests, then you have to double your P-values.

The Bonferroni correction is highly robust and it works in all circumstances. One issue is that it can be  
quite conservative. So the result of the Bonferroni correction is that it tends errs on the side of declaring effects not significant.

A second issue with Bonferroni (and all other) corrections is that they don't give guidance on what constitutes
the set of tests to include. That is, what number to multiply your P-values by. The mathematics unfortunately
can't help this question. As an example, imagine
that  you're looking at engagement statistics by web site design and find some interesting positive results
for a new design. You
double check your results by running the same analysis comparing old designs you know not to be fundamentally different and find nothing significant, as you would expect. Certainly you shouldn't penalize your original
analysis by verifying it with a second confirmatory analysis? This is clearly a different mind set then
what we're trying to control for with multiplicity. Thus, unfortunately, there's no simple rules as to
what goes into multiplicity corrections and one must appeal to reasonableness and common sense.

## Effect sizes, significance, modeling

In every statistics course ever taught, this phrase is covered: *statistical significance is not practical significance.*  This draws a discussion of the fact that just by reasons of having a large sample size
you can detect miniscule, practically unimportant, effects. I think the picture is a lot more complicated
than this simple phrase and idea suggests. In this section we discuss these more complex instances.
What does it mean to get a significant or a non significant result in hypothesis testing.

**What does a marginal signficiance imply?**

Let's go through some thought experiments. Imagine that a very large epidemiological study of nutrition finds
a slightly significant result, P-value of 0.049 associating hot dog consumption to colorectal cancer incidence.
This is right under what is the typical standard of significance. So the question I would ask to you is does the
larger sample size bolster the evidence or hinder it? In one sense the larger sample implies more evidence.
On the other hand, why did it take such a large sample size only to get a barely significant effect?

Let's consider another similar thought experiment. A well done A/B test, with a reasonable sample size,
no missing data or other complexities, finds one ad campaign is not
significantly  better than another; the P-value is just above the standard threshold for significance.
Does the good study design bolster confidence in the lack of significance or not?

If this seems confusing, it's because it is confusing. These questions don't have a consistent answer
among researchers who study problems like this!

One point worth emphasizing is that we cannot simply interpret the result of hypothesis test outside of the context. In other words, P-values and the results of hypothesis tests are not portable across settings.
They're not as well calibrated across settings as we would hope.

**Effect sizes**

Another consideration is that the size of the effect matters. The size of the effect is often lost
when you just report the result of a hypothesis test or the P-value by itself. Thus, when you're managing
people, force them to report effects and relative effect sizes in addition to the results of their
hypothesis tests and P-values. Confidence intervals help with this greatly, as they at least put the
inference back into the units of the problem. This doesn't eliminate the need to consider context, as
what constitutes a large effect in an A/B test and a large observational epidemiological study may
be dramatically different. However, it gives you more relevant information to interpret in context.


**Calibrating error rates**

You might also ask level of error is tolerable? If you're in a circumstance where you're testing between two
policies, each equally viable a priori, and you have to make a decision between the two regardless. Here,
you can tolerate a high error level. Since you have to implement one or the other, so the most important consideration is making a decision.
Unless the evidence is perfectly equivocal, you're gonna take
evidence slightly in favor of A and go with A, or evidence slightly in favor of B and go with B. Contrast
this with the error rates for a regulatory agency like the Food and Drug Administration. They have to prevent dangerous and ineffective drugs from going to market. Therefore,
they put very high scrutiny on the amount of information and evidence required. They'd rather error on the
side of not approving an effective drug than risk approving an ineffective one. So the standard of evidence
is very different than in our earlier setting. So the result of a hypothesis test just can't be interpreted in
the same way.

**What biases are likely present**

Another relevant consideration is what biases are likely present?  
If you have a giant sample that's very biased,
then you might be finding an effect, but that effect may just be detecting that bias.


**Summary**

Hypothesis testing is a tool that rarely should be used in isolation. If
you're managing someone and they're just reporting P-values by themselves or the result of hypothesis test, you
need to push them to go further. Push them to give you effect sizes; push them to give you confidence
intervals; push them to put the results into the proper context of what's being studied and
to contrast the results with other related studies.

## Comparison with benchmark effects

In this section, we talk about ways to help us interpret effects when we're studying something that we don't
know too well. The idea is simply to compare things with benchmark effects.
The context we're considering is when it's hard to interpret an effect or its magnitude, because it's a newly
studied phenomenon. A solution is to compare effects or significance levels with known effects.

My colleague (Brian Schwartz) and I studied past occupational lead exposure on brain volume.
My colleague found an unadjusted effect estimate of -1.141 milliliters of brain volume lost
per 1 microgram of lead per gram of bone mineral increase. This is hard thing to interpret.
However, it might be easier to consider when we relate it to normal age related brain volume loss.
Normal aging, over the age of 40 say, results in about a half a percent of decline in brain volume
per year. If I take that half a percent decline in brain volume per year, and I look at the average
brain volume from my colleague's study, I can figure out that 1.41 ml decrease is roughly equivalent to about about one would lose in 20% of the year in normal aging. Then I could multiply appropriately if I wanted
to increase the amount of lead exposure being considered, so that 5 units of lead exposure is roughly
equivalent to an extra year of normal aging.

This technique is very powerful and it can be used in many ways. Here are some (made up)
examples just to give you further of an idea: *the P-value for
comparing this new ad campaign to our standard is 0.01. That's twice as small as the same P-value
for the ad that was so successful last year*. *The effect of a year of exposure to this
airborn pollutant on lung cancer incidence is equivalent to 20 years of heavy cigarette smoking.*

## Negative controls

Recall we're concerned with unclear results and we're giving some strategies for
interogating them. In this section, we're concerned with significant effects that arose out of
elaborate processing settings. Often in these settings, one is often concerned whether the process
somehow created the significance spuriously. This often happens in technological research areas.
In genomics, running groups of samples together creates spurious effects. In brain imaging,
physiological noise creates seemingly real, but actually uninteresting effects.

So now you're worried that your results are more due to process than a real effect. How do you check?
First, there's all of the regular protections of statistical inference. However, you'd like to make
sure in a more data centric way that doesn't require as many assumptions.
The idea is to perform a negative control experiment. You repeat the analysis for a variable that is
known to have no association. In brain imaging, we often do this with the ventricles, areas inside
the skull with no brain, only cerebrospinal fluid. We know that we can't see brain activation there,
since there's no brain there!

In general,  what are the characteristics of a good negative control? Well, they're variables that are
otherwise realistic, but known to have no association with the outcome.
So in our brain imaging case, they looked at something that was in the image already and
was subject to all the same processing experience of the rest of the image.
The main issue with negative controls is that it's often very hard to find something where you know
for sure there can't possibly be an effect.

Another strategy that people employ rather than negative controls, is permutation tests.
They actually break the association by permuting one of the variables. Since you'd be concerned about
what if you got a chance permutation that could fool you, you look at lots of them.
This is a bit more of an advance of a topic, but the idea is quite similar negative controls.

To sum up, if you're feeling queasy about the consequences of a complicated set of data munging and
analysis and several models being built, repeat the whole process for something that can't possibly exhibit an
association, and see what comes out. At the minimum,
it's a great way to offer a sanity check, and to check influences due  to process.


# The Decision is Obvious

Lecture notes: 

* [The decision is not obvious](https://docs.google.com/presentation/d/1o-WUGyT74xgY4iRP_G1Z89VB7znMh15fUsfLrR_vrf4/edit?usp=sharing)

* [Estimation target is relevant](https://docs.google.com/presentation/d/1tzGlR42QSvxw5OqlOdreBBoqGW1pguUsnhFb_SjH8FE/edit?usp=sharing)

## The decision is (not) obvious

Things are easy if your tests are
highly non-significant or highly significant. But what if they are right in between?
We touched on marginal effects before. But now we'd like to devote a little more space to the general
concept of what to do when the results of the test are just on the margin?

What are you most concerned with with a marginal effect?
Probably foremost on your mind should be the idea of power.
Namely, was the study set up in the first place to really adjudicate whether or not there was an effect.

Power is the probability of detecting an effect that is truly there. You want more power in a study.
Okay, studies that have a larger sample size have more power than otherwise similar studies a smaller
sample size. Studies that are trying to detect a bigger
effect have more power than otherwise similar studies trying to detect a smaller effect. In other words,
it's easier to spot an elephant than it is to spot a mouse. More error variablity in the system that
you're studying, the less power you will have to detect a signal in all that noise.

After a study was conducted and has marginal results, the first question to ask was: was
the power adequate, or at least having the discussion of whether this study was really set up for success. Unfortunately, post hoc, there's not that much that can be done about power. The obvious thing,
collecting more data or doing another study, is usually not feasible. Calculating power after the
study has been done is known to be a biased, error prone process. If you're doing this you need to be very sophisticated in the field of statistics and aware of the issues.

Because of this, in many cases all that you're left with is a critical discussion of the strength of the study.
Ask questions like the following. Is the sample size similar to what was used in other studies where
an effect was seen? Is the effect size relevant? Can you point to aspects of the study that may have
led to the marginal results, like missing data?
This kind of critical review is an important part of understanding an equivocal result and making decisions
based off of it.

## Estimation target is relevant

A common issue is that in either predictors or outcomes, we haven't measured the variable of interest,
we've measured a surrogate. Some classic examples include body mass index as a measure of body fat percentage,
GDP as a measure of national economic well-being and food frequency questionnaires for calorie consumptions.

First, we should consider the hallmarks of good surrogate variables.
The best surrogates are gonna be unbiased. That is, they're not systematically different than the variable
of interest. Ideally they have a known variance around the desired outcome. Consider weight obtained with
an unbiased scale. If you have a scale that's kind of noisy, but its average difference from the truth is
zero.  Then you can use that information in your analysis without much trouble. If you know the variance,
all the better and you can likely do something quite formal in your analysis.

A second very good setting is where you have the truth and the surrogate measured on some subset of the people and you can study and understand some amount of calibration. Consider activity monitors, like FitBits.
These devices counts steps and calories expended,
when they're actually measuring acceleration. If studying activity, one
could count exact steps and calories in a lab for a subset of subjects to help calibrate in a larger study.
You could use the gold standard data to understand the measurement variability and bias and use
that variability and bias in your analyses.

Another reasonable strategy is to use sensitivity analysis to consider bias and variability of your surrogate variable. That is, come up with some idea of how off your individual measurements will be and then factor that into the analysis. Another cool ideas is to add more measurement variation to your variables, just by adding
random normals to your data, for example, and seeing the consquence. You can increase the variance and bias
of the additional measurement error this way and see what impact it has.  A generalization of this idea is
the so called simulation extrapolation (SimEx) method. SimEx and other methods are beyond the scope of this
book. The interested reader should consider looking into surrogate variables and measurement error models
for further reading.


Finally, it's worth discussing when to throw in the towel.
If the variable that you're going to use in lieu of the one that you really want
is so unknown and unreliable an estimate of the desired outcome that no results would change your decision or
state of knowledge, then why bother running the analysis at all? Certainly goes through this exercise before
conducting the study or doing the analysis.


# Analysis Product is Awesome


Lecture notes:

* [Reproducibility](https://docs.google.com/presentation/d/1hrzer7bpGn8jzN9QlPEfgq3LhiVh25XEmiJuCYOedNk/edit?usp=sharing)
* [Version control](https://docs.google.com/presentation/d/1jfLVMX-OK8u4T4pzT5mT4pJ75g3yhng1G-rS40Md1sM/edit?usp=sharing)

In this chapter we consider the products of the analysis. This is usually some sort of report or presentation. If the analysis is far enough along, then it might be an app or web page. We have a coursera class exactly on topic of the technical [development of data products](https://www.coursera.org/course/devdataprod).

If the product is a report, ideally, it would clear and concisely written, with a nice narrative and interesting results. However, the needs of data science managers are variable enough that we focus on two components that make for good final products that are ubiquitous across all settings. These are making the report reproducible and making the report and code version controlled.

Analysis reproducible considers the fact that if we ask people to replicate their own analysis, let alone someone else's, they often get different results, sometimes, very different. We have a coursera class on making [reproducible reports](https://www.coursera.org/course/repdata). The benefits of using the right tools for reproducible reports are many. They include dramatically helping achieve the goal of reproducibility, but also: helping organize ones thinking by blending the code and the narrative into a single document, they help document the code in a way that commenting doesn't achieve and they help automate the report writing process.

Thus if you're managing data scientists, we suggest [knitr](http://yihui.name/knitr/) and [iPython notebooks](http://ipython.org/notebook.html). These tools knit the analysis and the report together. And they're easy to learn.

As for the content of the report, some other recommendations that come to mind.

Check the signs, magnitudes and units. Checking the signs means checking that your effects are in the direction that you expect. It's also helps enforce asking the people that you manage to do more than just reporting coefficients. Checking the magnitudes by comparison with other known effects (covered in an earlier lecture) is a really good thing to encourage. Finally, put units on everything (graph axes, coefficients, means, ...) And make sure to understand the units. I can't tell you how many times this small step has helped.

It's important to get the data scientists and analysts that you mange out of technical jargon speak and into interpretation and interpretability. For the former, I keep harping on this idea of comparison with other known effects. Secondly, I encourage the idea of effect critiquing. This is the idea of, instead of getting excited about an effect, become its biggest critic. Try to figure out every possible reason why it could be spurious. This almost always leads to new analysis that should be conducted. Finally, for interpretability, encourage parsimonious models with interpretable parameters. That is, place a premium on simplicity. This is, of course, if you're more interested in a data science experiment where you are trying to create new parsimonious knowledge. The situation changes if one is trying to only improve prediction (see the first lecture).

Finally, version control is just general good practice. Version control is the process of keeping versions of your software, code, data and reports. Modern version control software makes this process easy. Using good version control, the project can be reverted to any previous step, and all of the steps are commented. Tools like git make this possible in massively distributed settings where lots of people are working on the same project. Git is the version control software, and a git repository is the actual version control database. Collaboration on a git repository occurs on a server. Fortunately, there are tons of hosted git servers out there for general and business use. The biggest one is [GitHub](https://github.com/) though others like [bitbucket](https://bitbucket.org/) are also great. These offer nice web interfaces to the server as well. There's an entire [free book on git](https://git-scm.com/book/en/v2) and a million tutorials online.

Of course, git is one of many version control systems. The main point is recommend (or demand/force) a version control culture in your organization.
