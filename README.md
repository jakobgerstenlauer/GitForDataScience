# GitForDataScience
A short selection of typical git work flow patterns for data science projects.

## Overview
In data science projects, we can separate code into two broad categories: scripts and packages. 
Scripts have a linear structure, they may or may not include some ad-hoc function definitions but are in general characterized by the usage of classes and functions defined elsewhere (i.e. in external packages or libraries). Packages (or libraries), on the other hand, are self contained units of code which define classes and functions (or methods if OOP is applied). Packages do not run any data analyses and instead provide generic tools which can be applied in specific data analysis scripts. I think that depending on the type of code (scripts or packages) different git workflow patterns are appropriate:

## Git workflow patterns for packages

Packages are self-contained units of codes which are written with the purpose of providing generic tools for a potentially wide range of different users which are not aware of the inner workings of their functions. Based on the generic nature of packages, different users might end up becoming contributors of new features. Once the core functionalities of a package have been established and tested by one or a few authors, it makes sense to use the feature-branch work flow to further extend the package.

## Feature-branch workflow

Applicability of this workflow is based on the following requirements:
* Features are self-contained, relatively small extensions (i.e. easy and fast implementation) to the basic functionality of a package.
* Code in the package is organized in such a way as to allow extensions by users without requiring an in-depth understanding of the entirety of the code (modularity achieved by OOP or other forms of abstraction).
* Test frameworks allow to continuously test if extensions break existing features.

