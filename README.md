# New_task
#This folder contains solution for the below given problem statement
#I have used python to resolve the issue and choice of database is Azure sql database
#check solution.py for the code

Coding Exercise “QA checks”

The candidate can chose between on-premise or Cloud RDBMS; the programming language can be python or
PL/SQL, SQL knowledge is also needed. Once candidate has completed code they will upload in a Git repository
and email the link to the HR contact in Sky

Exercise:
I am a Data Engineer and I want to write a code to run QA checks.
The code is modular to allow future improvements such as adding an audit table.
The MVP will output the test results in a GUI.
In this exercise I want to write a draft code that can:
1 Read records from the table qa_tests stored in a RDBMS of my choice
• Table name: qa_tests
• Table columns:
1. code: unique identifier assigned to a qa_test
2. description: it describes the test in plain English
3. enabled: is the test to be executed? Y/ N
4. parameter: it contains a comma separated list of names
5. test_sql: the SQL that will be executed, it contains the parameters that are replaced with a
value received at run time
6. exp_result: to compare the sql returned value with its exp_result
   
All columns are VARCHAR2 (or equivalent, it depends on your chosen RDBMS)
code description enabled parameter test_sql exp_result
qa_ch_01 Runs the SQL against the
Channel table to count
duplicates. Duplicates
count must be 0
Y env Select count*) from (select
channel_code, count*)
from channel_table_env
group by channel_code
having count*) > 1)
0
qa_ch_02 Check the FK between
channel_code and its
child table
channel_transaction to
identify orphans at a
given date
Y env, date select count*)
from
channel_transaction_env A,
channel_table_env B
left join on (A.channel_code
= B.channel_code)
where B.channel_code is null
and B.transaction_date =
date
0
qa_ch_03 Counts the records in
channel_transaction
table at a given date that
have amount null
N date select count*) from
channel_transaction_env
where transaction_date =
date and transaction_amount
is null
0


2 Exec the SQL from test_sql after replacing in test_sql the parameters (the list is in column parameter) with
their run time value.
The output (in GUI) will be:
1. code
2. sql (the SQL that was executed, not the content from test_sql)
3. result (the SQL output)
I have choosen python to create the QA Result set and choice of database is Azure sql database
