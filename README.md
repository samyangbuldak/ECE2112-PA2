# ECE2112 - Programming Assignment 2

This repository contains my solutions for **Programming Assignment 2** in ECE2112 - Advanced Computer Programming and Algorithms.

The activity focuses on using **NumPy** for creating arrays, performing mathematical operations, normalization, reshaping, filtering, and saving arrays into files.

## Files

* `SAMOY_PA2.ipynb` - Jupyter Notebook containing the Python codes
* `X_normalized.npy` - Saved normalized array
* `above_mean.npy` - Saved array containing values above the mean
* `README.md` - Documentation of the program

---

## Importing NumPy

```python
import numpy as np
```

NumPy is imported as `np` to make its functions easier and shorter to call throughout the program.

---

## A. Reproducible Normalization Problem

```python
np.random.seed(2112)
X = np.random.randint(10, 101, size=(5, 5))
```

`np.random.seed(2112)` sets a fixed random seed so that the same random numbers are generated every time the program is executed.

`np.random.randint(10, 101, size=(5, 5))` generates a **5 × 5 array** containing random integers from **10 to 100**.

### Getting the Mean and Standard Deviation

```python
X_mean = X.mean()
X_std = X.std()
```

* `X.mean()` calculates the mean of all values in the array.
* `X.std()` calculates the standard deviation of the array.

### Normalizing the Array

```python
X_normalized = (X - X_mean) / X_std
```

The array is normalized using the formula:

```text
X_normalized = (X - mean) / standard deviation
```

Each element is subtracted by the mean and divided by the standard deviation. This results in normalized data with a mean close to `0` and a standard deviation close to `1`.

### Displaying the Results

```python
print("X: ", X)
print("The Normalized array is: ", X_normalized)
print("\nMean: ", X_normalized.mean())
print("\nSTD: ", X_normalized.std())
```

This displays the original array, normalized array, and verifies the mean and standard deviation of the normalized values.

### Saving the Array

```python
np.save('X_normalized.npy', X_normalized)
```

`np.save()` saves the normalized NumPy array into a `.npy` file named `X_normalized.npy`.

---

## B. Cubes Divisible by 4 Problem

```python
A = np.arange(1,101)
```

`np.arange(1,101)` creates an array containing numbers from **1 to 100**.

### Getting the Cubes

```python
B = A**3
```

`A**3` raises every element of array `A` to the power of 3.

### Reshaping the Array

```python
C = B.reshape(10,10)
```

`.reshape(10,10)` converts the one-dimensional array into a **10 × 10 matrix**.

### Finding Values Divisible by 4

```python
div_by_4 = C[C % 4 == 0]
```

`C % 4 == 0` checks which values have no remainder when divided by 4.

The matching values are then selected from array `C` and stored in `div_by_4`.

### Displaying the Results

```python
print("Shape of C: ", C.shape)
print("\nDivisible by 4:", div_by_4)
print("Number of selected items: ", div_by_4.size)
```

* `C.shape` displays the dimensions of the array.
* `div_by_4` displays all cubes divisible by 4.
* `.size` gives the total number of selected values.

---

## C. Above-Mean Squares Problem

```python
CC = np.arange(1,37)
```

This creates an array containing integers from **1 to 36**.

### Squaring and Reshaping

```python
S = ((CC **2).reshape(6,6))
```

Each number is squared using `**2`, then the resulting values are reshaped into a **6 × 6 matrix**.

### Finding the Mean

```python
S_mean = S.mean()
```

`S.mean()` calculates the average of all squared values in array `S`.

### Selecting Values Above the Mean

```python
above_mean = S[S > S_mean]
```

`S > S_mean` checks every value in the array and selects only the elements that are greater than the calculated mean.

### Displaying the Results

```python
print("\nS: ", S)
print("\nS mean: ", S_mean)
print("\nAbove mean: ", above_mean)
print("\nNumber of selected elements: ", above_mean.size)
```

This displays the squared matrix, its mean, the values above the mean, and the number of selected elements.

### Saving the Result

```python
np.save('above_mean.npy', above_mean)
```

The selected values are saved as a NumPy file named `above_mean.npy`.

---

## NumPy Concepts Used

The activity applies the following NumPy concepts:

* `np.random.seed()`
* `np.random.randint()`
* `np.arange()`
* `.mean()`
* `.std()`
* Array arithmetic
* `.reshape()`
* Boolean indexing
* Modulo operator `%`
* `.shape`
* `.size`
* `np.save()`

---

## Requirements

The program requires:

```text
Python
NumPy
Jupyter Notebook
```

NumPy can be installed using:

```bash
pip install numpy
```

---

## Summary

The activity demonstrates the basic use of NumPy in numerical computing. It includes generating reproducible random arrays, normalizing data, performing element-wise mathematical operations, reshaping arrays, filtering values using conditions, and saving NumPy arrays into `.npy` files.
