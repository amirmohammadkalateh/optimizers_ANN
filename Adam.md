# Adam Optimizer

Adam (Adaptive Moment Estimation) is an adaptive learning rate optimization algorithm designed for training deep neural networks. It combines the advantages of two popular methods: RMSProp and Momentum. Adam computes adaptive learning rates for each parameter.

## Key Features

* **Adaptive Learning Rates:** Adjusts the learning rate for each parameter based on estimates of first and second moments of the gradients.
* **Combines RMSProp and Momentum:** Leverages the benefits of both algorithms for efficient and effective optimization.
* **Computationally Efficient:** Requires little memory and is straightforward to implement.
* **Invariant to Diagonal Rescaling of Gradients:** Performs well even with sparse gradients or noisy problems.
* **Suitable for a Wide Range of Problems:** Works well in practice and compares favorably to other adaptive optimization algorithms.

## How Adam Works

Adam computes individual adaptive learning rates for different parameters from estimates of first and second moments of the gradients:

1.  **Compute Gradients:** Calculate the gradient of the loss function with respect to the parameters.
2.  **First Moment Estimation (Mean):**
    * Calculate an exponentially decaying average of past gradients (`m_t`).
    * `m_t = β1 * m_{t-1} + (1 - β1) * g_t`
    * Where `g_t` is the gradient at time step `t`, `β1` is a hyperparameter (typically 0.9).
3.  **Second Moment Estimation (Variance):**
    * Calculate an exponentially decaying average of past squared gradients (`v_t`).
    * `v_t = β2 * v_{t-1} + (1 - β2) * g_t^2`
    * Where `β2` is a hyperparameter (typically 0.999).
4.  **Bias Correction:**
    * Correct the first and second moment estimates for initialization bias.
    * `m_hat_t = m_t / (1 - β1^t)`
    * `v_hat_t = v_t / (1 - β2^t)`
5.  **Parameter Update:**
    * Update the parameters using the bias-corrected moment estimates.
    * `θ_t = θ_{t-1} - α * m_hat_t / (sqrt(v_hat_t) + ε)`
    * Where `α` is the learning rate, `θ` represents the parameters, and `ε` is a small constant to prevent division by zero (typically 1e-8).

## Parameters

* **α (Learning Rate):** Controls the step size.
* **β1 (Exponential Decay Rate for the First Moment Estimates):** Controls the decay rate of the moving average of the gradients.
* **β2 (Exponential Decay Rate for the Second Moment Estimates):** Controls the decay rate of the moving average of the squared gradients.
* **ε (Epsilon):** A very small number to prevent any division by zero in the implementation.

