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

A gist describing the feature-branch workflow can be found here:
https://gist.github.com/jakobgerstenlauer/2e6d99cf1ee8f7c9a5e890a2ff79fb08


## Git workflow patterns for scripts

Scripts are not self-contained units of codes, because they make only sense for a specific data set and they typically make use of severall packages for data processing, visualization, and statistical modelling. Scripts are typically used by one specific data scientist at a time and they change over time when new data becomes available or analysis objectives change. Based on this ephemeral nature of scripts, different git workflow patterns are appropriate:

## Tag workflow

All commits are made on a single branch (master). Whenever there are significant external changes, such as new updated versions of data sources, or whenever a certain version of several scripts is used to produce a specific output (a presentation, a report, or a summary data set) tags are used to label these specific versions. Because of the strong connection between code and data, it makes sense to also include the raw data or at least some summary information of the raw data in the version control system to make the analysis reproducible. 

## Quality assessment for scripts
In contrast to packages, the approach to tests differs: Instead of unit-tests, data scientists should use assertive statements (asserts, checks) to make sure that certain assumptions about the underlying data are valid. In R the validate package provides tools to define rules and apply them to a data set. Other crucial tests include statistical checks concerning goodness of fit, patterns in residuals, cross-validation, and the visualization of model predictions. General dangers of model misuse related to [extrapolation](https://en.wikipedia.org/wiki/Extrapolation), faulty input data, and confusing correlative with cause-effect relationships should also not be ignored.
