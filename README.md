# app-docker-package
![app-docker-compose](https://github.com/abdeltif-b/app-docker-package/assets/60190704/84d6410f-67f9-43cc-8d61-45fb4625c16c)

This repository hosts the Docker Compose configuration for a comprehensive application featuring multiple services designed to serve diverse functionalities. It primarily serves as a template and is not meant for external user deployment. The core services (t3 and functions) are linked to private GitHub repositories.


## Services
### Main App Services
- **PostgreSQL Database (db)**: This service provides a PostgreSQL database for data storage and retrieval, crucial for the application's data management.
- **Keycloak (keycloak)**: Keycloak is an open-source identity and access management solution. This service likely handles user authentication, authorization, and security aspects of the application.
- **Next.js Application (t3)**: A Next.js-based web application responsible for the frontend user interface as well as the main backend of the application. It serves the user interface and interacts with the backend services.
- **FastAPI Application (functions)**: A FastAPI-based application that serves as the backend for the application, providing API endpoints and business logic, used to handle some batch computing and heavy calculations.
- **PostgreSQL Backup (pgbackups)**: This service handles backup and data recovery for the PostgreSQL database, ensuring data safety and disaster recovery.
### Grafana / Prometheus Related Services
- **Grafana (grafana)**: Grafana is a monitoring and observability platform. This service provides a dashboard for monitoring various aspects of the application and underlying infrastructure.
- **Loki (loki)**: Loki is a log aggregation system. This service collects and stores application logs, making them available for analysis and monitoring.
- **Promtail (promtail)**: Promtail is an agent for collecting logs and forwarding them to Loki. It helps in collecting and forwarding application and container logs to Loki.
- **Prometheus (prometheus)**: Prometheus is an open-source monitoring and alerting toolkit. This service collects metrics and data from various parts of the application and infrastructure for monitoring and alerting purposes.
- **PostgreSQL Exporter (postgres-exporter)**: This service exports PostgreSQL-specific metrics and data for Prometheus to monitor and analyze the PostgreSQL database's performance.
- **Node Exporter (node-exporter)**: Node Exporter is used to collect system-level metrics from the host machine or server where the services are running. It provides insights into the host's resource usage.

## Usage
To deploy the entire application stack, use the provided Docker Compose file. Make sure you have Docker and Docker Compose installed on your system. Run the following command in the root directory of this repository:
```
docker-compose up -d
```
This will start all the defined services in detached mode. For more details and specific configurations, refer to the respective service's documentation.

## Environment Variables
For environment-specific configurations, update the required environment variable files, e.g., `db.env`, `keycloak.env`, `t3.env`, etc., and reference them in the service configurations.

## Configuration files
- **prometheus.yml**: This is a configuration file for setting up and configuring Prometheus. It includes scrape and alerting configurations as well as the Rule Files (`node_alerts.yaml`, `node_rules.yaml`, `postgres_exporter_alerts.yaml`).
- **promtail-config.yaml**: This is a separated configuration file for setting up and configuring Prometheus, specifying how Prometheus should scrape and collect metrics from containers managed by Docker.
- **datasources.yml**: A configuration file for Grafana setup. It defines data sources that Grafana can connect to for fetching metrics and logs.

