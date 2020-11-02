# Compound Metrics (WMD + Cosine Similarity)



## Performance

Most popular Metrics for evaluation Machine translation: 

+ WMD
+ Sentence Cosine Similarit 
+ Bert score



### Source to Machine Translation

#### XLM-Roberta Models

+ Wmd: XLM-Roberta-base

+ Cosine Similarity: XLM-Roberta-base

+ Bert-Score: XLM-Roberta-base

  

Pascal-50S

| Metric | de (pearson/spearman) | fr (pearson/spearman) |
| ------ | -- | -- |
| wmd | 36.046 / 38.470 | 31.851 / 36.304 |
| Similarity  | 48.304 / 52.001 | 44.881 / 57.697 |
| Bert score | 33.491 / 38.209 | 29.083 / 36.932 |
| Similarity + wmd| **50.813** / **53.280** | **47.701** / **58.267** |
| Similarity + Bert score |48.562 / 53.064|43.448 / 56.287|
| Bert score + wmd |36.248 / 38.408|32.239 / 36.891|
| Similarity + Bert score + wmd |47.949 / 52.676|42.624 / 54.730|



WMT-17

| Metric | deen  | zhen  | fien | lven | ruen | csen | enru | enzh |tren|
| ------ | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| wmd  | 36.614 / 35.519 | 50.062 / 50.429 |37.291 / 40.765|37.292 /  39.479|30.779 / 33.574|26.677 / 27.796|40.449 / 39.047|40.786/ 39.736|35.042 / 47.323|
| Similarity  | 45.648 / 49.684 | 51.398 / 53.159 |54.030 / **61.786**|55.511 / 56.442|54.121 / 50.829|46.416 / 49.051|50.534 / 51.355|45.779 / 45.581|54.044 /  61.965|
| Bert score | 40.903 / 40.353 | 50.991 / 51.025 |41.351 / 43.864|40.159  /  39.743|33.656 / 35.356|31.914 / 31.096|43.390 / 41.237|44.568 / 43.439|38.155 / 46.238|
| Similarity + wmd| 50.391 / 50.400 | 58.072 / 57.758 |**58.193** / **61.466**|**58.732** / **57.148**|**57.303** / **53.630**|**49.986** / **50.919**|**55.324** / **52.244**|50.303 / 49.132|**57.472** / **62.094**|
| Similarity + Bert score	| **52.267** / **50.990** |**60.030** / **59.172**|57.847 / 60.068|57.430 / 55.289|55.101 / 52.057|49.909 / 48.803|55.272 / 51.359|**53.140** / **52.522**|56.841 / 61.675|
| Bert score + wmd |39.480 / 39.295|49.600 / 51.003|38.616 / 43.243|37.428 / 39.828|32.931 / 35.063|30.345 / 30.264|41.791 / 40.670|43.059 / 42.596|34.671 / 46.751|
| Similarity + Bert score + wmd |51.275 / 49.761|59.526 / 58.521|56.220 / 58.754|55.768 / 54.434|52.374 / 50.218|47.699 / 46.689|53.630 / 50.086|52.447 / 51.900|55.504 / 61.334|



WMD-20

| Metric | neen | ende | eten | enzh | roen | sien | ruen |
| ------ | -- | -- | -- | -- | -- | -- | -- |
| wmd  | 36.107 / 37.945 | 45.643 / 45.388 |46.322 / 43.328|25.103 / 21.013|64.656 / 55.505|30.831 / 33.413|31.538 / 28.832|
| Similarity  | 31.294 / 33.881 | 33.042 / 37.848 |48.099 / 48.798|40.063 / 41.007|69.402 / 57.353|40.417 / 38.677|44.134 / 45.868|
| Bert score | 35.700 / 37.089 | 45.928 / 45.017 |45.950 / 42.827|25.980 / 21.709|67.289 / 56.603|30.906 / 35.261|31.965 / 29.546|
| Similarity + wmd| 35.656 / 37.192 | 41.951 / 43.712 |52.576/ 51.716|42.259 / **42.199**|71.138 / 61.133|41.561 / 40.242|**47.889** / **46.216**|
| Similarity + Bert score	| 39.237 / 40.605 |48.364 / 47.784|55.319 / 53.048|**42.664** / 41.689|72.664 / 62.359|42.604 / 42.292|47.508 / 43.644|
| Bert score + wmd |36.230 / 37.465|45.849 / 45.169|45.731 / 43.162|25.778 / 21.594|65.397 / 56.535|33.280 / 35.290|32.181 / 29.524|
| Similarity + Bert score + wmd |**40.048**/ **41.400**|**49.174** / **48.315**|**55.663** / **53.137**|42.113 / 41.196|**72.793** / **62.512**|**42.653** / **42.700**|46.576 / 42.539|

Conclusion ( src to mt ):

+ For one metric
  + In general, Sentence Cosine similarity shows great performance in the WMT-17, WMT-20 and Pascal-50s
    + This is highly possible because sentence level similarity is more important than token level similarity in source to machine translation.
  + Generally, Bert score shows better performance than wmd, which indicates the supiority of Bert score in the token level similarity.
