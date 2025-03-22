# Docker Compose Demo: NGINX with Filebeat Logging

## Project Overview
This project is a Docker Compose setup that demonstrates how to run an NGINX container integrated with Filebeat for log collection. Filebeat forwards logs to an Elasticsearch backend for further processing and visualization via Kibana.

## Why Elasticsearch & Filebeat?
For this demo, I initially evaluated several logging solutions such as OpenSearch, Fluentd, and Fluent Bit. However, during testing on Windows, I encountered compatibility issues with OpenSearch (especially with Filebeat and Fluentd integrations). To avoid these hurdles and ensure a smooth demo experience, I opted for:
 
- **Filebeat for Log Shipping:**  
  - It is lightweight and highly optimized for forwarding log data.
  - Easy to configure and maintain.
  - Well-documented and widely used in production for log collection.
  
- **Elasticsearch for Centralized Logging:**  
  - Provides robust, centralized log storage and indexing.
  - Seamless integration with Filebeat.
  - Offers excellent support for integrating machine learning models. This is critical for the HSF Conditions Database project, as the future ML model can analyze logs for anomaly detection, identify software bugs, and adjust system parameters dynamically.
  
This combination was chosen specifically for the *Intelligent Log Analysis for the HSF Conditions Database* project due to:
- The need for a centralized logging solution to aggregate logs from NGINX, Django, and the database.
- The ability to extend the system with ML-powered anomaly detection and dynamic configuration tuning.
- Elasticsearch’s centralized nature, ease of integration, and compatibility with additional ML models.

**Note:**  
For this demo, security features (such as TLS and authentication) have been disabled to keep the setup simple and focused on the logging pipeline. In a production environment, proper security measures would be implemented.

## How to Run the Project
### Prerequisites
Ensure you have the following installed on your system:
- [Docker](https://www.docker.com/get-started)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Steps to Run
1. Clone the repository:
   ```sh
   git clone <your-repo-url>
   cd <your-repo-folder>
   ```
2. Start the services:
   ```sh
   docker-compose up -d --build
   ```
3. Verify the running containers:
   ```sh
   docker ps
   ```
4. Check Elasticsearch indices to confirm logs are being ingested:
   ```sh
   curl http://localhost:9200/_cat/indices?v
   ```
5. Access Kibana for visualization:
   - Open [http://localhost:5601](http://localhost:5601) in your browser.



## Conclusion
This setup demonstrates a basic logging pipeline using NGINX and Fileba