# Application Monitoring

Application monitoring in IBM Cloud Pak for Multicloud Management provides various indicators like the below.

## 1. Execution Time and Memory Usage

The below image shows the Golden signals of an app in Kubernetes Serivce.

<img src="images/01-home.png" bordercolor=green>

1. Latency (Execution Time)
2. Traffic (No. of Requests)
3. Saturation (Memory usage)

### Latency (Execution Time)

<img src="images/02-latency.png" bordercolor=green>

### Traffic (No. of Requests)

<img src="images/03-traffic.png" bordercolor=green>

### Saturation (Memory usage)

<img src="images/04-saturation.png" bordercolor=green>


## 2. Tracing / transaction tracking

Here is the list of APIs called in this app.

<img src="images/05-api-calls.png" bordercolor=green>

You can choose the any of the API and find the tracing details as like the below images.

<img src="images/06-trace1.png" bordercolor=green>
<img src="images/07-trace2.png" bordercolor=green>
<img src="images/08-trace3.png" bordercolor=green>

The detailed explnation from the knowledge center is available at https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/monitor_tt.html


## 3. CPU and Memory usage

CPU and Memory usage can be seen more detailed at the Kubernetes POD level.

<img src="images/09-cpu.png" bordercolor=green>

<img src="images/10-memory.png" bordercolor=green>

<img src="images/11-cpu-memory.png" bordercolor=green>


## 4. Thread usage

Thread usage can be seen for the springboot applications at J2SE Application Runtime.

<img src="images/12-standalone-app-home.png" bordercolor=green>

<img src="images/13-standalone-app-home2.png" bordercolor=green>

<img src="images/14-standalone-app-thread.png" bordercolor=green>


## References

For further references read the IBM knowledge center.

Transaction tracking
https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/monitor_tt.html

Incident Resolution Flow for a Kubernetes App
https://www.ibm.com/support/knowledgecenter/SSFC4F_1.3.0/icam/overview_ui_start6.html