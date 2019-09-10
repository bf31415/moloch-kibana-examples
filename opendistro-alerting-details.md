
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

Install the elastic plugin

Now install the kibana plugin:

```
sudo /usr/share/kibana/bin/kibana-plugin install https://d3g5vo6xdbdb9a.cloudfront.net/downloads/kibana-plugins/opendistro-alerting/opendistro-alerting-1.1.0.0.zip
```
