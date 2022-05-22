This tutorial demonstrates how to use Elasticsearch workspace to explore cluster and export index to S3. 

## Setup

Create `docker-compose.yaml` file to launch locally 3-node Elasticsearch cluster with Kibana 

```yaml
version: '2.2'
services:
  es01:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.16.3
    container_name: es01
    environment:
      - node.name=es01
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es02,es03
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data01:/usr/share/elasticsearch/data
    ports:
      - 9200:9200
    networks:
      - elastic

  es02:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.16.3
    container_name: es02
    environment:
      - node.name=es02
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es03
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data02:/usr/share/elasticsearch/data
    networks:
      - elastic

  es03:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.16.3
    container_name: es03
    environment:
      - node.name=es03
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es02
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data03:/usr/share/elasticsearch/data
    networks:
      - elastic

  kib01:
    image: docker.elastic.co/kibana/kibana:7.16.3
    container_name: kib01
    ports:
      - 5601:5601
    environment:
      ELASTICSEARCH_URL: http://es01:9200
      ELASTICSEARCH_HOSTS: '["http://es01:9200","http://es02:9200","http://es03:9200"]'
    networks:
      - elastic
  
  workspace:
    image: alnoda/elasticsearch-workspace
    container_name: workspace
    ports:
      - 8020-8030:8020-8030
    networks:
      - elastic

volumes:
  data01:
    driver: local
  data02:
    driver: local
  data03:
    driver: local

networks:
  elastic:
    driver: bridge
```

and start it with `docker-compose up`   

Wait untill the cluster is fully ready, open Kibana on [http://localhost:5601](/http://localhost:5601/) and import sample datasets.  

<p align="center">
  <img src="https://raw.githubusercontent.com/bluxmit/alnoda-workspaces/main/workspaces/elasticsearch-workspace/img/Kibana-sample.png" alt="Kibana" width="750">
</p>

Go to the workspace Quickstart page for quick access to all the workspace tools 

<p align="center">
  <img src="https://github.com/bluxmit/alnoda-workspaces/blob/main/workspaces/ide-workspace/img/wid-ui.png?raw=true" alt="WID demo" width="900">
</p>

## Check cluster

Open browser-based terminal and check cluster nodes and shards

```
vulcanizer --host es01 nodes
vulcanizer --host es01 shards
```

<p align="center">
  <img src="https://raw.githubusercontent.com/bluxmit/alnoda-workspaces/main/workspaces/elasticsearch-workspace/img/vulcanizer-demo.png" alt="vulcanizer" width="750">
</p>

## Create backup

Use elasticdump to export index `kibana_sample_data_ecommerce` (from eCommerce sample dataset) to S3 

```
elasticdump \
  --s3AccessKeyId "${access_key_id}" \
  --s3SecretAccessKey "${access_key_secret}" \
  --input=http://es01:9200/kibana_sample_data_ecommerce \
  --output "s3://${bucket_name}/kibana_sample_data_ecommerce.json"
```

<p align="center">
  <img src="https://raw.githubusercontent.com/bluxmit/alnoda-workspaces/main/workspaces/elasticsearch-workspace/img/elasticdump-demo.png" alt="elasticdump" width="750">
</p>

## Schedule

Open workspace IDE and create file `/home/project/export.sh` file with the script to export data to S3. 
Make it executable with `chmod +x /home/project/export.sh`. 

<p align="center">
  <img src="https://raw.githubusercontent.com/bluxmit/alnoda-workspaces/main/workspaces/elasticsearch-workspace/img/IDE-demo.png" alt="IDE" width="750">
</p>

Open workspace Scheduler (user/pass: admin/admin), 
and schedule script, for example weekly. Select category - "general", plugin - "Shell Script"

<p align="center">
  <img src="https://raw.githubusercontent.com/bluxmit/alnoda-workspaces/main/workspaces/elasticsearch-workspace/img/Cronicle-demo.png" alt="Cronicle" width="750">
</p>
