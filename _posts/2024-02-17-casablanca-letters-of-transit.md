---
layout: post
title: Who signed the letters of transit in Casablanca? A not-wholly-necessary Bayesian approach
usemathjax: true
---

Last month, I was rewatching the great 1942 film *Casablanca* (as one does). Early on, the character Ugarte introduces the central [MacGuffin](https://en.wikipedia.org/wiki/MacGuffin) of the plot: the "letters of transit" that allow the bearer to move freely through Vichy or occupied territory. Watching with subtitles, I had to pause after this line:

![Letters of transit signed by General de Gaulle](/images/casablanca/letters_of_transit.png)

Letters of transit signed by General de Gaulle? This doesn't make much sense. Charles de Gaulle was the leader of the Free French forces, and his signature on certain papers would mean nothing in Vichy-controlled French West Africa, where the film is set.

I'm not the first to notice this. This [convincing blog post by Richard Langworth](https://richardlangworth.com/darlan-degaulle-casablanca) argues that the subtitle is a mistake, and the line says the letters are signed by General *Weygand*, not de Gaulle.  [Maxime Weygand](https://en.wikipedia.org/wiki/Maxime_Weygand) was the Vichy government's Delegate-General in French North Africa—which makes perfect sense in the context of the film. (Ugarte is played by the Hungarian-accented Peter Lorre, and it's not entirely clear whether he says "de Gaulle" or "Weygand" in the original audio.)

We can ask the question in terms of [Bayesian inference](https://en.wikipedia.org/wiki/Bayesian_inference). Given the evidence of the subtitle saying "General de Gaulle", what is the probability that Ugarte says "de Gaulle" in the actual film?

Let's define the following terms:

- $$P(D)$$: The prior probability that Ugarte says "de Gaulle" in the film.
- $$P(S\mid D)$$: The probability that the subtitle says "de Gaulle" given that Ugarte says "de Gaulle" in the film.
- $$P(S\mid\neg D)$$: The probability that the subtitle says "de Gaulle" given that Ugarte does *not* say "de Gaulle" in the film.


Given this, we want to solve for $$P(D\mid S)$$, the probability that Ugarte says "de Gaulle" in the film given that the subtitle says "de Gaulle".

What values should we assign to these terms?

Because the subtitle clearly says "de Gaulle", we can assume that $$P(S\mid D) = 1$$. That is, if the line is "de Gaulle", the subtitle will certainly say "de Gaulle".

The other probabilities don't have obvious values. We don't have the script handy. We'll make a chart of the possible values of $$P(D)$$ and $$P(S\mid\neg D)$$, and then solve for $$P(D\mid S)$$ depending on these values.

To solve for the probability that Ugarte says "de Gaulle" in the film given that the subtitle says "de Gaulle", we can use Bayes' theorem:

$$
P(D|S) = \frac{P(S|D)P(D)}{P(S)}
$$

We can also write $$P(S)$$ in terms of $$D$$ and $$\neg D$$:

$$
P(S) = P(S|D)P(D) + P(S|\neg D)P(\neg D)
$$

After doing so, we get the following result (code is available [here](https://github.com/khgiddon/casablanca-letters-of-transit)):

![Letters of transit signed by General de Gaulle](/images/casablanca/output_images.png)


Now, what probabilities should we assume for $$P(D)$$ and $$P(S\mid\neg D)$$? 

I assign high prior probability to Ugarte *not* saying de Gaulle, because the line does not make sense and there is an alternative (Weygand) that does make make sense. de Gaulle was famous at the time and one thinks it likely that someone on set would have noticed the error. I'd put $$P(D) = 0.05$$.

For $$P(S\mid\neg D)$$, or the probability that the subtitle says "de Gaulle" given that Ugarte does not say "de Gaulle," I'd put $$P(S\mid\neg D) = 0.5$$. If the subtitle writer was not looking at the script and was not sure what Ugarte said, they might have guessed "de Gaulle" because it's a much more famous name than Weygand, and may have been unfamiliar with the latter.

Using these inputs gives us $$P(D\mid S) = 0.095$$. That is, a 9.5% chance that Ugarte says "de Gaulle" in the film given that the subtitle says "de Gaulle." Substitute your own assumptions as you see fit! 

I'd argue that there's a much greater historical plot hole in the film—the question of why the Nazi officer Major Strasser does not arrest (or assassinate) Laszlo. Vichy would not be enough to protect him. The "answer" to that one is probably that there would not be nearly so compelling a movie if that were the case. True. All is forgiven.

