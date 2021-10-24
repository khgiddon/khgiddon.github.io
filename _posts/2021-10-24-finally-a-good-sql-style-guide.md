---
layout: post
title: Capitalization in SQL (and finally, a good style guide)
---

I've come across a number of SQL style guides and had major points of disagreement with most of them. My grumbling tends to come from, in general, their reliance on tradition rather than updating standards for the workflow of the modern analyst or engineer. To be more formal, we might say they are *path dependent*, and optimized for a set of conditions that no longer exist.

The most obvious example of this is in recommending "shouting" SQL keywords such as SELECT and WHERE in all-caps. SQL is a case-insensitive language. It should not be controversial to say that upper-case text is more difficult to write and (as designers know) more difficult to read. As someone who's conducted a fair number of live coding interviews for SQL exercise, I've seen candidates waste valuable time fumbling with toggling the caps-lock or shift key in virtual interviews. (Though from the candidate's perspective, you could argue that this is the conservative and optimal approach in case they end up with a bizarro interviewer who applies demerits for lack of capitalization.)

The path dependence comes from the inception of SQL before modern development environments. Today all development environments or SQL tools come with color-coded syntax highlighting that visually differentiates SQL keywords from other elements of a SQL query, with better readability than all-caps. Before syntax highlighting, visual differentiation via capitalization was arguably necessary. Some modern defenders of the capitalization [will assert](https://softwareengineering.stackexchange.com/questions/101316/what-good-reasons-are-there-to-capitalise-sql-keywords) that SQL is commonly seen in things like logs that do not have syntax highlighting, or sent in emails. 

On logs: I do come across SQL output in production logs. Mostly in this case, I'm chasing an error message because some scheduled prod script failed unexpectedly, and the error might point to a specific line in the script. But *development* should not be occurring in production logs of this type, and to complete debugging, the user will likely have to go back to the dev environment to make any code changes in some SQL. We can even concede that capitalization might marginally improve readability, here. But for most users this is a highly marginal use case, so the improvements would not exceed the cost of its implementation in other contexts.

Meanwhile, I can't remember seeing SQL sent in an email. Is anyone doing that regularly (and why aren't they using a more casual tool, or a more heavyweight one with version control)? I have, however, done my fair share of sending SQL scripts or snippets in tools like Slack. Slack isn't a development environment, but it does have syntax highlighting built into sending code complete with language auto-detection. 

Anyway, the defenders of capitalization are the champions of a dying cause.

Not without irony, I am using all-caps in this post to note SQL keywords. But this isn't a development environment, and we do have the need to differentiate SQL reserved words from plain old English text in the course of a paragraph. Syntax highlighting inline would be an option here, as would some code formatting, but capitalization is merely the lowest-hanging fruit.

What inspired this post was coming across [this SQL style guide on GitHub](https://gist.github.com/mattmc3/38a85e6a4ca1093816c08d4815fbebfb) by the user **mattmc3**. It recommends using all lower-case words in SQL, and has a few other good recommendations including using metadata fields (created_at, updated_at) in tables where applicable, consistent naming conventions, and preferring leading commas over trailing commas. 
(I do prefer leading commas but there's a high degree of individual preference here, so I wouldn't remotely begrudge anyone who uses trailing.) 

Overall, I don't think it's possible or remotely necessary to standardize best practices for all different cases (e.g., how long does a window function need to be for it to be broken up), and there's ample room for in-the-moment judgment. But best practices surrounding readability and consistent naming conventions within an organization make sense to implement, with likely positive returns on velocity and a reduced error unforced error rate.
