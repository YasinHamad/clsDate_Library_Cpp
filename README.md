# Brief Description  
This is a date library/class that contains 137 functions which perform 72 different functionalities to manipulate date in `Cpp`.  
  
# Purpose  
The purpose of this project is mainly to practice OOP.  
The project is related to [ProgrammingAdvices Roadmap](https://programmingadvices.com/p/roadmap) - Course 10 - Project Number 02.  
Feel free to check my notes/projects about this course [Course 10](https://github.com/YasinHamad/Programming_Basics/tree/main/course_10), and other courses [Programming Basics](https://github.com/YasinHamad/Programming_Basics).  
  
# Table of Content  
  
- [Brief Description](# Brief Description)  
- [Purpose](# Purpose)  
- [Constructors](# Constructors)  
- [Getters, Setters, and Properties](# Getters, Setters, and Properties)  
- [Enums](# Enums)  
- [Functionalities](# Functionalities)  
  
# Constructors  
How to create an object form this class?  
  
```cpp  
// this constructor builds an object that contains the current day, month, and year  
clsDate _test_date_1;  
cout << _test_date_1.ToString() << "\n";  
  
// this constructor builds the date object depending on a string value  
clsDate _test_date_2("11/12/2026");  
cout << _test_date_2.ToString() << "\n";  
  
// the first parameter is the day, the second is the month, and the third is the year  
clsDate _test_date_3(1, 3, 2026);  
cout << _test_date_3.ToString() << "\n";  
  
// the first parameter is the order/number of the day in its year, the second is the year  
clsDate _test_date_4(250, 2026);  
cout << _test_date_4.ToString() << "\n";  
```  
  
```output  
{Day:25, Month: 3, Year:2026}  
{Day:11, Month: 12, Year:2026}  
{Day:1, Month: 3, Year:2026}  
{Day:7, Month: 9, Year:2026}  
```  
  
# Getters, Setters, and Properties  
  
```cpp  
int getDay();  
void setDay(int day);  
__declspec(property(get = getDay, put = setDay)) int day;  
  
int getMonth();  
void setMonth(int month);  
__declspec(property(get = getMonth, put = setMonth)) int month;  
  
int getYear();  
void setYear(int year);  
__declspec(property(get = getYear, put = setYear)) int year;  
```  
  
# Enums  
  
```cpp  
enum enDateTime { enYear, enMonth, enDay, enHour, enMinute, enSeconds, enWeek_day, enYear_day, enDaylight_saving_time };  
enum enYearTime { enYearDays, enYearHours, enYearMinutes, enYearSeconds };;  
```  
  
# Functionalities  
## Functionality #1  
`string ToString();`  
  
<u>Inputs :</u>  
Nothing.  
  
<u>Outputs :</u>  
`string` : the date's data.  
  
<u>Explanation :</u>  
This function returns the date as string.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(10, 1, 2026);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:10, Month: 1, Year:2026}  
```  
  
## Functionality #2  
`static int GetDateTime(enDateTime _var);`  
  
<u>Inputs :</u>  
`enDateTime _var` : using this `enum` you can specify what you want to get, for example, current year, current day, current month, current minute, current second, etc.  
Check the [Enum Section](# Enum).  
  
<u>Outputs :</u>  
`int` : the current month/year/second as you choose.  
  
<u>Explanation :</u>  
This function returns the current time, you can choose to get the current year/month/day/minute/etc.  
Check the [Enum Section](# Enum).  
  
<u>Example of Usage :</u>  
```cpp  
cout << "Current year   : " << clsDate::GetDateTime(clsDate::enDateTime::enYear) << "\n";  
cout << "Current month  : " << clsDate::GetDateTime(clsDate::enDateTime::enMonth) << "\n";  
cout << "Current day    : " << clsDate::GetDateTime(clsDate::enDateTime::enDay) << "\n";  
cout << "Current hour   : " << clsDate::GetDateTime(clsDate::enDateTime::enHour) << "\n";  
cout << "Current minute : " << clsDate::GetDateTime(clsDate::enDateTime::enMinute) << "\n";  
cout << "Current second : " << clsDate::GetDateTime(clsDate::enDateTime::enSeconds) << "\n";  
// I actually don't know what is "daylight.." for, and I guess it's not important to know :-)  
// you can search if you want  
cout << "Daylight saving time : " << clsDate::GetDateTime(clsDate::enDateTime::enDaylight_saving_time) << "\n";  
cout << "Number of current day in current year : " << clsDate::GetDateTime(clsDate::enDateTime::enYear_day) << "\n";  
cout << "Number of curren day in current week  : " << clsDate::GetDateTime(clsDate::enDateTime::enWeek_day) << "\n";  
```  
  
```output  
Current year   : 2026  
Current month  : 3  
Current day    : 22  
Current hour   : 22  
Current minute : 57  
Current second : 58  
Daylight saving time : 0  
Number of current day in current year : 80  
Number of curren day in current week  : 0  
```  
  
## Functionality #3  
`static clsDate StringToDate(string str_date);`  
  
<u>Inputs :</u>  
`string str_date` : the string that containing the date.  
  
<u>Outputs :</u>  
`clsDate` : the date that is in the string.  
  
<u>Explanation :</u>  
This function takes a string as "1/1/2026" and converts it to `clsDate` object.  
  
<u>Example of Usage :</u>  
```cpp  
string test_string_1 = "11/4/2026";  
clsDate test_date_1 = clsDate::StringToDate(test_string_1);  
cout << test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:11, Month: 4, Year:2026}  
```  
  
## Functionality #4  
`static string DateToString(clsDate date);`  
`string DateToString();`  
  
<u>Inputs :</u>  
`clsDate date` : the date we want to convert.  
  
<u>Outputs :</u>  
`string` : the date as string separated by `/`.  
  
<u>Explanation :</u>  
These functions convert an object of type `clsDate` to string separated by `/`.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate test_date_1(11,4,2026);  
cout << test_date_1.DateToString() << "\n";  
cout << clsDate::DateToString(test_date_1) << "\n";  
```  
  
```output  
11/4/2026  
11/4/2026  
```  
  
## Functionality #5  
`static short GetDayOrderInWeek(clsDate date);`  
`short GetDayOrderInWeek();`  
  
<u>Inputs :</u>  
`clsDate date` : the date we want to word on.  
  
<u>Outputs :</u>  
`short` : the number of day in week.  
  
<u>Explanation :</u>  
These functions return the number of day in week.  
`0` means Sunday. `1` means Monday, and so on.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1, 1, 2026);  
  
cout << _test_date_1.GetDayOrderInWeek() << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(2, 1, 2026)) << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(3, 1, 2026)) << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(4, 1, 2026)) << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(5, 1, 2026)) << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(6, 1, 2026)) << "\n";  
cout << clsDate::GetDayOrderInWeek(clsDate(7, 1, 2026)) << "\n";  
```  
  
```output  
4  
5  
6  
0  
1  
2  
3  
```  
  
## Functionality #6  
`static string GetDayName(int number);`  
`string GetDayName();`  
  
<u>Inputs :</u>  
`int number` : is the number of day in week.  
It can be `[0-6]`, `0` is Sunday.  
  
<u>Outputs :</u>  
`string` : the day name, for example "Sunday", "Monday", etc.  
If the input is not between `[0-6]`, they return empty string.  
  
<u>Explanation :</u>  
These functions return the name of a day, for example "Sunday", "Monday", etc.  
  
<u>Example of Usage :</u>  
```cpp  
cout << clsDate::GetDayName(0) << "\n";  
cout << clsDate::GetDayName(1) << "\n";  
cout << clsDate::GetDayName(2) << "\n";  
cout << clsDate::GetDayName(3) << "\n";  
cout << clsDate::GetDayName(4) << "\n";  
cout << clsDate::GetDayName(5) << "\n";  
cout << clsDate::GetDayName(6) << "\n";  
cout << clsDate::GetDayName(7) << "\n";  
cout << "----------" << "\n";  
clsDate _test_date_1;  
// this will return your current day name :)  
cout << _test_date_1.GetDayName();  
```  
  
```output  
Sunday  
Monday  
Tuesday  
Wednesday  
Thursday  
Friday  
Saturday  
  
