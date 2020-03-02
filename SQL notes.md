source:
http://www.w3schools.com/sql/default.asp
source:
http://www.techonthenet.com/sql/like.php
SQL is Structured Query Language used to grab and edit data from a database.
A database is called a RDBMS Relational Database Management System.  Options include SQL Server, MySQL, Oracle, DB2, MS Access, etc.
memorize commands:
~/DesktopFolders/programming/SQL/SQLReference.html
source:
http://www.tutorialspoint.com/sql/sql-truncate-table.htm
quiz:
http://www.sqlquiz.com/

*SQL is NOT case sensitive
COLUMNS

select [distinct] col,col,col from tablename [where column='value' [and column=6]]  [order by column1 [asc],column2 [desc] ]        *the value IS case sensitive
asc is the default, only need to write the desc etc if you want a descending order somewhere
you can also use or!, you can combine multiple ands and ors, but use parenthesis!!!
we do not use quotes for number values.  Other possible operators are <> or !=, >, <, >=, <=, BETWEEN v1 AND v2 (inclusive range), LIKE pattern [ ESCAPE 'escape_character' ] 'likepattern', REGEXP 'regexpattern' (yay!!!!!!!!!!!!), IN (multiple values for a column)
select distinct "

Like patterns: (remember, regex is possible, so this is not necessary)
% matches any string any length
_ matches any character
whatever you choose to be the 'escape_character' is now your magic slosh.  Use it to precede % or _.
NOT LIKE allows you to find the complement set (all things that do NOT match pattern)

update tablename set col=val,col=val [where col=val]      *this is used to edit your data.  the where is almost always used.

insert into tablename (col,col,col) values (val,val,val);    *values in quotes when strings of course
* if you are inserting data for ALL the columns, you do not need to list which cols you are insterting.  By default it just follows the cols in order.


NOT AN EXHAUSTIVE LIST!:
create
alter
drop

insert into
update
delete

show

select top # [percent] OR select statement limit # (MySQL) OR select statement where rownum <= # (oracle)

TABLES
create table tbname (colname VARCHAR(#ofchars), colname CHAR(#ofchars), colname DATE, etc )
describe tablename - allows you to see the coltypes that you created.

INDECIS - like the index in the back of a book, but for the computer only (to be faster, like spotlight indexing)
create index inname on tbname
create unique index inname on tbname
drop index

CONSTRAINTS:
NOT NULL
UNIQUE - a column or combination of columns which TOGETHER uniquely identify a row.  (the TUPLE must be unique).  If you want more than one column to be independently unique, then just write more than one UNIQUE statement.
PRIMARY KEY (not null AND unique) - it is a column or combination of columns which uniquely identify a row!!
FOREIGN KEY (referential stuff)
CHECK condition
DEFAULT

to learn:
foreign key!


What is cursor?
cursor - Current Set Of Records.  database object pointing to a currently selected set of records.

What is locking?
locking - something RDBMS does to allow many users to access data at the same time without interfering!

What is a trigger?
A program attached to a table which is executed every time an INSERT INTO, UPDATE, or DELETE statement is made.  Triggers can use the special tables 'inserted' and 'deleted' when they want to!

SET NOCOUNT ON
CREATE TABLE Source (Sou_ID int IDENTITY, Sou_Desc varchar(10))
go
CREATE TRIGGER tr_Source_INSERT
ON Source
FOR INSERT AS
PRINT GETDATE()
go
INSERT Source (Sou_Desc) VALUES ('Test 1')


-------------------
PSQL
needs colons

