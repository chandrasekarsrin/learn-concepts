# grafana

- open source web application to visualize data.


data producer(like backend applications, iot sensors) -> data source(like prometheus, monitoring service(oracle internal service)) -> grafana queries the data source

Genearally supports 2 types of data:
- metrics
- errors

# Grafana dashboard design
1. choose pannel type
1. explore data available
1. choose very important data for first dashboard.

# MQL 
- syntax for quering metrics from monitoring service(oracle monitoring service)