----------  
Monday  
```  
  
## Functionality #7  
`static string GetMonthName(int month);`  
`string GetMonthName();`  
  
<u>Inputs :</u>  
`int month` : is the number of month `[1-12]`;  
  
<u>Outputs :</u>  
`string` : the month name.  
If the input is not between `[1-12]`, they return empty string.  
  
<u>Explanation :</u>  
These functions return the month name depending on its number.  
  
<u>Example of Usage :</u>  
```cpp  
cout << clsDate::GetMonthName(1) << "\n";  
cout << clsDate::GetMonthName(2) << "\n";  
cout << clsDate::GetMonthName(3) << "\n";  
cout << clsDate::GetMonthName(4) << "\n";  
cout << clsDate::GetMonthName(5) << "\n";  
cout << clsDate::GetMonthName(6) << "\n";  
cout << clsDate::GetMonthName(7) << "\n";  
cout << clsDate::GetMonthName(8) << "\n";  
cout << clsDate::GetMonthName(9) << "\n";  
cout << clsDate::GetMonthName(10) << "\n";  
cout << clsDate::GetMonthName(11) << "\n";  
cout << clsDate::GetMonthName(12) << "\n";  
cout << "----------" << "\n";  
clsDate _test_date_1;  
// this will return your current month name :)  
cout << _test_date_1.GetMonthName();  
```  
  
```output  
January  
February  
March  
April  
May  
June  
July  
August  
September  
October  
November  
December  
----------  
March  
```  
  
## Functionality #8  
`static string PrintDateLong(clsDate date);`  
`string PrintDateLong();`  
  
<u>Inputs :</u>  
`clsDate date` : the date we want to work on.  
  
<u>Outputs :</u>  
`string` : the date as `month_name, dd/mm/yy`.  
  
<u>Explanation :</u>  
These functions return a date in the following format `month_name, dd/mm/yy`.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.PrintDateLong() << "\n";  
cout << clsDate::PrintDateLong(clsDate(11, 4, 2026));  
```  
  
```output  
Monday, 23/3/2026  
Saturday, 11/4/2026  
```  
  
## Functionality #9  
`static bool IsLeapYear(int year);`  
`bool IsLeapYear();`  
  
<u>Inputs :</u>  
`int year` : the year we want to test.  
  
<u>Outputs :</u>  
`bool` : leap, or not leap year.  
  
<u>Explanation :</u>  
These functions check whether a year is leap or not.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.IsLeapYear() << "\n";  
cout << clsDate::IsLeapYear(2000);  
```  
  
```output  
0  
1  
```  
  
## Functionality #10  
`static int NumberOfDaysInYear(int year);`  
`int NumberOfDaysInYear();`  
  
<u>Inputs :</u>  
`int year` : the year we want to work on.  
  
<u>Outputs :</u>  
`int` : number of days in the year.  
  
<u>Explanation :</u>  
These functions return the number of days in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.NumberOfDaysInYear() << "\n";  
cout << clsDate::NumberOfDaysInYear(2000);  
```  
  
```output  
365  
366  
```  
  
## Functionality #11  
`static int NumberOfHoursInYear(int year);`  
`int NumberOfHoursInYear();`  
  
<u>Inputs :</u>  
`int year` : the year we want to work on.  
  
<u>Outputs :</u>  
`int` : number of hours in the year.  
  
