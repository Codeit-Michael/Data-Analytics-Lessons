# Data Analytics with Excel

## Formulas
Basic formula structure:
`=OPT(pla:ce;condition;ra:nge)` 
example:
=SUMIF(B2:B7;G2;D2:D7)
- This formula means:
if G2 value in B2-B7, add corresponding values in D2-D7 

Locking Vertically:
=SUMIF($B$2:$B$7;G3;$D$2:$D$7)

Locking Horizontally:
=SUMIF($B2:$B7;$G2;$D2:$D7)

## Tables
- By selecting the related properties and clicking insert table, they will 
transform into one official table where you can access it better. For example, 
you can create our table's total amount by doing `=SUM(Expense[Amount])` 
instead of doing it by range like `=SUM(D2:27)`
- Naming table is at Table designs to do the formula above by accessing its 
name.
- Table slicers - 
