---
layout: post
title:  "CmAKE recipe :cake: !"
date:   2024-05-05 19:35:37 -0500
categories: jekyll update
---
# Introduction
As you know, CMake is a build systems that allows us to compile large code files, libraries and versioning with
with set of rules and giving us the power to configure the build. Let us see how to do CMAKE to build some systems. CMake is mostly used for compiling C and C++ codebases, and I will be using C++ here.
I followed the official tutorial, please look at it. This just my notes and peasant level understanding.

# Compiling Single File
In this project we have two files tutorial.cpp and tutorial.h, indicating the source file and header file for the source file. What do we want to accompilish here:
- Build an executabe with a name
- Tell what version standard c++ to use (c++11, c++14, c++17)
- Version of the coder repo (2.1, 1.4 etc)
- 