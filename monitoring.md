## Monitoring

While having high availability and disaster recovery systems in place helps in the event of something going wrong with your PostgreSQL cluster,
monitoring helps you anticipate problems before they happen. Additionally, monitoring can help you diagnose and resolve additional issues that
may not result in downtime, but cause degraded performance.

The PGO Monitoring stack is a fully integrated solution for monitoring and visualizing metrics captured from PostgreSQL clusters created using PGO. By leveraging **pgMonitor**  to configure and integrate the various tools, components and metrics needed to effectively monitor PostgreSQL clusters, PGO Monitoring provides an powerful and easy-to-use solution to effectively monitor and visualize pertinent PostgreSQL database and container metrics. Included in the monitoring infrastructure are the following components:

**pgMonitor** - Provides the configuration needed to enable the effective capture and visualization of PostgreSQL database metrics using the various tools comprising the PostgreSQL Operator Monitoring infrastructure.

**Grafana** - Enables visual dashboard capabilities for monitoring PostgreSQL clusters, specifically using Crunchy PostgreSQL Exporter data stored within Prometheus

**Prometheus** - A multi-dimensional data model with time series data, which is used in collaboration with the Crunchy PostgreSQL Exporter to provide and store metrics. 

**Alertmanager** - Handles alerts sent by Prometheus by deduplicating, grouping, and routing them to receiver integrations.

In addition, all the metrics from individual namespaces on Kubernetes/Openshift cluster(s) can be pushed to a Thanos cluster maintained by your SRE team. **TODO** show how to configure it.



## Crunchydata monitoring Integration

1. Prometheus is configured to automatically discover Crunchydata database instances and scrape the metrics every 15 seconds.
2. The metrics collected by Prometheus are stored in a time-series database that are accessible via API, which is used by Grafana and Prometheus UI.
3.  Metrics gathered are evaluated against the alert rules defined and tuned by Crunchydata team. 


### **Additional components**

**pgnodemx**: A PostgreSQL extension that exposes system metrics (e.g. CPU utilization, memory consumption) from the container itself via SQL queries. Checkout the following [link](https://github.com/CrunchyData/pgnodemx) for more details on pgnodemx

**postgres_exporter**: A side car container that runs queries against the PostgreSQL database and exposes them as prometheus style metrics. Checkout the following [link](https://github.com/prometheus-community/postgres_exporter) for more details on postgres_exporter

[pgMonitor](https://access.crunchydata.com/documentation/pgmonitor/2.2/#:~:text=pgmonitor%20is%20an%20open%2Dsource,the%20health%20of%20the%20system.)  is your all-in-one tool to easily create an environment to visualize the health and performance of your PostgreSQL cluster.

![../Images/pgmonitor.gif](https://github.com/CrunchyData/pgmonitor/blob/development/hugo/static/images/PGMonitor.gif)




