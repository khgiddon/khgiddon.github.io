---
layout: post
title: Expected vs. actual exposures: a necessary validity check for A/B tests
---

All successful A/B tests are alike; each unsuccessful A/B test is unsuccessful in its own way.

The reasons an A/B can go awry are many, but I've found that a classification into two broad categories is generally applicable: misinterpretation of results, and failed engineering implementation. The A/B testing literature as targeted to Data Scientists tends to (understandably) focus on the former, as Data Scientists typically own the explanation of the data. Included in this "misinterpretation" category are factors such as the underpowering of a test or errors of statistical interpretation. But the most common way I've seen A/B tests fail is from the second category, a failed engineering implementation — where the implementation of the test either has technical issues that make proper interpretation impossible, or the implementation doesn't match the test spec.

Two caveats on definitions here:

1. I define failure here as a test that does not produce results that are usable to make the intended shipping decision, or an incorrect shipping decision is made. (A properly run experiment that results in a "no ship" decision is not a failure.)
2. A failed engineering implementation is not *necessarily* the fault of the implementing engineer. The test spec (as written by an analyst, product manager, or other engineer) may have omitted crucial details or set up the test for failure from the very beginning. Responsibility also lies with the analyst for catching errors of implementation visible in the data.

With this in mind, I've found that one (relatively simple) validity check can diagnose issues with A/B test setup, and I have not seen this check mentioned in A/B testing workflows. The validity check is: **After launching the experiment, does the number of exposed users in the experiment match the expected number of exposed users?**

In my experience, this type of analysis has detected issues with test setup a material percentage of the time. The passing of this validity check can provide confidence that the experiment was indeed implemented correctly. 

Let's break this down:

1. Every test spec should have an agreed-upon exposure point where randomization of the treatment occurs. Typically this exposure point should be as close to the product intervention (the difference between test and control treatments) as possible. (If the engineer doesn't know the exposure point, something is wrong already.) The number of users who are included in the experiment is based on the number of users who reach the exposure point and meet the exposure criteria.
2. After launching a test, the analyst should be able to look at whatever tooling he or she is using to assess results, and find the number of exposed users.
3. The analyst should now be able to compute the expected number of exposed users to the experiment (based on the exposure criteria) with an analysis *that does not rely on any A/B test tooling.* 
4. If the number of actual exposures from Step 2 does not match the expected number of exposures from Step 3, this is evidence that the test was not implemented correctly, or some other type of communication failure within the A/B test team occurred.

 While it depends on the complexity of the test setup, I've found that the data necessary for Step #3 is typically not available in some kind of off-the-shelf dashboard and relies on a custom analysis.

Here's an example in practice:

- We're running an A/B test on a checkout flow on an ecommerce site. The intervention is that we want to change the color of the checkout button on the checkout page after  users click a "Return to Cart" navigation button on the top right of their screen. We only want to change the color of the button for users who are logged in. The button only appears if a user has added an item to their cart.
- We launch the test. After it runs for 3 hours, we pull up our test tooling and we see that 1,000 users have been exposed and assigned to either a test or treatment group. The number of users in each treatment looks reasonable — 509 in test treatment, and 491 in control treatment. 
- We query our databases to check for the number of users that meet the test criteria over the same 3-hour period that the test was running. We look for users that had a "navigate to Return to Cart" event and had at least one item in their cart when this event occurred, and were also logged in. We find that, based on these criteria, we expected 750 users to be exposed to the test.

Something's wrong here: we're missing users we would expect to be exposed. Perhaps there was a different experiment running for a subset of users that preempted the exposure endpoint (not necessarily a problem for test validity, just something that needs to be understood). Or perhaps users were only exposed if they were logged in with an SSO provider like Facebook or Google, and not via the site's native login functionality.

We can also think of the opposite problem — if we found we expected 1,500 users to be exposed to the test, vs. the 1,000 that were actually exposed. Perhaps the criterion to only expose for logged-in users wasn't implemented. Or perhaps there is some type of dilution where the exposure endpoint is somehow being called elsewhere — for example, users are being exposed who navigate as part of a normal checkout flow, even though they don't see the intervention that is part of the "Return to Cart" flow.

Overall, this type of analysis either adds to the body of evidence that the test was implemented correctly, or gives the red flag signal that something needs to be understood (and potentially changed) before the experiment risks misinterpretation and an incorrect business decision.
