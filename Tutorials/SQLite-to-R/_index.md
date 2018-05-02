+++
title= "Importing SQLite DB into R"
date= 2018-04-30T11:30:45-04:00
description = "A workflow for importing DB into R"
weight = 112
+++

### I've got data, now what?

We've already explained how to [put data into a SQLite database](/Sqlite). Now we want to grab a subset of that data and pull it into R where we can analayze or visualize it, or combine it with other kinds of data. It is in fact quite straightforward.

We write a script that tells R to open a connection to the database; then we tell it what's inside that database; then we write an SQL query _in R_ that grabs just the bits we're interested in and passes it to a new R object; and then we shut the connection and clear the cache.

In this way, we're never directly modifying our datastore. We're always working on a copy of the data, which is handy because when we screw up - and we will - we can rest easy knowing the original data is still ok. The code looks like this:

```
# first we get the packages we need:
library(DBI)
library(RSQLite)

# now we open the connection:

con = dbConnect(SQLite(), dbname="YOUR-AMAZING-DATABASE.sqlite")

# we can see what's inside, eg, what tables are in the database?
alltables = dbListTables(con)
alltables

# write the query to get the information you want

myQuery <- dbSendQuery(con, "SELECT id, owner_id, caption, taken_at_timestamp FROM unique_posts")

# pass that information to an R object. The n = -1 bit means grab everything until there's nothing left to grab. Otherwise, you can specify how many rows etc.

my_data <- dbFetch(myQuery, n = -1)

# now that we're done, clear cache 
dbClearResult(myQuery)

# now carry on and begin manipulating my_data
# for more information see
# http://tiffanytimbers.com/querying-sqlite-databases-from-r/
# also perhaps this https://www.r-bloggers.com/using-sqlite-in-r/

```