<u>Explanation :</u>  
These functions return the number of hours in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.NumberOfHoursInYear() << "\n";  
cout << clsDate::NumberOfHoursInYear(2000) << "\n";  
```  
  
```output  
8760  
8784  
```  
  
## Functionality #12  
`static int NumberOfMinutesInYear(int year);`  
`int NumberOfMinutesInYear();`  
  
<u>Inputs :</u>  
`int year` : is the year we want to work on.  
  
<u>Outputs :</u>  
`int` : number of minutes in the year.  
  
<u>Explanation :</u>  
These functions return the number of minutes in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.NumberOfMinutesInYear() << "\n";  
cout << clsDate::NumberOfMinutesInYear(2000) << "\n";  
```  
  
```output  
525600  
527040  
```  
  
<u>Functions used for the example :</u>  
```cpp  
  
```  
  
## Functionality #13  
`static int NumberOfSecondsInYear(int year);`  
`int NumberOfSecondsInYear();`  
  
<u>Inputs :</u>  
`int year` : is the year we want to work on.  
  
<u>Outputs :</u>  
`int` : is the number of seconds in the year.  
  
<u>Explanation :</u>  
These functions return the number of seconds in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.NumberOfSecondsInYear() << "\n";  
cout << clsDate::NumberOfSecondsInYear(2000) << "\n";  
```  
  
```output  
31536000  
31622400  
```  
  
## Functionality #14  
`static int GetDaysInMonth(int month, int year);`  
`int GetDaysInMonth();`  
  
<u>Inputs :</u>  
`int month` : is the month we want to work on.  
`int year` : is the year that the month in.  
  
<u>Outputs :</u>  
`int` : is the number of days in the month.  
  
<u>Explanation :</u>  
These functions return the number of days of a specific month in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.GetDaysInMonth() << "\n";  
cout << clsDate::GetDaysInMonth(2, 2000) << "\n";  
cout << clsDate::GetDaysInMonth(2, 2001) << "\n";  
```  
  
```output  
31  
29  
28  
```  
  
## Functionality #15  
`static int GetHoursInMonth(int month, int year);`  
`int GetHoursInMonth();`  
  
<u>Inputs :</u>  
`int month` : is the month we want to work on.  
`int year` : is the year that the month in.  
  
<u>Outputs :</u>  
`int` : is the number of hours in the month.  
  
<u>Explanation :</u>  
These functions return the number of hours of a specific month in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.GetHoursInMonth() << "\n";  
cout << clsDate::GetHoursInMonth(2, 2000) << "\n";  
cout << clsDate::GetHoursInMonth(2, 2001) << "\n";  
```  
  
```output  
744  
696  
672  
```  
  
## Functionality #16  
`static int GetMinutesInMonth(int month, int year);`  
`int GetMinutesInMonth();`  
  
<u>Inputs :</u>  
`int month` : is the month we want to work on.  
`int year` : is the year that the month in.  
  
<u>Outputs :</u>  
`int` : is the number of minutes in the month.  
  
<u>Explanation :</u>  
These functions return the number of minutes of a specific month in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.GetMinutesInMonth() << "\n";  
cout << clsDate::GetMinutesInMonth(2, 2000) << "\n";  
cout << clsDate::GetMinutesInMonth(2, 2001) << "\n";  
```  
  
```output  
44640  
41760  
40320  
```  
  
## Functionality #17  
`static int GetSecondsInMonth(int month, int year);`  
`int GetSecondsInMonth();`  
  
<u>Inputs :</u>  
`int month` : is the month we want to work on.  
`int year` : is the year that the month in.  
  
<u>Outputs :</u>  
`int` : is the number of seconds in the month.  
  
<u>Explanation :</u>  
These functions return the number of seconds of a specific month in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
cout << _test_date_1.GetSecondsInMonth() << "\n";  
cout << clsDate::GetSecondsInMonth(2, 2000) << "\n";  
cout << clsDate::GetSecondsInMonth(2, 2001) << "\n";  
```  
  
```output  
2678400  
2505600  
2419200  
```  
  
## Functionality #18  
`static void PrintMonthCalender(clsDate date);`  
`void PrintMonthCalender();`  
  
<u>Inputs :</u>  
`clsDate date` : the date we want to work on.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions print the calendar of a specific month in a specific year.   
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
_test_date_1.PrintMonthCalender();  
clsDate::PrintMonthCalender(clsDate(1, 2, 2000));  
```  
  
```output  
_________________March__________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
1    2    3    4    5    6    7  
8    9    10   11   12   13   14  
15   16   17   18   19   20   21  
22   23   24   25   26   27   28  
29   30   31  
________________________________________  
________________February________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
          1    2    3    4    5  
6    7    8    9    10   11   12  
13   14   15   16   17   18   19  
20   21   22   23   24   25   26  
27   28   29  
________________________________________  
```  
  
## Functionality #19  
`static void PrintYearCalender(short year);`  
`void PrintYearCalender();`  
  
<u>Inputs :</u>  
`short year` : the year we want to work on.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions print the calendar of all months in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1;  
_test_date_1.PrintYearCalender();  
// this line will do the same, you can test it  
//clsDate::PrintYearCalender(2000);  
```  
  
```output  
________________________________________  
  
            Calender - 2026  
________________________________________  
  
________________January_________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
                    1    2    3  
4    5    6    7    8    9    10  
11   12   13   14   15   16   17  
18   19   20   21   22   23   24  
25   26   27   28   29   30   31  
  
________________________________________  
  
________________February________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
1    2    3    4    5    6    7  
8    9    10   11   12   13   14  
15   16   17   18   19   20   21  
22   23   24   25   26   27   28  
  
________________________________________  
  
_________________March__________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
1    2    3    4    5    6    7  
8    9    10   11   12   13   14  
15   16   17   18   19   20   21  
22   23   24   25   26   27   28  
29   30   31  
________________________________________  
  
_________________April__________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
               1    2    3    4  
