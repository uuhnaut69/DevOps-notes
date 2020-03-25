# Installation

1. Install s3 plugin

 ```bash
cd /usr/share/elasticsearch
sudo bin/elasticsearch-plugin install repository-s3
```

2. Add s3 credentials

```bash
bin/elasticsearch-keystore add s3.client.default.access_key
bin/elasticsearch-keystore add s3.client.default.secret_key
```

3. Reload security config

```bash
POST _nodes/reload_secure_settings
```

4. Start backup

```bash
PUT _snapshot/s3-snapshot
{
  "type": "s3",
  "settings": {
    "bucket": "s3-snapshot",
    "compress": true,
    "region": "us-east-1"
  }
}
```

5. Verify backup

```bash
POST /_snapshot/s3-snapshot/_verify
```

6. Back up kibana

```bash
PUT _snapshot/s3-snapshot/s3-kibana
{
  "indices": ".kibana",
  "include_global_state": false
}
```

7. Check backup

```bash
GET _snapshot/s3-snapshot/_all
```