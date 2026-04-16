# NumPy Cheat Sheet

## General Purpose

| Function / Method | Description | Example |
|---|---|---|
| `ndarray.dtype` | Return the data-type of the elements of the array. Arrays are homogeneous. | `np.array([1,2,3]).dtype` → `int64` |
| `ndarray.ndim` | Return the number of array dimensions (rank). e.g., returns `2` for a 4×3 array. | `np.array([[1,2],[3,4]]).ndim` → `2` |
| `ndarray.shape` | Return a tuple representing the array dimensions. | `np.array([[1,2],[3,4]]).shape` → `(2, 2)` |
| `ndarray.size` | Return the number of elements present in the array. | `np.array([[1,2],[3,4]]).size` → `4` |
| `numpy.save` | Save an array to `.npy` (NumPy) format. | `np.save('data.npy', arr)` |
| `numpy.load` | Load an array from `.npy` files. | `arr = np.load('data.npy')` |
| `numpy.random.random` | Return random floats from `[0.0, 1.0)`, in a specified shape. | `np.random.random((2,3))` → 2×3 array of floats |
| `numpy.random.randint` | Return random integers from `[a, b)`, in a specified shape. | `np.random.randint(1, 10, (2,3))` → 2×3 array of ints in [1,10) |
| `numpy.random.normal` | Return random samples from a Gaussian (normal) distribution. | `np.random.normal(0, 1, (3,))` → e.g. `[0.12, -1.03, 0.57]` |
| `numpy.random.permutation` | Return a randomly permuted sequence from the given list. | `np.random.permutation([1,2,3])` → e.g. `[3,1,2]` |
| `numpy.reshape` / `ndarray.reshape` | Return an array with a new shape, without affecting the original. | `np.arange(6).reshape(2,3)` → `[[0,1,2],[3,4,5]]` |

## Array Creation

| Function / Method | Description | Example |
|---|---|---|
| `numpy.ones` | Return a new array filled with `1`s. | `np.ones((2,3))` → `[[1,1,1],[1,1,1]]` |
| `numpy.zeros` | Return a new array filled with `0`s. | `np.zeros((2,2))` → `[[0,0],[0,0]]` |
| `numpy.full` | Return a new array filled with a specific value. | `np.full((2,2), 7)` → `[[7,7],[7,7]]` |
| `numpy.eye` | Return a 2-D identity array (`1`s on diagonal, `0`s elsewhere). | `np.eye(3)` → `[[1,0,0],[0,1,0],[0,0,1]]` |
| `numpy.diag` | Extract the diagonal elements. | `np.diag([[1,2],[3,4]])` → `[1, 4]` |
| `numpy.unique` | Return the sorted unique elements of an array. | `np.unique([3,1,2,1,3])` → `[1, 2, 3]` |
| `numpy.array` | Create an n-dimensional array. | `np.array([1,2,3])` → `[1, 2, 3]` |
| `numpy.arange` | Return evenly spaced values within `[a, b)`. | `np.arange(0, 10, 2)` → `[0, 2, 4, 6, 8]` |
| `numpy.linspace` | Return evenly spaced numbers over `[a, b]`. | `np.linspace(0, 1, 5)` → `[0, 0.25, 0.5, 0.75, 1.0]` |
| `ndarray.copy` | Return a copy of the array. | `b = a.copy()` — changes to `b` won't affect `a` |

## Operating with Elements and Indices

| Function / Method | Description | Example |
|---|---|---|
| `numpy.insert` | Insert values before the specified indices. | `np.insert([1,2,3], 1, 99)` → `[1, 99, 2, 3]` |
| `numpy.delete` | Return a new array after deleting sub-arrays along an axis. | `np.delete([1,2,3], 1)` → `[1, 3]` |
| `numpy.append` | Append values at the end of the array. | `np.append([1,2], [3,4])` → `[1, 2, 3, 4]` |
| `numpy.hstack` | Stack arrays horizontally (column-wise). | `np.hstack(([1,2],[3,4]))` → `[1, 2, 3, 4]` |
| `numpy.vstack` | Stack arrays vertically (row-wise). Result is at least 2-D. | `np.vstack(([1,2],[3,4]))` → `[[1,2],[3,4]]` |
| `numpy.sort` | Return a sorted copy of an array. | `np.sort([3,1,2])` → `[1, 2, 3]` |
| `ndarray.sort` | Sort an array **in-place**. | `a = np.array([3,1,2]); a.sort()` → `a` is now `[1, 2, 3]` |

## Set Operations

| Function / Method | Description | Example |
|---|---|---|
| `numpy.intersect1d` | Find the intersection of two arrays. | `np.intersect1d([1,2,3],[2,3,4])` → `[2, 3]` |
| `numpy.setdiff1d` | Find the set difference of two arrays. | `np.setdiff1d([1,2,3],[2,3,4])` → `[1]` |
| `numpy.union1d` | Return the unique, sorted union of two arrays. | `np.union1d([1,2],[2,3])` → `[1, 2, 3]` |

## Arithmetic and Statistical Operations

| Function / Method | Description | Example |
|---|---|---|
| `numpy.add` | Element-wise addition. | `np.add([1,2],[3,4])` → `[4, 6]` |
| `numpy.subtract` | Element-wise subtraction. | `np.subtract([5,6],[1,2])` → `[4, 4]` |
| `numpy.multiply` | Element-wise multiplication. | `np.multiply([2,3],[4,5])` → `[8, 15]` |
| `numpy.divide` | Element-wise true division. | `np.divide([10,9],[2,3])` → `[5.0, 3.0]` |
| `numpy.exp` | Calculate the exponential of all elements. | `np.exp([0, 1])` → `[1.0, 2.718]` |
| `numpy.power` | First array elements raised to powers from second array. | `np.power([2,3],[3,2])` → `[8, 9]` |
| `numpy.sqrt` | Return the non-negative square root, element-wise. | `np.sqrt([4, 9, 16])` → `[2.0, 3.0, 4.0]` |
| `ndarray.min` | Return the minimum along the specified axis. | `np.array([3,1,2]).min()` → `1` |
| `ndarray.max` | Return the maximum along a given axis. | `np.array([3,1,2]).max()` → `3` |
| `numpy.mean` / `ndarray.mean` | Compute the arithmetic mean along the specified axis. | `np.mean([1,2,3,4])` → `2.5` |
| `numpy.median` | Compute the median along the specified axis. | `np.median([1,2,3,4])` → `2.5` |
