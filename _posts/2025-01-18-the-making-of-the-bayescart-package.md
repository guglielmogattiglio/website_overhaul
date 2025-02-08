---
title: "BayesCART: a Python package for efficient Bayesian CART model search"
# last_modified_at: 2016-03-09T16:20:02-05:00
categories:
  - Blog
  - Coding
tags:
  - Bayesian CART
  - Python package development
  - Object oriented programming
  - Tree models
  - MCMC
permalink: /blog/bayescart-python-package/
excerpt: "Insights into the making of BayesCART packages: coding and optimization tricks to get the most out of your code."
---

### Introduction

[BayesCART](https://github.com/guglielmogattiglio/bayescart/) is a Python package for Bayesian Classification and Regression Trees (CART) with advanced Markov Chain Monte Carlo (MCMC) sampling. Designed for modularity, efficiency, and extensibility, it follows best practices of modern, high-performance machine learning software.

![A screenshot of the bayescart package code](/assets/posts/the-making-of-the-bayescart-package/bayescart_package_cut_better.png){:.cnt }

### At a glance

- **Advanced ML Algorithms**: Implements Bayesian MCMC samplers for flexible and scalable probabilistic tree modelling.
- **Efficient Software Design**: Built using modular OOP principles, leverages caching strategies and optimized tree operations for high performance.
- **Robust Engineering Practices**: Comprehensive documentation, type hints, and automated CI workflows enhance reliability and maintainability.
- **Scalability and Extensibility**: Designed to handle large datasets efficiently, with subclassing mechanisms allowing seamless expansion of features.
- **Parallelism and Performance**: Supports parallel execution to accelerate MCMC computations, leveraging multiprocessing for scalable inference.
- **Optimized Data Structures**: Integrates efficiently with pandas and numpy to manage data and speed up operations, reducing processing overhead.
- **Innovative Tempering Strategies**: Tackles multimodality in Bayesian CART models with custom MCMC tempering techniques, ensuring efficient posterior exploration and improved convergence.
- **Optimized Memory Usage**: Lightweight copy mechanisms reduce overhead during iterative tree updates, minimizing redundant computations.
**Design Philosophy and Modularity**. The package follows an object-oriented design with a hierarchical class structure for seamless extension and optimization. Memory and speed optimized methods can be introduced without modifying core infrastructure, and new sampling strategies integrate easily via subclassing.

### Computational Efficiency
Several design choices have been introduces to boost performance:

- _Optimized Copying_: NodeFast and TreeFast reduce memory overhead by copying only those attributes that would corrupt the sampling process.
- _Caching_: Likelihoods, priors, data, and other intermediate results are stored at the node level, minimizing redundant calculations.
- _Fast Sampling_: Custom samplers for prior distributions replace slower library routines.
- _Efficient Data Handling_: Data subsets are stored at each internal and leaf node to provide quick access. While this increases momery footprint, it sensibly speeds-up routine operations such as splitting and estimating parameters, because no pre-processing of the tree data is needed.

### Advanced MCMC and Tempering Strategies

BayesCART supports multiple tempering strategies for better posterior exploration:
- _Geometric Tempering_ (`BCARTGeom`): Designed for multimodal distributions, this method duplicates and flattens the posterior density function to facilitate exploration. It helps escape local modes but may require careful tuning of the temperature schedule to balance exploration and exploitation.
- _Likelihood-Based Tempering_ (`BCARTGeomLik`): Similar to Geometric tempering, but flattening is only applied to the integrated likelihood. By retaining prior information on the tree characteristics (e.g. size), the flatter posterior is biased towards less overfit trees, which are more likely. This method enhances mixing but can potentially distort prior information.
- _Pseudo-Prior Tempering_ (`BCARTPseudoPrior`): Introduces an auxiliary prior to smooth transitions between modes, biasing sampling towards smaller trees. This aids exploration as smaller trees are more easily changed by the MCMC. It shows similar performance as Likelihood-Based Tempering, but with a more theoretically sound formulation.

Moreover, a shared parallel tempering base class ensures modularity for new methods, allowing flexible implementation of alternative strategies. 

### Documentation and Testing

BayesCART adheres to best practices:
- Sphinx Documentation: Clear, well-maintained API references.
- Type Annotations: Improves readability and prevents common runtime errors.
- Automated Testing: CI workflows via GitHub Actions ensure reliability.

BayesCART extends the existing `treelib` Python library by embedding data, metadata and sampling logic within nodes. I am grateful to the `treelib` authors and maintainers for providing a simple yet robust implementation of trees.

### Additional resources

{% assign target_post = site.posts | where: "slug", "using-bcart-to-solve-cgm98" | first %}
{% assign target_post2 = site.posts | where: "slug", "bcart-theoretical-series" | first %}
- A [tutorial]({{ target_post.url }})  on how to use the package
- A [theoretical treatment]({{target_post2.url}}) of Bayesian CART, and tempering algorithms
- The [package documentation](https://guglielmogattiglio.github.io/bayescart/) and [official repo](https://github.com/guglielmogattiglio/bayescart)

