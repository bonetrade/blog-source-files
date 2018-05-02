+++
title = "Setting up a SQLite DB"
description = "A short tutorial on setting up a sqlite db and simple queries of same"
weight = 110
+++

The data that we scraped using Scrapy was output as json files. Json stands for 'JavaScript Object Notation' and records values as attribute-data pairs and lists these pairs in arrays. Because we are not building a complex multi-faceted database, and we might want to expose this data for other kinds of uses later on (perhaps as our [own API](https://programminghistorian.org/lessons/creating-apis-with-python-and-flask)), we are going to take that data and put it into a sqlite database.

This will also enable us to identify duplicate values (data that got captured via multiple searches or hashtags, for instance), extract and reshape the data for particular purposes, connect our data to R for subsequent analyses, and deposit the data in our data repo. 

## Requirements

+ [sqlitebiter](https://sqlitebiter.readthedocs.io/en/latest/index.html) a python utility for ingesting a wide variety of data formats into an sqlite db
+ python 

First, set up a virtualenv:

```
$ mkdir database-work
$ virtualenv database-work
$ source database-work/bin/activate
```

Install sqlitebiter:

```
$ pip install sqlitebiter
```

This will install a bunch of other dependencies - which is why we're using a virtualenv, so that these dependencies don't conflict with other packages we're using.

## Making the database

Assuming you have the concatenated file containing all of the results from the scrape as a properly formatted json file in the current folder,

```
sqlitebiter file scrape-results.json -o scrape-results-current-date.sqlite
```

Then, to finish things up,

```
$ sqlite3 scrape-results-current-date.sqlite
 >>> .schema
 >>> .exit
```

The `>>>` on the command line show us we're inside sqlite. We could continue to work on the command line with sqlite, but sometimes a gui does make life easier. We'll use [sqlitebrowser](http://sqlitebrowser.org/). Download and install. Then, open the dbbrowser and open the database you just created.

![Example screenshot of a typical DB-browser interface](https://github.com/sqlitebrowser/sqlitebrowser/raw/master/images/sqlitebrowser.png)

Click 'browse data' and you'll see the data in a clean table view. The data can be exported as csv. Here are some simple SQL queries we can run to do some common tasks for us. To run these, click 'execute sql' and paste the query into the edit window. Once the query is there (these queries can also be saved and loaded from file) hit the 'run' button to execute.

### Example Queries

A query to select distinct rows, that is to say, remove duplicate values:

```
select distinct
id, caption, display_url, owner_name, taken_at_timestamp
from
scrape-results-current-date;
```

make a new table from those distint values:

```
create table individual_posts
as 
select distinct id, caption, display_url, owner_name, taken_at_timestamp
from scrape-results-current-date;
```

select distinct rows by keyword in a field:

```
select distinct
id, caption, display_url, owner_name, taken_at_timestamp
from
individual_posts
where caption like '%sale%';
```

convert unix timestamp to human-readable date

```
UPDATE unique_posts SET taken_at_timestamp = datetime(taken_at_timestamp, 'unixepoch', 'localtime')
```