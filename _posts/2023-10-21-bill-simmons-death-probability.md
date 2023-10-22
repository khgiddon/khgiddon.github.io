---
layout: post
title: It is a near certainty that multiple people have died while listening to Bill Simmons
usemathjax: true
---

Over on Reddit, [someone asked](https://www.reddit.com/r/billsimmons/comments/17cvzm0/has_anyone_died_listening_to_the_bs_pod/) whether anyone has ever died while listening to podcaster Bill Simmons. It would be an undignified way to go: having the last thing in one's head be one of Bill's nuclear-level takes on sports or pop culture like saying that [Robert Forster isn't good in _Jackie Brown_](https://twitter.com/carternixon/status/1229872026602496001). Ugh. (Robert Forster is great in _Jackie Brown_.)

I do frequently listen to Bill Simmons's podcasts, and I thought the question was worthy of a more formal approach, both for the sake of scientific inquiry and also as a _memento mori_-esque caution. Below we explore the question: What is the probability that _at least one person_ has died while listening to Bill Simmons?

The title does give away the result: it is a near certainty that not only one but multiple people have died while listening to Bill. Let's go through the math.

### The death model

We first describe the general mathematical model we'll be filling out, which will require a series of assumptions. The goal of these assumptions is to balance the complexity of the model with the precision of the model, and overall we'll be looking for a ballpark figure.

First, we want to model the probability of death while listening to Simmons for _a given listener of the podcast_, in a given year. Then we will take a cohort approach later and look at all listeners of the podcast  over time.

Let us first consider probability of death. Probabilities of death given age and gender are available from the [Social Security Administration](https://www.ssa.gov/oact/STATS/table4c6.html), and we'll rely on those actuarial tables. For example, for a 33-year-old male the annual death probability is 0.002517, and for a 70-year-old male it is 0.026137.

- Assumption: Our model is yearly. We'll assume that the probability of death is constant over the course of a year.
- Assumption: All listeners are American. While this isn't true, this enables us to use the SSA actuarial tables.
- Assumption: Listeners of the podcast are representative of the general population in terms of their health.
- Assumption: The probability of death while listening to the podcast is independent of the overall probability of death. That is, we assume that listening to the podcast does not affect the probability of death for a given listener. Perhaps this isn't quite true, because listeners may be listening to the podcast while driving where death probability is higher vs. staying at home, or one of Bill's takes may be so bad that it causes a listener to just keel over and end it all. Or you could think that for those on their deathbed, they might finally put down their headphones and be less likely to be listening. But we'll go with the assumption of independence.

We need to make some assumptions about listener ages and genders in order to use the actuarial tables. I could not find good statistics about this online, so we'll make the following assumptions:

- Assumption: Bill's listeners' ages follow a uniform distribution between age 18 and age 75. That is, the probability of a listener being age $$x$$ is $$P_{\text{Age}}(x) = \frac{1}{75 - 18}$$.
- Assumption: Bill's listeners are 100% male. I know this isn't true in practice but it's close enough, and this won't be a significant source of error in the model.

Now we need to determine the percentage of time in a given year that the average listener spends listening to the podcast. A listener is defined as someone who downloads and listens to the podcast at least once a year. This is important for our model later: a listener is not the listener of a *given* episode, but someone who listens to the podcast at least once in a year (because we need to be able to join this with statistics on someone's death probability in a given year). 

For each listener, we want to find the percentage of the time they are listening to Bill Simmons. This can be modeled as the total number of annual podcast minutes released by Simmons, multiplied by the percentage of these minutes listened to by the average listener, all divided by the total number of minutes in a year. 

- Assumption: The relationship between how often a given listener listens to the podcast and death probability is independent. That is, more frequent listeners are not more likely to die on a rate basis. This enables to use averages and simplify the model.
- Assumption: Time spent listening is independent of listener age. That is, older listeners are not more likely to listen to the podcast more often than younger listeners. 

We also must decide whether we care about dying while Bill himself is speaking, or whether dying one of his guests or cohosts is speaking also counts. I believe the spirit of the original question is about Bill Simmons himself, so we'll go with that.

The percentange of time in a year that a user spends listening to the podcast requires the following assumptions:

- Assumption: Simmons releases a podcast 2–3 times per week, or 12 times per month / 144 times per year, including the *Bill Simmons Podcast* and its previous iterations and as a host on *The Rewatchables* podcast.
- Assumption: The average length of these podcasts is 93 minutes—this assumption is based on the measured length of the ten month-to-date October episodes. (This length is true recently but might not be true for early iterations of the podcast like the _BS Report_, but we'll go with it throughout time. Measuring  the October lengths only also doesn't take into account any variation in average episode lengths due to seasonality.) We'll also ignore the length of ad reads (which on Spotify aren't typically included in the episode lengths), even though it is Simmons usually speaking during the ad reads. The thought of dying while listening to Bill read an ad for SimpliSafe is too depressing to pursue further. We'll also ignore Bill's cancelled [HBO show](https://youtube.com/watch?v=y1dGNbtHdV8&ab_channel=HBO), because I don't know in that case if we can safely assume that listening and death are independent.
- Assumption: The average listener listens to 5% of total minutes of each podcast. This is a crticial assumption. But remember we're dealing with an *average* here of anyone who downloads and listens to the podcast over a year, including counting listeners who might only listen for a few minutes a year. If this seems low, it's because we're lumping in power-listeners with casual listeners.
- Assumption: Across all these podcasts, Bill is speaking 75% of the time. This is a guess. One could scrape all the episode transcripts and generate statistics about word count to get more scientific about this in particular.

Therefore the percent of time spent listening to Bill is:

$$ \displaylines{\tag{1} \text{Time spent listening to Bill Simmons} = \\ \text{Simmons podcasts per year} \\ \times \text{Length of each podcast (in minutes)} \\ \times \text{Episode completion pct} \\ \times \text{Pct of time Bill is speaking}} $$

Now we can input the values using our assumptions above, and we divide by the total number of minutes per year to get the percentage of time spent listening to Bill Simmons:

$$ \tag{2} \text{Pct of time spent listening to Bill Simmons} = \frac{144 \times 93 \times 0.05 \times 0.75}{525,600} = 0.096\% $$

Or, the average listener for a given year spends 0.096% of their time listening to Bill Simmons.

Now, for a given listener, the probability of death while listening to Bill Simmons is:

$$ \tag{3} P(BD)_{\text{y}} = P(D)_{\text{age, gender}} \times BR $$

Where:

- $$ P(BD)_{\text{y}} $$ is the probability of death while listening to Bill Simmons ("Bill Death") in a given year *y*
- $$ P(D)_{\text{y}} $$ is the probability of any death, conditional on the listener's age and gender
- $$ BR $$ is the "Bill Ratio," or the % of time spent listening to Bill Simmons. From equation (2) we know this is 0.096%.

Now we can calculate the probability of death while listening to Bill Simmons for a given listener in a given year. We need to extend this out over time for all of Bill's listeners since he first started podcasting.

### Number of annual listeners

Bill first launched the *BS Report* podcast in [May 2007](https://en.wikipedia.org/wiki/Bill_Simmons#:~:text=On%20May%208%2C%202007%2C%20Simmons,song%20written%20by%20Ronald%20Jenkees.) (under the name *Eye of the Sportsguy*). We'll model out 16 years of podcasts (15 full years from 2008–2022 and one year combining the 2007 and 2023 partial years.)

How many listeners does Bill have? 
In 2009, the podcast was [downloaded over 25 million times](http://www.espnmediazone3.com/us/2010/01/another-record-year-for-espn-digital-media/), and has likely grown in popularity since then. According to Edison Research, *The Bill Simmons Podcast* is currently [the most-downloaded sports podcast in the world](https://www.edisonresearch.com/weekly-insights-2-15-23-listening-makes-for-better-watching-the-top-sports-podcasts-revealed/). The Reddit braintrust seems to think that Bill could get between [500,00 and 1 million downloads per episode](https://www.reddit.com/r/billsimmons/comments/14h6oey/how_many_people_listen_to_bills_podcast_on_average/) (which is not the same as listeners), which would bring the total number of annual downloads north of 100 million.

But for our model we're looking for the number of yearly listeners (who download at least one episode), not the number of listeners per episode. Data on this is difficult to come by. We're going to assume 2 million annual unique listeners (some of who might only listen to one episode), meaning that each episode is downloaded by somewhere betwen 25% and 50% of annual unique listeners.

We could model the number of listeners per year differently for each year, but since Bill's podcast became popular very quickly after launching, we'll say:

- Assumption: Bill's podcasts have had 2 million unique listeners per years since 2007.

We could model this number separately by year to account for Bill's growing popularity (e.g., as a linear function), but in the absence of concrete data about this year, we'll use one constant number per year.

### The final model

Now we can put all the pieces together.

If the probability of death while listening to Bill Simmons for a given listener *l* in a given year *y* is $P(BD)_{\text{y}}$, then the probability of at least one death for two listeners in a given year is:

$$ \tag{4} P(\text{At least one death})_{\text{y}} = 1 - (1 - P(BD)_{\text{y,}l_1}) \times (1 - P(BD)_{\text{y,}l_2}) $$

Then for all listeners l in a given year, the equation will be:

$$ \tag{5} P(\text{At least one death})_{\text{y}} = 1 - \prod_{l=1}^{n_{y}
} (1 - P(BD)_{\text{y,}l}) $$

Substituting in equation (3) for $P(BD)_{\text{y,}l}$, we get:

$$ \tag{6} P(\text{At least one death})_{\text{y}} = 1 - \prod_{l=1}^{n_{y}} \left(1 - P(D)_{\text{age}_{l}, \text{gender}_{l}} \times BR \right)
 $$

To find a solution to the equation above using the actuarial tables provided by the Social Security Administration, we'll write a script in Python. The script is available [here](https://github.com/khgiddon/misc/blob/main/simmons/solve.ipynb).

After running this script, we find that *the probability of at least one death while listening to Bill Simmons is nearly 100%*, just in one given year. So not only is it a near certainty that someone has died while listening to Bill Simmons, but it's likely that someone has died while listening to Bill Simmons every single year.

Just a sensitivity check, in case one of our assumptions are off: if we assume that one of our assumptions is off by a factor of ten and we appropriately divide the death probability by 10, this still leaves an 82% probability of at least one death in a given year.

If we use 82% as the annual probability, we can ask for the the probability of at least one death over the course of 16 years. All of our assumptions are constant by year, we can simply use the following equation to find the probability of at least one death listening to Bill during his podcasting tenure:

$$ \tag{7} P(\text{At least one death})_{\text{16 years}} = 1 - (1 - P(\text{At least one death})_{\text{y}})^{16} \approx 100\% $$

Based on the earlier analysis, it seems to safe to say that multiple people have indeed heard Bill in their last moments on this Earth.

