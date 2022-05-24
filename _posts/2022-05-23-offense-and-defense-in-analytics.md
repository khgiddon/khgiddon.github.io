---
layout: post
title: Offense and defense in analytics
---

Consider the responsibilities of a typical Analyst in a technology company — whether in Product Analytics, Business Analytics, Marketing Analytics, or Data Science. A simplified model can classify their work into *offense* and *defense*:

- Offense: Analysis that investigates opportunities to grow the product or the business. This might include analysis of user behavior to locate gaps in the product offering, improving a recommendation or targeting algorithm in production, creating a customer segmentation, and much more.
- Defense: Analysis that investigates systems that may be broken and works to correct these systems — e.g., diagnosing the root cause of metric regressions, fixing production models that aren't working as intended, or generally seeking out anywhere that *current* processes are not operating as expected.

Note that this classification is purely about outputs that can be considered "analysis" and not related work such as building reporting, the management and maintenance of data pipelines, programs to manage data access and security, or any operational components of the Analyst role. I'm therefore defining defense somewhat differently than other writing I've seen which describes "defense" as focusing on data quality, security, and regulatory compliance.

Most of an Analyst's time will be spent on Offense. In a well-run Data organization, execution on Offense is self-evident in its value to the business, and is usually what an Analyst was "brought in to do." Powerful Offense has the potential to shape a clear product narrative through data, define north star metrics, and dramatically shift internal goals and resourcing. A well-known example of this is Facebook's "[seven friends in ten days](https://genius.com/Chamath-palihapitiya-how-we-put-facebook-on-the-path-to-1-billion-users-annotated)" mantra, referring to a benchmark in the user journey heavily correlated with retention. At Facebook, the application growth tactics to increase the number of new users who hit this benchmark subsequently became the guiding focus of the growth team.

My perception from years of observation is that most Analysts will prefer to spend their time on Offense. Defense is less loved. Reasons for this might include:

- When dealing with a highly visible defensive problem (something is clearly broken and metrics are tanking), there may be high pressure on the Analyst to resolve it.
- On the flip side of the coin, when dealing a mostly *invisible* defensive problem, because the problem is not easily observed there will be few advocates in the organization arguing to spend time on it. The sizing or the impact of correcting the problem may not be easily known without investing into an investigation.
- Defense usually isn't explicitly roadmapped, so it requires sidelining other initiatives that are on the roadmap.

A consequence of that general preference is that defensive analytics are underutilized and underrewarded relative to their value to the business. While working at Meta, I observed that one Analyst diagnosing something that was to that point invisibly broken might result in a metrics win that equals the entire work of a Product team for half the year.

Well-run Analytics organizations will champion spending an appropriate amount of time on Defense. The definition of an "appropriate" amount of time will be dependent on the complexity of the data, the product, and the business systems. With additional complexity comes increased opportunity for error.

Two brief suggestions for how to provide the right organizational incentives on Defense:

#### 1. Make Defense easier by designing auditable systems. 

Let's use an example from Performance Marketing. Say we buy users on a channel like Google where we optimize to a cost per conversion, and this cost has some daily variance. In some cases the need for Defense will be obvious (cost per conversion undergoes a step function change that's unexpected) and some cases it won't be (the return on marketing spend is slowly worsening, but it's difficult to tell because of the level of daily variance). The latter case might present challenges for Defensive analytics, because we might not know where to look to identify a problem.

We can lower the "startup cost" of going on Defense by creating reporting that tracks through a funnel or pipeline at each relevant step, to better isolate where issues may be occurring. That is, we can audit the entire data generative process rather than just a key metric.

One basic example: let's say there's a bug in the data pipeline we use for calculating user-level conversions. Root cause: A new feature was added to the product that we'd consider a conversion event, *and* this event was logged correctly in the product, but the downstream pipeline used for reporting marketing conversions didn't account for them because the event name needed to be manually added to a WHERE clause in a SQL script. As a result, we're underreporting conversion events, and needlessly lowering our marketing spend because the data indicates we're less profitable than we actually are.

If a report existed such as *number of conversion events reported to Google by type* (raw counts and/or comparison to the main analytics database), this report could be used to identify that such an event might be missing from the Marketing event pipeline, and might be the root cause of the decline in Google channel performance.

Overall, the more any kind of production process is easily auditable through ready-made reporting requiring no additional code, the easier it is to identify opportunities to go on Defense. The fixed cost and maintenance cost of these kinds of reports need to be balanced against the benefits, but for any production processes with potential for significant business interruption, they should often be worth the effort.


#### 2. Encourage exploratory analytics on Defense.

I'll define exploratory analytics here as analytics investigating a problem or opportunity that may or may not exist. Exploratory analytics is commonly deployed on Offense to find new business opportunities. But Analytics organizations should also encourage it on Defense — to check our assumptions on whether things are working as we think they should. This may involve tracing back a production system, or business problem, from start to finish.

Exploratory analytics requires picking up (figurative) rocks to check if there's something under them: most of the time there won't be, but sometimes there will be that makes the whole enterprise, on average, worth it. Conducting exploratory analytics should lower the median output (business value) of a given Analyst but raise the mean output. I've found that exploratory analytics often begins with a hunch — someone noticing something odd or awry when investigating a different data problem — and that good Analysts are usually tenacious in making time to follow their hunches through to a conclusion.

I suggest that Analytics leaders encourage exploratory Defensive work through performance expectations — e.g., by (1) setting a team standard that X% of time is spent on it, and (2) rewarding Defensive exploratory work in formal review settings, commensurate with its impact.

#### Coda: Defensive specialists?

It's worth asking as Analytics organizations scale, is it worth considering some Analysts to be "offensive specialists" and "defensive specialists"? Generally, I don't think so — the two skillsets are too correlated. Both Offense and Defense require the application of analytical rigor to the extent that the best Defensive Analysts are probably the best Offensive Analysts. An Analytics org will want their best Analysts working on the hardest problems where they can add the most value; on any given day, this might be on Defense or on Offense.
