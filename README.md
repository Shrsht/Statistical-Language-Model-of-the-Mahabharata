# Statistical-Language-Model-of-the-Shakespeare-Corpus

In this project,  we build a Statistical Language Model using the public domain corpus of William Shakespeare

Statistical Language Models attempt to capture the likelihood that a given sequence of words occur in a given "language" (the precise term is "corpus" or "corpora").
Here, "language" is a broad term that, in addition to the normal usage, may mean the language of a particular author or style. 

We use the Shakespeare corpus as found on [Project Gutenberg](https://www.gutenberg.org/) for the pupose of this investigation. 
As with all statistical models, the true data generating process is never known and thus we cannot know the true probability that a sequence of words will occur – however, we can estimate these probabilities via various methods, some of which are more reliable than others. 
For example, one might guess that the probability of a sentence is simply the product of the empirical probabilities (i.e., the number of times a word is observed in a dataset divided by the number of words in that dataset). 
This is one of the methods of estimating the probability of a sequence of words that we implement in this project. 
