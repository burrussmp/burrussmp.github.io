---
date: 2020-08-05

title: "Apache Spark"
tagline: ""
toc: true
excerpt: "Notes on Apache Spark (Python API)"
---
## Using Spark in Python

```python
! pip install pyspark
from pyspark import SparkContext, SparkConf
```

### Initialization

```python
conf = SparkConf().setAppName(appName).setMaster(master)
sc = SparkContext(conf=conf)
```

The *SparkContext* tells Spark how to access the cluster. The *appName* parameter is the name of the application to show on the cluster UI and *master* is the Spark, Mesos, or YARN cluster URL. You will want to launch the application with *spark-submit* instead of hard-coding.

## Abstractions (Components) in Apache Spark

Spark applications use a *driver program* that runs the *main()* which executes various operations in *parallel* across a cluster.

### Resilient Distributed Dataset (RDD)

An RDD is a collection of elements partitioned across nodes of a cluster that can be operated in parallel. They can recover from failure and can be persisted in memory in Spark.

There are two ways to create an RDD:

1. Parrallelize an existing collection in the driver program
2. Referencing a dataset in an external storage system (e.g. HDFS, HBase, or any data source offering a Hadoop InputFormat)

```python
    data = [1, 2, 3, 4, 5]
    distData = sc.parallelize(data,10) # 10 is the number of partitions to cut the data set into
    distData.reduce(lambda a, b: a + b) # a parallel operation performed on data array
```

**Important**: You specify the number of partitions and typically you want 2-4 partitions for each CPU in your cluster. 

### External Datasets

External Dataset Examples: Amazon S3, HBase, Cassandra, HDFS, etc.

Important Commands

1. textFileCommand(): Read in external file or specific text file.
2. wholeTextFiles(): Read in (filename,content) pairs from a directory of small text files

You can read in a text file using the `sc.textFile(filename)` command where `filename` can be replaced by the local path on the machine to the external storage (e.g "hdfs://").  Once created, the dataset can be operated on using *dataset operations* like *map()* and *reduce()*. By default, Spark will allocate 1 partition per 128MB block, but that can be specified by the second parameter.

### RDD Operations

There are two types of operations supported by RDDs: transformations (e.g. map) or actions (e.g. reduce). All transformations are *lazy* in that they do not compute the results right away but the transformations are remembered and computed whenever an action requires a result to be returned to the driver program.

This is useful for efficiency, but each transformed RDD may be computed each time the action is called. To stop, this you can use `persist` or `cache` in which Spark will keep the elements around the cluster for a much faster access the next time you query.

Basic example
```python
lines = sc.textFile("data.txt") # load in (but not actually just point)
lineLengths = lines.map(lambda s: len(s)) # add map to computation graph
lineLengths.persist() # designate lineLengths to be saved into memory AFTER the first time that it is used
totalLength = lineLengths.reduce(lambda a, b: a + b) # perform an action, so 1) partition data, 2) load, 3) map and persist, 4) reduce
```

### Functions in Spark

There are 3 recommended ways to pass functions into Spark.
1. Lambda expressions (e.g. `lambda s: len(s)`)
2. Local defs in Spark
3. Top-level functions in a module

#1 and #2 are easy, but when using #3 (like if you have a class whose function you are calling) then you cannot reference the class in the function otherwise the whole object will be sent to the cluster. To avoid this, copy whichever field you need into a local variable instead of accessing it externally and then pass in the function.

## Closures in Spark

It is important to understand the lifecycle and scope of variables in Spark.

### Local vs Cluster Modes

To execute jobs, Spark firsts breaks up the RDD operations into tasks which are executed by the *executor*. Prior to execution, Spark computes the task's **closure** which are variables and methods that need to be visible for the executor to perform its computations on the RDD. Because the *closure* is sent to each *executor* you may encounter issues, such common with mutable variables (i.e. no longer atomic.).

A common example is with a counter that references a global variable. The global variable will be sent to each executor within the closure as a copy, thus, if all executors update the variable, you will see that it actually doesn't actually count correctly. Instead, an **Accumulator** should be used.

### How to correctly print something

```python
rdd.take(NUMBER_TO_PRINT).foreach(println)
```

### Working with key-value pairs



### Shared Variables

Shared variables allow the programmer to share information across tasks or between the tasks and the driver programs. There are two types:

1. Broadcast: Cache a value in memory on all nodes
2. Accumulators: Variables that operations apply to (e.g. sum or counters)

## Important Snippets

This section covers small, important snippets that could be of use.

### Master URLS

Relevant Topics: [initialization](#initialization).

The *Master* URL can be a Spark, Mesos, or YARN Cluster URL. The following image can be useful as a guide to knowing what is what.

<figure style="display: block;text-align: center;margin:0px;">
  <img style="width:100%;height:auto;border:1px solid black;" src="/assets/Spark/MasterURL.png"/>
</figure>