5    6    7    8    9    10   11  
12   13   14   15   16   17   18  
19   20   21   22   23   24   25  
26   27   28   29   30  
________________________________________  
  
__________________May___________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
                         1    2  
3    4    5    6    7    8    9  
10   11   12   13   14   15   16  
17   18   19   20   21   22   23  
24   25   26   27   28   29   30  
31  
________________________________________  
  
__________________June__________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
     1    2    3    4    5    6  
7    8    9    10   11   12   13  
14   15   16   17   18   19   20  
21   22   23   24   25   26   27  
28   29   30  
________________________________________  
  
__________________July__________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
               1    2    3    4  
5    6    7    8    9    10   11  
12   13   14   15   16   17   18  
19   20   21   22   23   24   25  
26   27   28   29   30   31  
________________________________________  
  
_________________August_________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
                              1  
2    3    4    5    6    7    8  
9    10   11   12   13   14   15  
16   17   18   19   20   21   22  
23   24   25   26   27   28   29  
30   31  
________________________________________  
  
_______________September________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
          1    2    3    4    5  
6    7    8    9    10   11   12  
13   14   15   16   17   18   19  
20   21   22   23   24   25   26  
27   28   29   30  
________________________________________  
  
________________October_________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
                    1    2    3  
4    5    6    7    8    9    10  
11   12   13   14   15   16   17  
18   19   20   21   22   23   24  
25   26   27   28   29   30   31  
  
________________________________________  
  
________________November________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
1    2    3    4    5    6    7  
8    9    10   11   12   13   14  
15   16   17   18   19   20   21  
22   23   24   25   26   27   28  
29   30  
________________________________________  
  
________________December________________  
  
Sun  Mon  Tue  Wed  Thu  Fir  Sat  
          1    2    3    4    5  
6    7    8    9    10   11   12  
13   14   15   16   17   18   19  
20   21   22   23   24   25   26  
27   28   29   30   31  
________________________________________  
```  
  
## Functionality #20  
`static clsDate GetDate(int number_of_day_from_beginning_of_year, int year);`  
  
<u>Inputs :</u>  
`int number_of_day_from_beginning_of_year` : is the number/order of day in its year.  
`int year` : is the year that the day in.  
  
<u>Outputs :</u>  
`clsDate` : the date object, that contains day/month/year.  
  
<u>Explanation :</u>  
This function returns a `clsDate` instance depending on the year, and the order/number of day in that year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1 = clsDate::GetDate(32, 2026);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 2, Year:2026}  
```  
  
## Functionality #21  
`static void AddDaysToDate(clsDate& date, int days_to_add);`  
`void AddDaysToDate(int days_to_add);`  
  
<u>Inputs :</u>  
`clsDate& date` : the date we want to work on, by reference.  
`int days_to_add` : number of days we want to add to the date.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions add a specific number of days to a `clsDate` object.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.AddDaysToDate(20);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::AddDaysToDate(_test_date_1, 20);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::AddDaysToDate(_test_date_1, 366);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:21, Month: 1, Year:2026}  
{Day:10, Month: 2, Year:2026}  
{Day:11, Month: 2, Year:2027}  
```  
  
## Functionality #22  
`static short NumberOfDayInYear(clsDate date);`  
`short NumberOfDayInYear();`  
  
<u>Inputs :</u>  
`clsDate date` : the date we want to work on.  
  
<u>Outputs :</u>  
`short` : day order in the year.  
  
<u>Explanation :</u>  
These functions return the day order/number in a specific year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.NumberOfDayInYear() << "\n";  
cout << clsDate::NumberOfDayInYear(clsDate(2, 2, 2026)) << "\n";  
cout << clsDate::NumberOfDayInYear(clsDate(10, 12, 2026)) << "\n";  
```  
  
```output  
1  
33  
344  
```  
  
## Functionality #23  
`static clsDate CompareDates(clsDate date1, clsDate date2);`  
`clsDate CompareWithDate(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the date we want to compare.  
`clsDate` : is the date we want to compare with.  
  
<u>Outputs :</u>  
`clsDate` : returns the bigger date.  
  
<u>Explanation :</u>  
These functions compare two dates and return the bigger one.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
clsDate _test_date_2 = _test_date_1.CompareWithDate(clsDate(2, 2, 2026));  
clsDate _test_date_3 = clsDate::CompareDates(clsDate(2, 2, 2026), clsDate(4, 1, 2026));  
  
cout << _test_date_2.ToString() << "\n";  
cout << _test_date_3.ToString() << "\n";  
```  
  
```output  
{Day:2, Month: 2, Year:2026}  
{Day:2, Month: 2, Year:2026}  
```  
  
## Functionality #24  
`static bool IsEqualDates(clsDate date1, clsDate date2);`  
`bool IsEqualToDate(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to check their equality.  
`clsDate date` : is the date we want to check the equality with.  
  
<u>Outputs :</u>  
`bool` : equal, or not equal.  
  
<u>Explanation :</u>  
These functions check the equality of two dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(2, 3, 2026);  
cout << _test_date_1.IsEqualToDate(clsDate(2, 3, 2026)) << "\n";  
cout << clsDate::IsEqualDates(clsDate(2, 2, 2026), clsDate(3, 3, 2026)) << "\n";  
```  
  
```output  
1  
0  
```  
  
## Functionality #25  
`static bool IsLastDayInMonth(clsDate date);`  
`bool IsLastDayInMonth();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the day the last in the month, or not.  
  
<u>Explanation :</u>  
These functions return whether a day is the last day in the month or not.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(30, 1, 2026);  
cout << _test_date_1.IsLastDayInMonth() << "\n";  
cout << clsDate::IsLastDayInMonth(clsDate(31, 1, 2026)) << "\n";  
```  
  
```output  
0  
1  
```  
  
