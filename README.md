
# 📚  Observability

Observability Series! This repository contains the code and detailed explanations for setting up and understanding observability in Kubernetes using Prometheus, Grafana, Elasticsearch Fluentbit, Kibana, Jaeger, groundcover(eBPF), opentelemetry e.t.c.,.

## 📅 Overview of Each Day

### Day 1: Introduction to Observability
- **Concepts Covered**:
  - Introduction to Observability, Monitoring, Logging, and Tracing.
  - The difference between Monitoring and Observability.
  - Tools available for Monitoring and Observability.
  - Comparison between monitoring and observing in Bare-Metal Servers vs. Kubernetes.
- **Key Learning**:
  - Understand the fundamental concepts of observability.
  - Learn why monitoring and observability are crucial in modern IT environments.

### Day 2: Prometheus - Setting Up Monitoring
- **Concepts Covered**:
  - Introduction to Prometheus and its architecture.
  - Setup and configuration of Prometheus in an EKS cluster.
  - Installation of kube-prometheus-stack with Helm and integrating it with Grafana.
  - Basic queries and setup for monitoring with Prometheus and Grafana.
- **Key Learning**:
  - Get hands-on experience with Prometheus and Grafana.
  - Learn to install and configure Prometheus on Kubernetes.

### Day 3: Metrics and PromQL in Prometheus
- **Concepts Covered**:
  - Introduction to PromQL and basic querying techniques.
  - Aggregation and functions in PromQL to analyze metrics data.
- **Key Learning**:
  - Master the Prometheus Query Language (PromQL) for querying and analyzing metrics.

### Day 4: Instrumentation and Custom Metrics
- **Concepts Covered**:
  - Instrumentation for adding monitoring capabilities to applications.
  - Understanding different types of metrics in Prometheus: Counter, Gauge, Histogram, and Summary.
  - Writing custom metrics in a Node.js application using the `prom-client` library.
  - Dockerizing the application and deploying it on Kubernetes.
  - Setting up Alertmanager for alerting based on custom metrics.
- **Key Learning**:
  - Learn how to instrument applications to expose custom metrics.
  - Configure alerts in Alertmanager to monitor application performance.
  - Understand how to work with different types of metrics in Prometheus.

### Day 5: Logging with EFK Stack
- **Concepts Covered**:
  - Introduction to logging in distributed systems and Kubernetes.
  - Setting up the EFK stack (Elasticsearch, Fluentbit, Kibana) on Kubernetes.
  - Detailed setup and configuration for collecting and visualizing logs.
  - Cleaning up the Kubernetes cluster and resources.
- **Key Learning**:
  - Understand the importance of logging and how to set up

### Day 6: Distributed Tracing with Jaeger
- **Concepts Covered**:
  - Introduction to Jaeger and its architecture for distributed tracing.
  - Setting up Jaeger in a Kubernetes cluster using Helm.
  - Instrumenting services using OpenTelemetry to enable tracing.
  - Viewing and analyzing traces in the Jaeger UI.
  - Cleaning up the environment after setting up Jaeger.
- **Key Learning**:
  - Gain insights into distributed tracing and how it helps in debugging and performance optimization.
  - Learn how to set up and configure Jaeger for tracing in a microservices architecture.

### Day 7: OpenTelemetry – Setting Up Unified Observability
- **Concepts Covered**:
  - Introduction to OpenTelemetry, a unified framework for observability.
  - Understanding how OpenTelemetry integrates tracing, metrics, and logging.
  - Comparison of OpenTelemetry with prior observability tools like Jaeger, Prometheus
  - Supported programming languages and multi-language support in OpenTelemetry.
  - Step-by-step setup of OpenTelemetry in Kubernetes.
- **Key Learning**:
  - Learn how OpenTelemetry simplifies the process of collecting and exporting telemetry data.
  - Understand the benefits of a unified observability approach using OpenTelemetry.
  - Gain hands-on experience with setting up OpenTelemetry Collector, Prometheus, Jaeger, and Elasticsearch to monitor a Golang microservice application.

