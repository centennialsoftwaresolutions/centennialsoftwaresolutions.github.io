# "Finding the First and Last Fridays of Any Month Made Easy"

![excel_logo](excel_logo.png)

Ever needed to find the first or last Friday of a month in Excel? Look no further! In this post, we'll share two versatile formulas that do just that, and more. Whether you need the date of the first or last instance of any day in a given month, these functions have you covered. Let's get started!

###### First Instance

Given a Date in **A1** and a String in **A2**: First Sun, First Mon, etc. Return the Date of the **First Instance** of That Day

```
=(EOMONTH(A1,-1) + 1) + SWITCH(

WEEKDAY(EOMONTH(A1,-1)+1),

1, SWITCH(A2, "First Sun",0,   "First Mon",1,   "First Tue",2,   "First Wed",3,   "First Thu",4,   "First Fri",5,   "First Sat",6),

2, SWITCH(A2, "First Sun",6,"First Mon",0,"First Tue",1,"First Wed",2,"First Thu",3,"First Fri",4,"First Sat",5),

3, SWITCH(A2, "First Sun",5,"First Mon",6,"First Tue",0,"First Wed",1,"First Thu",2,   "First Fri",3,   "First Sat",4),

4, SWITCH(A2, "First Sun",4,   "First Mon",5,   "First Tue",6,   "First Wed",0,   "First Thu",1,   "First Fri",2,   "First Sat",3),

5, SWITCH(A2, "First Sun",3,   "First Mon",4,   "First Tue",5,   "First Wed",6,   "First Thu",0,   "First Fri",1,   "First Sat",2),

6, SWITCH(A2, "First Sun",2,   "First Mon",3,   "First Tue",4,   "First Wed",5,   "First Thu",6,   "First Fri",0,   "First Sat",1),

7, SWITCH(A2, "First Sun",1,   "First Mon",2,   "First Tue",3,   "First Wed",4,   "First Thu",5,   "First Fri",6,   "First Sat",0)

)
```

###### Last Instance

Given a Date in **A1** and a String in **A2**: First Sun, First Mon, etc. Return the Date of the **Last Instance** of That Day

```
 =(EOMONTH(A1,0)) + SWITCH(

WEEKDAY(EOMONTH(A1,0)),

1, SWITCH(A2, "Last Sun", 0,   "Last Mon",-6,   "Last Tue",-5,   "Last Wed",-4,   "Last Thu",-3,   "Last Fri",-2,   "Last Sat",-1),

2, SWITCH(A2, "Last Sun", -1,   "Last Mon", 0,   "Last Tue",-6,   "Last Wed",-5,   "Last Thu",-4,   "Last Fri",-3,   "Last Sat",-2),

3, SWITCH(A2, "Last Sun", -2,   "Last Mon",-1,   "Last Tue", 0,   "Last Wed",-6,   "Last Thu",-5,   "Last Fri",-4,   "Last Sat",-3),

4, SWITCH(A2, "Last Sun", -3,   "Last Mon",-2,   "Last Tue", -1,   "Last Wed", 0,   "Last Thu",-6,   "Last Fri",-5,   "Last Sat",-4),

5, SWITCH(A2, "Last Sun", -4,   "Last Mon",-3,   "Last Tue", -2,   "Last Wed", -1,   "Last Thu", 0,   "Last Fri",-6,   "Last Sat",-5),

6, SWITCH(A2, "Last Sun", -5,   "Last Mon",-4,   "Last Tue", -3,   "Last Wed", -2,   "Last Thu", -1,   "Last Fri", 0,   "Last Sat",-6),

7, SWITCH(A2, "Last Sun", -6,   "Last Mon",-5,   "Last Tue", -4,   "Last Wed", -3,   "Last Thu", -2,   "Last Fri", -1,   "Last Sat", 0)
)
```

###### The Excel Workbook I Used to Develop and Test This

https://docs.google.com/spreadsheets/d/1KLKINnWS_O47Rk7SA5hBstdEblnPbmu7/edit?usp=sharing&ouid=104422661029399872488&rtpof=true&sd=true 

###### References

Excel icon downloaded from \[[<u><span>link</span></u>](http://upload.wikimedia.org/wikipedia/commons/7/7f/Microsoft_Office_Excel_%282018%E2%80%93present%29.svg)\] as SVG and saved as a PNG using Microsoft Explorer.