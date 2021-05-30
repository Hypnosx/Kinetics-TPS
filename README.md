# Kinetics-TPS
ICCV DeeperAction Challenge - Kinetics-TPS Challenge on Part-level Action Parsing and Action Recognition.

![overview](overview.gif)

#### Overview

---

Traditionally, action recognition has been treated as a high-level video classification problem. However, such manner ignores detailed and middle-level understanding about human actions. To fill this gap, we deeply investigate explainable action recognition in videos, by explicitly encoding human actions as spatio-temporal composition of body parts and objects. Specifically, we first develop a large-scale Kinetics-TPS benchmark for this study. Different from existing video action datasets, our Kinetics-TPS provides 7.9M annotations of 10 body parts, 4.5M body part states and 0.5 interactive objects in the frame level, which bring new opportunity to understand human action by compositional learning of body parts in 4743 videos. With Kinetics-TPS, we build up a novel progressive action graph network to recognize human actions in an explainable bottom-up manner, which progressively assembles body parts, their part_stats and relevant objects as compositional human representation, and subsequently exploit spatio-temporal relations among humans for action recognition. Finally, we validate generalization capacity of our approaches in two extra challenging problems of compositional action recognition, i.e., semi-supervised and few-shot settings. Extensive results show that, with Kinetics-TPS, we can significantly boost action recognition performance with explainable body composition.

#### Space Requirement

---

- train_videos：~ 4.9 GB
- test_videos：~ 1.2 GB
- annotations:  ~ 348 MB
- list:  ~ 3 KB
- total: ~ 6.4 GB

#### Dataset Structure

---

Manually unzip all the files. It may take a few minutes or hours. After unzipping the files, you will get all the data in the following folder structure:

```
Kinetics-TPS
|--train_videos
   |--classes_name
   		<24 folders named by classes>
   		|--videos_name.mp4
      		<3809 mp4 files named by videos>
|--test_videos
   |--classes_name
   		<24 folders named by classes>
   		|--videos_name.mp4
      		<934 mp4 files named by videos>   
|--train_annotations
   |--classes_name
   		<24 folders named by classes>
   		|--videos_name
      		<3809 folders named by videos> 
      		|--videos_name
      				< json files named by image_id> 
|--list
  |--body_part.txt
     <10 categories of parts labels> 
  |--part_stat.txt
     <74 categories of part_state labels>
  |--object.txt
     <75 categories of objects labels>
```

#### Documents

---

We will provide some detailed information about Kinetics-KPS dataset. You can also refer to https://deeperaction.github.io/kineticstps/.


###### Source Videos

- We collect **4743** source videos from Kinetics-motion dataset[1].
- So，it is not allowed to use Kinetics400[2]，Kinetics600[3]，Kinetics700[4] pretrained model.
- Notice, we use [ mmaction2 ](https://github.com/open-mmlab/mmaction2) ’s `tools/data/build_rawframes.py` and `mmcv==1.1.5` to extract frames. Frame name format is `img_%05d.jpg`, index start from 1.

###### Detailed Information of Vocabulary

- body part：
  - Human limbs must be distinguished between left and right.
- part state:
  - The label 'others' means the other part states that undefined in our vocabulary.
  - The label 'none' means the stat of body parts without movement.
- object:
  - The annotated objects labels refer to objects that interacted with body parts.

#### Reference 
[1]. Li, Chaolong, Zhen Cui, Wenming Zheng, Chunyan Xu, and Jian Yang. "Spatio-Temporal Graph Convolution for Skeleton Based Action Recognition." In Proceedings of the AAAI Conference on Artificial Intelligence, vol. 32, no. 1. 2018.
[2]. Carreira J, Zisserman A. Quo vadis, action recognition? a new model and the kinetics dataset [C]//CVPR. 2017
[3]. Carreira J, Noland E, Banki-Horvath A, et al. A Short Note about Kinetics-600 [J]. arXiv e-prints,2018: arXiv:1808.0134
[4]. Carreira J, Noland E, Hillier C, et al. A short note on the kinetics-700 human action dataset [J].arXiv preprint arXiv:1907.06987, 2019
