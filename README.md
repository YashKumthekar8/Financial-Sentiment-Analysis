This repository releases the code for stock movement prediction from tweets and historical stock prices.

> Stock movement prediction is a challenging problem: the market is highly *stochastic*, and we make *temporally-dependent* predictions from *chaotic* data. We treat these three complexities and present a novel deep generative model jointly exploiting text and price signals for this task. Unlike the case with discriminative or topic modeling, our model introduces recurrent, continuous latent variables for a better treatment of stochasticity, and uses neural variational inference to address the intractable posterior inference. We also provide a hybrid objective with  temporal auxiliary to flexibly capture predictive dependencies. We demonstrate the state-of-the-art performance of our proposed model on a new stock movement prediction dataset which we collected.

## Directories
- src: source files;
- res: resource files including,
    - Vocabulary file `vocab.txt`;
    - Pre-trained embeddings of [GloVe](https://github.com/stanfordnlp/GloVe). We used the GloVe obtained from the Twitter corpora which you could download [here](http://nlp.stanford.edu/data/wordvecs/glove.twitter.27B.zip).
- data: datasets consisting of tweets and prices which you could download [here](https://github.com/yumoxu/stocknet-dataset).

## Configurations
Model configurations are listed in `config.yml` where you could set `variant_type` to *hedge, tech, fund* or *discriminative* to get four corresponding model variants, HedgeFundAnalyst, TechincalAnalyst, FundamentalAnalyst or DiscriminativeAnalyst described in the paper. 

Additionally, when you set `variant_type=hedge, alpha=0`, you would acquire IndependentAnalyst without any auxiliary effects. 

## Running

After configuration, use `sh src/run.sh` in your terminal to start model learning and test the model after the training is completed. If you would like to do them separately, simply comment out `exe.train_and_dev()` or `exe.restore_and_test()` in `Main.py`.
