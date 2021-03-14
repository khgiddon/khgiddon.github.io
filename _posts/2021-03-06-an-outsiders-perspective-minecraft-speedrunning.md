---
layout: post
title: Luck and skill in Minecraft speedrunning
---

***This series of two posts does XYZ. This post provides a brief introduction to Minecraft speedrunning for anyone who might be unfamiliar, and also describes my personal interest in the subject. Feel free to skip to Part 2 that gets into the speedrunning framework and simulation.***

---

BREAK INTO PART 1: INTRODUCTION AND PART 2 for CALCS SO CAN BE DONE SEPARATELY?

I recently started reading up on the Minecraft speedrunning community. For anyone unfamiliar with "Minecraft" or "speedrunning": Minecraft is a video game based on exploration, world-building, and construction; and speedrunning is an attempt to complete a video game or part of a video game as quickly as possible. Speedrunning has grown into a popular subculture across many games: some of the most popular speedruns have [upward of 10 million views on YouTube](https://www.youtube.com/watch?v=CFkv6DtKf3w), and players frequently livestream speedrun attempts to substantial audiences on Twitch and other platforms. The website [speedrun.com](www.speedrun.com) serves as an archivist and provides leaderboards for many communities. As of March 2021, the site indicates that  Minecraft is the most popular game for speedrunning, with over 1,400 registered and active speedrunners.


I played Minecraft briefly back in 2011, when the game was still in beta. Back then, speedrunning as a whole was not the phenomenon it is today, but Minecraft was also basically impossible to speedrun because it was an open-ended sandbox game, and there was no obvious event one could attain in the game to mark the completion of a 'run.' But the game is continually being updated and since then the game has added boss fights; while there are different speedrunning "categories," most speedruns end with the player defeating a boss called the Ender Dragon.

My renewed interest in Minecraft was sparked by two factors:

### 1. The scandal

First, in December 2020, a prominent Minecraft speedrunner known as Dream was accused by the speedrunning community of cheating. Minecraft gameplay involves elements of randomness (killing hostile enemies drop items useful to the player with some probability). Dream received an exceptional sequence of item drops over a series of rns. The Minecraft Speedrunning Team (which "verifies" speedruns) released a [report](https://mcspeedrun.com/dream.pdf) that stating that the luck that Dream received was too good to be true, and concluded that Dream must have secretly modified his game in order to give himself better luck. Dream has denied all accusations but the community has generally agreed with the conclusions of the verifiers that Dream cheated. ([This article](https://www.polygon.com/2020/12/15/22176341/minecraft-youtube-dream-speedrun-cheating-mod-world-record-piglin) on *Polygon* provides a more detailed summary for anyone interested.)

The [report](https://mcspeedrun.com/dream.pdf) released by the Minecraft Speedrunning Team is an incredible artifact. It is thorough, precise, and rigorous; it explicitly tests the impact of various assumptions (i.e., conducts sensitivity analysis); and all åcalculations are reproducible. That is to say, it meets all criteria that one could reasonably want for this type of analysis. The central calculation relies on application of the [binomial theorem](https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/) (which should be familiar with any student of statistics or anyone who does data science professionally). So there was a nice application of my current line of work to the nostalgia kick of a hobby from ten years ago. 

The whole affair has the added bonus of getting a bunch of 14-year-olds to read up on the binomial formula. What a boon for math education! I can't think of a better backdoor way to get across that hey-you-might-actually-be-interested-in-algebra. One might wager that considering the reach of the scandal and analyses, at least one incremental future student will major in statistics. Thanks, Dream.

### 2. "What it takes"

Second, I've always been drawn to stories of devotion to particular vocations or hobbies, and the level of effort, talent, skill, practice, and perseverance required to become the best. (I don't think I've ever seen a snooker table in person, but I've been following the sport ever since reading about the amazing Ronnie O'Sullivan, "unhappy king of snooker," in a [2015 *New Yorker* article](https://www.newyorker.com/magazine/2015/03/30/follow-the-white-ball).) My interests in this span diverse fields like sports, business, art, music, politics, and literature, but also in particular and more esoteric subcultures. Video gaming is in many ways unique because of the lack of barriers  to entry to reaching the top of the field — it doesn't require reaching any particular age, level of education, or other credentialing.

(grinding definition)



## A framework for Minecraft speedrunning

Let's now develop a framework for Minecraft speedrunning, and what it takes to get the record. We can start by developing two concepts for our framework: *luck* and *skill*.

Luck in this context refers to factors outside the player's control (i.e., randomness). [FOOTNOTE ON HOW TECHNICALLY NOTHING IS RANDOM] In Minecraft speedrunning, there are two main sources of luck: map generation and item drops. For the most popular Minecraft speedrunning category ("random seed glitchless"), the starting map that the player is placed on is procedurally generated (i.e., has randomness but follows certain preprogrammed rules). Certain "seeds" (maps) will be inhospitable to speedrunners and impossible to set the record one. A player has to reset their game repeatedly to find a potential map that has the needed features required for a good speedrun. The second element of luck is item drops. When the player kills an enemy in the game, the enemy has a certain probability of dropping an item, some of which are needed to complete the speedrun. Dream was accused of modifying his game such that item drops occurred with greater frequency than was originally programmed.

Skill refers to factors in the player's control. What composes skill? We can list factors such as:

1. Mechanical knowledge: does the player have sufficient knowledge of the game mechanics to make correct decisions?
1. Decision-making: based on what is happening in the player's run, can they make the correct decisions that result in the highest probability of achieving a speedrunning record (e.g., mitigating bad luck or taking advantage of opportunities)?
1. Technical execution: can the player produce the series of inputs needed into my computer to accomplish what they are trying to achieve?
   
What's I'd exclude from on the list above is the ability to discover new strategies. Even though the strategic element is crucial to the game, any player competing publicly is typically posting his or her runs for others to see, so any strategic innovation that provides real benefits is likely to be picked up by others, negating much of the discoverer's initial advantage. In fact, one could classify innovations in speedrunning as a [public good](https://en.wikipedia.org/wiki/Public_good_(economics)): as a piece of knowledge, they meet the traditional public good criteria of being non-excludable (one can't prevent someone else from using a new speedrunning strategy) and non-rivalrous (using a new strategy doesn't "use it up" and prevent others from using it). (Of course, some types of knowledge can be made a non-public goods through legal regimes such as patents.)

So, we can think of the probability of setting a record on any given single speedrun as requiring a combination of luck and skill. The ratio of luck vs. skill will vary by game (and which components of skill matter will vary as well). For example, another game with a notable speedrunning community, Super Mario Bros., has at the highest level a low luck to skill ratio. Setting the record requires an extremely high degree of technical execution and perfect timing of inputs into the controller. The levels in Super Mario Bros. are not procedurally generated Minecraft, on the other hand, has a much lower ratio of luck to skill. Any given speedrun will likely be impossible to set the record on due to factors entirely outside the player's control (primarily the map generation). 

Now let's generalize these ideas. For any given game:

- There is some minimum level of skill to have a nonzero chance of getting the speedrun record.
- As a player's skill increases, the player has a higher probability of getting the record.
- The relationship between a player's level of skill and their probability of setting a speedrun record (on a per run basis) depends on the level of luck required for the run.

In a game with no luck, the relationship between skill and record probability may look something like this:

[FIG 1 - linear curve]

However, I'll posit. The top players in terms of skill have a similar level of skill. We can't observe the distribution exactly.

In a luck-heavy game there will likely be diminishing marginal returns (in terms of record probability) to increasing skill. In a skill-heavy game there may be flat or increasing marginal returns to increasing skill, as we saw above.

For a given game, one could think of a nonlinearity in the curve – for example, attaining a certain level of skill allows the player access to new strategies that dramatically increase one's record probability. One example of this [Super Mario Bros.] - many strategies of this type.

[GRAPH]



This will take the shape of an s-curve (also called a sigmoid).

There'll be some top echelon of speedrunners.

An ever-higher degree of luck. 

Any given record is likely to be extremely lucky, so the only way it can be beaten is by some combination of an even greater and more unlikely degree of luck, or developments in skill that are so great that a player can beat the record by being more skillful and less lucky. 

## Simulating the development of a speedrunning record


### Naive simulation

### Simulation with skill improvement 
However, we have to assume level of strategic improvement that the community engages with, and potential game updates that make speedrunning easier, and improvements in execution from the individual players.

Theoretical floor. 

( Probably cut this: If we model the shape of the distribution of speedrunning skill, and the associated sigmoid function that maps skill onto the , we could probabilistically )