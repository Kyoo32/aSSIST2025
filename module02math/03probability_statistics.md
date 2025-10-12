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

---

### Bayes' Theorem 

* **What it is:** Bayes' Theorem is a mathematical formula for updating our beliefs in light of new evidence. It's a formal way to use what we already know to make better predictions.

* **Direct Application: The Naive Bayes Classifier:**
    * This is a simple but powerful algorithm used for classification tasks. It uses Bayes' Theorem to calculate the probability of a class, given a set of features.
    * **The Analogy (Spam Filter 📧):** To figure out the probability that an email is **spam** given it contains the word "Viagra," Bayes' Theorem lets you use easier-to-measure probabilities:
        1. How often does "Viagra" appear in emails you *already know* are spam?
        2. What's the overall chance of *any* email being spam?
        3. How often does "Viagra" appear in *any* email?
    * It's called **"naive"** because it assumes all features (words) are independent, which isn't true but works well enough to be very useful.

* **Conceptual Foundation: Bayesian Machine Learning:**
    * This is a whole field of ML where model parameters (like weights) are not treated as single, fixed numbers but as **probability distributions** that represent our beliefs.
    * **The process:** You start with a **prior** belief about the parameters, combine it with the **likelihood** from your data, and get an updated **posterior** belief.
    * This allows models to express **uncertainty** in their predictions (e.g., "The price is $500k, and I'm 95% confident it's between $450k and $550k"). This is critical in fields like medicine or self-driving cars where knowing the model's confidence is essential.
 
#### Example
```python
# Import libraries
import numpy as np  # 수치 연산을 위한 numpy 라이브러리 
import matplotlib.pyplot as plt  # 데이터 시각화를 위한 matplotlib 라이브러리
import math  # 수학 함수를 위한 math 라이브러리
from itertools import product  # 반복 가능한 객체들의 데카르트 곱을 위한 product 함수
import pandas as pd  # 데이터 분석 및 처리를 위한 pandas 라이브러리

p_d = 0.01                            # 질병이 있을 사전 확률 (1%)
p_h = 0.99                            # 건강할 사전 확률 (99%)

p_pos_given_d = 0.95                  # 질병이 있을 때 양성이 나올 확률 (95%)
p_neg_given_d = 0.05                  # 질병이 있을 때 음성이 나올 확률 (5%)

p_pos_given_h = 0.05                  # 건강할 때 양성이 나올 확률 (5%)
p_neg_given_h = 0.95                  # 건강할 때 음성이 나올 확률 (95%)

def get_p_d_given_pos(p_d, p_h, p_pos_given_d, p_pos_given_h):
    p_d_given_pos = p_pos_given_d * p_d / (p_pos_given_d * p_d + p_pos_given_h * p_h)    # 베이즈 정리: P(D|Pos) = P(Pos|D)P(D) / [P(Pos|D)P(D) + P(Pos|H)P(H)]
    return p_d_given_pos

get_p_d_given_pos(p_d, p_h, p_pos_given_d, p_pos_given_h) # 양성 결과가 나왔을 때 실제로 질병이 있을 확률 계산
# 0.16101694915254236

```

---

### Common Distributions
* **Bernoulli Distribution:** This is used for a **single trial** with only **two possible outcomes** (e.g., success/failure, yes/no, 1/0). 🪙
    * **The key question is:** Will this *one* event succeed or fail?
    * **Examples:**
        * Will a *single user* click on an ad? (Yes/No)
        * Is a *single product* from the assembly line defective? (Defective/Not Defective)
        * Did a *single coin flip* land on heads? (Heads/Tails)

* **Poisson Distribution:** This is used for **counting the number of times** an event occurs within a **fixed interval** of time or space. ⏰
    * **The key question is:** *How many times* will this event happen in this interval?
    * **Examples:**
        * How many users visit a website *in one hour*?
        * How many calls does a call center receive *per minute*?
        * How many typos are on a *single page* of a book?

> **In simple terms:** Use **Bernoulli** for a single "yes/no" question. Use **Poisson** when you're counting occurrences over a period of time or an area.

---

### The Central Limit Theorem 

* **The Core Idea:** The Central Limit Theorem (CLT) is a fundamental concept that describes the shape of the distribution of sample means.

    > **In simple terms:** Imagine you're rolling a single die. The probability of getting any number (1 through 6) is the same (a flat, uniform distribution).
    >
    > Now, imagine you roll five dice and calculate their average. You do this again and again, thousands of times, and plot a histogram of all those averages.
    >
    > The CLT tells us that this new histogram of **averages** will form a beautiful **bell curve (a normal distribution)**, even though the original distribution of a single die roll was completely flat. 

* **Why It's So Important:**
    * It allows us to make inferences about a whole population using just a sample, even if we don't know the population's true distribution.
    * It is the foundation for many statistical methods, such as **hypothesis testing** and constructing **confidence intervals**. For example, it's why we can be confident that the average result from a political poll of 1,000 people is a good estimate of the entire country's opinion.
    * In machine learning, it helps us understand the behavior of model parameters and evaluate the significance of our results.

