---
layout: page
title: Primate Pose Estimation
description: Designed a deep learning model using rCNNs and CPM for the OpenMonkeyChallenge to estimate monkey poses in natural habitats. It tracks 17 monkey pose landmarks, with its accuracy measured by MPJPE. The model achieved an MPJPE of 0.217, enhancing wildlife monitoring and behavioral studies through AI.
img: assets/img/nonprimate_pose_estimation.png
importance: -6
category: Computer Vision
---

This project aims at estimating the pose of Non-Human Primates (NHP) in different environment settings. This projects particularly aims to approach the [OpenMonkeyChallenge](http://openmonkeychallenge.com/). OpenMonkeyChallenge is a computer vision benchmark challenge for NHP pose estimation. The data for this challenge consists of over 100,000 annotated photographs of NHPs in naturalistic contexts obtained from various sources for various species of monkeys and apes. The pose of the monkey is determined by 17 key pose landmarks including Nose, Left eye, Right eye, Head, Neck, Left shoulder, Left elbow, Left wrist, Right shoulder, Right elbow, Right wrist, Hip, Left knee, Left ankle, Right knee, Right ankle, and Tail. The dataset has been made publicly available by [Yao et. Al.](https://link.springer.com/article/10.1007/s11263-022-01698-2).


This project has been taken as part of Computer Vision (University of Minnesota, Fall 2022) coursework under [Dr. Junaed Sattar](https://junaedsattar.cs.umn.edu/).


[Project Report](https://portfolio-rv.s3.amazonaws.com/resume/project-papers/non-human-primate-pose-estimation.pdf)

<div class="row">
    <div class="col-sm-6 mt-3 mt-md-0">
        {% include figure.html path="assets/img/nppe_data_distr.png" title="Data Distribution" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-6 mt-3 mt-md-0">
        The OpenMonkeyChallenge provides a diverse dataset of 111,529 annotated images of 26 species (6 New World monkeys, 14 Old World monkeys, and 6 apes) of non-human primates in natural contexts with 17 landmark annotations.

        <br>
        <br>

        This dataset is split into training, validation and test datasets (60%, 20%, and 20% respectively)
    </div>
</div>
<div class="caption col-sm-6 mt-3 mt-md-0">
    Distribution of the data
</div>


The baseline for my method is based upon [Wei et. al.](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/Wei_Convolutional_Pose_Machines_CVPR_2016_paper.pdf) who use the Convolutional Pose Machine (CPM) to estimate the landmark locations in humans. CPM is divied into 3 stages that generate 18 belief images (17 for landmarks + 1 for background). These belief images convey the confidence that a landmark is at a location.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.html path="assets/img/nppe_architecture.png" title="Architecure" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Architecture: rCNN-CPM based architecture
</div>

The diverse anatomy and behaviour of non-human primate species make generalizing the relationships between image and context features for pose estimation difficult. To handle the differences between species I trained a CPM on each class of the monkey species (Old World, New World and Ape). Non-human primates are classified into one of the classes using a rCNN, and the corresponding CPM will estimate the landmark locations for that species.

<div class="row">
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/nppe_landmark1.png" title="landmark" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/nppe_landmark2.png" title="landmark" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/nppe_landmark3.png" title="landmark" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/nppe_landmark4.png" title="landmark" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-5 mt-md-0">
        {% include figure.html path="assets/img/nppe_landmark5.png" title="landmark" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Landmark Location Estimations. The blue X’s are the ground truth locations and the red circles are our estimated locations. This method can reasonably estimate the landmark locations for a variety of non-human primate species and poses.
</div>

The proposed and baseline method's efficacy in detecting the poses of the images were evaluated based on its [MPJPE](https://openaccess.thecvf.com/content_ICCV_2019/papers/Iskakov_Learnable_Triangulation_of_Human_Pose_ICCV_2019_paper.pdf) and [PCK](https://escholarship.org/content/qt7sk1s10g/qt7sk1s10g_noSplash_a8d7d492292a22ca3c20c0c99cbd9d1f.pdf?t=oub9r6). Overall, the model achieves comparable overall performance to the baseline. Additionally, the model gave better results for Apes and New World monkeys but could not outperform the baseline for Old World monkeys. 

The performance of our method could be further improved by performing additional data augmentation to limit the number of poor training samples (multiple or occluded non-human primates). Additionally, the number of stages in each CPM could be raised to increase the range of learned context features. Finally, more samples of New World Monkeys and Apes could be added so that Old World Monkeys do not dominate the dataset.
