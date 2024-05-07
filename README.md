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

As of 8.0, security is enabled by default. `setup` container is used here to make sure the certificate CA setup is established correctly. Having `security enabled` is a recommended practice and should not be disabled.

Build and run the application:

```sh
docker compose up --build
```

### Services

- setup
- es
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
