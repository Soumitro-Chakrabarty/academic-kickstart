---
title: 'ICASSP 2020 - Interesting Papers'
subtitle: 'Some interesting works from the first virtual ICASSP'
summary:
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

There were some really interesting works presented this year also at ICASSP and I am listing my choices based on my areas of interest of *single and multi-channel speech enhancement/separation, microphone array processing and acoustic parameter estimation*.

### Single-channel speech enhancement/separation

There has been a recent surge in works related to time-domain speech separation mainly due to the ideal-mask-surpassing performance as well as a flexible system design of the [TasNet](https://ieeexplore.ieee.org/document/8707065/) framework. Therefore in ICASSP, time-domain speech separation/enhancement seemed to be one the more popular topics.

These papers looked into the encoder-decoder design for TasNet architecture:

* [M. Pariente, S. Cornell, A. Deleforge, and E. Vincent, “Filterbank design for end-to-end speech separation,”](http://arxiv.org/abs/1910.10400)
  This paper proposes the use of analytic filters to design the analysis-synthesis filters and looks into designing both fixed as well as learnable filter-banks within a unified framework for the TasNet architecture. 
* [A Multi-Phase Gammatone Filterbank for Speech Separation Via Tasnet](http://arxiv.org/abs/1910.11615)
  They propose to use a deterministic gammatone filterbank for the encoder-decoder part of TasNet.
* [An Empirical Study of Conv-Tasnet](http://arxiv.org/abs/2002.08688)
  They propose to make the encoder-decoder part "deep" to facilitate the learning of richer and complex signal representations and evaluate the effect of this design choice. 

All three works took quite different approaches towards the encoder-decoder design and showed the importance of representation learning for time-domain approaches.