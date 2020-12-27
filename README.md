
# Data Wherhouse Project

## Introduction 
This project aims to create ETL pipeline that extracts Sparkify streaming app data from Amazon S3, stages them in Amzon Redshift, and transforms the data into a set of dimensional tables for Sparkify analytics team to continue finding insights in understanding which songs users listen to the most in the app.


## DataSets   
Sparkify app data resides in two public Amazon S3 buckets:

1- Song Dataset: (all files are in one directory in a JASON format)
    - Song data: 's3://udacity-dend/song_data'
    - a subset of real data from the Million Song Dataset 
    - contains the metadata on the song on the app and the artist of the song 
    
    

2- Log Dataset:(files are distributed  into several folders several folders without a common prefix, so we will use a descriptor file called "Log data json path" to extract them )
    - Log data: 's3://udacity-dend/log_data'
    - Log data json path: 's3://udacity-dend/log_json_path.json'
    - generated by event simulator based on the songs in the Million Song Dataset 
    - contains the logs on user activity in any given day   


## Running Requirements    

1- An available and running  AWS Redshift Cluster with 4" Node and "dc2.large" NodeType

2- An IAM role attached with an AmazonS3ReadOnlyAccess policy

Once the above is set, open a terminal and run the following python files: 


3- Run "create_tables.py"

4- Run "python etl.py"



## Project repository
we have two python files that should be run sequentially:

1- "sql_queries.py", contains the DROP, CRETE, INSERT, SELECT statements, or SQL queries, and it is referenced in "create_tables.py" AND "etl.py" files.

2- "create_tables.py", contains the functions that create and connect to the Sparkify DB and calls the queries or the statements in the "sql_queries.py" file.
    
3- "etl.py", contains the extraction and the loading of data from the S3 bucket and ingest them to the Redshift cluster

4- "dhw.cfg", it's a configuration file that contains the needed information about Redshift Cluster, IAM, S3, and DataWarehouse. 

As a result, create_tables.py must be run first, then etl.py could be run after for the ETL pipeline for the data loading and insertion.  
