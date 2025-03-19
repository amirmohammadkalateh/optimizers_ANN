# Nesterov Accelerated Gradient (NAG)

This repository provides a clear and concise implementation and visualization of the Nesterov Accelerated Gradient (NAG) optimization algorithm.

## What is Nesterov Accelerated Gradient (NAG)?

Nesterov Accelerated Gradient (NAG) is a first-order optimization algorithm that enhances the convergence speed of gradient descent, particularly in non-convex optimization problems common in machine learning and deep learning. It's a refinement of gradient descent with momentum, designed to address a key limitation: the "overshooting" problem.

**Detailed Explanation:**

* **Momentum's Limitation:**
    * Standard momentum accelerates gradient descent by accumulating a velocity vector in the direction of past gradients. However, it can lead to overshooting the minimum, as the accumulated velocity might carry the parameters too far.
* **NAG's Innovation: Look-Ahead Gradient:**
    * NAG addresses this by evaluating the gradient at a "look-ahead" position. This look-ahead is achieved by taking a step in the direction of the current momentum before calculating the gradient.
    * Essentially, it asks, "Where will my momentum take me?" and then calculates the gradient at that predicted future point.
    * This allows the algorithm to anticipate changes in the gradient and correct its trajectory before overshooting.
* **Mathematical Formulation (Simplified):**
    * Let `θ` represent the parameters, `v` the velocity (momentum), `η` the learning rate, and `μ` the momentum factor.
    * **Standard Momentum:**
        * `v_t = μ * v_{t-1} - η * ∇J(θ_{t-1})`
        * `θ_t = θ_{t-1} + v_t`
    * **NAG:**
        * `θ_lookahead = θ_{t-1} + μ * v_{t-1}`
        * `v_t = μ * v_{t-1} - η * ∇J(θ_lookahead)`
        * `θ_t = θ_{t-1} + v_t`
    * Where `∇J(θ)` is the gradient of the loss function `J` with respect to `θ`.

**Key Advantages:**

* **Faster Convergence:** NAG typically converges faster than standard gradient descent and momentum, especially in complex loss landscapes.
* **Reduced Oscillations:** The look-ahead mechanism helps to mitigate oscillations and improve stability.
* **Improved Accuracy:** By anticipating gradient changes, NAG can achieve more accurate convergence to the minimum.

## Implementation Details

This repository provides a Python implementation using `numpy` for numerical computations and `matplotlib` for visualization.

