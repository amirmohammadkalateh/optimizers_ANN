```markdown
# RMSProp (Root Mean Square Propagation)

RMSProp is an adaptive learning rate optimization algorithm designed to address the challenges of training deep neural networks, particularly in scenarios where gradients exhibit varying magnitudes. It's an effective alternative to traditional gradient descent, offering improvements in convergence speed and stability.

## Overview

Traditional gradient descent uses a single learning rate for all parameters, which can lead to slow convergence or oscillations if the gradients vary significantly across different dimensions. RMSProp tackles this issue by adapting the learning rate for each parameter based on the magnitude of its recent gradients.

## How it Works

RMSProp maintains a moving average of the squared gradients for each parameter. This moving average is then used to normalize the gradient before updating the parameters. Here's a breakdown of the steps:

1.  **Calculate Gradients:** Compute the gradients of the loss function with respect to the parameters.
2.  **Maintain Moving Average of Squared Gradients:**
    * Let $v_t$ represent the moving average of squared gradients at time step $t$.
    * Update $v_t$ using the following formula:
        $$v_t = \beta v_{t-1} + (1 - \beta) (\nabla L(\theta_t))^2$$
        * Where:
            * $\beta$ is the decay rate (typically around 0.9), controlling the influence of past gradients.
            * $\nabla L(\theta_t)$ is the gradient of the loss function $L$ with respect to the parameters $\theta$ at time step $t$.
            * $(\nabla L(\theta_t))^2$ represents element-wise squaring of the gradient.
3.  **Update Parameters:**
    * Update the parameters $\theta_t$ using the following formula:
        $$\theta_{t+1} = \theta_t - \frac{\alpha}{\sqrt{v_t} + \epsilon} \nabla L(\theta_t)$$
        * Where:
            * $\alpha$ is the learning rate.
            * $\epsilon$ is a small constant (e.g., $10^{-8}$) added to prevent division by zero.
            * $\sqrt{v_t}$ represents element-wise square root of the moving average.

## Key Advantages

* **Adaptive Learning Rates:** RMSProp adapts the learning rate for each parameter, allowing for faster convergence in complex landscapes.
* **Handles Varying Gradient Magnitudes:** It effectively addresses scenarios where gradients have different magnitudes across dimensions.
* **Mitigates Oscillations:** By normalizing gradients, RMSProp reduces oscillations and improves stability.
* **Suitable for Non-Convex Optimization:** Works well with non-convex loss functions commonly encountered in deep learning.

## Hyperparameters

* **Learning Rate ($\alpha$):** Controls the step size during optimization.
* **Decay Rate ($\beta$):** Controls the influence of past gradients (typically 0.9).
* **Epsilon ($\epsilon$):** Small constant for numerical stability.


```


