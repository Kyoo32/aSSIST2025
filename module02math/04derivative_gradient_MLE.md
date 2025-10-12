## Lecture 4: Calculus & Optimization 

* A **derivative** is a fundamental concept in calculus. It describes the instantaneous rate of change of a function's output as its input changes.

    > **In simple terms:** A derivative just tells you the **slope** of a function at one specific point. It answers the question, "How steep is this curve right *here*?"

* The **gradient** is a vector that points in the direction of the steepest ascent for a multi-variable function. It's calculated using the partial derivatives for each variable.

* **Activation Functions**: These are mathematical "gates" inside a neural network's neuron that introduce crucial **non-linearity**. Without them, a neural network could only learn simple, straight-line patterns.
    * **Sigmoid**: A function that squishes any number into a probability between 0 and 1. It's great for the output of binary classifiers.
    * **ReLU**: The most popular activation function. It simply outputs 0 for negative inputs and the input value itself for positive inputs.

***

### Optimization Methods

* **Gradient Descent**: This is an iterative method used to find the minimum value of a function when a direct solution (a closed-form solution) isn't available. Modern frameworks can perform these calculations for us thanks to **automatic differentiation**.

    > **In simple terms:** Gradient descent is like placing a ball in a big bowl (the loss function) and letting it roll downhill. The gradient tells the ball which way is the steepest "down" at any point, and it takes small steps in that direction until it settles at the bottom, finding the minimum error.

* **Maximum Likelihood Estimation (MLE)**: MLE is a powerful statistical technique for estimating the parameters of a distribution by finding the values that maximize the likelihood of the observed data. It answers the question: "Given the data I saw, what are the most plausible parameters that generated it?".

* **Minimizing the Negative Log-Likelihood**:
    * Maximizing the likelihood is mathematically the same as **minimizing the negative log-likelihood**. We use the logarithm for computational convenience.
    * This principle is the foundation for many ML algorithms. When you minimize a loss function like **Cross-Entropy**, you are performing Maximum Likelihood Estimation. This method is used to train important models like **logistic regression**.
