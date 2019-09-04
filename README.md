

### Introduction

The purpose of this repo is to host kibana based visualizations which are based on the moloch (molo.ch) schema in elasticsearch.

Moloch is an open source platform for ingesting pcaps, parsing the packets, possibly summarizing related packets into a "session" and then publishing this "session" data to elasticsearch.   Moloch has defined a schema which maps a number of specific packet attributes into a corresponsing elastic fields.  Moloch also has the ability to summarize individual packet attributes into more aggregate information that is then written to elastic via additional elastic field.

#### What is kibana?

Kibana is the web UI to the "ELK" stack.  As such, kibana can natively access data in elastic.  Further, kibana has a number of predefined visualization types (line graphs, heatmaps, etc.) which can easily be created to visualize the data in moloch.  

The picture below shows, in a simple form, session information based on the session's lastpacket timestamp.  

![](https://github.com/bf31415/moloch-kibana-examples/blob/master/Screen%20Shot%202019-09-04%20at%2008.34.03.png)

The above is conceptually the same info one sees on the session page:

![](https://github.com/bf31415/moloch-kibana-examples/blob/master/Screen%20Shot%202019-09-04%20at%2008.52.14.png)


#### Why kibana?

The moloch platform does much of the heavy lifting- it provides a scaleable way to ingest pcaps and push key attributes of this data to elastic.   Kibana provides an easy way to create visualizations.  

The intent here is to combine these to capabilities, namely to provide a means for moloch users to either publish one or more of their kibana visualization's of moloch data or to use others published kibana visualizations for use in their ELK ecosystem.


### Examples

Suppose you wanted to see the traffic by source->destination IP for a number of different protocols.  Here's an example of showing that information in real-time via heatmaps:


![](https://github.com/bf31415/moloch-kibana-examples/blob/master/heatmap-example.png)

The above heatmap is defined in [here]:https://github.com/bf31415/moloch-kibana-examples/blob/master/examples/dashboard-heatmap-example.ndjson


### How do I get info into my kibana?

The steps to important a visualization or dashboard is as follows:

* For the target visualization, download the code to your local system.  You can do this with git clone or simply copy the contents and storing them into a file locally.  note that the filename might need top end in ".ndjson" for kibana to accept it.
* in kibana, select the management icon.  On the left side of the kibana page, look for the gear shaped object-- likely the last icon on the column.  if you hover over it, "management" will appear.  select this button.
* On the subsequent page, look for the Kibana section and under that look for saved objects.  select that.
* you should now be at the saved objects page.  select import.
* on the pop-up, select import again
* then select the local file with the target visualization.
* if that step is successful, you should then be able to select import (at bottom) 




#### What are the names of the moloch fields in elastic?

Go here: http://VIEWER-IP:8005/help#fields



