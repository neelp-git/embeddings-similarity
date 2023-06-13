# An Experiment with Similarity Search and Embeddings
 Do LLM embeddings truly capture sentence semantics? Do similarity functions such as cosine and Euclidean distance truly represent semantic similarity?

To answer these questions, albeit in a limited way (and perhaps more to validate them), we set up an experiment as described below. Follow along in [the accompanying Jupyter notebook](https://github.com/neelp-git/embeddings-similarity/blob/main/similarity.ipynb).

## Experiment

1. Write an interesting sentence. 
2. Add many variations of the sentence without changing the core meaning or semantics. (ChatGPT was used for this purpose.)
3. Add other variations that have similar words or subject, but are clearly dissimilar in meaning. 
4. Perform a semantic search with a query sentence that is similar to the original sentence. Use different similarity functions. 
5. Compute accuracy of the similarity function using the formula (n - d)/n, where n is the total number of similar sentences and d is the number of non-similar sentences in the top n results.

We used Hugging Face's LLM 'all-MimiLM-L6-v2' to generate embeddings. We used cosine and dot product similarity functions from sentence_transformer.util library, and computed the Euclidean distance with numpy's numalg.norm function.

## Results and caveats
We performed two searches with two query sentences. Both searches yielded 83% accuracy with n=6 and d=1. Interestingly, accuracy scores were identical for cosine, dot matrix, and Euclidean distance similarity. (The latter perhaps should be expected for a very small dataset.)

This was admittedly a very limited experiment, and clearly no conclusion should be drawn. The main goal was to experiment with the tools and confirm the intuition behind semantic vector proximity in the embeddings space. We can say that these goals were achieved.

## Code
You can view the code and results in [this](https://github.com/neelp-git/embeddings-similarity/blob/main/similarity.ipynb) Jupyter notebook.

## Next step
As a next step, we will explore other tools (LLMs and vector databases) possibly with bigger dataset for further validation.