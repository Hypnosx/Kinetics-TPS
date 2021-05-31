# Kinetics-TPS
ICCV DeeperAction Challenge - Kinetics-TPS Challenge on Part-level Action Parsing and Action Recognition.

![overview](overview.gif)

#### Overview

---

Traditionally, action recognition has been treated as a high-level video classification problem. However, such manner ignores detailed and middle-level understanding about human actions. To fill this gap, we deeply investigate action recognition in videos, by explicitly encoding human actions as spatio-temporal composition of body parts. Specifically, we develop a large-scale Kinetics-Temporal Part State (Kinetics-TPS) benchmark for this study. Different from existing video action datasets, our Kinetics-TPS provides 7.9M annotations of 10 body parts, 7.9M part state (i.e., how a body part moves) and 0.5M interactive objects in the video frames of 24 human action classes, which bring new opportunity to understand human action by compositional learning of body parts.


#### Space Requirement

---

- train_videos：~ 4.96 GB
- test_videos：~ 1.26 GB
- annotations:  ~ 348.6 MB
- list:  ~ 68 KB
- total: ~ 6.56 GB

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
           <932 mp4 files named by videos>
 |--train_annotations
    |--classes_name
       <24 folders named by classes>
       |--videos_name
           <3809 folders named by videos>
           |--videos_name
               < 574851 json files named by image_id>
 |--list
   |--body_part.txt
      <10 categories of parts labels>
   |--part_stat.txt
      <74 categories of part_state labels>
   |--object.txt
      <75 categories of objects labels>
   |--video_train_flist.csv
      <number of frames per video in train set>
   |--video_test_flist.csv
      <number of frames per video in test set>

```

#### Documents

---

We will provide some detailed information about Kinetics-KPS dataset. You can also refer to https://deeperaction.github.io/kineticstps/.


###### Frame Extraction

-	We use mmaction2 ’s tools/data/build_rawframes.py and mmcv==1.1.5 to extract frames. Frame name format is img_%05d.jpg, index start from 1.
-	You can check the number of extracting frames results from the files: video_train_flist.csv and video_test_flist.csv.


###### Detailed Information of Vocabulary

- body part：
  - Human limbs must be distinguished between left and right.
- part state:
  - The label 'others' means the other part states that undefined in our vocabulary.
  - The label 'none' means the stat of body parts without movement.
- object:
  - The annotated objects labels refer to objects that interacted with body parts. 
  - The label 'none' means the other objects that undefined in our vocabulary.


#### Reference 
[1]. Li, Chaolong, Zhen Cui, Wenming Zheng, Chunyan Xu, and Jian Yang. "Spatio-Temporal Graph Convolution for Skeleton Based Action Recognition." In Proceedings of the AAAI Conference on Artificial Intelligence, vol. 32, no. 1. 2018.

[2]. Carreira J, Zisserman A. Quo vadis, action recognition? a new model and the kinetics dataset [C]//CVPR. 2017

[3]. Carreira J, Noland E, Banki-Horvath A, et al. A Short Note about Kinetics-600 [J]. arXiv e-prints,2018: arXiv:1808.0134

[4]. Carreira J, Noland E, Hillier C, et al. A short note on the kinetics-700 human action dataset [J].arXiv preprint arXiv:1907.06987, 2019
