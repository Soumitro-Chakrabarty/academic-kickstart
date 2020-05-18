---
title: 'ICASSP 2020 - Highlights'
subtitle: 
summary: 'My highlights from this year's virtual ICASSP.
authors:
- Soumitro Chakrabarty

featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: ''
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---

This year ICASSP was supposed to be held in Barcelona, but unfortunately due to the COVID-19 crisis, it had to turn into a virtual conference. Though I missed the typical face-to-face interaction with fellow researchers, I really appreciate the availability of presentation videos online beyond the period of the conference. 

There were some really interesting works presented this year also at ICASSP and I am listing my highlights based on my areas of interest of machine learning based methods for *single and multi-channel speech enhancement and separation, microphone array processing and acoustic parameter estimation*. 

### Single-channel speech enhancement and separation

There has been a recent surge in works related to time-domain speech separation mainly due to the ideal-mask-surpassing performance as well as a flexible system design of the [TasNet](https://ieeexplore.ieee.org/document/8707065/) framework. Therefore in ICASSP, time-domain speech separation/enhancement seemed to be one the more popular topics.

A few papers looked into the encoder-decoder design for TasNet architecture:

* [M. Pariente et al., Filterbank design for end-to-end speech separation](http://arxiv.org/abs/1910.10400)  
  This paper proposes the use of analytic filters to design the analysis-synthesis filters and looks into designing both fixed as well as learnable filter-banks within a unified framework for the TasNet architecture. A result of this work is this toolkit- [Asteroid](https://github.com/mpariente/asteroid).

* [Ditter et al., A Multi-Phase Gammatone Filterbank for Speech Separation Via Tasnet](http://arxiv.org/abs/1910.11615)  
  They propose to use a deterministic gammatone filterbank for the encoder-decoder part of TasNet.
  
* [Kadioglu et al., An Empirical Study of Conv-Tasnet](http://arxiv.org/abs/2002.08688)  
  They propose to make the encoder-decoder part "deep" to facilitate the learning of richer and complex signal representations and evaluate the effect of this design choice. 

All three works took quite different approaches towards the encoder-decoder design that were inspired by separate design considerations. It seems we will see this line of investigation in future works also for different related tasks.

While these methods focused on the design of the encoder-decoder, another work  

* [Tzinis et al., Two-Step Sound Source Separation: Training On Learned Latent Targets](http://arxiv.org/abs/1910.09804)  

took the approach of pre-training the representation learning part separately, and showed improvements over the end-to-end training procedure adopted by TasNet inspired networks. 

Another work

* [Heitkaemper et al., Demystifying TasNet: A Dissecting Approach](http://arxiv.org/abs/1911.08895)  

did an in-depth analysis of the benefits of time-domain separation compared to frequency-domain methods by sequentially replacing components of a frequency-domain method to move towards the TasNet approach. The high time-resolution and the time-domain loss seem to be the main source of performance gains for TasNet. However, all the compared methods in the paper still have a hard time with reverberant environments. 

Conv-TasNet was also applied for the task of real-time single-channel speech enhancement 

* [Sonning et al., Performance Study of a Convolutional Time-Domain Audio Separation Network for Real-Time Speech Denoising](https://ieeexplore.ieee.org/document/9053846/)  

where the authors showed that small look-ahead (future time frames) even in the range of 10-20 ms can really help the denoising performance. There were some other interesting works on real-time speech enhancement

* [Xia et al., Weighted Speech Distortion Losses for Neural-network-based Real-time Speech Enhancement](http://arxiv.org/abs/2001.10601)  
  This is also the baseline method of the [DNS Challenge](https://dns-challenge.azurewebsites.net/).

* [Takeuchi et al., Real-time speech enhancement using equilibriated RNN](http://arxiv.org/abs/2002.05843)


Some other interesting works related to single-channel speech separation but unrelated to the TasNet idea

* [Lam et al., Mixup-breakdown: A Consistency Training Method for Improving Generalization of Speech Separation Models](http://arxiv.org/abs/1910.13253)  
  They propose a semi-supervised learning approach they call Mixup-Breakdown based on the original [mixup](https://arxiv.org/abs/1710.09412) combined with breakdown technique to include unlabeled inputs in training to improve generalization. The idea seems really nice.
  
* [Kim et al., Boosted Locality Sensitive Hashing: Discriminative Binary Codes for Source Separation](http://arxiv.org/abs/2002.06239)  
  This work addresses the issue of speech denoising in resource-constrained conditions and proposes the use of learned hash codes to efficiently represent audio spectra. What is really interesting is the completely different formulation of TF mask estimation problem. 
  

### Multi-channel speech enhancement and separation

Time-domain methods also made their way into multi-channel methods with some methods that were related to TasNet

* [Zhang et al., On End-to-end Multi-channel Time Domain Speech Separation in Reverberant Environments](https://ieeexplore.ieee.org/document/9053833/)  
  The paper replaces the inter-channel phase difference (IPD) based spatial information encoding in [Gu et al., End-to-End Multi-Channel Speech Separation](https://arxiv.org/pdf/1905.06286.pdf) with a Conv2D spatial encoder

