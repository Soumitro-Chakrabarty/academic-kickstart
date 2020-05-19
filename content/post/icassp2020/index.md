---
title: 'ICASSP 2020 - Highlights'
subtitle: ''
summary: My highlights from this year's virtual ICASSP.
authors:
- Soumitro Chakrabarty

tags:
- *

featured: false
draft: false

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Placement options: 1 = Full column width, 2 = Out-set, 3 = Screen-width
# Focal point options: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight
image:
  placement: 1
  caption: 'Source: pixabay.com'
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

There were some really interesting works presented this year also at ICASSP and I am listing my highlights based on my areas of interest of machine learning based methods for 

* [Single-channel speech enhancement and separation](#single-channel-speech-enhancement-and-separation)
* [Multi-channel speech enhancement and separation](#multi-channel-speech-enhancement-and-separation)
* [Parameter estimation](#parameter-estimation)

## Single-channel speech enhancement and separation

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


Some other interesting works on single-channel speech separation but unrelated to the TasNet idea

* [Lam et al., Mixup-breakdown: A Consistency Training Method for Improving Generalization of Speech Separation Models](http://arxiv.org/abs/1910.13253)  
  They propose a semi-supervised learning approach they call Mixup-Breakdown based on the original [mixup](https://arxiv.org/abs/1710.09412) combined with breakdown technique to include unlabeled inputs in training to improve generalization. 
  
* [Kim et al., Boosted Locality Sensitive Hashing: Discriminative Binary Codes for Source Separation](http://arxiv.org/abs/2002.06239)  
  This work addresses the issue of speech denoising in resource-constrained conditions and proposes the use of learned hash codes to efficiently represent audio spectra. What is really interesting is the completely different approach to the TF mask estimation problem. 

* [Maiti et al., Speaker Independence of Neural Vocoders and Their Effect on Parametric Resynthesis Speech Enhancement](http://arxiv.org/abs/1911.06266)  
  This is a nice idea of using parametric speech synthesis methods for speech enhancement. The authors show the speaker independence of WaveGlow, LPCNet and WaveNet and show how they can be used for speech enhancement for unseen speaker and noise scenarios. The seeming mismatch between the objective and subjective test results for the LPCNet enhancement output makes this an interesting read.
  
## Multi-channel speech enhancement and separation

Time-domain methods also made their way into multi-channel approaches 

* [Zhang et al., On End-to-end Multi-channel Time Domain Speech Separation in Reverberant Environments](https://ieeexplore.ieee.org/document/9053833/)  
  The paper replaces the inter-channel phase difference (IPD) based spatial information encoding in [Gu et al., End-to-End Multi-Channel Speech Separation](https://arxiv.org/pdf/1905.06286.pdf) with a Conv2D spatial encoder which is learnt jointly with the TasNet model applied to a reference channel. 
  
* [Ochiai et al., Beam-TasNet: Time-domain Audio Separation Network Meets Frequency-domain Beamformer](https://ieeexplore.ieee.org/document/9053575/)  
  The idea here is a nice way of combining TasNet with conventional beamforming. They first apply TasNet to every input channel to get separated sources at each channel, resolve channel permutation, then use the separated outputs for each source to compute the spatial covariance matrices and the beamformer weights. 

* [Luo et al., End-to-end Microphone Permutation and Number Invariant Multi-channel Speech Separation](http://arxiv.org/abs/1910.14104)  
  The paper proposes a separation method that is invariant to number of microphones, their ordering and is able to take into account global information from all channels rather than using pairwise information by using the transform-average-concatenate (TAC) method.

An interesting paper from Amazon and co.

* [Tolooshams et al., Channel-Attention Dense U-Net for Multichannel Speech Enhancement](http://arxiv.org/abs/2001.11542)  
  They propose a channel-attention unit, inspired by self-attention, at every layer which can be interpreted as non-linear beamforming at each layer. The improvements due to channel-attention seem small compared to the contribution of the Complex Dense U-Net but the idea is interesting.
  
Spatial cue preserving separation for hearing aids using time-domain convolutions was also presented

* [Luo et al., Real-Time Binaural Speech Separation with Preserved Spatial Cues](https://ieeexplore.ieee.org/document/9053215/)

where a MIMO TasNet was used to obtain stereo output for each source. 

## Parameter estimation 

Our work in this year's ICASSP was related to making direction-of-arrival (DOA) estimation signal-aware

* [Mack et al., Signal-Aware Broadband DOA Estimation Using Attention Mechanisms](https://ieeexplore.ieee.org/document/9053658)

where we showed a simple mechanism of including signal-awareness in an existing CNN based multi-speaker DOA estimation method that can work in real-time. Checkout the [Demo Videos](https://www.audiolabs-erlangen.de/resources/2020-ICASSP-SigAwareDOA).

Another interesting work on DOA estimation came from Amazon

* [Sundar et al., Raw Waveform Based End-to-end Deep Convolutional Network for Spatial Localization of Multiple Acoustic Sources](https://ieeexplore.ieee.org/document/9054090/)

where they formulated the DOA estimation problem as a two-stage estimation problem. In the first-stage, the DOA range is divided into coarse sectors and the sector of source location is estimated via classification. Within each active sector the estimation of accurate DOA of the sources are formulated as regression problem. The work uses raw waveform for this task.

Other typical parameters of interest in acoustic environment are the T<sub>60</sub> and direct-to-reverberant ratio (DRR). There were two interesting papers about this.

* [Looney et al., Joint Estimation Of Acoustic Parameters From Single-Microphone Speech Observations](https://ieeexplore.ieee.org/document/9054532/)  
  The paper proposes a CNN based joint estimator for T<sub>60</sub>, DRR as well as SNR. What is interesting is the detailed training data generation procedure. 
  
* [Bryan, N. Impulse Response Data Augmentation and Deep Neural Networks for Blind Room Acoustic Parameter Estimation](http://arxiv.org/abs/1909.03642)  
  Similar to the previous paper, CNNs are used although separate models are trained for T<sub>60</sub> and DRR estimation. The intricate data augmentation technique for both 
  T<sub>60</sub> and DRR is the nice part here. 
  
One of the most interesting works for me in this ICASSP was this work on pitch estimation

* [Gfeller et al., Pitch Estimation Via Self-Supervision](https://ieeexplore.ieee.org/document/9053798/)  
  The authors propose to train a model for pitch estimation using mainly unlabelled samples and using only small amount of labelled samples for some form of calibration. The main idea is well summarised in the abstract:
    >The key to this is the observation that if one creates two examples from one original audio clip by pitch shifting both, the difference between the correct outputs is known, without even knowing the actual pitch value in the original clip. Somewhat surprisingly, this idea combined with an auxiliary reconstruction loss allows training a pitch estimation model.

Overall, things got really interesting this year with all the time-domain methods and some nice combination of signal processing techniques within deep learning models. 

