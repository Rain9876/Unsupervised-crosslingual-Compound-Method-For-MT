# Compound Metrics (Semantic Sentence Cosine Similarity + WMD / BERTScore)



## Combination Method

+ **Compound Scores = exp(A) + exp(B)**  where A and B are normalized metrics.

If Metric A, like WMD, WMDo metric, is negative correlated to our target, we give it exp(1-A), which makes sure that 1-A is still normalized in the range 0 to 1. Otherwise, using exp(A) like other positively correlated metric.



## Performance

Most popular Metrics for evaluation Machine translation: 

+ WMD 

+ Semantic Sentence Cosine Similarity

+ [BERTScore](https://github.com/Tiiiger/bert_score)

  

### Source to Machine Translation

#### XLM-Roberta Models

+ WMD: XLM-Roberta-base

+ Cosine Similarity: [XLM-Roberta-base-nli-stsb-mean-tokens](https://github.com/UKPLab/sentence-transformers)

+ BERTScore: XLM-Roberta-base

  

[Multi30K](https://github.com/multi30k/dataset)

| Metric | ende (pearson) | enfr (pearson) |
| ------ | -- | -- |
| wmd | 36.046 | 31.851 |
| Similarity  | 48.304  | 44.708 |
| Bert score | 33.491 | 29.024 |
| Similarity + wmd| **49.870** | **44.981**  |
| Similarity + Bert score |48.562 |43.325 |
| Bert score + wmd |36.668 |32.020 |



[WMT-17 segment level](http://www.statmt.org/wmt17/)

| Metric                  | deen       | zhen       | fien       | lven       | ruen       | csen       | enru       | enzh       | tren       | Avg        |
| ----------------------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| wmd                     | 36.616     | 50.062     | 37.291     | 37.292     | 30.779     | 26.677     | 40.449     | 40.786     | 35.042     | 37.222     |
| Similarity              | 45.648     | 51.398     | 54.030     | 55.511     | 54.121     | 46.416     | 50.534     | 45.779     | 54.044     | 50.831     |
| Bert score              | 40.903     | 50.991     | 41.351     | 40.159     | 33.656     | 31.914     | 43.390     | 44.568     | 38.155     | 40.565     |
| Similarity + wmd        | 50.422     | 59.424     | 56.590     | 56.910     | 53.420     | 47.619     | 53.759     | 51.297     | 56.237     | 53.964     |
| Similarity + Bert score | **52.267** | **60.030** | **57.847** | **57.430** | **55.101** | **49.909** | **55.272** | **53.140** | **56.841** | **55.315** |
| Bert score + wmd        | 38.451     | 49.292     | 37.584     | 36.711     | 32.158     | 29.124     | 41.028     | 42.155     | 33.647     | 37.794     |



[WMT-20 quality estimation task](http://www.statmt.org/wmt20/quality-estimation-task.html)

| Metric                  | neen       | ende       | eten       | enzh       | roen       | sien       | ruen       | Avg        |
| ----------------------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| wmd                     | 36.107     | 45.643     | 46.322     | 25.103     | 64.656     | 30.831     | 31.538     | 40.029     |
| Similarity              | 31.294     | 33.042     | 48.099     | 40.063     | 69.402     | 40.417     | 44.134     | 43.779     |
| Bert score              | 35.700     | 45.928     | 45.950     | 25.980     | 67.289     | 30.906     | 31.965     | 40.531     |
| Similarity + wmd        | 38.967     | 47.229     | 55.256     | **42.683** | 72.431     | 42.588     | **47.582** | 49.534     |
| Similarity + Bert score | **39.237** | **48.364** | **55.319** | 42.664     | **72.664** | **42.604** | 47.508     | **49.766** |
| Bert score + wmd        | 36.431     | 45.568     | 45.831     | 25.419     | 64.543     | 33.126     | 32.032     | 40.421     |



### References to Machine Translation

+ WMD Model: Roberta-Large
+ Cosine similarity: Roberta-Large-nli-stsb-mean-tokens
+ Bert Score Model: Roberta-Large

Multi30K
| Metric                     | dede       | frfr       | Avg        |
| -------------------------- | ---------- | ---------- | ---------- |
| wmd                        | 49.240     | 42.491     | 45.866     |
| Cos Similarity             | 48.672     | 44.636     | 46.654     |
| Bert_Score                 | 43.389     | 35.205     | 39.297     |
| Cos Similarity + wmd       | **54.584** | **50.132** | **52.358** |
| CosSimilarity + Bert_score | 52.653     | 46.153     | 49.403     |
| Bert_Score + wmd           | 49.379     | 42.433     | 45.906     |
                                                                    with XLM-Roberta-Base embedding

WMT-17

| Metric                      | deen       | zhen       | fien       | lven       | ruen       | csen       | tren       | Avg        |
| --------------------------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| wmd                         | 73.005     | 76.905     | 82.741     | 73.610     | 73.259     | 69.845     | 76.974     | 75.191     |
| Cos Similarity              | 61.229     | 65.334     | 72.984     | 70.286     | 69.987     | 62.232     | 65.355     | 66.772     |
| Bert_Score                  | 74.479     | 77.477     | 83.324     | 75.636     | 74.555     | 70.971     | 75.083     | 75.932     |
| Cos Similarity + wmd        | 75.526     | 77.924     | 84.688     | 78.068     | 78.645     | 73.144     | 78.093     | 78.013     |
| Cos Similarity + Bert_score | **76.988** | **78.503** | **86.010** | **79.210** | **79.638** | **74.616** | **78.216** | **79.026** |
| Bert_Score + wmd            | 73.889     | 77.055     | 84.113     | 74.975     | 74.189     | 70.599     | 77.728     | 76.078     |



## Others

WMT17 with Roberta-Base

| Metric                      | deen      | zhen      | fien      | lven      | ruen      | csen      | tren      | Avg       |
| --------------------------- | --------- | --------- | --------- | --------- | --------- | --------- | --------- | --------- |
| wmd                         | 0.667     | 0.743     | 0.818     | 0.693     | 0.705     | 0.663     | 0.744     | 0.719     |
| Cos Similarity              | 0.612     | 0.655     | 0.705     | 0.680     | 0.642     | 0.599     | 0.644     | 0.648     |
| Bert_Score                  | 0.683     | 0.740     | 0.818     | 0.693     | 0.707     | 0.675     | 0.718     | 0.719     |
| Cos Similarity + wmd        | 0.718     | **0.767** | 0.832     | **0.755** | 0.736     | 0.703     | **0.764** | 0.754     |
| Cos Similarity + Bert_score | **0.728** | **0.767** | **0.843** | **0.755** | **0.744** | **0.717** | 0.758     | **0.759** |
| Bert_Score + wmd            | 0.678     | 0.740     | 0.824     | 0.693     | 0.703     | 0.670     | 0.745     | 0.722     |



### Conclusion:

+ For one metric
  + Semantic Sentence Cosine similarity shows the worst performance in the WMT-17, Multi-30K in case of REF-MT and shows the best performance in case of SRC-MT
  + In general, Bert score completely outperforms than other two metrics
+ For two metrics
  + For BERTScore + WMD,  the performance drops for majority cases in comparsion to BERTScore
    + Both of them are the token level computation
    + The performance of BERTScore + WMD is lower than bert_score unless WMD achieves better performance than bert score 
  + Similarity + Bert score completely outperforms the other two combinations
+ For three metrics
  + Similarity + Bert score + wmd still works but not consistent in all language pairs due to the performance gap between three metrics. The performance dramtically improved unless their performance are close each other.