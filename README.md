# EyeGlaucoma

The dataset and code for the paper entitled *Generalization-Reinforced Semi-Supervised Learning for Glaucoma Assessment and a Multimodal and Multitask Dataset*.

# Dataset

The OCT RNFLT maps with labels can be accessed via this [link](https://drive.google.com/drive/folders/1F9wM5W-00XMd2tqlt8b_pyi_yjkRwfpc?usp=share_link). **Our dataset must be only used for non-profit academic education and research purposes. Our dataset must not be used for commercial activities or research grant applications.**

The glaucoma data of 1000 patients includes 1000 OCT RNFLT maps (dimension 225x225). The visual field, patient age, sex, race, glaucoma and progression label information are also included in the data.

1000 OCT RNFLT maps are in the rnflt_maps folder:
data_0001.npz
data_0002.npz
...
data_1000.npz

Each data contains the following attributes:
1) rnflt: OCT RNFLT map of size 225x225.
2) glaucoma: glaucomatous status, 0 for non-glaucoma and 1 for glaucoma.
3) progression: a vector corresponding to 6 different progression labels, 0 for non-progression and 1 for progression.
4) md: mean deviation value of visual field.
5) tds: 52 total deviation values of visual field.
6) age: patient age.
7) male: patient sex, 0 for female and 1 for male.
8) race: patient race.

Only the first 500 data (0001~0500) have progression label defined in 6 ways respectively:
progression[0]: md.
progression[1]: vfi.
progression[2]: td_pointwise.
progression[3]: md_fast.
progression[4]: md_fast_no_p_cut.
progression[5]: td_pointwise_no_p_cut.


# Abstract

<p align="center">
<img src="fig/glaucoma_detect.png" width="500">
</p>

Glaucoma is the number one cause of irreversible blindness globally. A major challenge for accurate glaucoma detection and progression forecasting is the bottleneck of limited labeled patients with the state-of-the-art (SOTA) 3D retinal imaging data of optical coherence tomography (OCT). To address the data scarcity issue, this paper proposes two solutions. First, we develop a novel generalization-reinforced semi-supervised learning (SSL) model called pseudo supervisor to optimally utilize unlabeled data. Compared with SOTA models, the proposed pseudo supervisor optimizes the policy of predicting pseudo labels with unlabeled samples to improve empirical generalization. Our pseudo supervisor model is evaluated with two clinical tasks consisting of glaucoma detection and progression forecasting. The progression forecasting task is evaluated both unimodally and multimodally. Our pseudo supervisor model demonstrates superior performance than SOTA SSL comparison models. Moreover, our model also achieves the best results on the publicly available LAG fundus dataset.  Second, we release a multimodal and multitask dataset including 1,000 patients with OCT imaging data and glaucoma labels and progression labels. This is the largest glaucoma detection dataset with 3D OCT imaging data and the first glaucoma progression forecasting dataset that is publicly available. Detailed sex and racial analysis are provided, which can be used by interested researchers for fairness learning studies. Our released dataset is benchmarked with several SOTA supervised CNN and transformer deep learning models.

# Requirements

To install the prerequisites, run:

```
pip install - r requirements.txt
```

# Experiments

To run the experiments on the task of glaucoma detection, run:

```
./glaucoma_detection_training.sh
```

To run the experiments on the task of progression forecasting, run:

```
./progression_forecasting_training.sh
```
