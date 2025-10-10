## Lecture 3 Probability & Statistics

- **Why They're So Important:** Machine learning models learn from data, and data from the real world is inherently messy, random, and **uncertain**. Probability and statistics give us the tools to handle this uncertainty.
    
    > **In simple terms:** Think of ML as being a detective. You have a pile of clues (**data**) and you need to build a theory (**model**).
    > 
    > - **Probability** is the language of confidence. It lets the detective say, "I'm 90% sure about my theory."
    >     
    > - **Statistics** is the set of tools for analyzing clues. It helps the detective find patterns and decide if the theory is actually good.
    >     
    
- **Where We Use Probability (Quantifying Uncertainty):**
    
    - **Building Models:** Many ML algorithms are built directly on probability. A classic example is the **Naive Bayes** algorithm, which uses probability to classify things like spam emails.
        
    - **Making Predictions:** Models often output a probability score. A classifier won't just say "that's a cat," it will say "there is a 95% probability that this is a cat."
        
    - **Loss Functions:** When training, we need to measure how wrong a model is. Many loss functions (like **cross-entropy**) are based on probability to measure the difference between the model's predicted probabilities and the actual outcomes.
        
- **Where We Use Statistics (Learning from Data):**
    
    - **Understanding Data (Descriptive Statistics):** Before building a model, we use statistics like **mean**, **median**, and **standard deviation** to explore and understand the dataset's properties.
        
    - **Evaluating Models (Inferential Statistics):** After training a model, we use statistical **hypothesis testing** (like A/B tests) to determine if its performance is genuinely good or just a result of random chance.
        
    - **Data Collection:** Statistics guides how we **sample** data to ensure it's a fair representation of the real world, helping to prevent bias in our models.
