<h1 align="center">AS-DETR: Aerial Sparse DETR for Efficient Tiny Object Detection</h1>

<p align="center">English | <a href="README.zh-CN.md">简体中文</a></p>

This repository is the project page for AS-DETR. The complete source code and pretrained weights will be released after the paper is accepted.

## Overview

AS-DETR studies efficient tiny object detection in aerial imagery, where object counts and spatial distributions vary substantially across scenes.

The method uses a continuous density map to coordinate query allocation, sparse feature processing, and decoder attention. A lightweight frequency-state-space encoder complements this density-guided pathway by preserving fine object details and modeling long-range context.

## Experimental results

The following results are reported in the manuscript for the final sparse AS-DETR model. AP values are expressed as percentages.

| Dataset | Evaluation split | AP | AP50 | AP75 | Source |
|---|---|---:|---:|---:|---|
| VisDrone2019 | Validation | **35.4** | **57.8** | **36.9** | Table I |
| AI-TOD-v2 | Test | **32.0** | **66.1** | **26.8** | Table II |
| DIOR | Test | — | **82.8** | — | Table III |

The DIOR comparison reports AP50 as its aggregate metric. A dash indicates a value not reported in the corresponding table.

### Efficiency on VisDrone2019

Both configurations below use an HGNetv2-B0 backbone and an input resolution of 800 × 800.

| Configuration | Parameters (M) | GFLOPs | AP | Inference time (ms) | FPS |
|---|---:|---:|---:|---:|---:|
| AS-DETR (Dense) | 13.6 | 196 | 36.5 | — | — |
| AS-DETR (Sparse) | 13.6 | **103** | 35.4 | **26.6** | **37.6** |

The sparse model uses **47.4% fewer GFLOPs** than the dense variant, with a **1.1-point AP decrease**. Accuracy, model size, and computational cost are from Table I; inference time and FPS are from Table XV. The manuscript's experimental setup uses PyTorch and NVIDIA GeForce RTX 4090 GPUs. The timing batch size, warm-up procedure, and inclusion of preprocessing or postprocessing are not specified in the manuscript.

## Release plan

The current release provides project information and manuscript-reported results. After paper acceptance, this repository will be updated with:

- The complete implementation.
- Pretrained model weights.
- Training and evaluation configurations.
- Installation, inference, and reproduction instructions.

## Citation

Publication details and a BibTeX entry will be added when available.
