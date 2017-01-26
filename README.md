# Spark on Kudu - Up and Running

Spark on Kudu is well integrated and full of great features. Get up and
running quickly with this small sample code project.

This code base developed and validated on CDH 5.7.5 with Kudu 1.1.0 release.

# Building

To build this sample code, run:

```sh
mvn clean package
```

# Running samples

After building the examples, run:

```sh
spark-submit \
--class com.cloudera.examples.spark.kudu.SparkKuduUpAndRunning \
--master yarn-client \
--jars jars/kudu-client-1.1.0.jar,jars/kudu-spark_2.10-1.1.0.jar \
target/spark-kudu-up-and-running-1.0.jar
```

We run in `yarn-client` mode simply so that we can see the output of the
`show()` calls in the terminal.

