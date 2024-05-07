# Running Elastic Stack Tools Using Docker Compose

## Contents

- [Elastic Stack Tools](#elastic-stack)
- [Compose Configuration](#compose)

## Elastic Stack <a name="elastic-stack"></a>

The Elastic tools used for this application:

- Elasticsearch
- Kibana
- Logstash
- Metricbeat
- Filebeat

`Elasticsearch` and `Kibana` starts from the `docker-compose.yml` file, while `Filebeat`, `Metricbeat`, and `Logstash` needs additional configuration from separate `yml` files.

### File Structure

```sh
├── .env
├── docker-compose.ymml
├── filebeat.yml
├── logstash.conf
└── metricbeat.yml
```

## Compose Configuration <a name="compose"></a>

As of 8.0, security is enabled by default. `setup-c` container is used here to make sure the certificate CA setup is established correctly. Having `security enabled` is a recommended practice and should not be disabled.

Build and run the application:

```sh
docker compose up --build
```

The `setup-c` container exits on purpose after it completes generating the certs and passwords.

Copy the `ca.crt` out of the `es01-c` container:

```sh
docker cp es01-c:/usr/share/elasticsearch/config/certs/ca/ca.crt /tmp/.
```

Output: `Successfully copied 3.07kB to /tmp/.`

Once the certificate is downloaded, run a curl command to query the `Elasticsearch node`:

```sh
curl --cacert /tmp/ca.crt -u elastic:Bucket-Sevenfold8-Residue https://localhost:9200
```

Output:

```sh
{
  "name" : "es01",
  "cluster_name" : "docker-cluster",
  "cluster_uuid" : "idRIZmHHSi6D8b3MEJNy7Q",
  "version" : {
    "number" : "8.7.1",
    "build_flavor" : "default",
    "build_type" : "docker",
    "build_hash" : "f229ed3f893a515d590d0f39b05f68913e2d9b53",
    "build_date" : "2023-04-27T04:33:42.127815583Z",
    "build_snapshot" : false,
    "lucene_version" : "9.5.0",
    "minimum_wire_compatibility_version" : "7.17.0",
    "minimum_index_compatibility_version" : "7.0.0"
  },
  "tagline" : "You Know, for Search"
}
```

The password `Bucket-Sevenfold8-Residue` comes from the value defined at `.env` file and used at `docker-compose.yml` file.

### Services

- setup
- es01
- kibana
- metricbeat
- filebeat
- logtstash

### Images

```sh
docker images
```

```sh

```

### Network

```sh
docker network ls
```

```sh

```

### Volumes

```sh
docker volume ls
```

```sh

```

### Containers

- setup-c
- es-c
- kibana-c
- metricbeat-c
- filebeat-c
- logstash-c

```sh
docker ps
```

```sh

```

```sh
docker ps -a
```

```sh

```