# Observability  (Prometheus and Grafana)
Observability tools are critical in DevOps for monitoring, logging, and gaining insights into the performance and behavior of your systems.
![Observability](https://github.com/Ankithv007/Kubernetes/blob/main/images/Observability.png)
Prometheus and Grafana are widely used together to monitor systems, gather metrics, and create beautiful dashboards for observability.
### architecture of prometheus
![architecture of prometheus](https://github.com/Ankithv007/Kubernetes/blob/main/images/Prometheus.png)
https://github.com/Ankithv007/Kubernetes/blob/main/images/Prometheus.png
1. Prometheus: Monitoring and Alerting Tool
Prometheus is an open-source system monitoring and alerting toolkit designed to capture metrics from different services and infrastructure, store them in a time-series database, and provide a query language to analyze this data. Prometheus is especially popular for Kubernetes environments.

* Key Concepts in Prometheus:
- Time-Series Database: Prometheus stores data as time-stamped metrics, which are collected at regular intervals (every few seconds or minutes). Each data point consists of a metric name, timestamp, and value.

- Metrics: Prometheus collects metrics in four types:
+ Counter: A metric that increases over time (e.g., number of requests).
+ Gauge: A metric that can increase or decrease (e.g., memory usage, temperature).
+ Histogram: A metric that samples observations and counts them into configurable buckets (e.g., request durations).
+ Summary: Similar to a histogram, but also provides quantiles (e.g., 90th percentile of request times).
- PromQL (Prometheus Query Language): Prometheus uses this powerful query language to retrieve metrics and perform operations such as aggregation, filtering, and arithmetic on metrics data.
- Targets: These are endpoints where Prometheus scrapes metrics. It pulls metrics from different exporters or directly from the services that expose them.
- Exporters: Prometheus needs to know where and how to gather metrics. Exporters are components that expose metrics for Prometheus to scrape. Common exporters include:
+ Node Exporter: Provides system-level metrics (CPU, memory, disk usage).
+ cAdvisor: Provides container-level metrics, typically used in Kubernetes environments.
+ Custom Exporters: You can build custom exporters for your applications.
- Alertmanager: Prometheus can trigger alerts based on predefined thresholds using Alertmanager. For example, if a service is down or CPU usage is too high, it sends alerts via email, Slack, etc.

How Prometheus Works:
1. Scraping Metrics: Prometheus pulls (scrapes) metrics from targets (usually services exposing /metrics endpoints) at regular intervals.
2. Storing Data: It stores this data in its own time-series database.
3. Querying Data: You can use PromQL to query this stored data to generate meaningful insights, such as the number of HTTP requests or CPU usage over time.
4. Alerting: Prometheus can evaluate query expressions at regular intervals and notify users if certain conditions are met (e.g., disk space running out).

2. Grafana: Visualization and Dashboarding Tool
Grafana is an open-source platform for monitoring and observability that provides flexible visualizations of data collected from various sources, including Prometheus.It is known for its ability to create rich, interactive dashboards to visualize time-series data.
- Key Features of Grafana:
+ Data Source Agnostic: Grafana supports multiple data sources, not just Prometheus. Other popular sources include Elasticsearch, InfluxDB, MySQL, and more.
+ Custom Dashboards: Grafana allows you to create customized dashboards by querying your data source and visualizing the data in various forms like line charts, bar graphs, heatmaps, gauges, and tables.
+ Alerts and Notifications: You can set alerts in Grafana and send notifications to email, Slack, PagerDuty, etc., based on specific conditions in your metrics.
+ Annotations: Grafana supports annotations, which allow you to highlight specific events (e.g., deployments, outages) on your dashboard, making it easy to correlatemetric changes with real-world events.
- Plugins: Grafana offers an extensive range of plugins to integrate with different data sources and add custom visualizations.
-  How Grafana Works with Prometheus:
1. Connect to Prometheus: You configure Grafana to use Prometheus as a data source.
2. Create Dashboards: Using Prometheus data, you can create interactive dashboards. For instance, a dashboard might visualize the CPU usage, memory consumption, and HTTP 3. request rates of a Kubernetes cluster.
4. PromQL in Grafana: While creating visualizations in Grafana, you write PromQL queries to retrieve metrics from Prometheus.
5. Alerting: Grafana also supports alerting, where you can set up thresholds (like if CPU usage exceeds 80%) and get notified via integrated alert channels.

### How Grafana Works with Prometheus:
1. Connect to Prometheus: You configure Grafana to use Prometheus as a data source.
2. Create Dashboards: Using Prometheus data, you can create interactive dashboards. For instance, a dashboard might visualize the CPU usage, memory consumption, and HTTP request rates of a Kubernetes cluster.
3. PromQL in Grafana: While creating visualizations in Grafana, you write PromQL queries to retrieve metrics from Prometheus.
4. Alerting: Grafana also supports alerting, where you can set up thresholds (like if CPU usage exceeds 80%) and get notified via integrated alert channels.

★ **Feature 1**: This is the first feature.
→ *Next Step*: Follow the instructions.
✔ **Task Completed**: This task is done.
**ankith b v**
*ankith b v*


