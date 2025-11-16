# Page-Rank-project
Linear Algebra PageRank project
Genesis
I wanted to apply the Linear Algebra I learned through my passion for coding. This project is a basic PageRank-style algorithm that determines the relative ranking of websites in a search engine. I used Python and NumPy for the implementation.


**Goal:**
Rank each website by its inter-website relational importance.


**Why It Works (Math Overview):**
Important websites tend to be linked more often and be linked by other important websites.
Represent each website with a probability vector

Va...Vi...Vn, where all components sum to 1.
​
Collect all website vectors into the columns of a matrix M.
Because each column sums to 1, **M is column-stochastic.
Perron–Frobenius Theorem:
Any non-negative column-stochastic matrix has an eigenvalue of 1 and all other eigenvalues with absolute value less than 1.
Matrix M therefore models a Markov chain whose steady-state distribution gives the long-run probability of being on each website.**
These final probabilities are used as the website rankings.

Problems
Problem 1: Closed-Link Loops
A subset of websites may only link to each other, inflating their importance by creating a closed feedback loop.
Problem 2: Dead Ends
A website with no outgoing links has a column that sums to 0, breaking the column-stochastic condition and preventing Markov chain convergence.

Solution: Damping Method
Introduce a random probability of “jumping” to any website.
Fix for Closed Loops
Random jumps let the algorithm escape from closed loops and converge to the correct steady-state probabilities.
Fix for Dead Ends
Random jumps prevent the algorithm from getting stuck.
Replace any dead-end website’s column with uniform probabilities 
1/n to keep M column-stochastic.


**How It Works (Coding Steps):**
Start with a uniform probability of landing on any website.
Construct probability vectors whose components sum to 1.
Build the Markov matrix M by placing these vectors as columns.
**Iterate using the Power Method: repeatedly compute
x ← Mx**
until convergence.
The converged vector is the steady-state distribution.
Rank websites according to their steady-state probability.
