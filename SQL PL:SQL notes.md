https://www.geeksforgeeks.org/plsql-introduction/

see:
asktom.oracle.com

python bindings:
https://cx-oracle.readthedocs.io/en/latest/user_guide/plsql_execution.html

more technical docs!:
https://docs.oracle.com/cd/E11882_01/appdev.112/e25519/subprograms.htm



Working example of calling a PL/SQL PROCESS from Python...
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In the DB, run the following PL/SQL block to define the process:

	create or replace procedure myproc (
	    a_Value1                            number,
	    a_Value2                            out number
	) as
	begin
	    a_Value2 := a_Value1 * 2;
	end;
	/

In Python, use the following:

	connection = get_connection()
	with closing(connection.cursor()) as cursor:
		outVal = cursor.var(int)
		cursor.callproc('myproc', [123, outVal])
		out = outVal.getvalue()
		print(out)
		# will print 246

