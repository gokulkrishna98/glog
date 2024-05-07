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

# Prerequisites
Have CMake Installed, C++/C basics. check using `cmake --version`, `gcc --verion`.

# Compiling Single File
In this project we have two files tutorial.cpp and tutorial.h, indicating the source file and header file for the source file. What do we want to accompilish here:
- Version of the coder repo (2.1, 1.4 etc)
- Tell what version standard c++ to use (c++11, c++14, c++17)
- Build an executabe with a 

Before starting let us have two files `draw.cpp` and `draw.h`. We create a file named `CMakeLists.txt` which will do the above mentioned steps.

## Versioning
The versioning is usually two numbers: major version number and minor version number. Small incremental updates are done through minor version number and big substantial changes are done through major version number. The convention is `major_num . minor_um` eg: 2.1, 4.2 etc. To do this first we have to mention project name and the version number, add the following in CMakefile.
```
project(Draw VERSION 1.0)
```
Now we may have to add this info to our cxx file for printing, debugging so we can access it in our program. This can be done via preprocessor directives using header file. CMake gives us a automatic way to create this header file by writing a input file to cmake. To do this create config.h.in file for config and add the following
```
#define Draw_VERSION_MAJOR @Draw_VERSION_MAJOR@
#define Draw_VERSION_MINOR @Draw_VERSION_MINOR@
```
Then add the following in `CMakeLists` to use config_file function
```
configure_file(config.h.in config.h)
```

we can use these variables in our program by including the config.h file, which will be created during cmake build step.

## SETTING C++ standard
We have option to tell cmake to use which c++ standard for the project. We can also tell if this requirement needs to be strict or optional. To do this add the following:
```
set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)
```

## Building executable
To do this we need to do two things:
1. mention the include directory.
2. mention the binary name.

To do this add the following:
```
add_executable(Draw draw.cpp)
target_include_directories(Draw PUBLIC "${PROJECT_BINARY_DIR}")
```
Let us look at the second command and what it does (target here means Draw):
- Draw: This is the name of the target (likely an executable or library) that you're specifying the include directories for.
- PUBLIC: This keyword specifies that the include directories should be used by the target and all of its dependents. That is it dictates visibility of the Target.
- "${PROJECT_BINARY_DIR}": This is a CMake variable that represents the binary directory of the project. It's where the compiled executables and libraries are stored.

There are lot of CMake versions, some are not backwards compatible, so we can mention CMake requirement in our build file. To do that add the following
```
cmake_minimum_required(VERSION 3.22.1)
```

The overal file will look somewhat like this:
```
cmake_minimum_required(VERSION 3.22.1)

project(Draw VERSION 1.0)

configure_file(config.h.in config.h)

set(CMAKE_CXX_STANDARD 11)
set(CMAKE_CXX_STANDARD_REQUIRED True)

add_executable(Draw draw.cpp)
target_include_directories(Draw PUBLIC "${PROJECT_BINARY_DIR}")
```

now create a folder called build and go there. Then run the following commands to build.
```
cmake <path to CMakeLists.txt>
cmake --build .
```

# Let us see how to add Library to our single executable project.




