# Method Details

## A. Converting “% Change” into a Decimal
- Excel:
  ```excel
  =VALUE(SUBSTITUTE(<cell>, "%", "")) 

E.g. “900%” → 9.0, “–90%” → –0.9

## B. Forecasting 12-Month Volume

Given Google’s 12-mo average G and 3-mo change C:

B (first 9-mo avg) = G / ((12 + 3*C) / 12)

A (last 3-mo avg) = B * (1 + C)

Spread into months May–Jan (use B) and Feb–Apr (use A):
= IF(COLUMN()-COLUMN($firstMonthCell)+1 <= 9, $B, $A)

## C. Forecasting 12-Month CPC (Low & High)

Follow the exact same steps—just replace “G” with your Low-Bid or High-Bid column.
Then, to get average CPC:

9-mo midpoint = (B_low + B_high)/2
3-mo midpoint = (A_low + A_high)/2
Spread those two midpoints into 12 months (same IF formula).
Overall avg CPC = =AVERAGE(<12 monthly midpoint cells>)

## D. Charting

Both line charts live on the Charts sheet. They use the 12-month rows for each keyword.
No special steps—you just select the table and Insert → Line Chart.
