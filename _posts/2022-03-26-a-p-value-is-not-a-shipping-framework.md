---
layout: post
title: A p-value is not a shipping framework
---

*[This post is intended for practitioners of A/B tests and assumes some familiarity with A/B testing concepts.]*

You're a product manager, analyst, or engineer working on a product change — let's say modifying a user onboarding flow. Following the standard practice at your company, you run an A/B test with your proposed changes. You take care to select one more or key outcome metrics; you run a power analysis to make sure to allocate an appropriate number of users to your test after considering these metrics' minimum detectable effects; you launch your test; and after reaching your appropriate power and experiment duration, you open your computer and anxiously look at your results.

Congratulations! Your two key metrics at different stages of your funnel — onboarding completion rate, and revenue — are both showing statistically significant increases at a 95% significance threshold. Even better yet, the effect sizes shown in the test have practical significance for your product. Following procedure, you take out your stamp that says "reject null hypothesis," and prepare to write up your win for the team.

Hold on — should you ship this change?

The answer is not a blanket "yes." The problem is that the results of a typical frequentist A/B test (such as the set of facts above) do not tell you whether to ship. They are silent on that question. They only tell you what the most likely effect size of your product change is (a delta) and the probability of observing an effect of that size given that no actual effect exists (a p-value). It requires a separate judgment to convert that set of facts to a shipping decision, which is where the messiness begins.

### Shipping decisions are cost-benefit analyses

When considering whether to ship, the relevant question to ask is most often: "Is this product change likely good for our business?" This is not a pure statistics problem; this is a problem about decision-making under uncertainty. A simplified framework to answer that question might be in terms of cost-benefit analysis: If we ship, what benefit do we get if we're "right," and what's the cost incurred by the business if we're "wrong," and what's the probability of being "right" vs. "wrong."

Some readers here might recognize that Bayesian statistical methods can help provide a more rigorous framework for answering this question. Bayesian methods are capable of outputting the probability an observed effect is true (after [choosing an appropriate prior](https://www.evanmiller.org/bayesian-ab-testing.html) for your experiment). With a Bayesian framework, you can even convert your experiment results directly to [a decision rule that tells you whether to ship](https://www.chrisstucchio.com/blog/2014/bayesian_ab_decision_rule.html)!

Yet in industry, explicit Bayesian A/B testing remains the exception, not the norm. A [blog post by David Robinson](http://varianceexplained.org/r/bayesian-ab-testing/) describing his organization's decision to remain using frequentist as opposed to Bayesian testing says that p-values are "the devil we know ...  switching to Bayesian testing requires getting everyone familiar with priors, posteriors, and the loss function — it’s trading one set of challenging concepts for another." 

From my own experience (even at companies at the cutting edge of experimentation technology such as Meta/Instagram), shipping decisions will usually involve looking at frequentist results (effect sizes and confidence intervals) and recommending a shipping decision based on those results. I hypothesize that most of the time when this occurs, the tests' practitioners or reviewers are implicitly using the kind of cost-benefit decision framework I discuss above, even if they don't realize it. For example, they may be applying the experiment's p-values and observed effect sizes to arrive at a mental cost-benefit analysis of shipping vs. not shipping a given change, based on the probability the observed effect in the experiment is true (or the effect size is above or below a certain threshold).

That kind of logic is statistically incorrect. A p-value is not the probability an effect is true — the concept of the probability an effect is true does not exist in frequentist statistics — *but the underlying statistical intuition is correct.* There needs to be some transfer function to convert the test results into a shipping decision! Treating the p-value as a probability becomes a shorthand heuristic to enable converting these results into something usable for a binary decision (to ship or not to ship.)

Making a shipping decision from frequentist data might also involve the *implicit* application of priors. Even though these won't be explicitly parameterized into a formal model, the test's practitioner is likely incorporating previously held beliefs on the effectiveness of the intervention in the process of making a "ship" or "no ship" recommendation. This process is implicitly Bayesian in nature even if the mental mechanics are obscured to the person conducting it. In baseball, an outfielder might catch a fly ball successfully most of the time, even if he can't tell you the formula for acceleration due to gravity as the ball's falling through the air. Likewise, an A/B test's practitioner might reach the correct shipping decision most of the time even though the conversion of the test data to the decision is a mental black box that shoehorns a p-value into a cost-benefit analysis.

### Even Bayes doesn’t get you all the way

Forgive the contradictory hyperbole in this heading. My last point is that even if you go the whole nine yards and compute a shipping rule based on Bayesian outputs, this isn't enough to say "ship." Shipping is ultimately a product decision for which experiment results are only one input.

I mentioned above that the relevant question to ask is "Is this product change good for our business?" A rigorous answer to that question looks beyond experiment results. For instance, there's a full suite of reasons you might want to ship something that shows negative user effects in the experiment results. For a partial list of examples:

1. you strongly expect your A/B test results understate the value to the user because there's negative novelty effects that you expect to fade over time
2.  you release a change that’s technically necessary simplify the codebase
3. you want to release an MVP of a product change to learn from and iterate on in the future
4. you need to respond to legal or regulatory risk
5. the entire company or product is being bet on a particular strategic pivot with which this product change is aligned

Theoretically, all of these factors could be quantified and modeled into the cost-benefit analysis. It's a good skillset to have. But for all but the most consequential decisions, making these factors explicit likely doesn't add marginal value to make a better decision, after considering the opportunity cost required to actually model them.

Where does this leave us? I think there are two takeaways:

- Shipping decisions will always involve a mental "black box" model of converting the relevant data and other factors into a binary ship/no ship decision. Bayesian A/B testing makes more of the math explicit and can help make better decisions more often, but still doesn't contain the full set of product considerations required for a decision.
- Shipping decisions might apply the p-value in a statistically incorrect way by informally treating it as a probability. Based on my experience this occurs with some frequency, but my intuition is that this still leads to the correct shipping decision most of the time.


*Thanks to Will Seifstad for comments on a draft of this post!*
