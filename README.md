# Ubiquitous Giggle
The Ubiquitous Giggle repository offers a practical guide to building scalable microservices using Spring Boot and Spring Cloud. It covers essential topics such as design patterns, the 12-Factor App methodology, and resilience techniques like circuit breakers and retries. The project also emphasizes monitoring and logging, integrating tools like Prometheus, Grafana, and the ELK stack for centralized tracking and alerting. Additionally, it implements Load Balancing and Service Discovery, utilizing tools like Spring Cloud LoadBalancer and Eureka for seamless traffic distribution and dynamic service registration. <br><br>With boilerplate code provided, this repository serves as a starting point for implementing cloud-native, fault-tolerant, and maintainable microservices, making it an ideal resource for developers looking to master modern application architectures.



## Table of Contents

1. [Features](#features)
2. [Installation](#installation)
3. [Usage](#usage)
4. [Contributing](#contributing)
5. [Application Start](#application-start)
6. [Badges](#badges)

---
## Animation of Working Overview
<img src="docs/Crypto.gif" width="300"></img>

## Features

### 1. Config Server with Dynamic Reload
The project includes a **dedicated Config Server** that:
- Dynamically loads configuration properties without requiring a server restart.
- Supports **webhooks**, allowing instant updates to configuration values upon changes.

This ensures high availability and flexibility in managing application settings.

### 2. Eureka Server for Service Discovery
The **Eureka Server** provides:
- Centralized service registration and discovery.
- Seamless communication and scaling for microservices.

This simplifies service-to-service communication in distributed environments.

### 3. Gateway Server with Enhanced Security
A **Dedicated Gateway Server** is implemented, which:
- Acts as a single entry point for API requests.
- Includes **Spring Security** for robust authentication and authorization.
- Handles cross-cutting concerns like routing, rate-limiting, and monitoring.

### 4. Observability and Monitoring with Grafana-Labs Suite
For end-to-end observability, the project integrates:
- **Grafana Loki**: Log aggregation and querying.
- **Prometheus**: Metrics collection and alerting.
- **Promtail**: Log forwarding and processing.
- **Micrometer**: Application metrics instrumentation.
- **MinIO**:  High-performance, distributed object storage
- **Grafana Tempo**: Distributed tracing without the need for indexing
  This setup ensures comprehensive monitoring and troubleshooting capabilities.

This helps in tracing requests across microservices to identify and resolve performance bottlenecks.

## Installation

To get started with **Ubiquitous Giggle**, follow these steps:

1. Clone the repository:
   ```bash
   git clone https://github.com/okgaurav/ubiquitous-giggle.git
   ```

2. Navigate to the DockerEnv directory:
   ```bash
   cd DockerEnv/default
   ```

3. Start docker (it will install the required dependencies):
   ```bash
   docker compose up -d
   ```

## Usage

Once all services are up and running, follow the steps below to configure and utilize the Keycloak server:

### Accessing the Keycloak Server
Navigate to [localhost:7080](http://localhost:7080) to access the Keycloak server. Use the following default credentials to log in:
- **Username:** admin
- **Password:** admin

### Configuring Keycloak

1. **Create a Client:**
   - Define a new client and configure its credentials within the Keycloak server.

2. **Assign Permissions:**
   - Grant appropriate permissions for the microservices, namely **EXCHANGE** and **CRYPTO**.

3. **Authentication and Interaction:**
   - Use the generated client credentials in Postman to authenticate and interact with the services.


### Configuring the Grafana Dashboard

1. **Add a Data Source:**
   - Go to the "Configuration" section in the Grafana dashboard and select "Data Sources."
   - Click "Add data source" and configure the required connection settings (e.g., Prometheus, InfluxDB).

2. **Create and Customize Dashboards:**
   - Navigate to the "Dashboards" section and click "New Dashboard."
   - Add and customize visualization panels to display metrics, graphs, or logs specific to your application.

3. **Set Up Alerts:**
   - Define alerts for critical metrics by setting thresholds in the visualization panels.
   - Specify notification channels (e.g., email, Slack) to receive alerts promptly.

4. **Enable Dashboard Sharing:**
   - Use the "Share" option to generate a public link or export JSON files for sharing the dashboard with team members.

### Accessing the Grafana Dashboard
Navigate to [localhost:3000](http://localhost:3000) to access the Grafana dashboard.


### Best Practices

- **Monitor Regularly:** Ensure panels are updated with relevant metrics for effective monitoring.
- **Organize Effectively:** Use folders to manage and categorize dashboards based on their purpose or team.
- **Backup Dashboards:** Export dashboard configurations periodically to prevent data loss during migrations or updates.


## Contributing

We welcome contributions to **Ubiquitous Giggle**! To contribute:

1. Fork the repository.
2. Create a new branch for your feature or bug fix:
   ```bash
   git checkout -b feature-name
   ```
3. Commit your changes:
   ```bash
   git commit -m "Add feature"
   ```
4. Push your branch:
   ```bash
   git push origin feature-name
   ```
5. Open a pull request.

Please ensure your code follows our coding standards and includes tests where applicable.

## Application Start
1. Use curl to hit a request through gateway server
```bash
curl --request POST \
  --url http://localhost:8072/service/crypto/v1/api/bts \
  --header 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCIgOiAiSldUIiwia2lkIiA6ICJwSXNXM1pzVWFjcG5MYWtPeWZWdGFWU2phVlljOHI2NWdRVGtMQ0Q2NzlJIn0.eyJleHAiOjE3MzM1NjI0ODUsImlhdCI6MTczMzU2MjQyNSwianRpIjoiZDNlMTRjNDItMjhjYi00ZDdhLWI3YTEtM2M2ZTcwOGE1N2ZlIiwiaXNzIjoiaHR0cDovL2xvY2FsaG9zdDo3MDgwL3JlYWxtcy9tYXN0ZXIiLCJhdWQiOiJhY2NvdW50Iiwic3ViIjoiY2RhM2FlMzktNDEwOS00ZmZlLTgzMTktYjlkOGFiNmExYmFkIiwidHlwIjoiQmVhcmVyIiwiYXpwIjoiY3J5cHRvLWNjIiwiYWNyIjoiMSIsImFsbG93ZWQtb3JpZ2lucyI6WyIvKiJdLCJyZWFsbV9hY2Nlc3MiOnsicm9sZXMiOlsiZGVmYXVsdC1yb2xlcy1tYXN0ZXIiLCJvZmZsaW5lX2FjY2VzcyIsInVtYV9hdXRob3JpemF0aW9uIl19LCJyZXNvdXJjZV9hY2Nlc3MiOnsiYWNjb3VudCI6eyJyb2xlcyI6WyJtYW5hZ2UtYWNjb3VudCIsIm1hbmFnZS1hY2NvdW50LWxpbmtzIiwidmlldy1wcm9maWxlIl19fSwic2NvcGUiOiJvcGVuaWQgZW1haWwgcHJvZmlsZSIsImNsaWVudEhvc3QiOiIxNzIuMTcuMC4xIiwiZW1haWxfdmVyaWZpZWQiOmZhbHNlLCJwcmVmZXJyZWRfdXNlcm5hbWUiOiJzZXJ2aWNlLWFjY291bnQtY3J5cHRvLWNjIiwiY2xpZW50QWRkcmVzcyI6IjE3Mi4xNy4wLjEiLCJjbGllZW50X2lkIjoiY3J5cHRvLWNjIn0.Dog6bWWtB3-oiV5daXaQ0L3hSesSRLUBnR4CJz3oJ_8XVIpu26XGrpAnJSk7SySJVKn4w5p01rYsJ_hYCAdf4GdBafVCYgc-0i_AlPjzyptgNpYbOfiULYSiBRucRmYBssd2pR9FYzicucx-OVQ6P-1kMPPkdz61Lu7-ad55ln83q65GCoV6u7SD2TscdOXbFMEqw_Rxk4NOPuysfygKzxh7rUIuUmYtRpN-sMs3h-bOPtPeFgCsE4enX6XSGGNLjqjp_Aslr7H2qxKKC3AknnMG8wtKictFSvd7hfpCpDFaAjcfCA5MFNezxxiNnU1DlrIpxx3jMr6XHvtNAOBuKg' \
  --data '{
  "startDate": "2024-01-01",
  "endDate": "2024-12-30",
  "targetCurrency": "USD",
}'

   ```
2. output would be like
```json
{
  "startDate": "2024-01-01",
  "endDate": "2024-12-30",
  "targetCurrency": "USD",
  "highestMarket": 150.75,
  "lowestMarket": 100.25
}
   ```
## Badges

[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://choosealicense.com/licenses/mit/)
[![GPLv3 License](https://img.shields.io/badge/License-GPL%20v3-yellow.svg)](https://opensource.org/licenses/)
[![AGPL License](https://img.shields.io/badge/license-AGPL-blue.svg)](http://www.gnu.org/licenses/agpl-3.0)

![Logo](docs/McDev.svg)