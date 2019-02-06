MySQL is a RDBMS owned by Sun Microsystems but is now free and open source!

startup:
if your computer has been restarted, you must launch the daemon via "mysqld".  Then mysql will work just fine.

installation:
worked!: (see bottom to access)
https://ariejan.net/2007/12/12/how-to-install-mysql-on-ubuntudebian/
didn't quite work:
http://www.tutorialspoint.com/mysql/mysql-installation.htm
creating stuff!:
http://dev.mysql.com/doc/refman/5.1/en/database-use.html


RDBMS vocab:
index - index like in the back of a book!
primary key - a unique key in a table
foreign key - the linking pin btw two tables
compound key - key consists of multiple columns


GROUP BY
select colA, count(colA) from tbl group by colA
whenever two or more vals are the same in colA, they are grouped into one row, and count(colA) will show how many of them there are.
select colA, max(colB) from tbl group by colA
this is the same, byt now max(colA) will show for each group, the max val in colB.

IN
where col=a or col=b or col=c
can be replaced by
where col in (a,b,c)

BETWEEN
same as SQL

UNION
select cola, colb from table1
union
select colc, cold from table2

will combine the tables where cola and colc are merged, and colb and cold are merged.  It acts as a real union (duplicates don't appear twice).  To get duplicates, use UNION ALL instead.

COUNT
select count(*) from table
gives the number of rows
select count(*) from table where col=val
gives the number of rows that fit the criteria

MAX / MIN / AVG / SUM
select max(col) from table
will tell you the maximum value in that column.

RAND()
gets a rand btw 0 and 1
ORDER BY RAND()
allows you to reorder the rows randomly

CONCAT( col1, col2, ...)
combines cols by concatenating their values

DATE AND TIME FUNCTIONS
many functions that let you get current date, reformat, add dates together, etc
http://www.tutorialspoint.com/mysql/mysql-date-time-functions.htm

NUMBERIC FUNCTIONS
functions like sin(), pi, ceil, degrees, power, sqrt that can be applied to values
http://www.tutorialspoint.com/mysql/mysql-numeric-functions.htm

STRING FUNCTIONS
just like numeric, but for string manipulation instead of numbers! :)  SOME GOOD ONES:
LOWER
UPPER
http://www.tutorialspoint.com/mysql/mysql-string-functions.htm

\g - go!!!
\G - go, display vertically