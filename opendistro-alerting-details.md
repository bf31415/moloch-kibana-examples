
# Alerting via Kibana UI

The OpenDistro open source [repository](https://opendistro.github.io/for-elasticsearch/) provides a way to provide alerting of elastic data by defining alerts, monitors and triggers via the Kibana UI.  

The alerting plugins are version specific-- one needs to run elastic 7.1.1 and kibana as thats the latest code the pluggins will support.  While Moloch supports elastic 7, testing has been on elastic 7.3.

There are two alerting plugs require for alerting support in the Kibana UI-- one for elastic and one for kibana.  The details below provide step-by-step instructions for installing and getting kibana alerts working.

# Install steps

1. Install the elastic and kibana 7.1.1 code.

```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.1.1-amd64.deb
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.1.1-amd64.deb.sha512
shasum -a 512 -c elasticsearch-7.1.1-amd64.deb.sha512
sudo dpkg -i elasticsearch-7.1.1-amd64.deb

wget https://artifacts.elastic.co/downloads/kibana/kibana-7.1.1-amd64.deb
wget https://artifacts.elastic.co/downloads/kibana/kibana-7.1.1-amd64.deb.sha512
shasum -a 512 -c kibana-7.1.1-amd64.deb.sha512
sudo dpkg -i kibana-7.1.1-amd64.deb
```

Restarting elastic and kibana probably couldn't hurt at this point:

```
sudo systemctl start elasticsearch
sudo systemctl start kibana.service
```

If you want to check that you're running the 7.1.1 code then do the following:

```
curl http://ELASTIC-IP:9200/
{
  "name" : "moloch-dev-opendistro",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "8UWHflJvQ8qmywAf2WSwyA",
  "version" : {
    "number" : "__7.1.1__",
    "build_flavor" : "default",
    "build_type" : "deb",
    "build_hash" : "7a013de",
    "build_date" : "2019-05-23T14:04:00.380842Z",
    "build_snapshot" : false,
    "lucene_version" : "8.0.0",
    "minimum_wire_compatibility_version" : "6.8.0",
    "minimum_index_compatibility_version" : "6.0.0-beta1"
  },
  "tagline" : "You Know, for Search"
}


sudo /usr/share/kibana/bin/kibana --version
__7.1.1__
```

Install the elastic plugin:

```
sudo bin/elasticsearch-plugin install https://d3g5vo6xdbdb9a.cloudfront.net/downloads/elasticsearch-plugins/opendistro-alerting/opendistro_alerting-1.1.0.0.zip
```

Now install the kibana plugin:

```
sudo /usr/share/kibana/bin/kibana-plugin install https://d3g5vo6xdbdb9a.cloudfront.net/downloads/kibana-plugins/opendistro-alerting/opendistro-alerting-1.1.0.0.zip
```

To confirm the plugins are installed do the following:

```
/usr/share/elasticsearch/bin/elasticsearch-plugin list
opendistro_alerting

/usr/share/kibana/bin/kibana-plugin  list
opendistro-alerting@1.1.0.0
```

If all looks good, then you should be able to go to Kibana UI (http://kibana-ip:5601) and see on the left side the set of main action icons an "A" with a circle around it.

# Configuring alerts

No need to recreate these details already defined on the opendistro site- visit [this](https://opendistro.github.io/for-elasticsearch-docs/docs/alerting/)  page and the links at the bottom for details on how to configure alerts. 







