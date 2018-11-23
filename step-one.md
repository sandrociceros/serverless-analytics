# Step 1: Upload a dataset to Amazon S3
The first step towards building this demo allows you to find and upload a publically available dataset to your private bucket. This bucket will serve as a data lake where you can ingest data coming from different sources e.g. structured or unstructured data coming from your real world applications in different formats e.g. json, csv, avro, parquet etc. in either compressed e.g. gzip, snappy etc. or uncompressed state. In this demo, we will use a single csv file (~750MB) that we'll source from a public dataset hosted on S3.

## 1.1: Finding a dataset
Data of trips taken by taxis and for-hire vehicles in New York City.
https://registry.opendata.aws/nyc-tlc-trip-records-pds/

The yellow and green taxi trip records include fields capturing pick-up and drop-off dates/times, pick-up and drop-off locations, trip distances, itemized fares, rate types, payment types, and driver-reported passenger counts. The data used in the attached datasets were collected and provided to the NYC Taxi and Limousine Commission (TLC) by technology providers authorized under the Taxicab & Livery Passenger Enhancement Programs (TPEP/LPEP). The  trip data was not created by the TLC, and TLC makes no representations as to the accuracy of these data.

## 1.2: Listing the data
The public dataset is uploaded in a public S3 bucket here:
```
s3://nyc-tlc
```
I used a Mac for this project and on the terminal window, I executed the following command to list all the contents of the S3 bucket. Please note, you will be able to execute the following command only if AWS CLI is installed and configured on your laptop (see appendix for details)
```
$ aws s3 ls "s3://nyc-tlc/trip data/" --summarize --human-readable

```
## 1.3: Uploading the data to your own private S3 bucket
After listing all the contents and understanding the folder structure, I decided to use the data available for November 2018 by uploading it to my private S3 bucket. The following command allowed me to copy the contents over to my bucket directly from the source bucket
```
$ aws s3 cp "s3://nyc-tlc/trip data/yellow_tripdata_2018-06.csv" s3://s6r8/ds-csv/nyc-tlc/
```

[<< Back](/README.md)