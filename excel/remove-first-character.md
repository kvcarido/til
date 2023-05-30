# Removing the First Character in a Column

I've needed to use this formula at work, where the census data I receive has a pesky space at the beginning of a text column. To ensure consistent formatting, I leveraged Excel functions to clean up the data.

Assuming your data is in column `A`, starting from cell `A1`, you'll want to use this formula in another column (let's say `B`) to display the formatted results.

```
=RIGHT(A1, LEN(A1)-1)
```

This formula uses the `RIGHT` function to extract the rightmost characters from a cell, and the `LEN` function to calculate the length of the cell contents. By subtracting 1 from the length, we remove the first character.

After entering the formula in cell B1, you can drag it down to apply the formula to the rest of the cells in column B, corresponding to the data in column A. The new values will be displayed in column B, without the first character.