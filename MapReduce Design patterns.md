Degin patterns are general patterns to solve problems. 3 of the most common map reduce design patterns are:

* Filtering patterns

* Summarization patterns

* Structural patterns


## Filtering Design patterns:

don’t change records. Only get a part of the data!

* Examples: sampling, random­sampling, top 10

Sampling is about pulling out a subset of the data for future processing. Typically, you'd use
sampling to extract a smaller but representative data set on which you could then perform further
analysis.

#### Top 10

An interesting application of mapreduce is making top N record lists. In RDBMS you would
normally first sort the data, then take top N records. In mapreduce this kind of approach will not
work, because the data is not sorted and is processed on several machines. Thus, the mappers
will first have to find their own top N lists, without sorting the data, and then send the local lists to the reducers who then can find the global top N list.

In relational data bases, we first sort the data and then pick the top N records. This doesn't work in map reduce as the data is not sorted and is distributed on several machines. Thus, in map reduce, each mapper gerenarte top N record of the block it is working with. Then reducer should find the global top N records.


## Summarization Patterns

Summarization patterns produce a top­level, summarized view of your data. You can group similar data together, for example by day, or by time of day, or by username and then calculate a statistic of some value, like min/max/average/mean etc. You can also build an index, or just simply count occurrences of something.

There are couple of problems that can be solved by using similar approach:

* numerical summarizations ­ finding count of value, as well as min, max, avg, median and other numerical values for your dataset

* inverted index: important when building a search engine or full text search functionality for your own
website or application

#### Inverted Index

It is often needed to build a reverse index from a data set, to enable faster searching. The obvious example would be a web search engine. You need to create a mapping from keywords to web links, to enable faster finding of relevant information. Think of it as an index for a book ­ you have a word, or term, and all pages you can find this term.

While the pattern itself is simple ­mapper outputs each word as the key, the link being the value, you have to be conscious of the fact that this type of mapreduce is susceptible to uneven key distribution.

#### Numerical summarization

Common uses for this type of analysis are:

* word or record count 

* min/max/count

#### Mean and Standard Deviation

Let’s say that you want to know if there is any correlation between day of week and how much
money people spend on items. Your task is to find out mean and standard deviation for sale per
day of week.


Mapper will need to have only output the day of week as the key and the sale amount as the
value. Reducer has to do all the maths.


In general ­ if you need to find out Average/Median/Standard deviation, these would have to be
calculated in the reducer.



**Combiners** are used to reduce the amount of input the reducer gets. This means, using combiner, each mapper can combine the result of the computation on each machine (node), then send the intermediate results to the reducer.


## Structural Patterns

These patterns usually are used when migrating data from relational data sets to hadoop. Hadoop doesn't care what format of the data it takes. We can benefit from hierarchical data then.

In order to use these patterns, the data in the relational data set should be:

1. data source linked by foreign keys
2. data must be structured and row-based