## Functionality #26  
`static bool IsLastMonthInYear(clsDate date);`  
`bool IsLastMonthInYear();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the month the last in the year, or not.  
  
<u>Explanation :</u>  
These functions return whether a month is the last month in the year or not.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(30, 1, 2026);  
cout << _test_date_1.IsLastMonthInYear() << "\n";  
cout << clsDate::IsLastMonthInYear(clsDate(1, 12, 2026)) << "\n";  
```  
  
```output  
0  
1  
```  
  
## Functionality #27  
`static void IncreaseDateByOne(clsDate& date);`  
`void IncreaseDateByOne();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to work on. By reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a date by one day.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(30, 1, 2026);  
_test_date_1.IncreaseDateByOne();  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOne();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate _test_date_2(31, 12, 2026);  
clsDate::IncreaseDateByOne(_test_date_2);  
cout << _test_date_2.ToString() << "\n";  
```  
  
```output  
{Day:31, Month: 1, Year:2026}  
{Day:1, Month: 2, Year:2026}  
{Day:1, Month: 1, Year:2027}  
```  
  
## Functionality #28  
`static int DifferentBtwDatesInDays(clsDate date1, clsDate date2, bool include_last_day = false);`  
`int DifferentInDaysWithDate(clsDate date, bool include_last_day = false);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to count the days between them.  
`clsDate date` : is the date we want to count the difference in days with it.  
`bool include_last_day` : is the last day, it is false by default.  
  
<u>Outputs :</u>  
`int` : is number of days between the dates.  
  
<u>Explanation :</u>  
These functions return the difference in days between two dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(30, 1, 2026);  
cout << _test_date_1.DifferentInDaysWithDate(clsDate(31, 1, 2026)) << "\n";  
  
cout << clsDate::DifferentBtwDatesInDays(clsDate(1, 1, 2026), clsDate(10, 2, 2026));  
```  
  
```output  
1  
40  
```  
  
## Functionality #29  
`static int GetDateInDays(clsDate date);`  
`int GetDateInDays();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`int` : number of days that forms the date.  
  
<u>Explanation :</u>  
These functions return the number of days that form a specific date.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(30, 1, 2026);  
cout << _test_date_1.GetDateInDays() << "\n";  
  
cout << clsDate::GetDateInDays(clsDate(20, 1, 0));  
```  
  
```output  
740011  
20  
```  
  
## Functionality #30  
`static clsDate GetSystemDate();`  
  
<u>Inputs :</u>  
Nothing.  
  
<u>Outputs :</u>  
`clsDate` : the current day, month, and year.  
  
