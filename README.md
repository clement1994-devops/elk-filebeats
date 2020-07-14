# ELKSTACK-FILEBEATS

Installations should be done in an order 


               *  Elastic search
               *  Kibana
               *  Logstash
               *  Filebeats
               
               
**Filebeat can be installed in host and it can be configured to input data to logstash for further process

wget https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-7.8.0-amd64.deb

dpkg -i filebeat-7.8.0-amd64.deb

systemctl enable filebeat

systemctl start filebeat

edit the /etc/filebeat/filebeat.yml

   
      Change the filebeat.input section
      
      - type: log
      
        enabled:  true
        
        paths:
        
        "specify the path where the logs to be fetched"
        
     Change the output section of logstash
     
       output.logstash
       
         hosts: ["192.168.50.112:5044"]
         
****

systemctl restart filebeat



Work flow : Filebeat(ship logs)-->Logstash(Process and Index logs)-->Elastic Search(store logs)-->Kibana(search and visualize logs)-->Nginx(reverse proxy)-->user



If you want to test this docker compose files in your pc,kindly change ip's mentioned in it to your local host ip.

ELK stack - filebeat implementation on a docker based platform for monitoring.