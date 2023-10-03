# Introduction to Pandas: Series and DataFrames

The Pandas Series and DataFrames are some of the core elements you need for Data Analysis with Python and the Pandas library. You can both use them for data reading, storing, modifying, and more. If you want to know more about Series and DataFrames, let's jump right into it.

## What are Series and What are DataFrames

Let's quickly identify first what is a `series` and what is a `data frame`. Both of them are datasets, they just have different shapes. They aren't the same, but they are very related.

The Series (`pandas.Series`) are datasets with 1-dimensional shapes. It is more likely an array or a list in Python. It can store any kind of object, and the cool thing is that you can customize its index with a different set of numbers (`int` or `float`) or you can also use strings (`str`). 

On the other hand, DataFrames (`pandas.DataFrames`) are 2-dimensional datasets. It has rows and columns which is very useful when creating a table. As I said, series and data frames are related to each other, it is because each column in a data frame is a Series. 

## Using the Series

Let's import the `pandas` module first, then use `pd.Series()` to create a series.

```python
import pandas as pd
```
```python
sr = pd.Series([1, 23, 34, 24, 51, 15])
```
![](sr1.jpg)

Calling our variable `sr` will return us a Series with a default numeric index. In able to change the index, we can use the `index` argument when creating the Series or after the Series was made.

```python
# customizing after a series was created
sr.index = ['q','w','e','r','t','y']
```
![](sr2.jpg)

```python
# customizing index while creating
sr = pd.Series(
    [1, 2, 3, 4, 5, 6],
    index=['Q', 'W', 'E', 'R', 'T', 'Y'],
    name="Number List"
)
```
![](sr3.jpg)


You can also name your Series. A Series name acts as a column name since DataFrame columns are actually Series.

By simply calling the variable `sr`, we can read the whole Series. In terms of reading a specific cell of an object, we can call it using an index like how we do in ordinary Python.

```python
>>> sr["Q"]
    1
```
You can also read objects using a range of indexes.

```python

sr["Q":"T"]

```
![](sr4.jpg)

```python

# other way of calling with index is using the .loc method
sr.loc["Q":"R"]

```
![](sr5.jpg)

We can still access object cells using a numeric index with the `.iloc` method.

```python

sr.iloc[2:-1]

```
![](sr6.jpg)

Using conditions with our Series, we can get a boolean series as an output. We can use this to read objects conditionally.

```python
sr >= 4

```
![](sr7.jpg)

```python

sr[sr >= 4]

```
![](sr8.jpg)

To add another object in your series, you can add an object like how we do it in Python dictionaries.

```python

sr["U"] = 78

```
![](sr9.jpg)

You can also add/merge a Series with another Series using `.append()`.

```python

sr.append(pd.Series([33,44,55]))

```
![](sr10.jpg)

As you notice, the index of the older objects remains the same (strings form) and the newly merged objects have a default numeric index value. The new objects got their indices from the old Series they're in, so if we modify their index and append it to other Series, the objects will retain their old index.

```python

sr.append(pd.Series([66,77,88], index=["I","O","P"]))

```
![](sr11.jpg)

However, we can reset the index of both Series by using the `ignore_index` argument.

```python

sr.append(pd.Series([55,56,67], index=["a","s","d"]), ignore_index=True)

```
![](sr12.jpg)

> Note: The modifications like `append` won't be saved automatically. If we call our Series, we will see there's nothing changed. 

```python
>>> sr
    Q     1
    W     2
    E     3
    R     4
    T     5
    Y     6
    U    78
    Name: Number List, dtype: int64
```

```python

# saving the operations we did
sr = sr.append(pd.Series([55,56,67], index=["a","s","d"]), ignore_index=True)
sr

```
![](sr13.jpg)

## Using DataFrames

For dealing with a bigger set of data/objects with multiple columns, we can use DataFrames.

![Create a DataFrame](df1.jpg)

Calling our DataFrame or Series with `.head()` will return the first rows of our dataset. Passing an `int` to this function will return the first `nth` rows, but will return the first 5 rows as default (if you don't pass a number). However, if you want to access the last rows, you can use the `.tail()` function.
![head function](df2.jpg)
![tail function](df3.jpg)

Like the Series, in order to access objects using a string index, we can use the `.loc` function, and for the numeric index, you can use `.iloc`.
![loc and iloc accessing](df4.jpg)

You can also specify what columns you only want to pick from them.
![return specified columns only](df5.jpg)

And if we can pick a row, we can also drop a row.
![drop function](df6.jpg)

Another thing you can use to access rows/objects is by passing a condition to the DataFrame.
![conditional accessing](df7.jpg)

To add another column in our DataFrame, we're going to use Series. Let's create another row for our DataFrame using the condition we used earlier.
![creating a column out of existing column](df8.jpg)
![adding the column to dattaframe](df9.jpg)

And if you ever want to rename a column or an index, let's say you put a wrong index or want to change the name of a column, you can use the `.rename()` function.
![rename function](df10.jpg)

Remember, all the changes won't be saved automatically unless you save it into a variable (or update its old variable).

![dataframe](df11.jpg)

One last thing, Pandas Series and DataFrames have more cool features. You can run `pandas.Series?` or `pandas.DataFrame?` to quickly view the documentation.

So there you have it! With Series and DataFrames in your toolkit, you've got the muscle to handle data like a pro. Whether you're diving into data for work, play, or sheer curiosity, Pandas has your back. I hope you find this blog helpful, thanks and have a good day.