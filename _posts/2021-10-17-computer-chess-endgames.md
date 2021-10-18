---
layout: post
title: Machine beats man on ancient front
---

The computer scientist Ken Thompson has an unusual distinction: his research has changed the rules of chess. Thompson has a [rich resume](https://en.wikipedia.org/wiki/Ken_Thompson), but it's quite a feather in one's cap to lay claim to changing a game that's existed for hundreds of years. Specifically, Thompson's work on chess endgames carved out several exceptions to the long-standing *fifty-move rule.* At least, his work did until Thompson's discoveries became too numerous, and chess's overlords threw up their hands and said they were getting rid of the computer-aided exceptions entirely.

### Endgames in computer chess

Thompson was one of the early pioneers of programming computers to play chess. He describes his involvement with the game in a  [fascinating oral history from 2005](http://archive.computerhistory.org/resources/text/Oral_History/Thompson_Ken/thompson.oral_history_transcript.2005.102657921.pdf). I'd recommend reading in full for any enthusiasts of either computer science or chess (and enthusiasts of both of these might find appropriately multiplicative enjoyment), but the big highlight is in the discussion of chess endgames. 

Endgames are the stage of a chess game where there are few pieces still left on the board. Around 1975, Thompson was speaking to another chess player who claimed that computers effectively had no chance of winning complex endgames. Thompson then spent the next ten years working on endgames, and proved his interlocutor incorrect.

Computer programs assess chess positions using an evaluation algorithm. A basic evaluation algorithm might be simply counting each player's number of pieces; a slightly more complex algorithm might assign numerical value to each type of piece. For example, a queen might be worth nine points in an evaluation function, and a knight worth only three. The evaluation functions get much more complex and might consider factors such as pawn structure, king safety, mobility, and more.

Computers then choose which move is best by searching for legal moves and running the evaluation function on the subsequent tree of possibilities can result from those legal moves. For example, on one player's turn, there might be 20 legal moves, and each of those 20 legal moves might lead to 20 more legal moves, and so on. While there are algorithmic tactics to speed up the search, the number of positions to potentially evaluate grows exponentially, so computers are fixed in the "depth" of their search by their memory and processing power.

At the time of Thompson's conversation, chess-playing computers were being used but were nowhere close to the skill of the best players. (Today, the converse is true, where the best players have effectively no chance of winning a set of games vs. the best chess computers.) In the 1970s, the best computers searched for moves at a depth of four ply (four "half moves" each time a player moves a piece). It was clear that many chess endgames required strategy and evaluation at a depth much greater than four ply or even eight ply, hence the idea that computers could never solve endgames. 

But as Thompson describes, he then thought that you could "absolutely solve [an endgame] by a different mechanism ... not by normal computer chess, You could just have the answer and look it up. You could make a table for everything that you’re supposed to do." Essentially, you could work backward from the simplest endgames and solve sub-problems:

> So the method is to lay out a chess board that has two kings on it and then look for all the positions that two kings can -- all combinations   positions of the two kings can be there -- and find which ones are mates. And surprise!, you’ll find none of them are mates, right. So then you put a king and a queen  against the king and you find all the mates in there, so then you have a list of all the mates in one. And then you build — instead of a move generator you build an unmove generator where you find all the positions that can arise from that. A move is like a very strange move, sometimes uncastling and stuff like that. But basically it’s just a move generator with different rules. So you find all positions that you can force the mates that you found in the last pass in two ply and then you do that again and again and again and again, and when you find no more, everything you didn't find is a draw. So you do it by exhaustive search, one ply at a time back from the
terminal positions, from the end positions.

Using this method, Thompson constructed endgame tablebases, where from a given board position, he could determine whether with ideal play from both players, the position was a win, loss, or draw, and how to achieve that result. In the 1980s, Thompson was able to compute this for all four-piece positions and five-piece positions. By his interview in 2005, all six-piece positions were solved, by the next generation of algorithms. As of the writing of this post in 2021, all seven-piece positions have been solved, and [some positions from the eight-piece tablebases are in progress](https://www.chess.com/blog/Rocky64/eight-piece-tablebases-a-progress-update-and-some-results). (It's been [estimated](https://www.chessprogramming.org/Syzygy_Bases) that running the full calculations for the eight-game tables would require approximately $700,000 of computing power today.)

Thompson [published his tablebases](https://www.chessprogramming.org/Endgame_Tablebases) under the caption "Play Chess with God." Reviewing some optimal endgame plays, the chess player Tim Krabbé [explained](https://research.swtch.com/chess) that:

> Playing over these moves is an eerie experience. They are not human; a grandmaster does not understand them any better than someone who has learned chess yesterday. The knights jump, the kings orbit, the sun goes down, and every move is the truth. It's like being revealed the Meaning of Life, but it's in Estonian.

The *New York Times* devoted [a story in 1986](https://www.nytimes.com/1986/08/26/science/machine-beats-man-on-ancient-front.html) to Thompson's tablebases  with the headline "MACHINE BEATS MAN ON ANCIENT FRONT." (Man, they truly don't write headlines like they used to.) One grandmaster is quoted: "By dint of brute force, the program has unearthed all kinds of results which eluded us. It was mindboggling for me."

Aesthetic considerations aside, Thompson's endgame tables also ran up against some long-held assumptions in the chess world, and posed problems for the fifty-move rule.

### The fifty-move rule

The fifty-move rule is a chess rule designed to speed up chess games in drawn positions. The rule currently states that either player can claim a draw if there have been no pawn movements and no captures within the previous fifty moves. (While I think it is safe to say that the fifty-move rule comes into play only rarely at the top level of chess, I couldn't find any exact statistics on how often the rule is applied. If you know of a source for this, please drop me a line!) The rule has a [rich history](https://en.wikipedia.org/wiki/Fifty-move_rule), with citations back to the sixteenth century, and with conditions resembling the modern rule put in place at a top London chess tournament in 1883.

At the time of the rule's formal inception in the 19th century, it was believed all winnable endgames could be won without exceeding the 50 moves given. In the early 20th century, players found several endgames (e.g., rook and bishop versus a rook) where a winning position might require more than 50 moves to complete. In 1965, chess's governing body, FIDE, then revised the rules in 1965 to account for this, stating that "the [maximum] number of moves can be increased for certain positions, provided that this increase in number and these positions have been clearly established before the commencement of the game." 

The problem was that Thompson's work on endgame tables kept turning up more and more examples of specific positions where more than 50 moves were required to convert a winning endgame. So, as Thompson notes, in the 1980s and 1990s, FIDE started adding an increasing number of exceptions to the 50-move rule in response to the endgame tables. Eventually, in the mid-1990s, the exceptions became too numerous and FIDE removed *all* exceptions. Back to fifty moves it became. As Thompson says, if you can't win in fifty moves, tough. 

So the tablebases continue to expand, though by the current rules any forced win exceeding fifty moves would not be able to be played in a game. As of early 2021, the longest known endgame that can be forced to a winning conclusion is 400 moves. There almost certainly exists a longer actual endgame, with more pieces, waiting to be discovered.






