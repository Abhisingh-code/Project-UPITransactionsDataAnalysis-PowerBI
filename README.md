## UPI-Transactions-Data-Analysis Dashboard

Dashboard Link : https://app.powerbi.com/groups/me/reports/4e3f4b73-f255-4180-9e50-7c6df1a04bec/385f7b1116ec9efa067c?redirectedFromSignup=1&experience=power-bi


### Problem Statement

This dashboard helps to understand UPI transaction patterns and financial behavior better. It helps to analyze transaction amounts, remaining balances, and trends across different months. Through different visuals, it provides insights into how users transact based on banks, cities, payment methods, and transaction types, & thus helps in identifying patterns and improving financial decision-making.

Since, transaction amounts fluctuate across different months, thus analysis is required to understand spending trends.

Also since balance varies over time, thus it is important to track financial stability and transaction behavior.


### Steps followed

Step 1 : Load data into Power BI Desktop, dataset contains UPI transaction details(Excel File).

Step 2 : Open power query editor & in view tab under Data preview section, check "column distribution", "column quality" & "column profile" options.

Step 3 : Also since by default, profile will be opened only for 1000 rows so you need to select "column profiling based on entire dataset".

Step 4 : Data cleaning in Power Query Editor
  
      (1) In column 'TranscationTime' random dates was given with time and this column represent only time in order to remove the dates from this column      
         (i) Select 'TranscationTime', under Transform tab, under Split column(By Delimiter), Select Space, check box Right-most delimiter , click ok.
      
      (2) columns 'CustomerAccountNumber' and 'MerchantAccountNumber' was in exponential form, click on data type for both column and change them to text and make sure '0' doesn't apper in the end.

