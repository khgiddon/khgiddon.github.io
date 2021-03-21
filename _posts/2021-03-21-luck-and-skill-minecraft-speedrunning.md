---
layout: post
title: Luck and skill in Minecraft speedrunning
---

Recently, I started learning more about the Minecraft speedrunning community. For anyone unfamiliar with "Minecraft" or "speedrunning": Minecraft is a video game based on exploration, world-building, and construction; and speedrunning is an attempt to complete a video game or part of a video game as quickly as possible. Speedrunning has grown into a popular subculture across many games: some of the most popular speedruns have [upward of 10 million views on YouTube](https://www.youtube.com/watch?v=CFkv6DtKf3w), and players frequently livestream speedrun attempts to substantial audiences on Twitch and other platforms. The website [speedrun.com](www.speedrun.com) serves as an archivist and provides leaderboards for many communities. As of March 2021, the site indicates that  Minecraft is the most popular game for speedrunning, with over 1,400 registered and active speedrunners. The size of the full Minecraft speedrunning "community," including watchers, likely numbers at least in the hundreds of thousands, based on YouTube and Twitch view counts.

I played Minecraft briefly back in 2011, when the game was still in beta. Back then, speedrunning as a whole was not the phenomenon it is today, but Minecraft was also basically impossible to speedrun because it was an open-ended sandbox game, and there was no obvious event one could attain in the game to mark the completion of a 'run.' But the game is continually being updated and since then the game has added boss fights; while there are different speedrunning "categories," most speedruns end with the player defeating a boss called the Ender Dragon.

My rediscovery and interest in Minecraft was sparked by two factors:

### 1. The scandal

First, in December 2020, a prominent Minecraft speedrunner known as Dream was accused by the speedrunning community of cheating. Minecraft gameplay involves elements of randomness (killing hostile enemies drop items useful to the player with some probability). Dream received an exceptional sequence of item drops over a series of rns. The Minecraft Speedrunning Team (which "verifies" speedruns) released a [report](https://mcspeedrun.com/dream.pdf) that stating that the luck that Dream received was too good to be true, and concluded that Dream must have secretly modified his game in order to give himself better luck. Dream has denied all accusations but the community has generally agreed with the conclusions of the verifiers that Dream cheated. ([This article](https://www.polygon.com/2020/12/15/22176341/minecraft-youtube-dream-speedrun-cheating-mod-world-record-piglin) on *Polygon* provides a more detailed summary for anyone interested.)

The [report](https://mcspeedrun.com/dream.pdf) released by the Minecraft Speedrunning Team is an incredible artifact. It is thorough, precise, and rigorous; it explicitly tests the impact of various assumptions (i.e., conducts sensitivity analysis); and all calculations are reproducible. That is to say, it meets all criteria that one could reasonably want for this type of analysis. The central calculation relies on application of the [binomial theorem](https://www.statisticshowto.com/probability-and-statistics/binomial-theorem/binomial-distribution-formula/) (which should be familiar with any student of statistics or anyone who does data science professionally). So there was a nice application of my current line of work to the nostalgia kick of a hobby from ten years ago. 

The whole affair has the added bonus of getting a bunch of 14-year-olds to read up on the binomial formula. What a boon for math education! I can't think of a better backdoor way to get across that hey-you-might-actually-be-interested-in-algebra. One might wager that considering the reach of the scandal and analyses, at least one incremental future student will major in statistics. Thanks, Dream!

### 2. The grind

Second, I've always been drawn to stories of devotion to particular fields or hobbies, and the level of effort, talent, skill, practice required to become the best at a given vocation. (I don't think I've ever seen a snooker table in person, but I've been following the sport ever since reading about the amazing Ronnie O'Sullivan, "unhappy king of snooker," in a [2015 *New Yorker* article](https://www.newyorker.com/magazine/2015/03/30/follow-the-white-ball).) My interests in this span diverse fields like sports, business, art, music, politics, and literature, but also down the rabbit hole of some more esoteric subcultures. 

Minecraft in this day and age can hardly be called esoteric, but like most video games it can distinguish itself by its lack of barriers to entry: reaching the top of the field doesn't require any particular age, level of education, or other credentialing. Instead, it requires perseverance. Speedrunning (and Minecraft in particular) typically requires spending hours and hours "[grinding](https://en.wikipedia.org/wiki/Grinding_(video_games))" if one is seriously attempting to pursue a record. The top speedrunners play Minecraft [for upward of 6 hours per day](https://www.youtube.com/watch?v=XCl-dtcIVOM), and many have fandoms that follow and support them. (Unusually, when I started writing this piece, the current record holder had been "[unknown](https://www.youtube.com/watch?v=8gpazgyj_tE)" in the community. His record stood for about three weeks.)  Minecraft is not unlike any other field where those at the top must be devoted students of their craft.

## A framework for Minecraft speedrunning

Let's now develop a framework for Minecraft speedrunning, and what it takes to get the record. We can start by developing two concepts for our framework: *luck* and *skill*.

Luck in this context refers to factors outside the player's control (i.e., randomness). In Minecraft speedrunning, there are two main sources of luck: map generation and item drops. For the most popular Minecraft speedrunning category ("random seed glitchless"), the starting map that the player is placed on is procedurally generated (i.e., has randomness but follows certain preprogrammed rules). Most "seeds" (starting maps) will be inhospitable to speedrunners and impossible to set the record on. A player has to reset their game repeatedly to find a potential map that has the needed features required for a good speedrun. The second element of luck is item drops. When the player kills an enemy in the game, the enemy has a certain probability of dropping an item, some of which are needed to complete the speedrun. Dream was accused of modifying his game such that item drops occurred with greater frequency than was originally programmed.

Skill refers to factors in the player's control. What composes skill? We can list factors such as:

1. Mechanical knowledge: does the player have sufficient knowledge of the game mechanics to make correct decisions?
1. Decision-making: based on what is happening in the player's run, can they make the correct decisions that result in the highest probability of achieving a speedrunning record (e.g., mitigating bad luck or taking advantage of opportunities)?
1. Technical execution: can the player produce the series of inputs needed into my computer to accomplish what they are trying to achieve?
   
I'd exclude the ability to discover new strategies from the above list. Even though the strategic element is crucial to the game, any player competing publicly is typically posting his or her runs for others to see, so any strategic innovation that provides real benefits is likely to be picked up by others, negating much of the discoverer's initial advantage. In fact, one could classify innovations in speedrunning as a [public good](https://en.wikipedia.org/wiki/Public_good_(economics)): as a piece of knowledge, they meet the traditional public good criteria of being non-excludable (one can't prevent someone else from using a new speedrunning strategy) and non-rivalrous (using a new strategy doesn't "use it up" and prevent others from using it). (Of course, some types of knowledge can be made a non-public goods through legal regimes such as patents.)

So, we can think of the probability of setting a record on any given single speedrun as requiring a combination of luck and skill. The ratio of luck vs. skill will vary by game (and which components of skill matter will vary as well). For example, another game with a notable speedrunning community, Super Mario Bros., has a low luck to skill ratio. Setting the record requires an extremely high degree of technical execution and perfect timing of inputs into the controller. The levels in Super Mario Bros. are not procedurally generated, so what the player has to navigate is similar on each playthrough. Minecraft, on the other hand, has a much lower ratio of luck to skill. Any given speedrun will likely be impossible to set the record on due to factors entirely outside the player's control (primarily the map generation). Reacting to one's map optimally as one is exploring it for the first time is a key element of Minecraft skill (i.e., decision-making under uncertainty and with incomplete information).

Now let's generalize these ideas. For any given game:

- There is some minimum level of skill to have a nonzero chance of getting the speedrun record.
- As a player's skill increases, the player has a higher probability of getting the record.
- The relationship between a player's level of skill and their probability of setting a speedrun record (on a per run basis) depends on the level of luck required for the run.

In a game with no luck, the relationship between skill and record-setting probability (on a per-run basis) may look something like this:

![Figure 1](/images/speedrun/fig1.png)

A player needs a minimum level of skill to have any chance of setting the record, and then increasing skill will result in linearly increasing returns.

For some games, there may also be nonlinearity in the curve – for example, attaining a certain level of skill allows the player access to new strategies that dramatically increase one's record probability:

![Figure 2](/images/speedrun/fig2.png){:height:250px}

One example of this is in Super Mario Bros. – there are many difficult-to-execute techniques (such as the "[flagpole glitch](https://www.youtube.com/watch?v=oBxBaMW9riw)") that are now near must-haves to set the record.

However, in a luck-heavy game there will likely be diminishing marginal returns (in terms of record probability) to increasing skill. Inferior players have access to the same luck as superior players, and luck becomes an increasingly large component of the balance. Thus we might expect the shape of the curve for a luck-heavy game like Minecraft to look something like this:

![Figure 2](/images/speedrun/fig3.png)

The speedrunner's curse is that any run that actually achieves the record is likely to be extremely lucky, so the only way it can be beaten is by some combination of an even greater and more unlikely degree of luck, or developments in skill such that a player can beat the record by being more skillful and less lucky. The current record holder wrote in the description for his video: "[god seed, god rng](https://www.youtube.com/watch?v=H3m5ZL7Nd2I)". ("RNG" – random number generator – refers to elements of randomness outside the player's control in speedrunning.) For every record that is set, the next one becomes harder.

Because each successive record results in a lower probability of any subsequent run beating it, any serious speedruner has to devote themselves to the "grind," resetting the game again and again, playing through maps that have no chance of delivering a record because of their RNG, in search of the perfect seed. And, perhaps in parallel, diving into "R&D" – researching, testing, and perfecting new strategies that might fractionally increase one's probability of getting in the record books.

From the outsider's perspective it appears to be a Sisyphean task – but hopefully Minecraft fandom continues to support and encourage speedrunners, making it a little less lonely to do battle against the roll of the dice.