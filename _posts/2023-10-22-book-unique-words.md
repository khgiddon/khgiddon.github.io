---
layout: post
title: "Joyce's Ulysses stands alone, or: word uniqueness in some canonical books"
---

While I'm (slowly) writing my own novel, I've tried to vary my own reading this year to include authors with different styles for some diversity of inspiration. It's been a pleasure to flit back and forth between, for instance, Pynchon and DeLillo and Tolstoy. *Le style c'est l'homme même,* as the French naturalist Buffon said: style is the man himself.

One element of literary style is diction (word choice) and one subelement of diction is the variety of words used, which can be quantified. This is not to say that all elements of diction can be quantified, or that a writer who uses more distinct words is a better writer, but only that quantitative analysis can reveal or confirm elements of a writer's style.

Using the online [Project Gutenberg library](https://www.gutenberg.org/), I've analyzed the text of some canonical books in the public domain to look at how the *distinct* word count grows with the total word count. A distinct word is a word that appears at least once in the text, and the distinct word count is the number of distinct words in the text. The total word count is the number of words in the corpus, including repeated words. I ignore case and punctuation (except hyphens) and a hyphenated word is considered one combined distinct word.

My selection of books was somewhat arbitrary—I looked at the top 100 most downloaded books and filtered to a subset of the list that I considered most renowned, and I wanted to keep the number small enough where individual trajectories could be seen when graphed. (See appendix for the list of books.) It would benefit from a more rigorous implementation in any future extensions.

Results are below.

![Distinct word count vs. total word count](/images/book_word_count.png)

A few observations:

1. *Ulysses* stands alone in terms of its distinctness—the shape of the function does not resemble any other books of similar length. This is unsurprising and matches the "eye test," given Joyce's use of neologisms and portmanteaus, e.g. "psychophysicotherapeutics" and (even better) "scrotumtightening."
2. *Little Women* follows nearly the exact same trajectory of *War and Peace* up until its end.
3. Two of the great Russian novels, *The Brothers Karamazov and *Anna Karenina*, have nearly identical trajectories.
4. A couple authors are represented here twice. Dostoyevsky's *The Brothers Karamazov* and *Crime and Punishment* have similar trajectories, but Tolstoy's *War and Peace* has more unique words versus *Anna Karenina* when comparing similar counts of cumulative words.

### Appendix: Code and replication materials

Book texts were scraped and analysis was done using Python. The code for this post is available on [GitHub](https://github.com/khgiddon/misc/tree/main/book_vocabulary/web_test).

The books represented in the graph are:

- Adventures of Huckleberry Finn by Mark Twain
- Anna Karenina by Leo Tolstoy
- Crime and Punishment by Fyodor Dostoevsky
- Dracula by Bram Stoker
- Emma by Jane Austen
- Great Expectations by Charles Dickens
- Little Women by Louisa May Alcott
- Middlemarch by George Eliot
- Moby Dick; Or, The Whale by Herman Melville
- Pride and Prejudice by Jane Austen
- The Brothers Karamazov by Fyodor Dostoevsky
- A Tale of Two Cities by Charles Dickens
- Ulysses by James Joyce
- War and Peace by Leo Tolstoy