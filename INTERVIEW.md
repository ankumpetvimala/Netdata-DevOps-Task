# Task 7: Netdata Interview Questions

## Q1: What does Netdata monitor?
**Answer:**  
Netdata monitors:
- System resources (CPU, memory, disk I/O, network)
- Running applications and services
- Container metrics (Docker, Kubernetes)
- Real-time performance data with 1-second granularity
- Custom metrics through plugins

## Q2: How do you view real-time metrics?
**Answer:**  
Real-time metrics are accessed via:
1. Web dashboard: `http://<server-ip>:19999`
2. Features:
   - Per-second metric collection
   - Interactive, zoomable charts
   - Pre-configured dashboards
   - No login required by default

## Q3: How is Netdata different from Prometheus?
**Answer:**  

| Feature          | Netdata                          | Prometheus                      |
|------------------|----------------------------------|---------------------------------|
| Setup            | Zero-configuration               | Manual configuration required   |
| Storage          | Short-term in-memory             | Long-term via TSDB              |
| Visualization    | Built-in dashboard               | Requires Grafana                |
| Scalability      | Single-node focus                | Cluster-wide monitoring         |
| Alerting         | Built-in                         | Requires Alertmanager           |

## Q4: What is a collector?
**Answer:**  
- A lightweight plugin that gathers specific metrics
- Types:
  - System collectors (CPU, disk, network)
  - Application collectors (Nginx, MySQL)
  - Custom collectors (via plugins)
- Auto-detects available metrics
- Runs with minimal performance impact

## Q5: What are some performance KPIs to watch?
**Critical KPIs:**  
1. **CPU**: Usage % per core, load average
2. **Memory**: RAM usage, swap activity
3. **Disk**: Read/write latency, IOPS
4. **Network**: Bandwidth, packet drops
5. **Containers**: Resource limits, throttling
6. **Applications**: Response times, error rates

## Q6: How to deploy Netdata on a VM?
**Deployment Methods:**  

**1. Docker (Preferred):**
```bash
docker run -d --name=netdata \
  -p 19999:19999 \
  -v netdataconfig:/etc/netdata \
  -v netdatalib:/var/lib/netdata \
  -v netdatacache:/var/cache/netdata \
  -v /etc/passwd:/host/etc/passwd:ro \
  -v /etc/group:/host/etc/group:ro \
  -v /proc:/host/proc:ro \
  -v /sys:/host/sys:ro \
  --restart unless-stopped \
  --cap-add SYS_PTRACE \
  --security-opt apparmor=unconfined \
  netdata/netdata
````
**2. Native Installation:
````
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
````
##Q7: How does Netdata alerting work?
Alert Mechanism:
- Threshold-based alert rules (/etc/netdata/health.d/)
- Multi-tier severity levels (Critical/Warning)
- Notification methods:
- Email (SMTP)
- Slack/Teams webhooks
- PagerDuty
- Custom scripts
- Silence/acknowledge functionality
- Historical alert database

Q8: What is a dashboard in this context?
Dashboard Features:
- Real-time monitoring interface
- Component breakdown:
- System overview section
- Context-aware charts
- Time-range selector
- Metric correlation tools
- Alarm status panel
- Customizable layouts
- No-SQL mode for troubleshooting
- Embeddable widgets
