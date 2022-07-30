Elastic Stack
==============

- Elasticsearch is a distributed document store. Instead of storing information as rows of columnar data, Elasticsearch stores complex data structures that have been serialized as JSON documents.
- Elasticsearch uses a data structure called an inverted index that supports very fast full-text searches.
- By default, Elasticsearch indexes all data in every field and each indexed field has a dedicated, optimized data structure. The ability to use the **per-field** data structures to assemble and return search results is what makes Elasticsearch so fast.
- **Elasticsearch** is the heart of the Elastic Stack, meaning that the technologies in the Elastic stack generally interact with Elasticsearch
- **Kibana** is an analytics and visualization platform, which lets you easily visualize data from Elasticsearch and analyze it to make sense of it. Basically just sends queries using the same REST API

- **Logstash** has been used to process logs from applications and send them to Elasticsearch, but Logstash has evolved into a more general purpose tool, meaning that Logstash is **a data processing pipeline**. 
  
  * The data that Logstash receives, will be **handled as events**, which can be anything of your choice. They could be log file entries, ecommerce orders, customers, chat messages, etc. 
  * These events are then processed by Logstash and shipped off to one or more destinations. A couple of examples could be Elasticsearch, a Kafka queue, an e-mail message, or to an HTTP endpoint. 
  * **A Logstash pipeline consists of three parts - or stages -** ``inputs``, ``filters``, and ``outputs``. Each stage can make use of a so-called plugin. An input plugin could be a file, for instance, meaning that Logstash will read events from a given file. 
  * It could also be that we are sending events to Logstash over HTTP, or we could look up rows from a relational database, or listen to a Kafka queue. There are a lot of input plugins, so chances are that you will find what you need. filter plugins are all about how Logstash should process them. Here we can parse CSV, XML, or JSON, for instance. We can also do data enrichment, such as looking up an IP address and resolving its geographical location, or look up data in a relational database. An output plugin is where we send the processed events to. Formally, those places are called stashes.
  * So in a nutshell, Logstash receives events from one or more inputs, processes them, and sends them to one or more stashes. 
  * You can have multiple pipelines running within the same Logstash instance.
  * Logstash is horizontally scalable. 
  * A Logstash pipeline is defined in a proprietary markup format that is similar to JSON.


- Installation: Docker.

  * ``docker pull docker.elastic.co/elasticsearch/elasticsearch:8.3.2``
  * ``docker network create elastic``
  * ``docker run --name es01 --net elastic -p 9200:9200 -p 9300:9300 -it docker.elastic.co/elasticsearch/elasticsearch:8.3.2``
  * ``DOCKER exec -it es01 /USR/SHARE/ELASTICSEARCH/BIN/ELASTICSEARCH-RESET-PASSWORD``
  * Verify: ``curl --cacert http_ca.crt -u elastic https://localhost:9200``

- Sending queries with ``cURL``

  * use ``https``
  * ``docker exec -it es01 curl -k -u elastic:<password> -X GET -H "Content-Type:application/json" [https://...]``
  * copy http_ca: ``docker cp <container-name>:/usr/share/elasticsearch/config/certs/http_ca.crt .`` 