Step 5 : Slicers Formatting:

       (1) Placed Five Slicers on the canvas and using the width(1280px) in 'canvas' settings' size of each slicer was decided.
           
         (i) Leave a space length of 20 from left-most and right-most side(1280 - 40 = 1240), five slicers are there so the space length between each slicer will be 20(20 * 4 = 80) and (1240 - 80 = 1160) now [1160/5 = 232(Length of each slicer)] and now remove four slicer and keep one for editing.
        
         (ii) Select the first slicer, under visualization pane, under general, properties, under size(Height = 80, width = 232), under position(Horizontal = 20, Vertical = 20) and these are properties for the remaining four slicers.   
  
         (iii) Place the second slicer in such a way that the space between the first & second should be the same that is 20(20+232+20 = 272(Horizontal position) and vertical remains the same.   

         (iv) Third slicer [232 * 2 = 464(length of first two slicers combined) and (20 + 20 + 20 = 60)is the space between the slicers and the Horizontal position should be(464 + 60 = 524)] and vertical remains the same.   
  

         (v) Fourth slicer [524 + 232 + 20(is the space between) third and fourth slicer and the total = 776 is the Horizontal position and vertical remains the same.   
 
         (vi) Fifth slicer [776 + 232 + 20(is the space between) fourth and fifth slicer and the total = 1028 is the Horizontal position and vertical remains the same.

         (vii) total 10 slicers are needed so, Now copy all the five slicers together, copy them and paste them exactly below the above slicer row.

Step 6 : Added a column 'Age Groups' using (DAX)

         Age Groups = if('UPI Transactions'[CustomerAge]<=25,"A1",
                      IF('UPI Transactions'[CustomerAge]<=35,"A2","A3"))  

![Age Groups](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-AGEGPS.jpg)                      


## Page 1 

Step 7 : Fields were added in the slicers for filtering data by:

(a) BankNameSent
(b) BankNameReceived
(c) City
(d) DeviceType
(e) Gender
(f) Age Groups
(g) MerchantName
(h) PaymentMethod
(i) Purpose
(j) TransactionType

![Slicers](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-SLICERSpg1.jpg)


Step 7 : Line chart was added to represent "Transaction by Month[Line] (Year 2024)" ('TransactionDate' keep the month and remove year, date, quarter(x-axis) and 'Amount'(Sum)(y-axis))

![Transaction by Month[Line] (Year 2024)](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-TSMLINE.jpg)

Step 8 : under Filters pane, under Filter on all pages, add curreny. 

![Filter](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-Filters.jpg)

## Page 2

Step 8 : Add the same 10 slicers as page 1

Step 9 : Matrix visual was added ('TransactionDate' keep the month and remove year, date, quarter under(Rows) and 'City', 'Currency' under (Columns) and 'Amount'(Sum), 'RemainingBalance'(Sum) under(Values)).

![Matrix Visual](https://github.com/Abhisingh-code/Uploadingimages/blob/3e9bf1f3f6d83dee5b584bc08cbee8e8507a547a/PJ-UPI-MTX.jpg)

Step 10 : under column tools change decimal places to '0' for 'Amount' and 'RemainingBalace' column.

Step 11 : Syncing the slicers on both the pages, select a slicer, under view tab, click SYNC Slicers and check boxes page 1 and page 2 and likewise for all the slicers. 

Step 12 : Conditional formatting was done in 'Matrix visual' for 'Amount' and 'RemainingBalace' column( High rate = dark colour and Lower Rate = light colour) 

Step 13 : Adding remaining charts on page 1: 

       (a) 'Stacked clustered column chart' to represent "Transaction by Month[Column] (Year 2024)" same fields as the Line chart "Transaction by Month[Line] (Year 2024)"

![Transaction by Month[Column] (Year 2024)](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-TSMCOLUMN.jpg)       
       
       (b) 'Stacked clustered column chart' to represent "Balance by Month[Column] (Year 2024)" ('TransactionDate' keep the month and remove year, date, quarter(x-axis) and 'RemainingBalance'(Sum)(y-axis))

![Balance by Month[Column] (Year 2024)](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-BMCOLUMN.jpg)       

       (c) 'Line Chart' to represent "Balance by Month[Line] (Year 2024)" ('TransactionDate' keep the month and remove year, date, quarter(x-axis) and 'RemainingBalance'(Sum)(y-axis))

![Balance by Month[Line] (Year 2024)](https://github.com/Abhisingh-code/Uploadingimages/blob/2fe18b3696319239d97f9b8154518d0b9b2a50b8/PJ-UPI-BMLINE.jpg)       

Now OVERLAP all these charts above the line chart in Step 7.

Step 14 : Adding Bookmarks On Page 1 to see all the charts by selection:

        * Under view tab, select selections
         
        * Under view tab, select bookmarks and add: 

  (a) Line chart Amounts, under selection hide all the other charts except "Transaction by Month[Line] (Year 2024)" now click on three ellipsis on "Line chart Amounts" and click update.

  (b) Column chart Amounts, under selection hide all the other charts except "Transaction by Month[Column] (Year 2024)" now click on three ellipsis on "Line chart Amounts" and click update.

  (c) Line chart Balance, under selection hide all the other charts except "Balance by Month[Line] (Year 2024)" now click on three ellipsis on "Line chart Amounts" and click update.

  (d) Column chart Balance, under selection hide all the other charts except "Balance by Month[Column] (Year 2024)" now click on three ellipsis on "Line chart Amounts" and click update. 

Under Insert tab, Under Buttons, click on navigator and click Bookmark Navigator (Bookmark Navigator should always be on top in selection pane).

Step 12 : The report was then published to Power BI Service.

Snapshot of Dashboard (Power BI Service)

![Page 1](https://github.com/Abhisingh-code/Uploadingimages/blob/3e9bf1f3f6d83dee5b584bc08cbee8e8507a547a/PJ-UPI-pg1.jpg)

![Page 2](https://github.com/Abhisingh-code/Uploadingimages/blob/3e9bf1f3f6d83dee5b584bc08cbee8e8507a547a/PJ-UPI-pg2.jpg)


## Insights

A multi-page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

[1] Monthly Balance Trend

Balance ranges between approximately 8.2M to 8.5M throughout the year.

Slight fluctuations are observed across months.

    thus, financial balance remains relatively stable with minor variations.  
[2] Transaction Amount Trend

Transaction amounts vary month by month.

Some months show higher spending compared to others.

    thus, user spending behavior changes over time.  
[3] City-wise Transactions

Transactions are recorded across cities like Bangalore, Delhi, Hyderabad and Mumbai.

    thus, UPI usage is widespread across major cities.  
[4] Currency-wise Analysis

Transactions are performed in multiple currencies such as EUR, USD, GBP and INR.

    thus, system supports multi-currency transactions.  
[5] User Segmentation

Data is segmented based on:

Bank, Device Type, Gender, Age Groups, Merchant, Payment Method, Purpose and Transaction Type.

    thus, detailed user behavior analysis can be performed.  
[6] Balance vs Transaction Insight

Despite fluctuations in transaction amounts, remaining balance stays relatively consistent.

    thus, users maintain stable financial balances.  
