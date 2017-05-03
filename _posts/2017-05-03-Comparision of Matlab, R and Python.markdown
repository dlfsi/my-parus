---
layout: post
title: Comparision of Matlab, Python and R
date: 2017-05-03
comments: true
external-url:
categories: Deep-Learning
---

> Matlab, Python and R are all REPL languages, which stands for Read, Evaluation, Print and then Loop, are all scripting languages as well.

Above three RPEL languages are much faster to write/debug codes than C++/C#/Java. It's ideal for research and backtesting with very strong vectorize calculation capabilities.

## MATLAB
MATLAB is a corporate development platform that has numerous native toolboxes, such as Statistics and machine learning, financial instruments, GARCH, neural networks and so on, can be compiled into C/C++ for better performance. But it's a little bit expensive for SME and individuals, although there're some corresponding freewares.

## R
R is similar with MATLAB, and it's **FREE**. R has a larger collection of advanced packages created by academic researchers. But R is slow and cannot be compiled into C/C++.

## Python
Python is **FREE** as well. In order to utilize vectorized capabilities, it's a must to install SciPy package to enable that. Pandas extension of Python is a quite handy tool for data manipulation and analysis, which can call R library. Moreover, Python can be compiled into C/C++ for better performance and via Numba, it can run on GPU.

## Comparison of MATLAB, Python and R
*1 for best*

|Features    |MATLAB|   R    |Python|
|------------|:------:|:------:|:----:|
|Easy for Use|   1  |   2    |   2  |
|    IDE     |   1  |   3    |   1  |
|    Speed   |   1  |   3    |   2  |
|  Toolboxes |   2  |   1    |   1  |
| Into C/C++ |   1  |  N/A   |   1  |
|    Price   |   2  |   1    |   1  |
