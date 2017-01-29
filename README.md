# Spark on Kudu - Up and Running

Spark on Kudu is well integrated and full of great features. Get up and
running quickly with this small sample code project.

This code base developed and validated on CDH 5.10.0 with Kudu 1.2.0 release.

# Building

Modify the Kudu master servers for your environment in the
`SparkKuduUpAndRunning.scala` source.

```scala
val master1 = "<changeme-kudu-master1>"
val master2 = "<changeme-kudu-master2>"
val master3 = "<changeme-kudu-master3>"
```

To build this sample code, run:

```sh
mvn clean package
```

# Running samples

The above build does not create an uber jar that will include all the kudu
client side Java and Spark libraries required. The jars will exist in your local
maven repository location right after building, however.

By default that location of these jars is under your `~/.m2` directory. Copy,
symlink, or simply include a direct path to the necessary jars with the `--jars`
option shown in the below `spark-submit` call.

For example, these are the jars we're looking for:

```
~/.m2/repository/org/apache/kudu/kudu-spark_2.10/1.2.0-cdh5.10.0/kudu-spark_2.10-1.2.0-cdh5.10.0.jar
~/.m2/repository/org/apache/kudu/kudu-client/1.2.0-cdh5.10.0/kudu-client-1.2.0-cdh5.10.0.jar
```

Assuming these are now found in the `lib` directory found in this project,
launch the job with:

```
spark-submit \
--class com.cloudera.examples.spark.kudu.SparkKuduUpAndRunning \
--master yarn-client \
--jars lib/kudu-spark_2.10-1.2.0-cdh5.10.0.jar,lib/kudu-client-1.2.0-cdh5.10.0.jar \
lib/spark-kudu-up-and-running-1.0.jar
```

We run in `yarn-client` mode simply so that we can see the output of the
`show()` calls in the terminal.
