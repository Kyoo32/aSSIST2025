## Lecture 2 Linear Models

- **Linear Models** can be represented by a data matrix and a weight vector and can be solved using tools from linear algebra.
    
    > **In simple terms:** Solving for the "weights" just means finding the best-fit line for your data. You measure how "bad" your line is using an error score (like **MSE**), which creates a big error "bowl" 🥣. The goal is to find the slope and intercept at the very bottom of that bowl, where the error is smallest.
    
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
