

### Introduction

The purpose of this repo is to host kibana based visualizations which are based on the moloch (molo.ch) schema in elasticsearch.

Moloch is an open source platform for ingesting pcaps, parsing the packets, possibly summarizing related packets into a "session" and then publishing this "session" data to elasticsearch.   Moloch has defined a schema which maps a number of specific packet attributes into a corresponsing elastic fields.  Moloch also has the ability to summarize individual packet attributes into more aggregate information that is then written to elastic via additional elastic field.

#### What is kibana?

Kibana is the web UI to the "ELK" stack.  As such, kibana can natively access data in elastic.  Further, kibana has a number of predefined visualization types (line graphs, heatmaps, etc.) which can easily be created to visualize the data in moloch.  

The picture below shows, in a simple form, session information based on the session's lastpacket timestamp.  

![](https://github.com/bf31415/moloch-kibana-examples/blob/master/Screen%20Shot%202019-09-04%20at%2008.34.03.png)

The above is conceptually the same info one sees on the session page:

![](https://github.com/bf31415/moloch-kibana-examples/blob/master/Screen%20Shot%202019-09-04%20at%2008.52.14.png)


#### H4 Why kibana?

The moloch platform does much of the heavy lifting- it provides a scaleable way to ingest pcaps and push key attributes of this data to elastic.   Kibana provides an easy way to create visualizations.  

The intent here is to combine these to capabilities, namely to provide a means for moloch users to either publish one or more of their kibana visualization's of moloch data or to use others published kibana visualizations for use in their ELK ecosystem.


### Examples

Suppose you wanted to see the traffic by source->destination IP for a number of different protocols.  Here's an example of showing that information in real-time via heatmaps:


![] https://github.com/bf31415/moloch-kibana-examples/blob/master/heatmap-example.png



#### What are the names of the moloch fields in elastic?

Go here: http://VIEWER-IP:8005/help#fields



