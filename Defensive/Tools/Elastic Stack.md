![[Pasted image 20260303140917.png]]
ELK stands for Elasticsearch, Logstash, and Kibana.

## Logstash
Logstash is a data processing engine that takes data from different sources, filters it, or normalizes it, and then sends it to the destination, which could be Kibana or a listening port. A Logstash configuration file is divided into three parts, as shown below.

1. The **Input** part is where the user defines the source from which the data is being ingested.
2. The **Filter** part is where the user specifies the filter options to normalize the log ingested above. 
3. The **Output** part is where the user wants the filtered data to be sent. It can be a listening port, Kibana Interface, Elasticsearch database, or file.

## Beats
Beats are host-based agents known as data-shippers that ship/transfer data from the endpoints to Elasticsearch.
## Kibana
Kibana is a web-based data visualization tool that works with Elasticsearch to analyze, investigate, and visualize data streams in real time.
![[Pasted image 20260303141238.png]]