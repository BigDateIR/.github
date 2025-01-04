# Twitter Stream Processing Pipeline

This guide provides step-by-step instructions to set up Kafka, Zookeeper, a streaming data application, and a storage system using Elasticsearch and Kibana.


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

## Links
- **Kibana**: [http://localhost:5601](http://localhost:5601)
- **Elasticsearch**: [http://localhost:9200](http://localhost:9200)



