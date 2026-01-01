# 🎉 Udemy - Complete A.I. & Machine Learning, Data Science Bootcamp

This repository contains my solutions to the assignments in the [Complete A.I. & Machine Learning, Data Science Bootcamp](https://www.udemy.com/share/102vAM3@KZ8PqghamqSnQXbmdDi9hdesg5DhYerlgHZ3CWmdWEp_7ewAETJsRRN-O9NMA_Rm/) on [Udemy](https://www.udemy.com/) by [Andrei Neagoie](https://www.udemy.com/user/andrei-neagoie/) and [Daniel Bourke](https://www.mrdbourke.com/).

## 🧭 Table of contents

- [🎓 Assignments](#🎓-assignments)
  - [Assignment 01 - Pandas Practice 🐼](#assignment-01---pandas-practice-🐼)
- [🛠️ My process](#🛠️my-process)
  - [What I learned 🧠](#what-i-learned-🧠)
- [👩🏽‍💻 Author](#👩🏽‍💻-author)

## 🎓 Assignments

### Assignment 01 - Pandas Practice 🐼

[View](./notebooks/assignments/pandas-exercises.ipynb) the jupyter notebook file.

## 🛠️ My process

### What I learned 🧠

**1. File Path Command**

In order to import the `car-sales.csv` file into a notebook, I had initially referenced the file as follows:

```python
# Import "../data/car-sales.csv" and turn it into a DataFrame
car_sales = pd.read_csv('.../data/assignments/car-sales.csv')
car_sales
```

This resulted in a `FileNotFoundError` when running the cell.

This was because I had used the `.../` prefix which is not a standard path command in programming.

A solution was to use the *"Two Dots"* rule which in file systems, navigates levels using two dots (..), not three.

| Prefix | Location |
| :--- | :--- |
| `./` | Current folder |
| `../` | Go up one level |
| `../../` | Go up two levels |

I successfully implemented this as follows:

```python
car_sales = pd.read_csv('../../data/assignments/car-sales.csv')
```

**2. Writing a `.csv` file to a new or nested folder**

This was done using [Pathlib](https://docs.python.org/3/library/pathlib.html).

```python
# Export the DataFrame you created to a .csv file
from pathlib import Path

filepath = Path('../../data/assignments/car-sales-export.csv')
filepath.parent.mkdir(parents=True, exist_ok=True)
df.to_csv(filepath)
```

**3. `.loc[]` vs. `.iloc[]`**

[`.loc[]`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.loc.html#pandas.DataFrame.loc) is primarily label based.

```python
df = pd.DataFrame(
  [[1, 2], [4, 5], [7, 8]],
  index=['cobra', 'viper', 'sidewinder'],
  columns=['max_speed', 'shield']
)
df
```

|   | max_speed | shield |
| :--- | ---: | ---: |
| cobra | 1 | 2 |
| viper | 4 | 5 |
| sidewinder | 7 | 8 |

<br>

A single label returns the row as a Series:

```python
df.loc['viper']
```
|   |   |
| :--- | ---: |
| max_speed | 4 |
| shield | 5 |

<br>

A list of labels where using `[[]]` returns a DataFrame:

```python
df.loc[['viper', 'sidewinder']]
```

|   | max_speed | shield |
| :--- | ---: | ---: |
| viper | 4 | 5 |
| sidewinder | 7 | 8 |

<br>

Single label for row and column:

```python
df.loc['cobra', 'shield']
```

```bash
2
```

<br><br>

[`.iloc[]`](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.iloc.html#pandas.DataFrame.iloc) is primarily integer position based indexing (from `0` to `length-1`) for selection by position.

```python
mydict = [
  {'a': 1, 'b': 2, 'c': 3, 'd': 4},
  {'a': 100, 'b': 200, 'c': 300, 'd': 400},
  {'a': 1000, 'b': 2000, 'c': 3000, 'd': 4000}
]
df = pd.DataFrame(mydict)
df
```

|   | a | b | c | d |
| --- | ---: | ---: | ---: | ---: |
| 0 | 1 | 2 | 3 | 4 |
| 1 | 100 | 200 | 300 | 400|
| 2 | 1000 | 2000 | 3000| 4000 |

<br>

Indexing just the rows:
  - With a scalar integer

  ```python
  df.iloc[0]
  ```

  |   |   |
  | :--- | ---: |
  | a | 1 |
  | b | 2 |
  | c | 3 |
  | d | 4 |

  <br>

  - With a list of integers

  ```python
  df.iloc[[0]]
  ```

  |   | a | b | c | d |
  | :--- | ---: | ---: | ---: | ---: |
  | 0 | 1 | 2 | 3 | 4 |

  <br>

  ```python
  df.iloc[[0, 1]]
  ```

  |   | a | b | c | d |
  | :--- | ---: | ---: | ---: | ---: |
  | 0 | 1 | 2 | 3 | 4 |
  | 1 | 100 | 200 | 300 | 400 |

  <br>

  - With a slice object

  ```python
  df.iloc[:3]
  ```

  |   | a | b | c | d |
  | :--- | ---: | ---: | ---: | ---: |
  | 0 | 1 | 2 | 3 | 4 |
  | 1 | 100 | 200 | 300 | 400 |
  | 2 | 1000 | 2000 | 3000 | 4000 |

## 👩🏽‍💻 Author

| Platform | Link |
| :--- | :--- |
| **Blog** | [https://grace-sampao.github.io](https://grace-sampao.github.io) |
| **LinkedIn** | [Grace Sampao](https://www.linkedin.com/grace-sampao) |
| **X** | [@grace_sampao](https://x.com/grace_sampao) |
| **Email** | sampaograce@gmail.com |