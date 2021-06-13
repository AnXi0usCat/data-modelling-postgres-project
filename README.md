# Data Modeling with Postgres

## Introduction

A startup called Sparkify wants to analyze the data they've been collecting on songs and user activity on their new music streaming app. The analytics team is particularly interested in understanding what songs users are listening to. Currently, they don't have an easy way to query their data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

They'd like a data engineer to create a Postgres database with tables designed to optimize queries on song play analysis, and bring you on the project. Your role is to create a database schema and ETL pipeline for this analysis. You'll be able to test your database and ETL pipeline by running queries given to you by the analytics team from Sparkify and compare your results with their expected results.

## Project Description
In this project, you'll apply what you've learned on data modeling with Postgres and build an ETL pipeline using Python. To complete the project, you will need to define fact and dimension tables for a star schema for a particular analytic focus, and write an ETL pipeline that transfers data from files in two local directories into these tables in Postgres using Python and SQL.

** Facts and Dimensions

I have used Star schema model to store the Sparkify data.
We have one fact table `songplays` 
We have dimension tables for `songs`, `artists`, `users` and `time`


**Fact songplays**

| COLUMN| TYPE| CONSTRAINT|
|---|---|---|
|   songplay_id| BIGSERIAL  |   PRIMARY KEY| 
|   start_time |   NUMERIC  |              | 
|   user_id    |   TEXT     |              | 
|   level      |   TEXT     |              | 
|   song_id    |   VARCHAR  |              |  
|   artist_id  |   VARCHAR  |              | 
|   session_id |   INTEGER  |              | 
|   location   |   TEXT     |              | 
|   user_agent |   TEXT     |              |


**Dimension songs**

| COLUMN  | TYPE   | CONSTRAINT   |
|---|---|---|
|   song_id    |   VARCHAR  |   PRIMARY KEY| 
|   title      |   VARCHAR  |      NOT NULL| 
|   artist_id  |   VARCHAR  |      NOT NULL| 
|   year       |   INTEGER  |      NOT NULL| 
|   duration   |   NUMERIC  |      NOT NULL| 


**Dimension artists**

| COLUMN  | TYPE   | CONSTRAINT   |
|---|---|---|
|   artist_id   |   VARCHAR  |   PRIMARY KEY| 
|   name        |   VARCHAR  |      | 
|   location    |   TEXT     |      | 
|   latitude    |   VARCHAR  |      | 
|   longitude   |   VARCHAR  |      | 


**Dimension users**

| COLUMN  | TYPE   | CONSTRAINT   |
|---|---|---|
|   user_id    |   TEXT       |   PRIMARY KEY| 
|   first_name |   TEXT       |      | 
|   last_name  |   TEXT       |      | 
|   gender     |   VARCHAR(1) |      | 
|   level      |   TEXT       |      | 


**Dimension time**

 | COLUMN  | TYPE   | CONSTRAINT   |
|---|---|---|
|    start_time    |    TEXT      |     PRIMARY KEY|
|    hour          |    TEXT      |        NOT NULL| 
|    day           |    TEXT      |        NOT NULL|
|    week          |    TEXT      |        NOT NULL| 
|    month         |    TEXT      |        NOT NULL| 
|    year          |    TEXT      |        NOT NULL| 
|    weekday       |    TEXT      |        NOT NULL|



## Files used

### etl.py
The ETL is in the file **etl.py** and is divided in the next sections:

1. Connect to the database.
2. Process **song files**.
3. Process **log_files**.
    
## sql_queries.py

This file contains all the queries to the database. 
In this file are:
1. CREATE statemnts for all the tables.
2. INSERT statemnts for all the tables.
3. DELETE statements for all the tables.