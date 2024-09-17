java c
HUDM 5026 - Introduction to Data Analysis and 
Graphics in R 
HW 00 – Getting Started 
1 Data and File Paths To analyze data in R, you need to be able to import. The method you use for importing data will depend on what format the data are in. Data may be found in many formats and ﬁle extensions including those based on speciﬁc software packages such as Microsoft Excel (.xlsx), SPSS (.sav), Stata (.dta), SAS (.sas7bdat), MATLAB (.mat), or those based on more universal data extensions such as text ﬁles (.txt) or comma-separated values ﬁles (.csv). We will focus ﬁrst on the more universal extensions because they are more broadly applicable. Most data analysis packages allow you to save data as a comma-separated values ﬁle, so we will begin with that.There is a ﬁle called “acupuncture.csv” in the “Data Sets” folder on the course Can-vas page. Save the data set to your computer. Be sure to note where you save it be-cause we will need to ﬁnd it again. On my machine, a Mac, the ﬁle path is located at /Users/bryankeller/Documents/Data/acupuncture. csv. How do you ﬁnd the ﬁle path on your machine? On a Mac, you can right-click on the ﬁle and then press the alt/option key on your keyboard and select “Copy ‘acupuncture.csv’ as Pathname”. Then paste the ﬁle path to a text ﬁle. Alternatively, you could select "Get Info." Then, highlight the ﬁle path next to the "Where" information and copy and paste it into a text ﬁle.
This will produce the ﬁle path up to and including the folder that contains the ﬁle, but it will not include the ﬁle itself, so you will need to add that.  That is, copy/paste will produce the following:
/Users/bryankeller/Documents/Data
Since we know the name of the ﬁle is acupuncture. csv, we simply add that onto the end of the ﬁle path as follows:
/Users/bryankeller/Documents/Data/acupuncture. csvOn a machine running Windows OS, the process is similar.  Hold shift and right-click on the ﬁle and select “Copy as path” .   Alternatively,  you could select “Properties”,  go to the "General" tab, and select "Location". Typically on machines running Windows OS the ﬁle path will start with a capital letter that indicates the drive, followed by a colon and a backslash. On your machine, it might be something like the following:
C:\Users\YourName\Documents\acupuncture . csv
Note, however, that R requires that you use forward slashes or double backslashes, but not single backslashes, so you must convert this ﬁle path:
C:/Users/YourName/Documents/acupuncture . csv
Once you know the ﬁle path, you will be able to use functions in R to import the ﬁle.
2    Functions for Importing A useful function for importing .csv ﬁles is read. csv(). The ﬁrst argument to the function is file where you will give the ﬁle path in quotes. The function also has other important arguments including header  =  TRUE: whether the ﬁrstrow of data should be included as the column names, na. strings  =  "NA":  where you list character strings that indicate missing data, and others. To import the acupuncture data ﬁle to my R workspace I have to assign it a name and then use read. csv() to import the data.  There is a header here and I have no missing data so Ido not need to change the default values for either of those arguments, so I can leave them out of my call to read. csv().
dat  <- read. csv(file = "/Users/bryankeller/Documents/Data/acupuncture. csv")Now that the data have been imported to my 代 写HUDM 5026 - Introduction to Data Analysis and Graphics in RMatlab
代做程序编程语言working environment, I can act on them (e.g.,  display,  manipulate,  summarize,  analyze, etc.).   Several functions that I ﬁnd useful for understanding imported data are dim(), head(), and str(). dim() gives the number of rows and columns for a matrix-like object.  head() shows the ﬁrst 6 rows of a data set. str() gives a summary of each column in a data frame.  Here is the output for each of these functions for the acupuncture data set called dat:
>  dim(dat)
[1]  301     9> head(dat) id age sex migraine chronicity acupuncturist group pk1 pk5 1 104 32 1 1 14 12 0 16.00 15.33333 2 108 56 1 1 40 9 0 16.50 23.25000 3 112 45 1 1 27 9 1 9.25 6.25000 4 113 45 1 1 30 9 1 42.50 51.25000 5 114 49 1 1 49 9 1 24.25 25.25000 6 126 47 1 1 42 5 0 21.00 15.25000 
>  str(dat)
’data . frame’:  301  obs .  of    9  variables:
$  id                        :   int     104  108  112  113  114  126  130  131  135  137   . . .
$  age                   :   int    32  56  45  45  49  47  46  64  59  53   . . .
$  sex                   :  int     1  1  1  1  1  1  1  1  1  1   .  . .
$  migraine           :  int     1  1  1  1  1  1  1  1  1  1   . . .
$  chronicity      :   int    14  40  27  30  49  42  3  23  40  32   . . .
$  acupuncturist:   int    12  9  9  9  9  5  7  7  7  7   . . .
$  group                  :   int     0  0  1  1  1  0  1  1  0  1   .  . .
$  pk1                   :  num     16   16 . 5  9 . 25  42 . 5  24 . 25   .  .  .
$  pk5                   :   num     15 .33  23 . 25  6 . 25  51 . 25  25 . 25   .  .  .
There are other functions for importing in base R and in other packages. We will explore more of these in the future.
3    Homework 0.0 
1.  Use dim() to examine the dimensions of the acupuncture data in dat. How many rows and columns are there?
2.  Use str() to examine dat. What are the variable names?  Verify with the names() function. What are the variable classes (e.g., numeric,integer, character, logical, etc.)?
3.  Use head() to examine dat. Do the values make sense for each variable?  Why or why not?
4.  Use read. csv() to import the acupuncture data again, however this time make two changes. First, name the imported data dat2 instead of dat.  Second, use the header
=  FALSE argument within your call to the read. csv() function.
5.  Use dim() to examine dat2. Do the dimensions of dat1 and dat2 diﬀer? If so, why?
6.  Use str() to examine dat2. What are the variable names? Verify with the names() function. What are the variable classes (e.g., numeric,integer, character, logical, etc.)? Explain why they changed as compared with dat.
7.  Use head() to examine dat2. Do the values make sense for each variable? Why or why not?
8.  There is package called readr that has a function in it called read_csv().  Note that the only diﬀerence in name is the use of an underscore instead of a dot. The read_csv() function will import the data as a tibble. A tibble is a form. of data frame. used in the tidyverse, a suite of packages for data science in R. Install the readr package and then load it as follows:
install. packages("readr")
library(readr)Then, use the function read_csv() to import the acupuncture data again, this time calling it dat3.  Use dim(), head(), and str() to examine the data.  We will discuss the properties of tibbles and data frames in more detail soon.





         
加QQ：99515681  WX：codinghelp
