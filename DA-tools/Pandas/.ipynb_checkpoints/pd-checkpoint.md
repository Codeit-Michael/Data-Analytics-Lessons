## Basic Essentials

- `pd.date_range("YrMtDt", periods=int(ranre))` = creates DateTimeIndex
- `df.index` and `df.columns` = returns columns and indices
- `df.to_numpy` = basically converts dataframes to a numpy array
- `df.describe` = returns basic data info such as `mean`, `std`, etc.
- `df.T` = will transpose (flip, row>>col col>>row) your dataframe
- `df.sort_index(axis="rows|cols"/1|2)` = sorts depending on axis (for all rows/columns)
- `df.sort_values(by="colName")` = sorts value of a column and moving them with the same set of data row they have
- `df.loc` (by label) and `df.iloc` (by int) = for accessing rows
- `df.at` (by label) and `df.iat` (by int) = accessing a scalar
- `df.isin()` = check if the passed obcject/s is/are in a df/column
- `df.copy` = copies a df
- `df.reindex` =  you to change/add/delete the index on a specified axis. This returns a copy of the data.
- 



## Data Cleaning Process
1. First look at the Data (data read)
- Read the data from data file or api

2. Remove duplicates
- You can use `df.drop_duplicates()`

3. Dropping columns 
- `df.drop(columns="colName")`

4. Data Stripping (for objects with wrong characters)
- `df["colName"].str.strip("charVal")` - this will strip both sides
- `.lstrip()` for left only, `.rstrip()` right only
- it will automatically strip all the characters inside the "str" args of these functions

5. Data Cleaning messy columns (like phone no. column with different format )

**A. Removing unnecessary characters**
- We can use `.replace()` function and regex for cleaning a data field like phone number.
- `df["colName"].str.replace("[^a-zA-Z0-9]", "")` = this means all charcters which is not an A-Z (upper() and lower()) or a number 0-9 will be replaced by `""` or an empty string.

**B. Restructuring**
- You can use `functions` or `lambda` for it like formatting `123456789` to `123-456-789`.
- `df["colName"].apply(lambda x: x[0:3] + "-" x[3:6] + "-" x[6:10])` this works as long as the col data is converted to `str`

6. Splitting Columns
- `df[["Street Address", "Barangay", "City"]] = df["Address"].str.split(',', 2)`
- This wont replace the existing columns of `Address`, its's just gonna create 3 more columns 