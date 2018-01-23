# MaxScale in Docker
Dockerized MariaDB MaxScale

## Run
You need to specify the addresses for DB1-DB3 as well as passwords for service and monitoring users:
```
docker run -e DB1_ADDRESS=127.0.0.1 -e DB2_ADDRESS=127.0.0.2 -e DB3_ADDRESS=127.0.0.3 -e SERVICE_PWD="SuperSecret1234" -e MONITOR_PWD="EvenMoreSecret" maxscale:2.1.1
```
## Configuration
Config is done through env vars. Following env vars are available

| Name                | Default value       | Description                         |
|---------------------|---------------------|-------------------------------------|
| THREADS             | 2                   | Thread count to run MaxScale        |
| SERVICE_USER        | maxscale            | Service user                        |
| SERVICE_PWD         | `None`              | Password for the service user       |
| READ_WRITE_PORT     | 3307                | Listen port for read7write service  |
| READ_WRITE_PROTOCOL | MySQLClient         | Protocol for read/write service     |
| MASTER_ONLY_PORT    | 3306                | Listen port for master only service |
| MONITOR_USER        | maxscale            | Monitoring user                     |
| MONITOR_PWD         | `None`              | Password for the monitoring user    |
| CLI_ADDR            | localhost           | Listen address for the CLI          |
| CLI_PORT            | 6603                | Listen port for the CLI             |
| DB1_ADDRESS         | `None`              | Address for backend DB1             |
| DB1_PORT            | 3306                | Port for backend DB1                |
| DB1_PRIO            | 1                   | Priority for backend DB1            |
| DB2_ADDRESS         | `None`              | Address for backend DB2             |
| DB2_PORT            | 3306                | Port for backend DB2                |
| DB2_PRIO            | 2                   | Priority for backend DB2            |
| DB3_ADDRESS         | `None`              | Address for backend DB3             |
| DB3_PORT            | 3306                | Port for backend DB3                |
| DB3_PRIO            | 3                   | Priority for bakcend DB3            |

To use a complete custom config, mount a config file:
```docker run -v /home/customfile.cnf:/etc/maxscale.cnf maxscale:2.1.1```
