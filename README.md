<p align="center"><a href="http://geomesa.github.io"><img align="center" width="50%" src="https://raw.githubusercontent.com/geomesa/geomesa.github.io/master/img/geomesa-2x.png"></img></a>
<br/>
<img align="center" height="150px" src="http://www.geomesa.org/img/geomesa-overview-848x250.png"></img>
</p>

GeoMesa is an open-source, distributed, spatio-temporal database built on top of the Apache Accumulo column family store. GeoMesa implements standard Geotools interfaces to provide geospatial functionality over very large data sets to application developers.  GeoMesa provides plugins for exposing geospatial data stored in Accumulo via standards-based OGC HTTP services and cluster monitoring and management tools within the GeoServer administrative interface.  
<a href="https://gitter.im/locationtech/geomesa?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge" target="_blank"><img src="https://badges.gitter.im/Join%20Chat.svg" alt="Join the chat at https://gitter.im/locationtech/geomesa"></img></a>

#### ![LocationTech](https://pbs.twimg.com/profile_images/2552421256/hv2oas84tv7n3maianiq_normal.png) GeoMesa is a member of the [LocationTech](http://www.locationtech.org) working group of the Eclipse Foundation.

## Versions and Downloads

**Latest 1.3 milestone**: 1.3.0-m0
* [![Build Status](https://api.travis-ci.org/locationtech/geomesa.svg?branch=geomesa-1.3.0-m0_2.11)](https://travis-ci.org/locationtech/geomesa) 
* [Accumulo Release tarball](https://repo.locationtech.org/content/repositories/geomesa-releases/org/locationtech/geomesa/geomesa-accumulo/geomesa-accumulo-dist/1.3.0-m0/geomesa-accumulo_2.11-1.3.0-m0-bin.tar.gz)
* [Kafka08 Release tarball](https://repo.locationtech.org/content/repositories/geomesa-releases/org/locationtech/geomesa/geomesa-kafka/geomesa-kafka-dist/geomesa-kafka-08-dist/1.3.0-m0/geomesa-kafka-08_2.11-1.3.0-m0-bin.tar.gz)
* [Source](https://github.com/locationtech/geomesa/archive/geomesa-1.3.0-m0.tar.gz)

**Development version (source only)**: 1.3.0-m1-SNAPSHOT
* [![Build Status](https://api.travis-ci.org/locationtech/geomesa.svg?branch=master)](https://travis-ci.org/locationtech/geomesa)
* [Source](https://github.com/locationtech/geomesa/archive/master.tar.gz)

**Latest 1.2 release**: 1.2.6 
* [![Build Status](https://api.travis-ci.org/locationtech/geomesa.svg?branch=geomesa-1.2.6)](https://travis-ci.org/locationtech/geomesa) 
* [Release tarball](https://repo.locationtech.org/content/repositories/geomesa-releases/org/locationtech/geomesa/geomesa-dist/1.2.6/geomesa-dist-1.2.6-bin.tar.gz)
* [Source](https://github.com/locationtech/geomesa/archive/geomesa-1.2.6.tar.gz)

**1.1.x release**: geomesa-1.1.0-rc.7 
* [![Build Status](https://travis-ci.org/locationtech/geomesa.svg?branch=geomesa-1.1.0-rc.7)](https://travis-ci.org/locationtech/geomesa)
* [Release tarball](https://repo.locationtech.org/content/repositories/geomesa-releases/org/locationtech/geomesa/geomesa-assemble/1.1.0-rc.7/geomesa-assemble-1.1.0-rc.7-bin.tar.gz)
* [Source](https://github.com/locationtech/geomesa/archive/geomesa-1.1.0-rc.7.tar.gz)

<b>NOTE:</b> The current recommended version is `1.2.6`. The most recent tar.gz assembly can be 
[downloaded here](https://repo.locationtech.org/content/repositories/geomesa-releases/org/locationtech/geomesa/geomesa-dist/1.2.6/geomesa-dist-1.2.6-bin.tar.gz) 
which contains the [Accumulo distributed runtime jar](geomesa-accumulo/geomesa-accumulo-distributed-runtime), [Accumulo GeoServer plugin](geomesa-gs-plugin/geomesa-accumulo-gs-plugin), and [command line tools](geomesa-tools).

GeoMesa artifacts can be downloaded from the [LocationTech Maven repository](https://repo.locationtech.org/content/repositories/geomesa-releases/)

Snapshots are available in the [LocationTech Snapshots Repository](https://repo.locationtech.org/content/repositories/geomesa-snapshots/)

### Upgrading

To upgrade between minor releases of GeoMesa, the versions of all GeoMesa components **must** match. 

This means that the version of the `geomesa-accumulo-distributed-runtime` JAR installed on Accumulo tablet servers **must** match the version of the `geomesa-accumulo-gs-plugin` JAR installed in the WEB-INF/lib directory of GeoServer.

## Maven Integration

GeoMesa artifacts are published to the LocationTech Maven repository. To include GeoMesa in your project,
add the following repositories to your pom:

```xml
<repositories>
  <repository>
    <id>locationtech-releases</id>
    <url>https://repo.locationtech.org/content/groups/releases</url>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
  </repository>
  <repository>
    <id>geomesa-snapshots</id>
    <url>https://repo.locationtech.org/content/repositories/geomesa-snapshots</url>
    <releases>
      <enabled>false</enabled>
    </releases>
    <snapshots>
      <enabled>true</enabled>
    </snapshots>
  </repository>
  <repository>
    <id>boundlessgeo</id>
    <url>http://repo.boundlessgeo.com/main</url>
  </repository>
  <repository>
    <id>osgeo</id>
    <url>http://download.osgeo.org/webdav/geotools</url>
  </repository>
  <repository>
    <id>conjars.org</id>
    <url>http://conjars.org/repo</url>
  </repository>
</repositories>
```

## Building from Source

Requirements:

* [Java JDK 8](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
* [Apache Maven](http://maven.apache.org/) 3.2.2 or later
* [git](http://git-scm.com/)
* [Accumulo](http://accumulo.apache.org) version 1.5.x or 1.6.x and/or [Kafka](http://kafka.apache.org/) version 0.8.2.x.

Navigate to where you would like to download this project.

    git clone git@github.com:locationtech/geomesa.git
    cd geomesa

The project is managed by Maven. The version of Accumulo supported is controlled by the `accumulo-1.5` property; to target Accumulo 1.5:   

    mvn clean install -Daccumulo-1.5

If the property is omitted, support for Accumulo 1.6 is assumed:

    mvn clean install

The `build/mvn` script is a wrapper around Maven that builds the project using the [Zinc](https://github.com/typesafehub/zinc) incremental compiler:

    build/mvn clean install -Daccumulo-1.5  # Accumulo 1.5
    build/mvn clean install                 # Accumulo 1.6

From the root directory, the commands above will build JARs for each sub-project with its additional dependencies bundled.


## Documentation

* [Quick Start](http://www.geomesa.org/geomesa-quickstart/) on the main [documentation](http://www.geomesa.org/) site.
* [FAQ](http://www.geomesa.org/faq/)
* [Tutorials](http://www.geomesa.org/tutorials/)
* GeoMesa [Users](https://locationtech.org/mhonarc/lists/geomesa-users/) and [Dev](https://locationtech.org/mhonarc/lists/geomesa-dev/) mailing list archives
* READMEs are provided under most modules: [Tools](geomesa-tools), [Jobs](geomesa-jobs), etc

## GeoMesa Project Structure

* [**geomesa-accumulo**](geomesa-accumulo/geomesa-accumulo-datastore): the implementations of the core Accumulo indexing structures, Accumulo iterators, and the GeoTools interfaces for exposing the functionality as a `DataStore` to both application developers and GeoServer. Assembles a jar with dependencies that must be distributed to Accumulo tablet servers lib/ext directory or to an HDFS directory where Accumulo's VFSClassLoader can pick it up.
* [**geomesa-blobstore**](geomesa-blobstore): an Accumulo-based store  designed to store and retrieve files which have spatio-temporal data associated with them. 
* [**geomesa-compute**](geomesa-compute): utilities for working with distributed computing environments. Currently, there are methods for instantiating an Apache Spark Resilient Distributed Dataset from a CQL query against data stored in GeoMesa. Eventually, this project will contain bindings for traditional map-reduce processing, Scalding, and other environments.
* [**geomesa-convert**](geomesa-convert): a configurable and extensible library for converting data into SimpleFeatures.
* **geomesa-dist**: packages the GeoMesa distributed runtimes, GeoMesa GeoServer plugins, and GeoMesa Tools.
* **geomesa-features**: includes code for serializing SimpleFeatures and custom SimpleFeature implementations designed for GeoMesa.
* **geomesa-filter**: a library for manipulating and working with GeoTools Filters.
* **geomesa-gs-plugin**: packages plugins which provide WFS and WMS support for various `DataStore` types including [**accumulo**](geomesa-gs-plugin/geomesa-accumulo-gs-plugin), bigtable, kafka, and stream DataStores. These are packaged as zip files and can be deployed in GeoServer by extracting their contents into geoserver/WEB-INF/lib/
* **geomesa-hbase**: an implementation of GeoMesa on Apache HBase and Google Cloud Bigtable.
* [**geomesa-jobs**](geomesa-jobs): map/reduce and scalding jobs for maintaining GeoMesa.
* [**geomesa-kafka**](geomesa-kafka/geomesa-kafka-datastore): an implementation of GeoMesa in Kafka for maintaining near-real-time caches of streaming data.
* [**geomesa-process**](geomesa-process): analytic processes optimized on GeoMesa data stores.
* [**geomesa-raster**](geomesa-raster): adds support for ingesting and working with geospatially-referenced raster data in GeoMesa.
* **geomesa-security**: adds support for managing security and authorization levels for data stored in GeoMesa. 
* [**geomesa-stream**](geomesa-stream): a GeoMesa library that provides tools to process streams of `SimpleFeatures`.
* [**geomesa-tools**](geomesa-tools): a set of command line tools for managing features, ingesting and exporting data, configuring tables, and explaining queries in GeoMesa.
* [**geomesa-utils**](geomesa-utils): stores our GeoHash implementation and other general library functions unrelated to Accumulo. This sub-project contains any helper tools for geomesa. Some of these tools such as the GeneralShapefileIngest have Map/Reduce components, so the geomesa-utils JAR lives on HDFS.
* **geomesa-web**: web services for accessing GeoMesa.
* **geomesa-z3**: the implementation of Z3, GeoMesa's space-filling Z-order curve.

## Scala console via scala-maven-plugin

To test and interact with core functionality, the Scala console can be invoked in a couple of ways.  From the root directory by specifying geomesa-accumulo-datastore 

    cd geomesa-accumulo
    mvn -pl geomesa-accumulo-datastore scala:console

By default, all of the project packages in `geomesa-accumulo-datastore` are loaded along with JavaConversions, JavaConverters.
