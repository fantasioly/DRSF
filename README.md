## Let Synthetic Data Shine: Domain Reassembly and Soft-Fusion for Single Domain Generalization
<!---
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/sora-singular-value-decomposed-low-rank/domain-adaptation-on-cityscapes-to-acdc)](https://paperswithcode.com/sota/domain-adaptation-on-cityscapes-to-acdc?p=sora-singular-value-decomposed-low-rank) <br />	
[![PWC](https://img.shields.io/endpoint.svg?url=https://paperswithcode.com/badge/sora-singular-value-decomposed-low-rank/domain-generalization-on-gta-to-avg)](https://paperswithcode.com/sota/domain-generalization-on-gta-to-avg?p=sora-singular-value-decomposed-low-rank) <br />
--->

![framework](assets/framework.png)

## abstract
Single Domain Generalization (SDG) aims to train models with consistent performance across diverse scenarios using data from a single source.  While using latent diffusion models (LDMs) show promise in augmenting limited source data, we demonstrate that directly using synthetic data can be detrimental due to significant feature distribution discrepancies between synthetic and real target domains, leading to performance degradation. To address this issue, we propose Discriminative Domain Reassembly and Soft-Fusion (DRSF), a training framework leveraging synthetic data to improve model generalization. We employ LDMs to produce diverse pseudo-target domain samples and introduce two key modules to handle distribution bias. First, Discriminative Feature Decoupling and Reassembly (DFDR) module uses entropy-guided attention to recalibrate channel-level features, suppressing synthetic noise while preserving semantic consistency. Second, Multi-pseudo-domain Soft Fusion (MDSF) module uses adversarial training with latent-space feature interpolation, creating continuous feature transitions between domains. Extensive SDG experiments on object detection and semantic segmentation tasks demonstrate that DRSF achieves substantial performance gains with only marginal computational overhead. Notably, DRSF's plug-and-play architecture enables seamless integration with unsupervised domain adaptation paradigms, underscoring its broad applicability in addressing diverse and real-world domain challenges.

## Installation

Please follow the instruction in [INSTALL.md](INSTALL.md) to install and use this repo.

For installation problems, please consult issues in [ maskrcnn-benchmark
](https://github.com/facebookresearch/maskrcnn-benchmark).

This code is tested under Ubuntu20.04 with Python 3.9 and PyTorch 1.12.0.

## Datasets
The datasets used in the repository can be downloaded from the following links:

* [Adverse-Weather](https://drive.google.com/drive/folders/1IIUnUrJrvFgPzU8D6KtV0CXa8k1eBV9B)
* [Adverse-Weather-generation](https://drive.google.com/file/d/1F5Q7kO3uZCI6mWApW9e3-1yHVrBH37IN/view)

The datasets should be organized in the following structure.
```
datasets/
├── Adverse-Weather
│   ├── daytime_clear
│   ├── daytime_foggy
│   └── dusk_rainy
│   └── night_rainy
│   └── night_sunny
└── Adverse-Weather-generation
│   ├── daytimeclear
│   ├── daytimefoggy
│   └── duskrainy
│   └── nightrainy
│   └── nightsunny
```

## Training
For experiments in our paper, we use the following script to run SDG-OD task:

```shell
python tools/train_net.py --config-file configs/da_faster_rcnn/e2e_da_faster_rcnn_R_50_FPN_masking_cs.yaml
```

## Evaluation
The trained model could be evaluated with the following script:
```shell
python tools/test_net.py --config-file "configs/da_faster_rcnn/e2e_da_faster_rcnn_R_50_FPN_masking_cs.yaml" MODEL.WEIGHT <path_to_store_weight>/model_final.pth
```

 ### TODO LIST

- [x] configuration
- [x] Release evaluation
- [x] Release Object Detection
- [ ] Release Segmentation
- [ ] Release Model Zoo

<section class="section" id="BibTeX">
  <div class="container is-max-desktop content">
    <h2 class="title">BibTeX</h2>
    <pre><code>@Article{li2025letsyntheticdatashine,
      title={Let Synthetic Data Shine: Domain Reassembly and Soft-Fusion for Single Domain Generalization}, 
      author={Hao Li and Yubin Xiao and Ke Liang and Mengzhu Wang and Long Lan and Kenli Li and Xinwang Liu},
      year={2025},
      url={https://arxiv.org/abs/2503.13617}, 
}</code></pre>
  </div>
</section>