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

  * **SingleClusterMonitor**

  * **MultiClusterMonitor**
  

* **Service**

  A service will execute the action in its own thread and report metrics
 
  * **ProduceService**
  
    Report produce rate & availability 
  
  * **ConsumeService**
  
  * **TopicManagementService**
  
  * **StatsdMetricsReporterService**
  
  * **DefaultMetricsReporterService**






