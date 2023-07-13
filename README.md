# Project: Data Modeling with mysql



## Summary of the Project

### Introduction

An idea named **kikkify**, to analyze the data that's been collecting on songs and user activity on a music streaming app. The analytics part was particularly interested in understanding what songs users are listening to. Currently, there are no easy way to query the data, which resides in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.

The idea was to create a **mysql database** with tables designed to optimize queries on song play analysis, and bring you on the project. 

Goals for the projects are to:

1. create a **database schema**  

2. create an **ETL pipeline** for this analysis

3. **test the created database and ETL pipeline** by running queries given to me by the analytics team from Sparkify and compare my results with their expected results.

   

## Database schema design 

Database schema that was utilized in this project is one of the simplest data mart schemas named **Star Schema** which consist in our case of one **fact table** - **songplays** and several **dimension tables - artists, users, songs and time** from which two are the most relevant - **artists and songs** since it was utilized for the ETL and desired queries.


## ETL pipeline

ETL pipeline was designed with a main focus on getting the insights into understanding what songs users are listening to. 

The whole ETL pipeline reads the json data from `song_data` and `log_data` files located in two local directories , processes it  and  inserts them into the Postgres database kikkifydb in created tables using Python and SQL. Tables where the data is inserted in the database are `songplays`, `users`, `artists`, `songs` and `time`.  Time table has no defined relationship with the existing tables.


## Explanation of the files in the repository

In addition to the **data files**, the project workspace includes **six files**:

1. `test.ipynb` displays the first few rows of each table to let you check your database. - **it was used for testing of the development**
2. `create_tables.py` drops and creates your tables. You run this file to reset your tables before each time you run your ETL scripts.
3. `etl.ipynb` reads and processes a single file from `song_data` and `log_data` and loads the data into your tables. This notebook contains detailed instructions on the ETL process for each of the tables. **- it was used for development**
4. `etl.py` reads and processes files from `song_data` and `log_data` and loads them into your tables. You can fill this out based on your work in the ETL notebook.
5. `sql_queries.py` contains all sql queries, and is imported into the last three files above.
6. `README.md` provides summary and discussion on the project.
7. `database_schema_diagram.png` is an image of a database schema diagram.



## How to run Python scriptss

Below are steps you can follow to complete the project:

### Create Tables.

1. Run `create_tables.py` to create the database and tables.

### Build ETL Pipeline

Run `etl.py`, where process the entire datasets. Remember to run `create_tables.py` before running `etl.py` to reset your tables. 



## Data files

#### Song Dataset

The first dataset is a subset of real data from the [Million Song Dataset](https://labrosa.ee.columbia.edu/millionsong/). Each file is in JSON format and contains metadata about a song and the artist of that song. The files are partitioned by the first three letters of each song's track ID. For example, here are filepaths to two files in this dataset.

```txt
song_data/A/B/C/TRABCEI128F424C983.json
song_data/A/A/B/TRAABJL12903CDCF1A.json
```

And below is an example of what a single song file, TRAABJL12903CDCF1A.json, looks like.

```json
{"num_songs": 1, "artist_id": "ARJIE2Y1187B994AB7", "artist_latitude": null, "artist_longitude": null, "artist_location": "", "artist_name": "Line Renaud", "song_id": "SOUPIRU12A6D4FA1E1", "title": "Der Kleine Dompfaff", "duration": 152.92036, "year": 0}
```

#### Log Dataset

The second dataset consists of log files in JSON format generated by this [event simulator](https://github.com/Interana/eventsim) based on the songs in the dataset above. These simulate app activity logs from a music streaming app based on specified configurations.

The log files in the dataset you'll be working with are partitioned by year and month. For example, here are filepaths to two files in this dataset.

```txt
log_data/2018/11/2018-11-12-events.json
log_data/2018/11/2018-11-13-events.json
```

And below is an example of what the data in a log file, 2018-11-12-events.json, looks like.



![img](https://s3.amazonaws.com/video.udacity-data.com/topher/2019/February/5c6c15e9_log-data/log-data.png)
