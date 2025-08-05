# Julia and Python Linear Algebra Cheatsheet

## Importing Libraries
**Julia:**
```julia
using LinearAlgebra
```

**Python:**
```python
import numpy as np
```

---

## Creating Matrices
**Julia:**
```julia
A = [1 2; 3 4]   # 2x2 matrix
B = rand(3, 3)   # 3x3 random matrix
```

**Python:**
```python
A = np.array([[1, 2], [3, 4]])  # 2x2 matrix
B = np.random.rand(3, 3)        # 3x3 random matrix
```

---

## Visualizing Matrices in Python
### Example 1: 2x2 Matrix
```python
A = np.array([[1, 2],
              [3, 4]])
```
This corresponds to:
```
1  2
3  4
```

### Example 2: 3x2 Matrix
```python
B = np.array([[1, 2],
              [3, 4],
              [5, 6]])
```
This corresponds to:
```
1  2
3  4
5  6
```

---

## Creating a Zero Matrix and Populating It
**Julia:**
```julia
Z = zeros(3,3)   # 3x3 zero matrix
Z[1,2] = 5       # Assigning value to (1,2) position
```

**Python:**
```python
Z = np.zeros((3,3))  # 3x3 zero matrix
Z[0,1] = 5           # Assigning value to (0,1) position
```

---

## Identity Matrix
**Julia:**
```julia
I = I(3)  # 3x3 Identity matrix
```

**Python:**
```python
I = np.eye(3)  # 3x3 Identity matrix
```

---

## Matrix Transpose
**Julia:**
```julia
A'  # Transpose of A
```

**Python:**
```python
A.T  # Transpose of A
```

---

## Matrix Multiplication vs Dot Product
**Julia:**
```julia
C = A * B  # Matrix multiplication
D = dot(A, B)  # Dot product
```

**Python:**
```python
C = np.dot(A, B)  # Matrix multiplication
C = A @ B  # Alternative multiplication
D = np.dot(A.flatten(), B.flatten())  # Dot product of flattened arrays
```

### Difference:
- **Matrix multiplication (`*` in Julia, `@` or `np.dot` in Python)** performs standard matrix multiplication.
- **Dot product (`dot(A, B)` in Julia, `np.dot(A.flatten(), B.flatten())` in Python)** computes the sum of the element-wise products of two arrays.

---

## Solving Linear Systems (Ax = b)
**Julia:**
```julia
x = A \ b  # Solves Ax = b
```

**Python:**
```python
x = np.linalg.solve(A, b)  # Solves Ax = b
```

---

## Eigenvalues and Eigenvectors
**Julia:**
```julia
eigvals(A)    # Eigenvalues of A
eigvecs(A)    # Eigenvectors of A
```

**Python:**
```python
eigenvalues, eigenvectors = np.linalg.eig(A)  # Eigenvalues & Eigenvectors
```

---

## Singular Value Decomposition (SVD)
**Julia:**
```julia
U, S, V = svd(A)
```

**Python:**
```python
U, S, V = np.linalg.svd(A)
```

---

## QR Decomposition
**Julia:**
```julia
Q, R = qr(A)
```

**Python:**
```python
Q, R = np.linalg.qr(A)
```

---

## Cholesky Decomposition (For Positive Definite Matrices)
**Julia:**
```julia
C = cholesky(A)
L = C.L  # Lower triangular matrix
```

**Python:**
```python
L = np.linalg.cholesky(A)  # Lower triangular matrix
```

---

## Norms
**Julia:**
```julia
norm(A, 2)  # 2-norm (Spectral norm)
norm(A, Inf)  # Infinity norm
```

**Python:**
```python
np.linalg.norm(A, 2)  # 2-norm (Spectral norm)
np.linalg.norm(A, np.inf)  # Infinity norm
```

---

## Trace of a Matrix
**Julia:**
```julia
tr(A)  # Trace of A
```

**Python:**
```python
np.trace(A)  # Trace of A
```

---

## Rank of a Matrix
**Julia:**
```julia
rank(A)  # Rank of A
```

**Python:**
```python
np.linalg.matrix_rank(A)  # Rank of A
```

---

This cheatsheet provides a quick reference for performing fundamental linear algebra operations in both Julia and Python.
