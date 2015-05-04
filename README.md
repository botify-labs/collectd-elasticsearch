elasticsearch-collectd-plugin
=====================

A [ElasticSearch](http://elasticsearch.org) plugin for [collectd](http://collectd.org) using collectd's [Python plugin](http://collectd.org/documentation/manpages/collectd-python.5.shtml).

Common Stats :
 * Docs (Total docs & Deleted docs)
 * Store size
 * Indexing (Total, time, Total delete, Delete time)
 * Get (Total, Time, Exists otal, Exists time, Missing total, Missing Time)
 * Search (Total query, total time, total fetch, total fetch time)
 * JVM Memory (Heap commited, Heap Used, Non heap commited, Non heap used)
 * JVM Threads (Count & Peak)
 * JVM GC (Time & Count)
 * Transport stats (Server open, RX count, RX size, TX count, TX size)
 * HTTP Stats (Current open & Total open)

ES 1.0 Stats :
 * Cache (Field Eviction, Field Size, Filter evictions, Filter size)
 * JVM Collectors
 * FLush (Total count, total time)
 * Merges (Current count, current docs, current size, Merge total size, docs a time)
 * Refresh (Total & Time)

ES Index Stats :
 * docs The number of docs / deleted docs (docs not yet merged out).  Note, affected by refreshing the index. Also, docs.count here include the count of nested documents. So if you have a single document with 2 associated nested documents, the index’s docs.count will show 3.
 * store The size of the index.
 * indexing Indexing statistics, can be combined with a comma separated list of types to provide document type level stats.
 * get Get statistics, including missing stats.
 * search Search statistics. You can include statistics for custom groups by adding an extra groups parameter (search operations can be associated with one or more groups). The groups parameter accepts a comma separated list of group names. Use _all to return statistics for all groups.
 * warmer Warmer statistics.
 * merge Merge statistics.
 * fielddata Fielddata statistics.
 * flush Flush statistics.
 * completion Completion suggest statistics.
 * refresh Refresh statistics.
 * suggest Suggest statistics.

Install
-------
 1. Place elasticsearch_collectd.py in /opt/collectd/lib/collectd/plugins/python (assuming you have collectd installed to /opt/collectd).
 2. Configure the plugin (see below).
 3. Restart collectd.

Configuration
-------------
 * _Verbose_             boolean (default: false) -  enable verbose logging from the plugin.
 * _Host_                string (default: "localhost") - the hostname of the elasticsearch server to query for metrics.
 * _Port_                integer (default: 9200) - the elasticsearch port number.
 * _Cluster_             string (default: "elasticsearch") - the elasticsearch cluster name to use.
 * _Indexes_             array  (default: [ ]) - A comma seperated list of strings.  The string contains the index to collect statistics from.
 * _EnableIndexStats_    boolean (default:false) - enable statistics for indexes in the cluster.
 * _EnableNodeStats_     boolean (default:true) - enable statistics for the nodes in the cluster.
 * See elasticsearch.conf as an example of the syntax.

Requirements
------------
 * collectd 4.9+
 * Elasticsearch 0.9.x or 1.X
