# ECE2112_PA2

**Made by:** Matthew Zowie F. Berza

**Section:** 2ECE-D

--------
This repository contains the Programming Assignment #1 for ECE2112, implemented in a Jupyter Notebook. It covers NumPy array creation, matrix reshaping, vectorized operations, statistical metrics, Boolean indexing, and saving arrays as binary files.

# A. REPRODUCIBLE NORMALIZATION PROBLEM

**Objective:** Create a reproducible $5 \times 5$ random integer array, normalize its elements using standard score (Z-score) normalization, and save the resulting array.

-------
**Discussion:** Setting `np.random.seed(2112)` ensures reproducible pseudo-random integer generation when constructing the $5 \times 5$ array $X$ via `np.random.randint(10, 101, size=(5, 5))`. Normalization applies the formula:
$$Z = \frac{X - \bar{x}}{\sigma}$$
where $\bar{x}$ is calculated using `np.mean(X)` ($46.36$) and $\sigma$ using `np.std(X)` ($25.864$). Evaluating `np.mean(X_normalized)` yields `0.0` and `np.std(X_normalized)` yields `0.9999999999999999`, confirming a normalized mean of 0 and a standard deviation of 1.

The solution was constructed as:
```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```

# B. CUBES DIVISIBLE BY 4 PROBLEM

**Objective:** Generate the first 100 positive integers, compute their cubes, reshape the output into a $10 \times 10$ array, and extract all values divisible by 4 using Boolean indexing while preserving row-major order.

--------
**Discussion:** The sequence of integers $1$ through $100$ is generated using `np.arange(1, 101)` and cubed element-wise using vectorized exponentiation `c**3`. The resulting array is reshaped into a $10 \times 10$ matrix using `.reshape(10, 10)`. The Boolean mask `C % 4 == 0` evaluates each value for divisibility by 4, extracting a 1D array of 50 selected elements starting at $8$ ($2^3$) and ending at $1,000,000$ ($100^3$).

The solution was constructed as:

```Python
c = np.arange(1, 101)[cite: 4]
C = (c**3)[cite: 4]
Cc = C.reshape(10, 10)[cite: 4]

div_by_4 = C[C % 4 == 0][cite: 4]

np.save("div_by_4.npy", div_by_4)[cite: 4]
sd = np.std(X)[cite: 4]
```
# C. ABOVE-MEAN SQUARES PROBLEM

**Objective:** Create a $6 \times 6$ array containing the squares of the first 36 positive integers, compute its mean, and use Boolean filtering to select elements strictly greater than the mean.

**Discussion:** Sequential integers $1$ through $36$ are created, reshaped into a $6 \times 6$ grid using `.reshape(6, 6)`, and squared element-wise (`s**2`) to form matrix $S$ with values ranging from $1$ to $1296$. Computing `np.mean(S)` yields $S_{\text{mean}} \approx 450.167$. Applying the Boolean filter `S > S_mean` extracts 15 elements that strictly exceed the mean, ranging from $484$ ($22^2$) to $1296$ ($36^2$).

The solution was constructed as:

```Python
s = np.arange(1, 37)[cite: 4]
s = s.reshape(6, 6)[cite: 4]
S = s**2[cite: 4]

S_mean = np.mean(S)[cite: 4]
above_mean = S[S > S_mean][cite: 4]

np.save("above_mean.npy", above_mean)[cite: 4]
```