+ For two metrics
  + Cosine similarity + Bert_score / WMD are better, which shows the sentences-level similarity is important.
  + For Bert_score + wmd,  the performance drops for majority cases in comparsion to Bert score
    + Considering both of them are the token level computation,
    + Generally, the performance is lower than bert_score unless wmd achieves better performance. 
    + If wmd is not much worse than bert score ( less than 1% ), then Bert_score + wmd is slighly better than just using bert_score. Otherwise, wmd is the reason lead Bert_score + wmd worse.
  + The effect of combining Cosine similarity with Bert score is much larger than combining with WMD. Cosine similarity + Bert score completely outperform just using Bert score and Bert score + wmd. 
    + And Cosine similarity + wmd outperforms than Bert score + wmd when Cosine similarity is better than bert score
  + Cosine similarity + wmd and Cosine similarity + Bert score are depends.
    + Cosine similarity + wmd is better in the WMT-17 and Pascal-50S
    + Cosine similarity + bert score is better in the WMT-20
+ For three metrics:
  + Cosine similarity + Bert score + wmd shows great performance in the WMT-20 datasets
  + Cosine similarity + Bert score + wmd drops in the WMT-17 and Pascal-50S , which works like (cosine similarity + bert score) + (Bert score + wmd) 



## SOTA 

### References to Machine Translation

+ WMD Model: Roberta-Large
+ Cosine similarity: Roberta-Large-nli-stsb-mean-tokens
+ Bert Score Model: Roberta-Large



Pascal-50s

| Metric | de (pearson/spearman) | fr (pearson/spearman) |
| ------ | -- | -- |
| wmd  | 51.766 / 55.909 | 43.911 / 50.808 |
| wmdo |51.986 / 55.915|44.098 / 50.808|
| Similarity  | 45.118 / 52.549 | 40.485 / 48.092 |
| Bert_Score | 49.552 / 55.745 | 40.107 / 51.096 |
| Similarity + wmd| 50.785 / 55.487 | 45.374 / 50.916 |
| Similarity + Bert_score	| 52.278 / 57.546 |45.094 / 52.793|
| Bert_Score + wmd |52.826 / 55.950|44.622 / 51.180|
| Similarity + wmdo |50.827 / 55.492|45.416 / 50.923|
| Similarity+ Bert_Score+ wmd |**52.793** / **57.783**|**45.618** / **52.952**|



WMT-17

| Metric | deen  | zhen  | fien | lven | ruen | csen |tren|
| ------ | -- | -- | -- | -- | -- | -- | -- |
| wmd  | 73.005 / 73.733 | 76.905 / 76.031 |82.741 / 82.468|73.610 /  73.614|73.259 / 74.841|69.845 / 70.504|76.974 / 76.728|
| wmdo |72.921 / 73.671|76.866 / 75.974|82.742 / 82.448|73.495 / 73.502|73.241 / 74.797|69.838 /  70.447|76.963 / 76.667|
| Similarity  | 61.229 / 63.498 | 65.334 / 63.756 |72.984 / 77.439|70.286 / 70.210|69.987 / 67.812|62.232 / 60.668|65.355 /  68.903|
| Bert_Score | 74.479 / 74.448 | 77.477 / 75.488 |83.324 / 83.694|75.636 / 74.504|74.555 / 75.099|70.971 / 70.553|75.083 / 75.910|
| Similarity + wmd| 70.903 / 70.890 | 73.469 / 70.534 |80.883 / 81.815|75.388 / 73.988|75.821 / 73.230|69.268 / 66.825|73.759 / 73.817|
| Similarity + Bert_score	| 76.988 / 76.840 |78.503 / 76.155|86.010 / 86.626|79.210 / 78.031|79.638 / 77.918|74.616 / 72.688|78.216/ 77.946|
| Bert_Score + wmd |74.178 / 74.815|77.260 / 76.071|84.306 / 83.901|75.359 / 74.822|74.459 / 75.633|70.841 / 71.061|77.397 / 76.660|
| Similarity + wmdo |70.905 / 70.897|73.449 / 70.512|80.884 / 81.813|75.364 / 73.967|75.828 / 73.258|69.265 / 66.832|73.774 / 73.812|
| Similarity + Bert_Score + wmd |**77.585** / **77.415**|**79.382** / **77.348**|**86.644** / **87.119**|**79.563** / **78.515**|**79.956** / **78.588**|**75.066** / **73.481**|**79.253** / **78.652**|



Conclusion (ref to mt):

Similarity + Bert_Score + wmd  >  Similarity + Bert_Score  > Bert_Score >  Bert_Score + wmd >  wmd > Similarity + wmd > similarity

+ For one metric
  + Sentence Cosine similarity shows the worst performance in the WMT-17, Pascal-50s.
  + In general, Bert score completely outperforms than other two metrics in the WMT-17
+ For two metrics
  + For Bert_score + wmd,  the performance drops for majority cases in comparsion to Bert score
    + Considering both of them are the token level computation,
    + Generally, the performance of Bert_score + wmd is lower than bert_score unless wmd achieves better performance than bert score 
  + Similarity + Bert score completely outperforms the other two combinations
  + Bert score + wmd is better than similarity + wmd in general, considering Bert score is significantly outperforms than similarity
+ For three metrics
  + Similarity + Bert score + wmd has an absolute advantage for both WMT-17 and Pascal-50S