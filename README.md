# Contrastive Semi-supervised Learning for Underwater Image Restoration via Reliable Bank (CVPR 2023)
Shirui Huang*, Keyan Wang*+, Huan Liu, Jun Chen, Yunsong Li

*Equal Contributions
+Corresponding Author

Xidian University, McMaster University

## Introduction
This is the official repository for our recent paper, "Contrastive Semi-supervised Learning for Underwater Image Restoration via Reliable Bank [link](https://arxiv.org/pdf/2303.09101.pdf)", where more implementation details are presented.

## Abstract
Despite the remarkable achievement of recent underwater image restoration techniques, the lack of labeled data has become a major hurdle for further progress. In this work, we propose a mean-teacher based **Semi**-supervised **U**nderwater **I**mage **R**estoration (**Semi-UIR**) framework to incorporate the unlabeled data into network training. However, the naive mean-teacher method suffers from two main problems: (1) The consistency loss used in training might become ineffective when the teacher's prediction is wrong. (2) Using L1 distance may cause the network to overfit wrong labels, resulting in confirmation bias. To address the above problems, we first introduce a reliable bank to store the ``best-ever" outputs as pseudo ground truth. To assess the quality of outputs, we conduct an empirical analysis based on the monotonicity property to select the most trustworthy NR-IQA method. Besides, in view of the confirmation bias problem, we incorporate contrastive regularization to prevent the overfitting on wrong labels. Experimental results on both full-reference and non-reference underwater benchmarks demonstrate that our algorithm has obvious improvement over SOTA methods quantitatively and qualitatively.

<img src='overview.png'>

<p align="center">Figure 1. An overview of our approach.</p>

## Dependencies

- Ubuntu==18.04
- Pytorch==1.8.1
- CUDA==11.1

Other dependencies are listed in `requirements.txt`
We also thanks the repository: [IQA-Pytorch](https://github.com/chaofengc/IQA-PyTorch).

## Data Preparation

Run `data_split.py` to randomly split your paired datasets into training, validation and testing set.

Run `estimate_illumination.py` to get illumination map of the corresponding image.

Finally, the structure of  `data`  are aligned as follows:

```
data
├── labeled
│   ├── input
│   └── GT
│   └── LA
├── unlabeled
│   ├── input
│   └── LA
│   └── candidate
└── val
    ├── input
    └── GT
    └── LA
└── test
    ├── benchmarkA
        ├── input
        └── LA
```

You can download the training set and test sets for our paper [here](https://drive.google.com/drive/folders/1ctTGuAwsGCKReTezJXxnT5-Re9MRseS0?usp=share_link). 

## Test

Put your test benchmark under `data/test` folder, run `estimate_illumination.py` to get its illumination map.

Run `test.py` and you can find results from folder `result`.

## Train

To train the framework, run `create_candiate.py` to initialize reliable bank. Hyper-parameters can be modified in `trainer.py`.

Run `train.py` to start training.

## Citation
If you use the code in this repo for your work, please cite the following bib entries:

### Our arxiv version:
```latex
@article{huang2023contrastive,
  title={Contrastive Semi-supervised Learning for Underwater Image Restoration via Reliable Bank},
  author={Huang, Shirui and Wang, Keyan and Liu, Huan and Chen, Jun and Li, Yunsong},
  journal={arXiv preprint arXiv:2303.09101},
  year={2023}
}
```

## Contact

If you have any problem with the released code, please do not hesitate to contact us by email (shiruihh@gmail.com).
