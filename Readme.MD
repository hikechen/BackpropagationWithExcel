# Implementing Backpropagation Neural Networks Using Excel

**Author:** Chen Shao-Jie  
**Date:** March 20, 2019

---

This document demonstrates how to implement a simple neural network with backpropagation entirely within Microsoft Excel. No programming code is required—just Excel formulas and built-in features.

## Introduction

Backpropagation is a fundamental algorithm for training neural networks, commonly used in machine learning. In this demonstration, we'll use Excel's iterative calculation capabilities to train a neural network on the XOR problem, a classic example illustrating the limitations of linear classifiers and the capability of multi-layer perceptrons.

## Setting Up Excel for Iterative Calculation

Excel can perform iterative calculations, enabling recursive updates needed for neural network training.

1. Open Excel, navigate to **File > Options > Formulas**.
2. Enable **"Enable iterative calculation"** and set the **"Maximum Iterations"** (e.g., 40 iterations).

![Insert image here: Iterative calculation settings screenshot]

To verify this feature:

- Enter `=A1+1` in cell `A1` and press `F9` repeatedly. You will see the number increment, confirming Excel’s iterative calculation capability.

![Insert image here: Simple iterative calculation demonstration]

## XOR Dataset

The XOR function dataset:

| Input 1 (X) | Input 2 (Y) | Output (XOR) |
|------------|------------|--------------|
| 0          | 0          | 0            |
| 0          | 1          | 1            |
| 1          | 0          | 1            |
| 1          | 1          | 0            |

## Neural Network Structure

We use a 2–3–1 neural network architecture:
- **2 input neurons**
- **3 neurons in one hidden layer**
- **1 output neuron**
- Bias terms are included

![Insert image here: Neural network diagram]

## Implementation in Excel

### Initial Setup

Define Excel cells for:
- **State management** (Training/Reset states)
- **Counters** for dataset index (`Idx`) and forward/backward propagation (`FB`)
- **Weights** initialized with random normal values (e.g., using Excel formula: `=NORMINV(RAND(),0,1/SQRT(n))`)

### Forward Propagation

Calculate neuron outputs using matrix multiplication (`MMULT`) and apply the sigmoid activation function:

\[ output = \sigma(x) = \frac{1}{1 + e^{-x}} \]

Example Excel formula:

```
=MMULT(TRANSPOSE(J16:L18), H16:H18)
```

*Note:* Press `Ctrl+Shift+Enter` to execute matrix operations.

### Loss Calculation

Use Mean Squared Error (MSE) to calculate loss:

\[ Loss = (predicted - actual)^2 \]

### Backpropagation and Weight Update

Apply the gradient descent method:

- Calculate gradients (deltas) for hidden and output layers.
- Update weights using:

\[ new\ weight = old\ weight - learning\ rate \times delta \times input \]

These updates occur iteratively based on Excel’s iterative calculations.

## Training Process

Initiate training by repeatedly executing Excel’s iterative calculations (e.g., press `F9`). The network progressively reduces loss and adjusts outputs to match the XOR dataset:

**Before Training:** Outputs are near random values (approx. 0.5).

**After Training (approx. 30 seconds):**
- Loss decreases significantly.
- Output predictions align closely with XOR truth values.

![Insert image here: Training result before and after comparison]

## Visualization

To visualize the network’s performance, we map outputs over a grid of input values and create a surface plot in Excel:

- Populate a grid with computed outputs.
- Generate a 3D surface chart.

![Insert image here: Excel surface plot of XOR decision boundary]

This visualization clearly demonstrates the non-linear boundary learned by the network, successfully solving the XOR classification problem.

## Conclusion

This implementation demonstrates that Excel’s iterative calculation feature can effectively simulate neural network training using backpropagation. Although limited compared to conventional programming methods, it provides an insightful educational perspective on neural networks.

---

You can download the Excel file to explore the implementation further (Insert download link here). Remember to enable iterative calculation to run correctly.

