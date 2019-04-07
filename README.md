# RSforWordTranslation
## Reconstructed Similarity for Faster GANs-Based Word Translation to Mitigate Hubness
In machine word translation, nearest neighbor (NN) retrieval is able to search the best-Ktranslation candidates as linguistic labels of a source query from a unified multilingual semantic feature space. However, NN is polluted by hubs in the high-dimensional feature space. Many proposed approaches remove hubs in the list of translation candidates to relieve this problem. However, this approach to eliminating hubs is flawed because they also have corresponding translations. To address this issue, we propose a novel reconstructed similarity (RS) retrieval for the neural machine word translation model to mitigate the hubness problem regardless of whether it is a hub. Different from previous work, RS reduces the impact of hubness pollution in dense and high-dimensional space and allows the hubs to have the same probability as the target candidates without being inappropriately excluded. In addition, RS improves the quality of bilingual dictionaries by measuring the bilateral similarity of the bilingual and monolingual distance of each of the source query embeddings. Additionally, to model the unsupervised machine word translation, we introduce GANs to map the source and target word distribution into a shared semantic space. We also construct a tiny GAN topology for neural machine word translation, which is at least 52 faster than previous GAN-based models. To further align cross-lingual embedding distributions, we provide orthogonal Procrustes mapping, global-awareness of the transformation matrix and rescaling of the target embeddings as flexible and optional multirefinements. The results show that our model outperforms the state of the art by nearly 4% in distant languages such as English to Chinese and English to Finnish. 
Compared with a precision@1 of 47.00% from English to Finnish, our model obtains a precision@1 of 47.53\% and achieves state-of-the-art results in a fully unsupervised form. Moreover, our model achieves competitive results in the shortest time among GAN-based models, which easily trade off between speed and accuracy. 

**Our main contributions include the following:**
- We first propose the global-awareness of the transformation matrix W that fuses global and local weights, which obtains a subtle improvement.
- We introduce a novel reconstructed similarity retrieval for selecting the best-k target candidates that evaluates the likelihood of candidates combining bilingual and monolingual distances. This approach eliminates the hubness pollution without excluding the hubs. Additionally, it extends previous work and achieves competitive performances.
- Our model significantly reduces model training time, which only takes a few minutes with a single CPU and is approximately 52X~105X faster than previous GAN-based models.		
- Our unsupervised word translation model obtains the state of the art on the bilingual lexicon extraction task. It reaches a precision@1 of 47.53%  translating English to Finnish and outperforms supervised methods without a single parallel sign.

## Bilingual Lexicon Induction
We report the results of our model on the test sets (English to Italian, German, Finnish, Spanish), compared to previous methods.
From the results, we notice that the performances of close languages, such as English and Spanish, generally show superior results to the long distance languages. As shown in the last row, our model achieves remarkably outstanding precision in different language pairs. Additionally, our model shows a marked improvement in the test of English to Finnish and outperforms the state of the art in many language datasets. (Word translation precision@k for k=1. Language codes: `EN' is English, `IT' is Italian, `ES' is Spanish, `de' is German, `fi' is Finnish.)

Method 	| EN-IT | EN-DE | EN-FI | EN-ES
-|-|-|-|-
Mikolov et al. (2013)\cite{mikolov2013exploiting} (*) | 34.93 | 35.00 | 25.91 | 27.73
Faruqui et al. (2014)\cite{faruqui2014improving} (*) | 38.40 | 37.13 | 27.60 | 26.80
Shigeto et al. (2015)\cite{shigeto2015ridge} (*) | 41.53 | 43.07 | 31.04 | 33.73
Dinu et al. (2014)\cite{dinu2014improving} (*) | 38.53 | 38.93 | 29.14 | 30.40
Lazaridou et al. (2015)\cite{Lazaridou2015Hubness} (*) | 40.2 | - | - | -
Xing et al. (2015)\cite{xing2015normalized} (*) | 36.87 | 41.27 | 28.23 | 31.20
Artetxe et al. (2016)\cite{artetxe2016learning} (*) | 39.27  | 41.87 | 30.62 |  31.40
Zhang et al. (2016)\cite{zhang2016ten} (*) | 36.73 | 40.80 | 28.16 | 31.07		
Smith et al. (2017)\cite{smith2017offline} (*) | 44.53 | 43.33 | 29.42 | 35.13
Artetxe et al. (2018)\cite{artetxe2018generalizing} (*) | 45.27 | 44.13 | 32.94 | 36.53
Lample et al. (2018)\cite{conneau2017word} | 77.80 | 74.12 |  43.96 | 81.73 
Our | 78.00 | 73.53 | 47.53 | 81.64 
 
## Visualization
we visualize three translation scenarios by projecting mapped bilingual word embeddings from 300 dimensions to 2D at prediction time. 
This visualization shows the process of how RS works from an experimental view and fully demonstrates that RS promotes the confidence of more appropriate target translations without considering whether it is a hub. The word embeddings are projected from 300-dim to the 2D plane using PCA. The five vectors in Spanish (black) are the 5 nearest neighbors of the source query, and the values below the red word labels are the distance from the query. Another five vectors in English (red) are the 5 nearest neighbors of the target candidate that is in the best-k list, and the values below the black labels are the distance from the candidate. In addition, the table in the top right corner reports the similarity of the query and the back-translation value is shown with red labels.
![](https://github.com/djzgroup/RSforWordTranslation/blob/master/visualizaition.jpg)

## References
- [1] Gang Yu and Junsong Yuan. Fast action proposals for human action detection and search. In Proceedings of the IEEE conference on computer vision and pattern recognition, pages 1302-1311, 2015.
- [2] Philippe Weinzaepfel, Zaid Harchaoui, and Cordelia Schmid. Learning to track for spatio-temporal action localization. In Proceedings of the IEEE international conference on computer vision, pages 3164-3172, 2015.
- [3] Xiaojiang Peng and Cordelia Schmid. Multi-region two-stream r-cnn for action detection. In European Conference on Computer Vision, pages 744-759. Springer, 2016.
- [4] Suman Saha, Gurkirt Singh, Michael Sapienza, Philip HS Torr, and Fabio Cuzzolin. Deep learning for detecting multiple space-time action tubes in videos. British Machine Vision Conference, 2016.
- [5] Jiawei He, Mostafa S Ibrahim, Zhiwei Deng, and Greg Mori. Generic tubelet proposals for action localization. arXiv preprint arXiv:1705.10861, 2017.
- [6] gurkirt Singh, Suman Saha, Michael Sapienza, Philip Torr, and Fabio Cuzzolin. Online real-time multiple spatiotemporal action localisation and prediction. In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition, pages 3637-3646, 2017.

## Acknowledgment
This work was supported in part by the National Natural Science Foundation of China under Grant 61702350 and Grant 61472289 and in part by the Open Project Program of the State Key Laboratory of Digital Manufacturing Equipment and Technology, HUST, under Grant DMETKF2017016.