<u>Explanation :</u>  
This function return the current date, depending of the system configurations.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1 = clsDate::GetSystemDate();  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:23, Month: 3, Year:2026}  
```  
  
## Functionality #31  
`static void IncreaseDateByXDays(int X, clsDate& date);`  
`void IncreaseDateByXDays(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of days we want to add.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by X number of days.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByXDays(10);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByXDays(10, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:11, Month: 1, Year:2026}  
{Day:21, Month: 1, Year:2026}  
```  
  
## Functionality #32  
`static void IncreaseDateByOneWeek(clsDate& date);`  
`void IncreaseDateByOneWeek();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one week.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneWeek();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneWeek(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:8, Month: 1, Year:2026}  
{Day:15, Month: 1, Year:2026}  
```  
  
## Functionality #33  
`static void IncreaseDateByXWeeks(int X, clsDate& date);`  
`void IncreaseDateByXWeeks(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of weeks we want to add.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by X number of weeks.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByXWeeks(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByXWeeks(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:8, Month: 1, Year:2026}  
{Day:22, Month: 1, Year:2026}  
```  
  
## Functionality #34  
`static void IncreaseDateByOneMonth(clsDate& date);`  
`void IncreaseDateByOneMonth();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one month.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneMonth();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneMonth(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:1, Month: 2, Year:2026}  
{Day:1, Month: 3, Year:2026}  
```  
  
## Functionality #35  
`static void IncreaseDateByXMonths(int X, clsDate& date);`  
`void IncreaseDateByXMonths(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of months we want to add.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by X number of months.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByXMonths(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByXMonths(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:1, Month: 2, Year:2026}  
{Day:1, Month: 4, Year:2026}  
```  
  
## Functionality #36  
`static void IncreaseDateByOneYear(clsDate& date);`  
`void IncreaseDateByOneYear();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneYear();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneYear(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:1, Month: 1, Year:2027}  
{Day:1, Month: 1, Year:2028}  
```  
  
## Functionality #37  
`static void IncreaseDateByXYears(int X, clsDate& date);`  
`void IncreaseDateByXYears(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of years we want to add.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by X number of years.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByXYears(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByXYears(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:1, Month: 1, Year:2027}  
{Day:2, Month: 1, Year:2029}  
```  
  
## Functionality #38  
`static void IncreaseDateByOneDecade(clsDate& date);`  
`void IncreaseDateByOneDecade();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one decade.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneDecade();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneDecade(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:4, Month: 1, Year:2036}  
{Day:6, Month: 1, Year:2046}  
```  
  
## Functionality #39  
`static void IncreaseDateByXDecades(int X, clsDate& date);`  
`void IncreaseDateByXDecades(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of decades we want to add.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by X number of decades.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByXDecades(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByXDecades(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:4, Month: 1, Year:2036}  
{Day:9, Month: 1, Year:2056}  
```  
  
## Functionality #40  
`static void IncreaseDateByOneCentury(clsDate& date);`  
`void IncreaseDateByOneCentury();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one century.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneCentury();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneCentury(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:25, Month: 1, Year:2126}  
{Day:18, Month: 2, Year:2226}  
```  
  
## Functionality #41  
`static void IncreaseDateByOneMillennuim(clsDate& date);`  
`void IncreaseDateByOneMillennuim();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions increase a specific date by one millennium.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,1,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.IncreaseDateByOneMillennuim();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::IncreaseDateByOneMillennuim(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 1, Year:2026}  
{Day:31, Month: 8, Year:3026}  
{Day:1, Month: 5, Year:4027}  
```  
  
## Functionality #42  
`static void DecreaseDateByOne(clsDate& date);`  
`void DecreaseDateByOne();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one day.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOne();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOne(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:30, Month: 11, Year:2026}  
{Day:29, Month: 11, Year:2026}  
```  
  
## Functionality #43  
`static void DecreaseDateByXDays(int X, clsDate& date);`  
`void DecreaseDateByXDays(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of days we want to remove.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by X number of days.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByXDays(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByXDays(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:30, Month: 11, Year:2026}  
{Day:28, Month: 11, Year:2026}  
```  
  
## Functionality #44  
`static void DecreaseDateByOneWeek(clsDate& date);`  
`void DecreaseDateByOneWeek();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one week.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneWeek();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneWeek(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:24, Month: 11, Year:2026}  
{Day:17, Month: 11, Year:2026}  
```  
  
## Functionality #45  
`static void DecreaseDateByXWeeks(int X, clsDate& date);`  
`void DecreaseDateByXWeeks(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of weeks we want to remove.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by X number of weeks.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByXWeeks(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByXWeeks(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:24, Month: 11, Year:2026}  
{Day:10, Month: 11, Year:2026}  
```  
  
## Functionality #46  
`static void DecreaseDateByOneMonth(clsDate& date);`  
`void DecreaseDateByOneMonth();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one month.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneMonth();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneMonth(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:1, Month: 11, Year:2026}  
{Day:1, Month: 10, Year:2026}  
```  
  
## Functionality #47  
`static void DecreaseDateByXMonths(int X, clsDate& date);`  
`void DecreaseDateByXMonths(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of months we want to remove.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by X number of months.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByXMonths(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByXMonths(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:1, Month: 11, Year:2026}  
{Day:1, Month: 9, Year:2026}  
```  
  
<u>Functions used for the example :</u>  
```cpp  
  
```  
  
## Functionality #48  
`static void DecreaseDateByOneYear(clsDate& date);`  
`void DecreaseDateByOneYear();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneYear();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneYear(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:1, Month: 12, Year:2025}  
{Day:1, Month: 12, Year:2024}  
```  
  
## Functionality #49  
`static void DecreaseDateByXYears(int X, clsDate& date);`  
`void DecreaseDateByXYears(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of years we want to remove.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by X number of years.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByXYears(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByXYears(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:1, Month: 12, Year:2025}  
{Day:30, Month: 11, Year:2023}  
```  
  
## Functionality #50  
`static void DecreaseDateByOneDecade(clsDate& date);`  
`void DecreaseDateByOneDecade();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one decade.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneDecade();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneDecade(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:28, Month: 11, Year:2016}  
{Day:26, Month: 11, Year:2006}  
```  
  
## Functionality #51  
`static void DecreaseDateByXDecades(int X, clsDate& date);`  
`void DecreaseDateByXDecades(int X);`  
  
<u>Inputs :</u>  
`int X` : is the number of decades we want to remove.  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by X number of decades.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByXDecades(1);  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByXDecades(2, _test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:28, Month: 11, Year:2016}  
{Day:23, Month: 11, Year:1996}  
```  
  
## Functionality #52  
`static void DecreaseDateByOneCentury(clsDate& date);`  
`void DecreaseDateByOneCentury();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one century.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneCentury();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneCentury(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:6, Month: 11, Year:1926}  
{Day:13, Month: 10, Year:1826}  
```  
  
## Functionality #53  
`static void DecreaseDateByOneMillennuim(clsDate& date);`  
`void DecreaseDateByOneMillennuim();`  
  
<u>Inputs :</u>  
`clsDate& date` : is the date we want to edit, by reference.  
  
<u>Outputs :</u>  
Nothing.  
  
<u>Explanation :</u>  
These functions decrease a specific date by one millennium.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(1,12,2026);  
cout << _test_date_1.ToString() << "\n";  
  
_test_date_1.DecreaseDateByOneMillennuim();  
cout << _test_date_1.ToString() << "\n";  
  
clsDate::DecreaseDateByOneMillennuim(_test_date_1);  
cout << _test_date_1.ToString() << "\n";  
```  
  
```output  
{Day:1, Month: 12, Year:2026}  
{Day:2, Month: 4, Year:1026}  
{Day:3, Month: 8, Year:25}  
```  
  
## Functionality #54  
`static bool IsEndOfWeek(clsDate date);`  
`bool IsEndOfWeek();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the day the last in the week? or not.  
  
<u>Explanation :</u>  
These functions check whether a day is the last in the week or not.  
Sunday is the first day in the week.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.IsEndOfWeek() << "\n";  
cout << clsDate::IsEndOfWeek(clsDate(27, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
1  
0  
```  
  
## Functionality #55  
`static bool IsItWeekend(clsDate date);`  
`bool IsItWeekend();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the day a weekend day, or not.  
  
<u>Explanation :</u>  
These functions check whether a day is a weekend day or not.  
The weekend days is the last two days in the week. The first day in the week is Sunday. (In my situation :)  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.IsItWeekend() << "\n";  
cout << clsDate::IsItWeekend(clsDate(27, 3, 2026)) << "\n";  
cout << clsDate::IsItWeekend(clsDate(26, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
1  
1  
0  
```  
  
## Functionality #56  
`static bool IsBusinessDay(clsDate date);`  
`bool IsBusinessDay();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the day a business day or not.  
  
<u>Explanation :</u>  
These functions check whether a day is a business day or not.  
The business days are the first 5 days in the week. (In my situation :)  
The first day in the week is Sunday.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.IsBusinessDay() << "\n";  
cout << clsDate::IsBusinessDay(clsDate(27, 3, 2026)) << "\n";  
cout << clsDate::IsBusinessDay(clsDate(26, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
0  
0  
1  
```  
  
## Functionality #57  
`static int DaysUntilTheEndOfWeek(clsDate date);`  
`int DaysUntilTheEndOfWeek();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`int` : is the number of days remained to reach the last day in the week.  
  
<u>Explanation :</u>  
These functions return how many days a specific date needs to reach the last day in the week.  
The first day in the week is Sunday.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.DaysUntilTheEndOfWeek() << "\n";  
cout << clsDate::DaysUntilTheEndOfWeek(clsDate(27, 3, 2026)) << "\n";  
cout << clsDate::DaysUntilTheEndOfWeek(clsDate(26, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
0  
1  
2  
```  
  
## Functionality #58  
`static int DaysUntilTheEndOfMonth(clsDate date);`  
`int DaysUntilTheEndOfMonth();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`int` : is the number of days remained to reach the last day in the month.  
  
<u>Explanation :</u>  
These functions return how many days a specific date needs to reach the last day in the month.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.DaysUntilTheEndOfMonth() << "\n";  
cout << clsDate::DaysUntilTheEndOfMonth(clsDate(27, 3, 2026)) << "\n";  
cout << clsDate::DaysUntilTheEndOfMonth(clsDate(26, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
3  
4  
5  
```  
  
## Functionality #59  
`static int DaysUntilTheEndOfYear(clsDate date);`  
`int DaysUntilTheEndOfYear();`  
  
<u>Inputs :</u>  
`clsDate date` : is the date we want to work on.  
  
<u>Outputs :</u>  
`int` : is the number of days remained to reach the last day in the year.  
  
<u>Explanation :</u>  
These functions return how many days a specific date needs to reach the last day in the year.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(28, 3, 2026);  
cout << _test_date_1.PrintDateLong() << "\n";  
  
cout << _test_date_1.DaysUntilTheEndOfYear() << "\n";  
cout << clsDate::DaysUntilTheEndOfYear(clsDate(27, 3, 2026)) << "\n";  
cout << clsDate::DaysUntilTheEndOfYear(clsDate(26, 3, 2026)) << "\n";  
```  
  
```output  
Saturday, 28/3/2026  
278  
279  
280  
```  
  
## Functionality #60  
`static int GetWeekendDays(clsDate date1, clsDate date2);`  
`int GetWeekendDays(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to calculate how many weekend days are there between them.  
`clsDate date` : is the date we want to calculate how many weekend days are there between it and the date that is in the object.   
  
<u>Outputs :</u>  
`int` : is the number of weekend days between the two dates.  
  
<u>Explanation :</u>  
These functions return the number of weekend days between two specific dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.GetWeekendDays(clsDate(31, 3, 2026)) << "\n";  
  
cout << clsDate::GetWeekendDays(clsDate(24, 3, 2026), clsDate(7, 4, 2026)) << "\n";  
```  
  
```output  
2  
4  
```  
  
## Functionality #61  
`static int GetBusinessDays(clsDate date1, clsDate date2);`  
`int GetBusinessDays(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to calculate how many business days are there between them.  
`clsDate date` : is the date we want to calculate how many business days are there between it and the date that is in the object.   
  
<u>Outputs :</u>  
`int` : is the number of business days between the two dates.  
  
<u>Explanation :</u>  
These functions return the number of business days between two specific dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.GetBusinessDays(clsDate(31, 3, 2026)) << "\n";  
cout << clsDate::GetBusinessDays(clsDate(24, 3, 2026), clsDate(7, 4, 2026)) << "\n";  
```  
  
```output  
5  
10  
```  
  
## Functionality #62  
`static int GetVacationDays(clsDate date1, clsDate date2);`  
`int GetVacationDays(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to calculate how many vacation days are there between them.  
`clsDate date` : is the date we want to calculate how many vacation days are there between it and the date that is in the object.   
  
<u>Outputs :</u>  
`int` : is the number of vacation days between the two dates.  
  
<u>Explanation :</u>  
These functions return the number of vacation days between two specific dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.GetVacationDays(clsDate(31, 3, 2026)) << "\n";  
cout << clsDate::GetVacationDays(clsDate(24, 3, 2026), clsDate(7, 4, 2026)) << "\n";  
```  
  
```output  
5  
10  
```  
  
## Functionality #63  
`static clsDate EndOfVacation(clsDate startDate, short duration);`  
`clsDate EndOfVacation(short duration);`  
  
<u>Inputs :</u>  
`clsDate date` : is the first day of the vacation.  
`short duration` : is the duration of the vacation.  
  
<u>Outputs :</u>  
`clsDate` : is the first working day.  
  
<u>Explanation :</u>  
These functions return the first working day of an employee that took a vacation, taking into consideration the weekend days.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << (_test_date_1.EndOfVacation(10)).ToString() << "\n";  
cout << (clsDate::EndOfVacation(clsDate(7, 4, 2026), 5)).ToString() << "\n";  
```  
  
```output  
{Day:7, Month: 4, Year:2026}  
{Day:14, Month: 4, Year:2026}  
```  
  
## Functionality #64  
`static bool IsDate1AfterDate2(clsDate date1, clsDate date2);`  
`bool IsAfterDate(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to compare them.  
`clsDate date` : is the date we want to compare the current object with.  
  
<u>Outputs :</u>  
`bool` : is the first date bigger than the second? or not.  
  
<u>Explanation :</u>  
These functions check whether a specific date is bigger than another one or not.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.IsAfterDate(clsDate(11, 3, 2026)) << "\n";  
cout << clsDate::IsDate1AfterDate2(clsDate(7, 4, 2026), clsDate(5, 5, 2026)) << "\n";  
```  
  
```output  
1  
0  
```  
  
## Functionality #65  
`static bool IsDate1BeforeDate2(clsDate date1, clsDate date2);`  
`bool IsBeforeDate(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to compare them.  
`clsDate date` : is the date we want to compare the current object with.  
  
<u>Outputs :</u>  
`bool` : is the first date smaller than the second? or not.  
  
<u>Explanation :</u>  
These functions check whether a specific date is smaller than another one or not.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.IsBeforeDate(clsDate(11, 3, 2026)) << "\n";  
cout << clsDate::IsDate1BeforeDate2(clsDate(7, 4, 2026), clsDate(5, 5, 2026)) << "\n";  
```  
  
```output  
0  
1  
```  
  
## Functionality #66  
`static int CompareDates2(clsDate date1, clsDate date2);`  
`int CompareDates2(clsDate date);`  
  
<u>Inputs :</u>  
`clsDate date1` and `clsDate date2` : are the dates we want to compare them.  
`clsDate date` : is the date we want to compare the current object with.  
  
<u>Outputs :</u>  
`int` : `1` means the first date is bigger, `0` means they are equal, and `-1` means the second date is bigger.  
  
<u>Explanation :</u>  
These functions compare two dates.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.CompareDates2(clsDate(11, 3, 2026)) << "\n";  
cout << clsDate::CompareDates2(clsDate(7, 4, 2026), clsDate(5, 5, 2026)) << "\n";  
cout << clsDate::CompareDates2(clsDate(5, 5, 2026), clsDate(5, 5, 2026)) << "\n";  
```  
  
```output  
1  
-1  
0  
```  
  
## Functionality #67  
`static int GetYearTime(int year, enYearTime time);`  
`int GetYearTime(enYearTime time);`  
  
<u>Inputs :</u>  
`int year` : is the year we want to work on.  
`enYearTime time` : specify how you want to get the year, for example, as days, hours, minutes, or seconds.  
  
<u>Outputs :</u>  
`int`.  
  
<u>Explanation :</u>  
These functions return a specific year as days, hours, minutes, or seconds.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.GetYearTime(clsDate::enYearTime::enYearDays) << "\n";  
cout << clsDate::GetYearTime(2026, clsDate::enYearTime::enYearHours) << "\n";  
cout << clsDate::GetYearTime(2026, clsDate::enYearTime::enYearMinutes) << "\n";  
cout << clsDate::GetYearTime(2026, clsDate::enYearTime::enYearSeconds) << "\n";  
```  
  
```output  
365  
8760  
525600  
31536000  
```  
  
## Functionality #68  
`static char* GetCurrentTime();`  
`static char* GetGreenwichTime();`  
  
<u>Inputs :</u>  
Nothing.  
  
<u>Outputs :</u>  
`char*` : which is a C string.  
  
<u>Explanation :</u>  
These functions return the current time as in the example below.  
  
<u>Example of Usage :</u>  
```cpp  
printf("%s \n", clsDate::GetCurrentTime());  
printf("%s \n", clsDate::GetGreenwichTime());  
```  
  
```output  
Tue Mar 24 22:40:24 2026  
  
Tue Mar 24 20:40:24 2026  
```  
  
## Functionality #69  
`static clsDate ReadDate();`  
  
<u>Inputs :</u>  
Nothing.  
  
<u>Outputs :</u>  
`clsDate` : the object that just read.  
  
<u>Explanation :</u>  
This function read/fill a `clsDate` object from the screen.  
  
<u>Example of Usage :</u>  
```cpp  
cout << (clsDate::ReadDate()).ToString() << "\n";  
```  
  
```output  
Enter the day: 11  
Enter the month: 2  
Enter the year: 2022  
{Day:11, Month: 2, Year:2022}  
```  
  
## Functionality #70  
`static bool ValidateDate(clsDate date);`  
`bool ValidateDate();`  
  
<u>Inputs :</u>  
`clsDate` : is the date we want to work on.  
  
<u>Outputs :</u>  
`bool` : is the date valid or not.  
  
<u>Explanation :</u>  
These functions validate a date object.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.ValidateDate() << "\n";  
cout << clsDate::ValidateDate(clsDate(1,1,-1)) << "\n";  
cout << clsDate::ValidateDate(clsDate(30,2,2026)) << "\n";  
cout << clsDate::ValidateDate(clsDate(22, 23, 2026)) << "\n";  
```  
  
```output  
1  
0  
0  
0  
```  
  
## Functionality #71  
`static clsDate ReadDateAsString();`  
  
<u>Inputs :</u>  
Nothing.  
  
<u>Outputs :</u>  
`clsDate` : is the date that just read.  
  
<u>Explanation :</u>  
This function reads a `clsDate` object from screen as string and converts it to `clsDate` object.  
  
<u>Example of Usage :</u>  
```cpp  
cout << (clsDate::ReadDateAsString()).ToString() << "\n";  
```  
  
```output  
Please enter date dd/mm/yyyy: 12/1/2026  
{Day:12, Month: 1, Year:2026}  
```  
  
## Functionality #72  
`static string FormatDate(clsDate date, string date_formated = "dd/mm/yyyy");`  
`string FormatDate(string date_formated = "dd/mm/yyyy");`  
  
<u>Inputs :</u>  
`clsDate` : is the date we want to print.  
`string date_formated` : is the format you want.  
It's important to put the `dd mm yyyy`, in your string.  
  
<u>Outputs :</u>  
`string` : the formatted string.  
  
<u>Explanation :</u>  
These functions return a date as string in a specific formatted way.  
  
<u>Example of Usage :</u>  
```cpp  
clsDate _test_date_1(24, 3, 2026);  
cout << _test_date_1.FormatDate("dd # mm # yyyy") << "\n";  
cout << clsDate::FormatDate(clsDate(11, 12, 2026), "day: dd, month: mm, year: yyyy.") << "\n";  
```  
  
```output  
24 # 3 # 2026  
day: 11, month: 12, year: 2026.  
```  
