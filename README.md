# Statistical-Language-Model-of-the-Shakespeare-Corpus

In this project,  we build a Statistical Language Model using the public domain corpus of William Shakespeare

Statistical Language Models attempt to capture the likelihood that a given sequence of words occur in a given "language" (the precise term is "corpus" or "corpora").
Here, "language" is a broad term that, in addition to the normal usage, may mean the language of a particular author or style. 

We use the Shakespeare corpus as found on [Project Gutenberg](https://www.gutenberg.org/) for the pupose of this investigation. 
As with all statistical models, the true data generating process is never known and thus we cannot know the true probability that a sequence of words will occur – however, we can estimate these probabilities via various methods, some of which are more reliable than others. 
For example, one might guess that the probability of a sentence is simply the product of the empirical probabilities (i.e., the number of times a word is observed in a dataset divided by the number of words in that dataset). 
This is one of the methods of estimating the probability of a sequence of words that we implement in this project. 

## APPROACH

We build 3 different models using the given corpus: 
* Uniform Probabalistic Language Model
* Unigram Probabalistic Language Model
* N-Gram Probabalistic Language Model

### Model 1: Uniform Language Models


A uniform language model is one in which each **unique** word is **equally likely** to appear in any position, unconditional of any other information.

Let's put into context what this means by using the following example corpus:

py
>>> corpus = 'when I eat pizza, I smile, but when I drink Coke, my stomach hurts'
>>> tokenize(corpus)
['\x02', 'when', 'I', 'eat', 'pizza', ',', 'I', 'smile', ',', 'but', 'when', 'I', 'drink', 'Coke', ',', 'my', 'stomach', 'hurts', '\x03']



$$P(\text{when I drink Coke I smile}) = P(\text{when}) \cdot P(\text{I}) \cdot P(\text{drink}) \cdot P(\text{Coke}) \cdot P(\text{I}) \cdot P(\text{smile}) = \left( \frac{1}{14} \right)^6$$



### Model 2: Unigram Language Models

A unigram language model is one in which the **probability assigned to a token is equal to the proportion of tokens in the corpus that are equal to said token**. That is, the probability distribution associated with a unigram language model is just the empirical distribution of tokens in the corpus. 

Let's understand how probabilities are assigned to tokens using our example corpus from before.

py
>>> corpus = 'when I eat pizza, I smile, but when I drink Coke, my stomach hurts'
>>> tokenize(corpus)
['\x02', 'when', 'I', 'eat', 'pizza', ',', 'I', 'smile', ',', 'but', 'when', 'I', 'drink', 'Coke', ',', 'my', 'stomach', 'hurts', '\x03']

$$P(\text{when I drink Coke I smile}) = P(\text{when}) \cdot P(\text{I}) \cdot P(\text{drink}) \cdot P(\text{Coke}) \cdot P(\text{I}) \cdot P(\text{smile}) = \frac{2}{19} \cdot \frac{3}{19} \cdot \frac{1}{19} \cdot \frac{1}{19} \cdot \frac{3}{19} \cdot \frac{1}{19}$$

### N-Gram Language Models

Now we will build an N-Gram language model, in which the probability of a token appearing in a sentence **does depend** on the tokens that come before it. 

The chain rule above specifies that the probability that a token occurs at in a particular position in a sentence depends on **all** previous tokens in the sentence. However, it is often the case that the likelihood that a token appears in a sentence is influenced more by **nearby** tokens. (Remember, tokens are words, punctuation, or `'\x02'` / `'\x03'`).

The N-Gram language model relies on the assumption that only nearby tokens matter. Specifically, it assumes that the probability that a token occurs depends only on the previous $N-1$ tokens, rather than all previous tokens. That is:

$$P(w_n|w_1,\ldots,w_{n-1}) = P(w_n|w_{n-(N-1)},\ldots,w_{n-1})$$

To train an N-Gram model, we must compute a conditional probability for every $N$-token sequence in the corpus. For instance, suppose again that we are training a trigram model. Then, for every 3-token sequence $w_1, w_2, w_3$, we must compute $P(w_3 | w_1, w_2)$. To do so, we use:

$$P(w_3 | w_1, w_2) = \frac{C(w_1, w_2, w_3)}{C(w_1, w_2)}$$
