---
layout:     post
title:      A deep learning framework for geodesics under spherical Wasserstein-Fisher-Rao metric and its application for weighted sample generation
subtitle:   Yang Jing, Jiaheng Chen, Lei Li, Jianfeng Lu
date:       2022-09-11
updated:   2022-09-11
author:     Jing Yang
stickie:    false
header-img: img/scene6.jpg
catalog: true
tags:
    - Preprint
---

## Abstract

Wasserstein-Fisher-Rao (WFR) distance is a family of metrics to gauge the discrepancy of two Radon measures, which takes into account both transportation and weight change. Spherical WFR distance is a projected version of WFR distance for probability measures so that the space of Radon measures equipped with WFR can be viewed as metric cone over the space of probability measures with spherical WFR. Compared to the case for Wasserstein distance, the understanding of geodesics under the spherical WFR is less clear and still an ongoing research focus. In this paper, we develop a deep learning framework to compute the geodesics under the spherical WFR metric, and the learned geodesics can be adopted to generate weighted samples. Our approach is based on a Benamou-Brenier type dynamic formulation for spherical WFR. To overcome the difficulty in enforcing the boundary constraint brought by the weight change, a Kullback-Leibler (KL) divergence term based on the inverse map is introduced into the cost function. Moreover, a new regularization term using the particle velocity is introduced as a substitute for the Hamilton-Jacobi equation for the potential in dynamic formula. When used for sample generation, our framework can be beneficial for applications with given weighted samples, especially in the Bayesian inference, compared to sample generation with previous flow models.

## ArXiv

[https://arxiv.org/abs/2208.12145]: https://arxiv.org/abs/2208.12145

