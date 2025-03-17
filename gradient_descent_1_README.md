```markdown
# Gradient Descent Example

This repository demonstrates a simple implementation of the gradient descent algorithm to find the minimum of a quadratic function.

## Code Explanation

### Function Definition

```python
def func(x):
  return x**2
```

This function defines the quadratic function $f(x) = x^2$, which we aim to minimize.

### Gradient Function

```python
def func_grad(x):
  return 2*x
```

This function calculates the gradient (derivative) of $f(x)$ with respect to $x$, which is $f'(x) = 2x$. The gradient indicates the direction of the steepest ascent of the function at a given point.

### Gradient Descent Algorithm

```python
def gradient_descent(lr, func_grad):
  x = -10
  x_values = [x]
  for i in range(10):
    x -= lr * func_grad(x)
    x_values.append(x)
    print("iteration 10, x : %s" % x)
  return x_values
```

This function implements the gradient descent algorithm:

1.  **Initialization:**
    * `x` is initialized to -10, representing the starting point.
    * `x_values` is initialized as a list containing the starting point.
2.  **Iteration:**
    * The loop iterates 10 times.
    * In each iteration, `x` is updated by subtracting the product of the learning rate (`lr`) and the gradient (`func_grad(x)`). This moves `x` in the direction opposite to the gradient, aiming to reach the minimum.
    * The updated `x` is appended to `x_values`.
    * The current value of x is printed.
3.  **Return:**
    * The function returns the list `x_values`, containing the values of `x` at each iteration.

* `lr`: learning rate, a parameter that controls the step size in each iteration.

### Visualization

```python
import numpy as np
import matplotlib.pyplot as plt

def search_path(x_vals, func):
  x_line = np.arange(-15, 15, 0.01)
  plt.plot(x_line, [func(x) for x in x_line])
  plt.plot(x_vals, [func(x) for x in x_vals], "ro-")
```

This function visualizes the gradient descent process:

1.  **Generate x-axis data:**
    * `x_line` is created using `numpy.arange` to generate a range of x-values for plotting the function.
2.  **Plot the function:**
    * `plt.plot(x_line, [func(x) for x in x_line])` plots the graph of $f(x) = x^2$ over the generated range.
3.  **Plot the search path:**
    * `plt.plot(x_vals, [func(x) for x in x_vals], "ro-")` plots the path taken by the gradient descent algorithm.
        * `x_vals` are the x-coordinates of the iterations.
        * `[func(x) for x in x_vals]` are the corresponding y-coordinates.
        * `"ro-"` specifies red circles connected by lines.
4.  **Display the plot:**
    * `plt.show()` displays the generated plot.

### Execution

```python
x_values = gradient_descent(0.1, func_grad)
search_path(x_values, func)
```

This section executes the gradient descent and visualization:

1.  `gradient_descent(0.1, func_grad)` performs the gradient descent with a learning rate of 0.1 and stores the results in `x_values`.
2.  `search_path(x_values, func)` plots the function and the search path taken by the algorithm.


