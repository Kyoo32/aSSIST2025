## Lecture 2 Linear Models

- **Linear Models** can be represented by a data matrix and a weight vector and can be solved using tools from linear algebra.
    
    > **In simple terms:** Solving for the "weights" just means finding the best-fit line for your data. You measure how "bad" your line is using an error score (like **MSE**), which creates a big error "bowl" 🥣. The goal is to find the slope and intercept at the very bottom of that bowl, where the error is smallest.
    
Of course. Here is a note on Ordinary Least Squares (OLS) in the Lecture 2 format, including a simple Python example.



### Ordinary Least Squares (OLS) 

  * **What it is:** Ordinary Least Squares (OLS) is the most common method used to perform linear regression. Its goal is to find the single best-fitting straight line through a set of data points.

  * **How it Works:** OLS determines the "best" line by finding the one that **minimizes the sum of the squared residuals**. A "residual" is simply the vertical distance (the error) between an actual data point and the line.

    > **In simple terms:** Imagine your data points are tent pegs in the ground. OLS finds the exact position for a straight tent pole that makes the total squared length of all the vertical strings connecting the pegs to the pole as small as possible.

  * **Why Square the Errors?** We square the errors to make them all positive (so that errors above and below the line don't cancel each other out) and to heavily penalize larger errors.


This code finds the slope and intercept for the line that best fits the data according to OLS.

```python
import numpy as np
from sklearn.linear_model import LinearRegression

# 1. Create some sample data
# We need X to be a 2D array for scikit-learn
X = np.array([[1], [2], [3], [4], [5]]) # Feature (e.g., hours studied)
y = np.array([2, 4, 5, 4, 6])          # Target (e.g., test score)

# 2. Create and fit the OLS model
model = LinearRegression()
model.fit(X, y)

# 3. Get the results (the parameters of the best-fit line)
slope = model.coef_[0]
intercept = model.intercept_

print(f"The best-fit line is: y = {slope:.2f}x + {intercept:.2f}")
# This is the line that minimizes the sum of squared errors for this data.
```

### Matrix Decomposition 
- **Matrix Decomposition** is breaking a matrix down into two or three simpler matrices.
    
    - **LU Decomposition:** Used to solve linear systems.
        
    - **QR Decomposition:** Used for improved numerical stability.
        
    - **SVD (Singular Value Decomposition):** Used to separate _any_ matrix into its most fundamental components1
        
- **PCA (Principal Component Analysis)** is used to reduce the dimensions of data by finding new axes that maximize the data's variance, or spread.
    
- **SVD** can be used to calculate a low-rank approximation of a matrix, which is useful for recommender systems and image compression.
    
    > **PCA & SVD in simple terms:**
    > 
    > - **The Goal (PCA):** You have messy data with too many columns. PCA is a tool for **dimensionality reduction**. It finds the most interesting viewpoints of your data. It's like turning a 3D object to find the 2D shadow that shows its shape the best.
    >     
    > - **The Engine (SVD):** SVD is the master tool that says _any_ matrix transformation is just three simple steps: **Rotate -> Scale -> Rotate**. For image compression, it finds the most "important" parts of the picture, so you can throw away the details and keep a very similar-looking image that's much smaller. 🖼️
    >     
    > 
    > **The Connection:** PCA is the statistical goal (simplify my data!), and SVD is the powerful mathematical engine that actually does the work to achieve it.

