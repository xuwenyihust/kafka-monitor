# Kafka Monitor

## Project Overview

### Layout

* src
 
  * main
  
    * java/com/linkedin/kmf
     
      * consumer
      
      * producer
      
      * partitioner
      
      * common
      
      * apps
      
      * topicfactory

* bin

### Structure

* **App**

  Start some producers/consumers, take predefined sequence of actions periodically
  
  These periodic or long-running actions: implemented in services
  
  A **typical App**: composed of 1 producer service, 1 consumer service & 1 broker bounce service

  * **SingleClusterMonitor**

  * **MultiClusterMonitor**
  

* **Service**

  A service will execute the action in its own thread and report metrics
 
  * **ProduceService**
  
    Report produce rate & availability 
    
    interface: `com.linkedin.kmf.producer.KMBaseProducer`
  
  * **ConsumeService**
  
    Report message loss rate, message duplicate rate & end-to-end latency
    
    interface: `com.linkedin.kmf.consumer.KMBaseConsumer`
  
  * **TopicManagementService**
  
    Ensure that every broker is leader of at least one partition of the monitor topic (to check produce availability)
    
    interface: `com.linkedin.kmf.topicfactory.TopicFactory`
  
  * **StatsdMetricsReporterService**
  
  * **DefaultMetricsReporterService**






