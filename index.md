---
title: Home
---

# Object Discovery Challenge 

in accordance with [VPLOW workshop](https://vplow.github.io/vplow_3rd.html) at CVPR 2023, Vancouver, Canada.

<!-- {% include figure.html img="car-images.png" alt="intro image here" caption="SOFAR (SOCAR: Socially-Obtained CAR image dataset" width="99%" %} -->
 

<!-- <div class="toc" markdown="1"> -->
## Introduction

  Object discovery is the task of automatically identifying and grouping semantically coherent objects without human intervention. Discovery algorithms typically address several challenges like novelty detection, open world recognition and clustering, capabilities which are essential for systems deployed in-the-wild. This year, to facilitate discussions among researchers who have different backgrounds, we host a teaser challenge which studies a system's capabilities to discover and group novel object categories in a large unlabeled dataset.

 
<!-- </div> -->


<!-- <div class="toc" markdown="1"> -->
## Organizers

This challenge is being organized by the Perception Intelligence (PI) lab at University of Maryland, College Park. 

The main organisers are:

* Anubhav
* Sonaal Kant
* Pulkit Kumar
* Abhinav Shrivastava

## Important Dates

* May 9 2023, Challenge Announcement
* June 10 2023, challenge will be closed
* June 15 2023, participants will be selected to present
* June 18 2023, workshop starts


<!-- </div> -->

<!-- <div class="toc" markdown="1"> -->
## Task and Evaluation Metric
 The task of the challenge is to discover novel objects in a large corpus of unlabeled images using knowledge about known objects. Specifically, given a labeled dataset with K known objects and a large unlabeled dataset consisting of U (not known a-priori) unknown objects, algorithms should output a set of M (not known a-priori) clusters, each of which contains regions belonging to an object class. Additionally, an object detector should be trained for each cluster whose performance is evaluated on a held-out set to assess the real world applicability of the object discovery system.

The primary evaluation metric is the Area under the curve of Purity coverage plots [1][2] and PASCAL VOC style mean Average Precision at an IoU threshold of 0.50. Additionally we also report the number of clusters, number of objects discovered, Correct Localization.


<!-- <div class="toc" markdown="1"> -->
### Protocol of Algorithm Design
Proposed algorithms for this challenge will operate on widely used object detection datasets, i.e. PASCAL VOC 2007 and COCO 2014, and report results on two splits. Object discovery systems should be very careful about the assumptions of prior knowledge. To be precise, initializations used by algorithms should never be exposed/trained on categories they wish to discover. This curtails the pre-training of any network on the ImageNet [5] dataset using labeled data.


While we do not discourage teams from using weights of networks trained on ImageNet using labels, only weights trained using self-supervision will be considered for ranking on the leaderboard. While there is no restriction on the usage of models, teams should compare the model performance to a standard ResNet-50 network trained using DINO algorithm[3]. Teams should describe in detail, without fail, each component used and the amount of improvement they offer.
<!-- </div> -->

 
<!-- <div class="toc" markdown="1"> -->
## Dataset description

All systems submitted to the challenge are allowed to use three datasets, namely ImageNet 2012, PASCAL VOC 2007 and COCO 2014 datasets. See respective websites for the dataset formats.

**Labeled dataset**: The object detection dataset, PASCAL VOC 2007 split is considered as the labeled dataset for this challenge. Teams can use the region level labels to train object detection models for their submissions. We assume the 20 categories of PASCAL-VOC as the known categories.

**Discovery Set**: The COCO 2014 train set, without any labels, is used as the discovery dataset. The remaining categories, not common with PASCAL-VOC, are considered the novel categories. Teams are encouraged not to assume the number of novel categories to be known a-priori.

**Pre-training dataset**: To train object detection datasets, ImageNet pre-training is a standard practice. Teams can leverage self-supervised or supervised learning to obtain weights for initialization. However, only the results using self-supervised learning will be considered for ranking.

**Evaluation set**: All systems will be evaluated on the discovery performance and object detection performance. For object discovery, results are reported on the COCO 2014 train set. For object detection on the 20 known classes and the newly discovered objects, results will be reported on the COCO minival set.



<!-- </div> -->
 
<!-- <div class="toc" markdown="1"> -->
## Output format

All teams are required to return two csv files for evaluating object discovery and object detection performance. For object discovery, evaluated on COCO 2014 train split, the file format should be as follows. `<image_id>, <x1>,<y1>,<x2>,<y2>,<cluster_id>` Here `<image_id>` is the unique identifier of an image as used in COCO 2014 train set. For object detection, evaluated on COCO minival, the file format is as follows. `<image_id>, <x1>,<y1>,<x2>,<y2>,<cluster_id>,<conf_score>`
<!-- </div> -->

## Baseline code
Participant's can refer to the baseline code providied [here](https://github.com/learn2phoenix/cvpr22_vplow_ow). The code is based on [2].

 
## Evaluation protocol
Submissions will be ranked based on the following metric:

\begin{equation}
\begin{aligned}
  {performance} = \frac{\Sigma_{1}^{N}\frac{Purity_{i}*C_{i}}{rank_{i}}}{D}
\end{aligned}
\end{equation}

{% raw %}
  $${N} = \text{Total number of clusters}$$
  $${C}_{i} = \text{Number of objects in cluster i}$$
  $${Purity}_{i} = \text{Purity of cluster i}$$
  $${rank}_{i} = \text{Rank of cluster i based on purity}$$
  $${D} = \text{Total number of objects in the dataset}$$
{% endraw %}

## References

 [1] Carl Doersch, Abhinav Gupta, and Alexei A. Efros. Context as Supervisory Signal: Discovering Objects with Predictable Context. In ECCV 2014 

 [2] Sai Saketh Rambhatla, Rama Chellappa, Abhinav Shrivastava. The Pursuit of Knowledge: Discovering and Localizing Novel Categories using Dual Memory. 

 [3] Mathilde Caron, Hugo Touvron, Ishan Misra, Hervé Jégou, Julien Mairal, Piotr Bojanowski, Armand Joulin. Emerging Properties in Self-Supervised Vision Transformers

## Contact:

* Anubhav(anubhav[AT]umd[DOT]edu)
* Sonaal Kant (sonaal[AT]umd[DOT]edu)
* Pulkit Kumar (pulkit[AT]umd[DOT]edu)
* Abhinav Shrivastava (abhinav[AT]umd[DOT]edu)

<!-- </div> -->

 
> built using [Jekyll](https://jekyllrb.com/) and [GitHub Pages](https://pages.github.com/)
>
> Last build date: {{ site.time | date: "%Y-%m-%d" }}.
>
> <a href="http://creativecommons.org/licenses/by-sa/4.0/" rel="license"><img style="border-width: 0;" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" alt="Creative Commons License" /></a>
