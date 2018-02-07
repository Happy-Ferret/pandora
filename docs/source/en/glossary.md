title: Glossary
---

We bring in some terminologies to define key concepts in pandora.js. What they represent may differ with common understandings. Here we list them with their meanings in the context of pandora.js.


## Application Related Terminologies

### procfile.js

> Process model definition file
  
A description file used to define the process model of the application.

### Application

> Application

An application is a computer program designed to perform a group of coordinated functions, tasks, or activities for the benefit of the user. Here we mean Node.js applications.

### Fork 

> Based on require('child_process').fork();

Simply create a new process, which becomes the child process of the caller, and launch the Node.js application in the child process.

### Cluster 

> Based on require('cluster');

A single instance of Node.js runs in a single thread. To take advantage of multi-core systems, users will sometimes want to launch a bunch of Node.js processes to handle the load. The relationships of those Node.js processes can be described via the process model.

### Service

> Functions provided by pandora.js

A Service implementation followed the standard pandora service start/stop specifications.

Here is the launching sequences of services:

1. Init and launch basic middlewares.
2. Start the main program of the application.
3. Create A standard proxy object proxy for services, thus services can be invoked through the IPC-Hub in other process.

### Process

> Process

An instance of a computer program that is being executed. Processes of different types may execute different programs.

## Metrics Related Terminologies

### EndPoint

> EndPoint

EndPoint is the end entity of the metrics transport tunnel. It collects and aggregates specified types of data.

There are different EndPoints for different types of data:
- MetricsEndPoint, used to collect and aggregate system metrics; 
- HealthEndPoint, used to manage the application health information; 
- ErrorEndPoint, used to collect and aggregate error logs.

### Indicator

> Indicator

The client part of the EndPoint. It collects specified types of data, such as a specific error or a specific configuration, etc.

Each endpoint used to have multiple indicators work for it. They communicate via the IPC.


### Actuator

> Actuator

Actuator is the manager of endpoints. It has two responsibilities:

1. Manage endpoints, provides endpoints registry and lookup services.
2. Expose metrics data, provides different ways to retrieve metrics data for application owners, e.g. HTTP and CLI.