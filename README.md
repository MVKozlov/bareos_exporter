## bareos_exporter
[![Go Report Card](https://goreportcard.com/badge/github.com/vierbergenlars/bareos_exporter)](https://goreportcard.com/report/github.com/vierbergenlars/bareos_exporter)

[Prometheus](https://github.com/prometheus) exporter for [bareos](https://github.com/bareos) data recovery system

### [`Dockerfile`](./Dockerfile)

### Usage with [docker](https://hub.docker.com/r/vierbergenlnars/bareos_exporter)
1. Create a file containing your mysql password and mount it inside `/bareos_exporter/pw/auth`
2. **(optional)** [Overwrite](https://docs.docker.com/engine/reference/run/#env-environment-variables) default args using ENV variables
3. Run docker image as follows
```bash
docker run --name bareos_exporter -p 9625:9625 -d vierbergenlars/bareos_exporter:latest -dsn mysql://user:password@host/dbname
```
### Metrics

- Total amout of bytes and files saved
- Latest executed job metrics (level, errors, execution time, bytes and files saved)
- Latest full job (level = F) metrics
- Amount of scheduled jobs

### Flags

Name    | Description                                                                                 | Default
--------|---------------------------------------------------------------------------------------------|----------------------
port    | Bareos exporter port                                                                        | 9625
endpoint| Bareos exporter endpoint.                                                                   | "/metrics"
dsn     | Data source name of the database that is used by bareos. Protocol can be `mysql://` or `postgresql://`. The rest of the string is passed to the database driver. | "mysql://bareos@unix()/bareos?parseTime=true"
