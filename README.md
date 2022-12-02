# Statistical-Language-Model-of-the-Mahabharata

In this project,  we build a Statistical Language Model using the public domain corpus of the Rāmāyana.
The Rāmāyana is a Sanskrit epic composed by the poet Vālmīki around the 4th century BCE. Given the ancient origins of the text, we will use a Statistical Language Model to xplore the question of 'textual interpolations', i.e an entry or passage in a text that was not written by the original author. 


Statistical Language Models attempt to capture the likelihood that a given sequence of words occur in a given "language" (the precise term is "corpus" or "corpora").
Here, "language" is a broad term that, in addition to the normal usage, may mean the language of a particular author or style. We use the RAmayana corpus as found on [Project Gutenberg](https://www.gutenberg.org/) for the pupose of this investigation. 
As with all statistical models, the true data generating process is never known and thus we cannot know the true probability that a sequence of words will occur – however, we can estimate these probabilities via various methods, some of which are more reliable than others. 
For example, one might guess that the probability of a sentence is simply the product of the empirical probabilities (i.e., the number of times a word is observed in a dataset divided by the number of words in that dataset). 
This is one of the methods of estimating the probability of a sequence of words that we implement in this project. 
