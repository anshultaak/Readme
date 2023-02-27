## Executive Summary

Jeff and Andy have reported that there is some sort of data discrepancy happening in snowflake reporting

## Leadup

Database team reported that there is data discrepancy happening in Snowflake reporting.


### Fault

Data team Received Data Alert where it shows rise in data quality rule for unique registrations in Production


### Detection

Data team detected this via Data Alert email, on further investigations reported that the issue shows duplication of registrations. 

SELECT * FROM silver_bert_enrollment.dbo_registrations where ID = '30b67cf1-a038-42e6-935f-2c909f221834'; -- returning 2 rows. Expected 1 row

 

The overall count of duplicates is 423  which is more, than in  registrations_cfa (123):

 

select count(*) from

(SELECT id,count(*) FROM silver_bert_enrollment.dbo_registrations

group by id

having count(*)>1);

 

and

 

SELECT REGISTRATION_ID, COUNT(*) FROM GOLD.REGISTRATIONS_CFA GROUP BY REGISTRATION_ID HAVING COUNT(*)>1;

# Root causes
The 14th of February in 2023, added a new column to registrations, but it caused a problem because it was done at the same time as another process, and it made too many copies of the same information.


#Mitigation and resolution
Column added to registrations during deployment yesterday overlapped with incremental pipeline causing unintended duplicates in data lake. 

Data team follow the following steps:

Stop current incremental runs.

Suspend incremental triggers

Run Full load

Validate and Communicate to Will and Matt that full load is complete

Fix the underlying issue in incremental run

Deploy the fix

Validate

Enable Incremental load and Communicate to Will and Matt that incremental has been enabled
