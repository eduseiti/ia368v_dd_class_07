# ia368v_dd_class_07
Dense Passage Retriever implementation.

## Notebooks created for this activity:

* [DensePassageRetriever.ipynb](DensePassageRetriever.ipynb): DPR implementation using 2 encoders, as the original [paper](https://arxiv.org/abs/2004.04906).

* [DensePassageRetriever_single_model.ipynb](DensePassageRetriever_single_model.ipynb): DPR implementation using a single encoder for both passages and queries.

* [validate_DPR_TREC_COVID.ipynb](validate_DPR_TREC_COVID.ipynb): Trained DPR validation, using FAISS-GPU to index only the documents listed in the TREC-COVID QRELS, applying the encoder to the **title + text** concatenation.

* [DPR_TREC_COVID.ipynb](DPR_TREC_COVID.ipynb): DPR complete pipeline for TREC-COVID queries and documents dataset, still using FAISS-GPU.

* [exhaustive_search.ipynb](exhaustive_search.ipynb): Applying the exhaustive search to rerank TREC-COVID documents, using encoded data produced by the previous notebook, just to check if there are differences when compared to FAISS-GPU.


## Referred notebooks from other exercises:

This exercise resolution has dependencies on the following notebooks from the [previous exercise](https://github.com/eduseiti/ia368v_dd_class_06):

* [explore_trec_covid.ipynb](https://github.com/eduseiti/ia368v_dd_class_06/blob/main/explore_trec_covid.ipynb): TREC COVID dataset preparation for expansion and Pyserini's BM25 processing.

* [explore_ms_marco_passage.ipynb](https://github.com/eduseiti/ia368v_dd_class_06/blob/main/explore_ms_marco_passage.ipynb): Prepare MS MARCO Passage Development dataset to fine-tune T5-base for doc2query, attempting to have more data (~532k).


## Results

These are the main results, obtained accross different experiments/explorations:


|    | eval loss | nDCG@10 | |
|----|:---: |:---: |:---: |
| 2 encoders, batch=32,<br/>higher reranking score<br/>QRELS docs only| 0.0721 | 0.5861|
| 2 encoders, batch=32,<br/>higher reranking score | 0.0721 | 0.3187 |
| 2 encoders, batch=32,<br/>mean reranking score | 0.0721 | 0.3197 |
| 2 encoders, batch=32,<br/>mean reranking score<br/>200k data | 0.0528 | 0.3049 |
| 1 encoder, batch=32,<br/>mean reranking score<br/>200k data | 0.0495 | 0.3214 |
| 1 encoder, batch=32,<br/>mean reranking score<br/>400k data<br/>epoch end eval | 0.0379 | 0.3310 | epoch 0 |
| 1 encoder, batch=32,<br/>mean reranking score<br/>400k data<br/>during epoch eval | 0.0294 | 0.3104 | between epochs 1 and 2 |
| 1 encoder, batch=32,<br/>mean reranking score<br/>400k data<br/>epoch end eval | 0.0537 | 0.3783 | epoch 2 |
| 1 encoder, batch=128,<br/>mean reranking score<br/>400k data<br/>epoch end eval | 0.0689 | **0.3844** |

<br/>

Check [here a presentation](https://docs.google.com/presentation/d/1KO3AMiQLrfFaTogyeBww7c4VteSd910o61kKATEwqSs/edit?usp=share_link) commenting this exercise resolution.

