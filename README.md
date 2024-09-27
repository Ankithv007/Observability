# Observability  (Prometheus and Grafana)
Observability tools are critical in DevOps for monitoring, logging, and gaining insights into the performance and behavior of your systems.
![Observability](https://github.com/Ankithv007/Kubernetes/blob/main/images/Observability.png)
Prometheus and Grafana are widely used together to monitor systems, gather metrics, and create beautiful dashboards for observability.

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


