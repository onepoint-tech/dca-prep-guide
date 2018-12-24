# Configure logging drivers

## Official Docker Documentation
[Configure logging drivers](https://docs.docker.com/engine/admin/logging/overview/)  

- none	: No logs are available for the container and docker logs does not return any output.
- json-file	: The logs are formatted as JSON. The default logging driver for Docker.
- syslog	: Writes logging messages to the syslog facility. The syslog daemon must be running on the host machine.
- journald	: Writes log messages to journald. The journald daemon must be running on the host machine.
- gelf		: Writes log messages to a Graylog Extended Log Format (GELF) endpoint such as Graylog or Logstash.
- fluentd	: Writes log messages to fluentd (forward input). The fluentd daemon must be running on the host machine.
- awslogs	: Writes log messages to Amazon CloudWatch Logs.
- splunk	: Writes log messages to splunk using the HTTP Event Collector.
- etwlogs	: Writes log messages as Event Tracing for Windows (ETW) events. Only available on Windows platforms.
- gcplogs	: Writes log messages to Google Cloud Platform (GCP) Logging.
- logentries : Writes log messages to Rapid7 Logentries.

## Official Docker success center
[Docker Logging Design and Best Practices](https://success.docker.com/article/logging-best-practices)

Docker supports different logging drivers used to store and/or stream container stdout and stderr logs of the main container process (pid 1). By default, Docker uses the **json-file** logging driver, but it can be configured to use many other drivers by setting the value of log-driver in ```/etc/docker/daemon.json``` followed by restarting the Docker daemon to reload its configuration.

The logging driver settings apply to ALL containers launched after reconfiguring the daemon (restarting existing containers after reconfiguring the logging driver does not result in containers using the updated config). To override the default container logging driver run the container with ```--log-driver``` and ```--log-opt options```. Swarm-mode services, on the other hand, can be updated to use a different logging driver on the go by using docker ```service update --log-driver <DRIVER_NAME> --log-opt <LIST OF OPTIONS> <SERVICE NAME>.```

Docker Engine logs handled by the default system manager logger. Usually **systemd**, which uses **journald** for logging and **journalctl** for accessing the logs. To access the Engine logs use ```journalctl -u docker.service```


