# Sparse Matrix Library in Modern C++

A lightweight C++ library implementing a **generic sparse matrix data structure** with multiple storage strategies, compressed representations, and efficient linear algebra operations.

This project was developed to explore the implementation of sparse linear algebra data structures from first principles, with a focus on **performance**, **memory efficiency**, and **modern C++ programming**.

---

## Key Features

* 🚀 Generic implementation using **C++ templates**
* 📦 Support for both **row-wise** and **column-wise** sparse storage
* 🔄 Dynamic conversion between **compressed** and **uncompressed** representations
* ⚡ Efficient sparse **matrix-vector multiplication**
* 📐 Computation of common matrix norms:

  * 1-norm
  * Infinity norm
  * Frobenius norm
* 📄 Matrix Market (`.mtx`) file reader
* 🔢 Support for both integral types and `std::complex`
* ⏱️ Performance benchmarking of different storage strategies

---

## Project Overview

The library revolves around a templated class:

```cpp
Matrix<T, StorageOrder>
```

where:

* `T` is the data type (integral or `std::complex`)
* `StorageOrder` specifies whether the matrix is stored **row-wise** or **column-wise**

The implementation allows users to efficiently manipulate sparse matrices while choosing the storage strategy that best suits their application.

---

## Storage Strategies

Two storage layouts are supported:

* **ROW_WISE**
* **COL_WISE**

Although both represent the same mathematical object, they differ in traversal order and can exhibit different performance characteristics depending on the operation being performed.

---

## Compression

Matrices can exist in two different states.

### Uncompressed

* Efficient insertion and modification of elements
* Suitable while building the matrix

### Compressed

* Optimized for arithmetic operations
* Faster matrix-vector multiplication
* Read-only structure (new elements cannot be inserted)

This design mirrors the workflow adopted by many scientific computing libraries, where matrices are first assembled and later compressed for efficient numerical computations.

---

## Supported Operations

The library currently implements:

* Sparse matrix construction
* Element insertion and access
* Matrix resizing
* Compression / decompression
* Matrix-vector multiplication
* Matrix multiplication with single-column matrices
* Matrix norm computation
* Matrix Market import (`.mtx`)
* Stream output (`<<`)

---

## Benchmark

The project includes a benchmarking example using the **lnsp_131** Matrix Market dataset.

The following configurations are compared:

* Row-wise vs Column-wise storage
* Compressed vs Uncompressed matrices

Execution times are measured for:

* Sparse matrix-vector multiplication
* Matrix norm computation

allowing direct comparison of the impact of storage layout and compression on performance.

---

## Example

```cpp
Matrix<double, ROW_WISE> A;

A.read_mtx("lnsp_131.mtx");

A.compress();

std::vector<double> x(...);

auto y = A * x;
```

---

## Building

Clone the repository and compile with:

```bash
make
```

This generates the executable:

```bash
./main
```

Before compiling:

* Update the `PACS_ROOT` variable in the `Makefile`
* Place the `lnsp_131.mtx` dataset in the project directory

---

## Possible Extensions

Future improvements include:

* CSR / CSC dedicated storage formats
* Sparse-sparse matrix multiplication
* Iterative solvers (Conjugate Gradient, GMRES)
* Parallelization with OpenMP
* Unit testing
* CMake build system
* Continuous Integration (GitHub Actions)

---

## Why Sparse Matrices?

Sparse matrices appear naturally in many computational fields, including:

* Machine Learning
* Graph Analytics
* Scientific Computing
* Optimization
* Computational Physics
* Finite Element Methods
* Numerical Linear Algebra

Efficient sparse data structures are essential for scaling algorithms to large real-world datasets while minimizing memory usage and computational cost.

---

## Repository Structure

```
.
├── include/
├── src/
├── main.cpp
├── Makefile
└── README.md
```

---

## Author

Statistics PhD student with interests in:

* Machine Learning
* Artificial Intelligence
* Scientific Computing
* Quantitative Research
* Numerical Optimization
* High-performance C++

This project was developed as an exercise in implementing efficient numerical data structures and understanding the design choices behind sparse linear algebra libraries.
