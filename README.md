# visda2019-multisource

We release the source code of our submission (Rank 1) for Multi-Source Domain Adaptation task in VisDA-2019. Details can be referred in [Technical report](https://arxiv.org/pdf/1910.03548.pdf).

All the pretrained models, synthetic data generated via [CycleGAN](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix) , and submission files can be downloaded from the [link](https://drive.google.com/open?id=1qayUpvuBWcTBwsHhbNSRKrw3BXArkrlF).

## Prerequisites

You may need a machine with 4 GPUs and PyTorch v1.1.0 for Python 3.

## Training
### Train source only models
1. Go to the `Adapt` folder

2. Train source only models

  ```bash experiments/<DOMAIN>/<NET>/train.sh```

Where `<DOMAIN>` is clipart or painting, `<NET>` is the network (e.g. `senet154`)

Then repeat the following procedures 4 times.

### Train the end-to-end adaptation module

  ```bash experiments/<DOMAIN>/<NET>_<phase_id>/train.sh``` 

### Extract features

1. Copy the adaptation models to the folder `ExtractFeat/experiments/<phase_id>/<DOMAIN>/<NET>/snapshot`

2. Extract features by running the scripts

  ```bash experiments/<phase_id>/<DOMAIN>/scripts/<NET>.sh```

3. Copy the features from ```experiments/<phase_id>/<DOMAIN>/<NET>/<NET>_<source_and_target_domains>/result``` to ```dataset/visda2019/pkl_test/<phase_id>/<DOMAIN>/<NET>```

### Train the feature fusion based adaptation module
1. Go to the `FeatFusionTest` folder

2. Train feature fusion based adaptation module

  ```bash experiments/<phase_id>/<DOMAIN>/train.sh```

3. Copy the pseudo labels file to ```Adapt/experiments/<DOMAIN>/<NET>_<next_phase_id>``` for the next adaptation.

## Citation
Please cite our technical report in your publications if it helps your research:

```
@article{pan2019visda,
  title={Multi-Source Domain Adaptation and Semi-Supervised Domain Adaptation with Focus on Visual Domain Adaptation Challenge 2019},
  author={Pan, Yingwei and Li, Yehao and Cai, Qi and Chen, Yang and Yao, Ting},
  booktitle={Visual Domain Adaptation Challenge},
  year={2019}
}
```

## Acknowledgements
Thanks to the domain adaptation community and the contributers of the pytorch ecosystem.

Pytorch pretrained-models [Cadene](https://github.com/Cadene/pretrained-models.pytorch) and [EfficientNet](https://github.com/lukemelas/EfficientNet-PyTorch)
