# AdaGrad (Adaptive Gradient Algorithm)

AdaGrad is an adaptive learning rate optimization algorithm designed to address some of the shortcomings of standard gradient descent. It adapts the learning rate to the parameters, performing larger updates for infrequent and smaller updates for frequent parameters. This makes it suitable for handling sparse data.

## Overview

Traditional gradient descent uses a single learning rate for all parameter updates. This can be problematic when dealing with datasets where some features are more frequent than others. AdaGrad improves upon this by adjusting the learning rate for each parameter individually based on the historical gradients.

## How it Works

1.  **Initialization:**
    * Initialize the parameters ($\theta$) and the learning rate ($\eta$).
    * Initialize a vector $s$ to accumulate the squared gradients for each parameter, setting it to zero.

2.  **Gradient Calculation:**
    * Compute the gradient of the objective function ($g_t$) with respect to the parameters at time step $t$.

3.  **Accumulate Squared Gradients:**
    * Update the squared gradient accumulator $s_t$:
        * $s_t = s_{t-1} + g_t \odot g_t$ (where $\odot$ denotes element-wise multiplication).

4.  **Parameter Update:**
    * Update the parameters:
        * $\theta_{t+1} = \theta_t - \frac{\eta}{\sqrt{s_t} + \epsilon} \odot g_t$
        * where $\epsilon$ is a small constant (e.g., $10^{-8}$) to prevent division by zero.

## Key Features

* **Adaptive Learning Rates:** AdaGrad adapts the learning rate for each parameter, providing larger updates for infrequent parameters and smaller updates for frequent parameters.
* **Suitable for Sparse Data:** It performs well with sparse data because it increases the learning rate for parameters that are updated infrequently.
* **Automatic Learning Rate Tuning:** Reduces the need for manual tuning of the learning rate.

## Advantages

* Handles sparse data effectively.
* Eliminates the need to manually tune the learning rate for each parameter.
* Adapts well to problems with varying feature frequencies.

## Disadvantages

* **Decreasing Learning Rate:** The accumulated squared gradients ($s_t$) continuously increase, leading to a diminishing learning rate over time. This can cause the algorithm to stop learning prematurely.
* **Sensitivity to Initial Learning Rate:** The initial learning rate ($\eta$) still needs to be chosen carefully.
