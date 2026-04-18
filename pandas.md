# Pandas Cheat Sheet

## Initialization and Utility

| Function / Method | Description | Example |
|---|---|---|
| `pd.read_csv(path)` | Read a CSV file and load it as a DataFrame. | `df = pd.read_csv('data.csv')` |
| `pd.DataFrame(data)` | Create a 2-D heterogeneous tabular data structure. | `pd.DataFrame({'A': [1,2], 'B': [3,4]})` |
| `pd.Series(data, index)` | Create a 1-D labeled array. | `pd.Series([10, 20], index=['a', 'b'])` |
| `Series.shape` / `DataFrame.shape` | Return a tuple representing the dimensions. | `df.shape` → `(1000, 5)` |
| `Series.ndim` / `DataFrame.ndim` | Return the number of dimensions (rank). | `pd.Series([1,2]).ndim` → `1`, `df.ndim` → `2` |
| `Series.size` / `DataFrame.size` | Return the total number of elements. | `df.size` → `5000` (1000 rows × 5 cols) |
| `Series.values` | Return the data as a NumPy array. | `pd.Series([10, 20]).values` → `array([10, 20])` |
| `Series.index` | Return the index (labels) of the Series. | `pd.Series([10, 20], index=['a','b']).index` → `Index(['a', 'b'])` |
| `DataFrame.isnull()` | Return a same-sized bool object: `True` where NaN, `False` otherwise. | `df.isnull()` → DataFrame of `True`/`False` |
| `DataFrame.count(axis)` | Count non-NaN values along an axis. `axis=0` → column-wise. | `df.count()` → count per column |
| `DataFrame.head(n)` | Return the first `n` rows (default `n=5`). | `df.head(3)` → first 3 rows |
| `DataFrame.tail(n)` | Return the last `n` rows (default `n=5`). Supports negative indexing. | `df.tail(3)` → last 3 rows |
| `DataFrame.describe()` | Generate descriptive stats (count, mean, std, min, max, etc.). | `df.describe()` → summary stats table |
| `DataFrame.min()` | Return the minimum value along the given axis. | `df['Age'].min()` → `18` |
| `DataFrame.max()` | Return the maximum value along the given axis. | `df['Age'].max()` → `65` |
| `DataFrame.mean()` | Return the mean of values along the given axis. | `df['Salary'].mean()` → `52000.0` |
| `DataFrame.corr()` | Compute pairwise correlation of columns (excluding NaN). | `df.corr()` → correlation matrix |
| `DataFrame.rolling(window)` | Provide rolling window calculations. | `df['Price'].rolling(15).mean()` → 15-day rolling average |
| `DataFrame.loc[label]` | Access rows and columns by label(s). | `df.loc[0:5, 'Name']` → first 6 rows of `Name` column |
| `DataFrame.groupby(by)` | Group the DataFrame by a column or mapping function. | `df.groupby('City').mean()` → mean per city |

## Manipulation

| Function / Method | Description | Example |
|---|---|---|
| `Series.drop(index)` | Drop element(s) at the given index(es). | `s.drop(['a', 'c'])` → Series without labels `a`, `c` |
| `DataFrame.drop(labels)` | Drop specified rows or columns. | `df.drop('Age', axis=1)` → DataFrame without `Age` column |
| `DataFrame.pop(item)` | Return a column and remove it from the DataFrame. | `ages = df.pop('Age')` → `ages` is a Series, `df` no longer has `Age` |
| `DataFrame.insert(loc, col, values)` | Insert a column at a specified location. | `df.insert(2, 'Country', ['US', 'UK'])` |
| `DataFrame.rename(mapper)` | Rename columns or row indexes using a dict-like mapping. | `df.rename(columns={'old': 'new'})` |
| `DataFrame.set_index(keys)` | Set the DataFrame's row index using an existing column. | `df.set_index('ID')` → `ID` column becomes the index |
| `DataFrame.dropna(axis)` | Remove rows (`axis=0`) or columns (`axis=1`) containing NaN. | `df.dropna()` → rows with any NaN removed |
| `DataFrame.fillna(value)` | Replace NaN values with a specified value or method. | `df.fillna(0)` → all NaN replaced with `0` |
| `DataFrame.interpolate(method)` | Fill NaN with interpolated values using the given method. | `df.interpolate(method='linear')` → linear interpolation |