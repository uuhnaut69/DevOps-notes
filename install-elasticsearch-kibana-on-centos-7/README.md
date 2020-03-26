# Elasticsearch Manual Installation

1. Download

```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.8.1.rpm
```
```bash
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-6.8.1.rpm.sha512
```

2. Install repository

```bash
sudo rpm --install elasticsearch-6.8.1.rpm
```

3. Basic config

- Go to directory:

  ```bash
  cd /etc/elasticsearch
  ```
- Edit <span style='color:red'>elasticsearch.yml</span> via Vim or Nano
  
  - Find "network.host", delete "#" symbol, and set value to "0.0.0.0" 
  
  - Find "http.port", delete "#" symbol, and set value to "9200" . And save config file.
  
4. Enable port 9200 in order to make it public access, using "iptables -I INPUT -p tcp -m tcp --dport 9200 -j ACCEPT"

5. Save IP config

```bash
sudo iptables-save
```

# Kibana Manual Installation

1. Download

```bash
wget https://artifacts.elastic.co/downloads/kibana/kibana-6.8.1-x86_64.rpm
```
2. sudo rpm --install kibana-6.8.1-x86_64.rpm

3. Enable port 5601 in order to make it public access, using "iptables -I INPUT -p tcp -m tcp --dport 5601 -j ACCEPT"

4. Save IP config

```bash
sudo iptables-save
```

5. Enable kibana

```bash
sudo systemctl enable kibana
```

6. Start kibana

```bash
sudo systemctl start kibana
```
