# Secure ELK Stacks

1. Go to directory

```bash
cd /etc/elasticsearch
```

2. Edit <span style='color:red'>elasticsearch.yml</span> via Vim or Nano .Add 2 following lines & save:

```bash
xpack.security.enabled: true
discovery.type: single-node
```

3. Restart elasticsearch

```bash
sudo systemctl restart elasticsearch
```

4. Go to directory

```bash
cd /usr/share/elasticsearch/
```

5. Run command to generate password auto for ELK stacks:

```bash
bin/elasticsearch-setup-passwords auto
```

Or to define password

```bash
bin/elasticsearch-setup-passwords interactive
```