# Twitter Stream Processing Pipeline

This guide provides step-by-step instructions to set up Kafka, Zookeeper, a streaming data application, and a storage system using Elasticsearch and Kibana.

it implements a comprehensive data pipeline to process and visualize a continuous stream of tweets. The pipeline is designed to ingest, process, store, and visualize tweet data in real-time, enabling users to analyze tweets based on text, time, and location.

Pipeline Components:
Stream Ingestion:

Simulates a live Twitter feed using a tweet generator or Twitter API.
Streams tweets into an Apache Kafka topic for scalability and intermediate storage.
Processing:

Tweets are processed using Apache Spark (Scala) to extract hashtags, analyze sentiment, and transform data into a structured JSON format.
Each tweet is enriched with metadata such as hashtags, sentiment scores, and geolocation.
Storage:

Processed tweets are stored in Elasticsearch for efficient querying and indexing.
The schema is designed to support fast searches and geo-spatial queries.
Visualization:

A user-friendly web application allows users to:
Search tweets containing specific keywords.
Display tweets on an interactive map based on their geo-coordinates using Leaflet.
View a trend diagram showing the temporal distribution of tweets over time.
Analyze sentiment using a sentiment gauge.
Key Features:
Real-time processing of tweets with batch sizes of 9600 records every 10 seconds.
Support for temporal and spatial queries.
Integration with Elasticsearch for scalable and efficient storage.
Sentiment analysis using Spark NLP or TextBlob.
Interactive web-based visualization.
Tools & Technologies:
Apache Kafka: For message streaming and intermediate storage.
Apache Spark (Scala): For processing and sentiment analysis.
Elasticsearch: For data storage and indexing.
Leaflet.js: For interactive map visualization.
TextBlob/Spark NLP: For sentiment analysis.

---
Trello Link
#https://trello.com/invite/b/6759dfb03158c1e0ee340f45/ATTI1a96dc0efce6c5e2177cf3053ef15555902E2E0E/twitter-streaming-project-bd-ir
---
## Setup Instructions

### 1. Start Kafka and Zookeeper
1. **Start Zookeeper**:
   Run the following command:
   ```bash
   zookeeper-server-start.bat ..\..\config\zookeeper.properties
   ```
   
2. **Start Kafka**:
   Run the following command:
   ```bash
   kafka-server-start.bat ..\..\config\server.properties
   ```

3. **Create Kafka Topics**:
   - Create the required topics:
     ```bash
     kafka-topics.bat --create --topic produced_data --bootstrap-server localhost:9092
     kafka-topics.bat --create --topic send_consumer_data --bootstrap-server localhost:9092
     ```

---

### 2. Run the Streaming Data Code
1. Navigate to the streaming project directory.
2. Ensure SBT is installed and loaded.
3. Run the streaming code

---

### 3. Run the Kafka Producer
1. Navigate to the Kafka producer project directory.
2. Run the producer script:
   ```bash
   python test.py
   ```

---

### 4. Start Elasticsearch and Kibana
1. Navigate to the directory containing the `docker-compose.yml` file for Elasticsearch and Kibana.
2. Start the containers:
   ```bash
   docker compose up
   ```
3. Verify the services:
   - **Kibana**: Open [http://localhost:5601](http://localhost:5601) in your browser.
   - **Elasticsearch**: Open [http://localhost:9200](http://localhost:9200) in your browser.

---

### 5. Run the Storage Code
1. Open a new terminal and navigate to the storage project directory.
2. Run the storage application:
   ```bash
   python main.py
   ```

---

### 6. Verify the Setup
- Ensure the following components are running:
  - **Kafka** and **Zookeeper**
  - **Streaming Application**
  - **Kafka Producer**
  - **Elasticsearch and Kibana**

---
### Final Result
This reppository for final result for elasticsearch and kibana without run any code: to run it : 1.un zip 2 files elasticsearch_data.tar.gz and kibana_data.tar.gz

2.edit docker-compose.yml to volumes for elasticsearch and kibana to make it for kibana
volumes:

    PULL PATHE TO (kibana_data)file :/usr/share/kibana/data

    for elasticsearch
    volumes:

    PULL PATHE TO (elasticsearch_data)file:/usr/share/elasticsearch/data

3.make go to file that contane (elasticsearch_data , kibana_data and docker-compose.yml) by use cd

4.then run in TERMINAL to run docker-compose -f docker-compose.yml up -d ,and i run the containers

5.open :http://localhost:5601 to run kibana, and http://localhost:9200/ to see elasticsearch
 
 
---
## Links
- **Kibana**: [http://localhost:5601](http://localhost:5601)
- **Elasticsearch**: [http://localhost:9200](http://localhost:9200)



