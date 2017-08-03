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


### App

Start some producers/consumers, take predefined sequence of actions periodically
  
These periodic or long-running actions: implemented in services
  
A **typical App**: composed of 1 producer service, 1 consumer service & 1 broker bounce service

* **SingleClusterMonitor**

* **MultiClusterMonitor**
  

### Service


```java
/*interface Service*/

void start();

void stop();

boolean isRunning();

void awaitShutDown();
```

A service will execute the action in its own thread and report metrics
 
* **ProduceService**

  ```java 
  public class ProduceService implements Service
  ```
  
  Report produce rate & availability 
    
  interface: `com.linkedin.kmf.producer.KMBaseProducer`
  
* **ConsumeService**

  ```java
  public class ConsumeService implements Service
  ```
  
  Report message loss rate, message duplicate rate & end-to-end latency
    
  interface: `com.linkedin.kmf.consumer.KMBaseConsumer`
  
* **TopicManagementService**
  
  Ensure that every broker is leader of at least one partition of the monitor topic (to check produce availability)
    
  interface: `com.linkedin.kmf.topicfactory.TopicFactory`
  
* **StatsdMetricsReporterService**
  
* **DefaultMetricsReporterService**

  ```java
  public class DefaultMetricsReporterService implements Service
  ```





