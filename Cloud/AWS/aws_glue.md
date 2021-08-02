# AWS GLUE

## What is AWS Glue?

AWS Glue is serverless tool developed for the purpose of extracting, transforming and loading data. This process is referred to as ETL.

AWS Glue enables busineses to extract data from one source, transform the data and then loa it into a data warehouse.

AWS Glue consists of a central metadata rerpository known as the aws Glue Data Catalog, an ETL engine that automatically generates Python or Scala code and a flexible scheduler that handles dependency resolution, job monitoring, and retries.

AWS Glue is designed to work with semi-structured data. It introduces a component called a *dynamic frame*, which you can use in your ETL scripts.

A dynamic frame is similar to an Apache Spark dataframe, which is a data abstraction used to organize data into rows and columns.


## When Should I Use AWS Glue?

You can use AWS Glue to organize, cleanse, validate and formate data for storage in a data warehouse or data lake.


## AWS GLUE: How it Works

AWS Glue uses other AWS services to orchestrate your ETL jobs to build data warehouses and data lakes and generate output streams.

AWS Glue calls API operations to transform your data, create runtime logs, store your job logic and create notifications to help you monitor your job runs.

With AWS Glue, you can create jobs using table definitions in your Data Catalog.

Job consists of scripts that contain the programming logic that performs the transformation.

You use triggers to initiate jobs either on a schedule or as a result of a specified event.

With you input, AWS Glue generates the code that is required to transform your data from source to target.


### Data Sources

AWS Glue supports the following data sources:

- Data Stores
  - Amazon S3
  - RDS
  - DynamoDB
  - MongoDB and Amazon DocumentDB
  - JDBC

- Data Streams
  - Amazon Kinesis Data Streams
  - Apache Kafka

### Data Targets

AWS Glue supports the following data targets

- Amazon s3
- RDS
- JDBC
- MongoDB and Amazon DocumentDB.


## AWS Glue Concepts

The following diagram shows the Architecute of AWS Glue Environment.

![](https://github.com/amarnadh19/books/blob/main/images/aws_glue2.png?)

You define *jobs* in AWS Glue to accomplish the work that is required to extract, transform, andload data from a data source to a data target.

You typically perform the following actions:

-  For data store sources, you define a crawler to populate your AWS Glue Data Catalog with metadata table definitions. You point your crawler at a data store, and the crawler creates table definitions in the Data Catalog.
   
 In addition to table definitions, the AWS Glue Data Catalog contains other metadata that is required to define ETL jobs. You use this metadata when you define a job to transform your data.

- AWS Glue can generate a script to transform your data. Or, you can provide the script in the AWS Glue console or API.

- You can run your job on demand, or you can set it up to start when a specified trigger occurs. The trigger can be a time-based schedule or an event.


	Note:

	Tables and databases in AWS Glue are objects in the AWS Glue Data Catalog. They contain metadata; they don't contain data from a data store.


## AWS Glue Terminology


### AWS Glue Data Catalog

The persistent metadata store in AWS Glue. It contains table definitions, job definitions, and other control information to manage your AWS Glue environment. 

Each AWS account has one AWS Glue Data Catalog per region.

### Classifier

Determines the schema of your data. AWS Glue provides classifiers for common file types such as SCV, JSON, AVRO, XML and others.

It also provides classifiers for common relational database using JDBC connections.

You can write you own classifier.


### Connection

A Data Catalog object that contains the properties that are required to connect to a particular data store.


### Crawler

A program that connects to a data store either source or target. It progresses through a prioritized list of classifiers to determine the schema for your data, and then creates metadata tables in AWS Glue Data Catalog.


### Database

A set of associated Data Catalog table definitions organized into a logical group.


### Data Store, data source, data target

A *Data store* is a repository for persistently storing your data. 

A *Data Source* is data store that is used as input to a process or transform.

A *data target* is a data store that a process or transform writes to.

### Development endpoint

An environment that you can use to develop and test your AWS Glue ETL scripts.

### Dynamic Frame

A distributed table that supports nested data such as structures and arrays.

Each record is self-describing, designed for schema flexibility with semi structured data.

Each record contains both data and the schema that describes that data.

Dynamic frames provide a set of advanced trnasformations for data cleaning and ETL.


### Job

The business logic that is required to perform ETL work. It is composed of a transformation script, data sources, and data targets.

Job runs are initiated by triggers that can be scheduled or triggered by events.


### Notebook server

A web-based environment that you can use to run your PySpark statement. PySpark is a Python dialect for ETL programming.


### Script

Code that extracts data from sources, tranforms it, and loads it into targets. AWS Glue generates pySpark or Scala scripts.


### Table

The metadata definition that represents your data.

Whether your data is in an Amazon Simple Storage Service (Amazon S3) file, an Amazon Relational Database Service (Amazon RDS) table, or another set of data, a table defines the schema of your data.

A table in the AWS Glue Data Catalog consists of the names of columns, data type definitions, partition information, and other metadata about a base dataset.


### Transform

The code logic that is used to manipute your data into a different form.


### Trigger

Initiates an ETL job. Triggers can be defined based on a scheduled time or an event. 


---

## Why is AWS Glue so powerful?

Glue is powerful because it combines the speed and performance of apache Spark with the Data organization of Hive.

Glue has default time of two days.

AWS Glue will allow you to have faster data integration by reducing the time it takes to analyze your data. 

It will also automate your data integration tasks by crawling data sources, identifying data formats, and suggesting relevant schemas to store your data.

AWS Glue runs serverlessly. You can pay for the resources that are used while running a job.

A crawler essentially allows us to gather data from multiple data stores and then create one data table.

Combined with AWS Glue this can allow us to transform our data too. 


![](https://github.com/amarnadh19/books/blob/main/images/aws_glue1.png?)

An S3 bucket has an Excel Sheet file with business data to be analyzed. This is our source data store. We create a crawler to gather information so that AWS Glue can transform it into a different format. AWS Athena can then be used to perform analytics on the combined and newly formatted data.

