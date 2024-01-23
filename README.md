# IAM

- Account is a closed bucket of resources.
- The root user is the owner of your account.
- IAM users for tailor made permissions to fulfill daily tasks.
- Groups to easily manage permissions for a set of users.

## ARNs

- Amazon Resource Names: `arn:partition:service:region:account-id:resource-id`
- How resources are uniquely identified across all of AWS.

## Tips and Tricks

- Grant least privilege.
- Rotate access keys regularly.
- Use multi-factor authentication.
- Don't use root account for daily work
- Leverage IAM roles as much as possible

# Shared Responsibility Model

- AWS is responsible for the security of the cloud.
- You are responsible for security in the cloud.

# Availability Zones

1. **Definition**: Availability Zones (AZs) are distinct locations within an AWS Region that are engineered to be isolated from failures in other AZs. They offer physical redundancy and high availability in the AWS infrastructure.

2. **Characteristics**:

   - Each AZ consists of one or more discrete data centers, each with redundant power, networking, and connectivity.
   - AZs in a region are connected through low-latency links.
   - They are physically separate, such that even in the case of a natural disaster affecting one zone, the others continue to operate normally.

3. **Use Case**: By distributing your instances across multiple AZs, you can achieve high availability and fault tolerance. For instance, you can run critical workloads in multiple AZs to ensure continuous operation even if one AZ goes down.

# Other Types of Zones in AWS

1. **Regions**: A Region is a geographical area that consists of two or more Availability Zones. It's the broadest network tier in AWS. Each Region is a separate geographic area, like US West (Oregon) or Asia Pacific (Sydney).

2. **Local Zones**: AWS Local Zones are extensions of AWS Regions that are geographically closer to users. They bring certain AWS services very close to the end-user, reducing latency. Local Zones are ideal for applications that require single-digit millisecond latencies to end-users or on-premises data centers.

3. **Wavelength Zones**: These are AWS infrastructure deployments that embed AWS compute and storage services within the telecommunications providers' data centers at the edge of the 5G network. Wavelength Zones are designed to minimize latency and are ideal for mobile and connected devices.

4. **AWS Outposts**: While not a 'zone' in a traditional sense, AWS Outposts bring native AWS services, infrastructure, and operating models to virtually any data center, co-location space, or on-premises facility. They are fully managed and supported by AWS and provide a consistent hybrid experience.

# EC2

Amazon EC2 provides resizable compute capacity in the cloud. It's designed to make web-scale cloud computing easier for developers. Essentially, EC2 simplifies the process of running applications on a cloud server. With EC2, you can launch virtual servers, configure security and networking, and manage storage. EC2 offers scalability within minutes, meaning you can quickly scale up or down as your computing requirements change.

## Instance Types

An "instance" is a virtual server in EC2 for running applications. AWS provides a variety of instance types optimized to fit different use cases. Instance types comprise varying combinations of CPU, memory, storage, and networking capacity.

1. **General Purpose**: Balanced CPU-to-memory ratio. Ideal for applications that use these resources in equal proportions, such as web servers and development environments. Examples: `t2.micro`, `m5.large`.

2. **Compute Optimized**: High performance processors. Suited for compute-bound applications that benefit from high-performance CPUs. Examples: Applications like batch processing, media transcoding, high-performance web servers, high-performance computing (HPC).

3. **Memory Optimized**: Deliver fast performance for workloads that process large data sets in memory. Ideal for high-performance databases, distributed web scale in-memory caches, mid-size in-memory databases, real-time big data analytics.

4. **Storage Optimized**: Designed for workloads that require high, sequential read and write access to large data sets on local storage. They are optimized for applications like distributed file systems, data warehousing applications, high-frequency online transaction processing (OLTP) systems.

## Amazon Machine Image (AMI)

An AMI is a template that contains a software configuration (operating system, application server, and applications). When you launch an instance, you select an AMI to use as a template. AWS offers a variety of AMIs, each configured with different operating systems and software packages.

- **Pre-configured AMIs**: AWS provides pre-configured AMIs such as those with Amazon Linux, Windows Server, Ubuntu, etc.
- **Custom AMIs**: You can also create your own AMI from an existing instance. This is useful for creating multiple instances that are configured the same way.

# VPC

A virtual network in the context of AWS (Amazon Web Services) and specifically AWS Virtual Private Cloud (VPC) is a logically isolated section of the AWS Cloud. It's virtual because it's not a physical network, but it's designed to provide the same features and functionality as a traditional network.

## Characteristics of a Virtual Network in AWS VPC

1. **Logical Isolation**: It's separated from other virtual networks in the AWS Cloud. This isolation ensures that resources within each VPC are secure and cannot be accessed by resources in other VPCs unless explicitly allowed.

2. **Customizable IP Address Range**: You can select your own IP address range for the VPC, adhering to the IP protocol standards. This range is used to assign IP addresses to instances (virtual servers) within the VPC.

3. **Subnets**: Within a VPC, you can create subnets, which are segments of the VPC’s IP address range where you can place groups of isolated resources. Subnets can be designated as public (accessible from the internet) or private (not accessible from the internet).

4. **Control Over Routing**: You can create route tables to determine where network traffic from your subnets should be directed, such as to the internet, to other subnets, or to other VPCs.

5. **Internet Connectivity**: Although VPCs are isolated from the internet by default, you can enable access to/from the internet by attaching an internet gateway and configuring routing rules.

6. **Security Controls**: You can use security groups and network access control lists (ACLs) to control inbound and outbound traffic at the instance and subnet level, respectively.

7. **Connection to On-Premises Networks**: You can connect a VPC to your own networks over the internet using VPN (Virtual Private Network) connections or through AWS Direct Connect for a more secure and consistent network experience.

8. **AWS Resource Hosting**: Within a VPC, you can launch AWS resources such as Amazon EC2 instances (virtual servers), databases, and more.

## Functionality

- The virtual network functions like a traditional network in many ways but with the benefits of AWS’s scalable infrastructure.
- It allows you to use AWS services in a network that you define and control, including the selection of IP address ranges, creation of subnets, and configuration of route tables and network gateways.

## Adhering to IP Protocol Standards

When setting up an AWS VPC, you select an IP address range for your network. This selection must adhere to the Internet Protocol (IP) standards, which are guidelines set for formatting IP addresses. These standards include:

1. **IPv4 and IPv6**: The two versions of IP used for assigning addresses. IPv4 uses a 32-bit address format (e.g., 192.0.2.1), while IPv6 uses a 128-bit format (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334).
2. **Address Ranges**: You must choose a range that doesn't overlap with other networks you are connected to. This is to ensure unique addressing and avoid conflicts.

## Subnets in AWS VPC

A subnet, or subnetwork, is a subdivision of an IP network. In AWS VPC, a subnet is a range of IP addresses in your VPC.

1. **Purpose of Subnets**: Subnets allow you to segment your VPC's IP address range into smaller groups, making network management and security easier. For instance, you might have a subnet for front-end servers (like web servers) and another for back-end systems (like databases).
2. **Public vs. Private Subnets**:
   - **Public Subnet**: These have a route to the internet through an internet gateway, making resources in these subnets accessible from the internet. Useful for servers that need to serve requests from the internet.
   - **Private Subnet**: These do not have a route to the internet and are used for resources that shouldn't be accessible from the internet, like databases or application servers.

## Route Tables

A route table contains a set of rules, called routes, that determine where network traffic from your subnet or gateway is directed.

1. **Function:** The route table directs traffic based on the destination IP address. For each route in the table, it specifies the destination CIDR and a target (like an internet gateway, another subnet, etc.).

2. **Why 'Route Table':** It's called a route table because it's used to 'route' traffic to different destinations based on rules. Just like a routing table in traditional networking, it guides data packets to their destinations.

## Internet Gateway and Routing Rules

An internet gateway is a component in AWS VPC that allows communication between your VPC and the internet.

1. **Functionality of Internet Gateway:**

- It serves as a target in your VPC route tables for traffic that's destined for the internet.
- It provides a way for instances in your VPC to communicate with the outside world and vice versa.

2. **Configuring Routing Rules:**

- When you set up an internet gateway, you need to update the route table of your VPC to include a route that directs internet-bound traffic to the gateway.
- For example, you might add a route specifying that traffic destined for any address outside your VPC (0.0.0.0/0 for IPv4 or ::/0 for IPv6) should be directed to the internet gateway.

# EC2

Allows users to rent virtual computers on which they can run their own computer applications. EC2 offers scalable computing capacity in the AWS cloud, reducing the need for upfront hardware investments and allowing for quicker development and deployment of applications.

## Common mistakes

- Ignoring security groups
- Choosing the wrong instance type
- Poor monitoring
- Not optimizing costs
- Neglecting backups

## Why choose over lambda

- Higher performance for certain workloads
- More control over the underlying infrastructure
- Cost control

## Virtual machines

EC2 instances are virtual machines (VMs) in the cloud. Unlike physical servers, virtual
machines use software to create an abstraction from their underlying hardware.

## Amazon Machine Image (AMI)

An Amazon Machine Image (AMI) is a template that contains a software configuration (for example, an operating system, an application server, and applications). From an AMI, you launch an instance, which is a copy of the AMI running as a virtual server in the cloud. You can launch multiple instances of an AMI.

## Instance types

- General purpose
- Compute optimized
- Memory optimized
- Storage optimized
- Accelerated computing

## Connecting to an instance

Typically, you connect to an instance using SSH (Linux) or RDP (Windows). However, you can also connect to an instance using a serial console.

## Lifecycle of an instance

1. **Launch**: You launch an instance from an AMI.
2. **Start**: You start the instance.
3. **Stop**: You stop the instance.
4. **Hibernate**: You hibernate the instance.
5. **Reboot**: You reboot the instance.
6. **Retire**: The instance is retired.
7. **Terminate**: You terminate the instance.

## Monitoring

Use CloudWatch to monitor your EC2 instances. CloudWatch provides metrics such as CPU utilization, disk reads and writes, and network traffic. It's important to monitor your instances so that you can react to changes in performance or resource usage.

# ECS

Amazon ECS is a fully managed container orchestration service provided by AWS. It allows you to easily run, stop, and manage containers on a cluster. Your containers are defined in a task definition that you use to run individual tasks or services. ECS can be used with both EC2 and AWS Fargate, which is a serverless compute engine for containers.

Fargate is a serverless compute engine for containers. It allows you to run containers without having to manage servers or clusters. You simply define your containerized applications and Fargate handles the rest. It's a good choice for running containers if you don't want to manage servers or if you want to run containers at scale.

## Containers

Containers are like lightweight, standalone packages that contain everything needed to run a piece of software. This includes the code, runtime, system tools, libraries, and settings. They are isolated from other containers and the host system, ensuring that they work uniformly regardless of where they're deployed.

Think of a container as a shipping container for goods. Just as a shipping container can be loaded with different items (furniture, electronics, etc.) and then shipped anywhere in the world, knowing it will fit perfectly on any ship or truck, a software container can be packed with an application and its dependencies and moved across different computing environments, assured it will run the same way everywhere.

## Task definitions

Task definitions are blueprints for your applications in the context of Amazon ECS. They define how your containers should run, specifying things like which Docker images to use, how many resources (like CPU and memory) are needed, how the containers should communicate with each other, and what commands should be executed inside the containers.

Consider a task definition as a recipe for a meal. Just like a recipe specifies ingredients, quantities, and the steps to prepare a dish, a task definition outlines the necessary components (like images and resources) and instructions for running your application containers.

## Service

In ECS, a service maintains and runs a specified number of instances of a task definition simultaneously. It ensures that the specified number of tasks are always running and replaces any tasks that fail or stop. This is crucial for applications that should be continuously available and scalable.

Imagine a service as a bus service in a city. Just as a bus service ensures a certain number of buses are always on specific routes, regardless of whether a bus breaks down or completes its route, an ECS service ensures that a specified number of tasks are always running for your application.

## Clusters

Clusters are groups of EC2 instances that you use to run your containers with ECS. They represent the underlying infrastructure (like servers) on which your tasks and services are run. Clusters can contain multiple instances and can run multiple tasks across those instances.

Think of a cluster as a housing estate. In this estate, each house (EC2 instance) can host several families (containers). The entire estate (cluster) is managed to ensure it accommodates all families comfortably, just like a cluster manages resources to run your containers efficiently.

## Task

In Amazon ECS, a task is an instance of a task definition. It is the actual running version of your application or a part of it. When you tell ECS to run a task, it launches the container specified in your task definition on an available EC2 instance within your cluster. A task can consist of one or multiple containers that are run together on the same host.

Think of a task as a musician playing a concert. The task definition is like the sheet music that tells the musician what to play (it's the blueprint), and the task itself is the actual performance. Just as a musician follows the sheet music to perform a piece, a task uses the task definition to run your application. If you have multiple musicians (containers) playing together, they all follow the same sheet music (task definition) but perform their parts (run their specific containers) simultaneously. This concert is then hosted at a venue (an EC2 instance within a cluster), which provides the space and resources for the performance.

## Task scheduling

Task scheduling refers to the process of assigning tasks to container instances within a cluster.

Lifecycle of a task:

- Provisioning
- Pending
- Activating
- Running
- Deactivating
- Stopping
- Deprovisioning
- Stopped

# Lambda

Lambda abstracts away the underlying infrastructure and allows you to run code without having to manage servers.

However, it doesn't mean that there are no servers. It just means that you don't have to manage them. AWS manages the servers for you, so you can focus on writing code.

## Cold Start

A cold start occurs when a Lambda function is invoked for the first time or after it has been updated. When this happens, the Lambda service needs to allocate resources and set up the execution environment for the function. This can take some time, resulting in a delay before the function starts executing.

## How to reduce cold starts

- Keep functions warm: Regularly invoke your lambda function.
- Use provisioned concurrency: Provisioned concurrency allows you to keep a specified number of functions initialized and ready to respond to requests.
- Optimize package size: Reduce the size of your deployment package to reduce the time it takes to download and extract it.
- Bootstrap as much code as possible outside of your handler: Move code that doesn't need to be executed on every invocation outside of your handler function.

## Tips and tricks

- Keep your functions stateless and idempotent.
- Use cloudwatch alarms
- Pick the right database solution
- Use Layers to share dependencies
- Focus on event driven architecture

# Amazon RDS

Amazon Relational Database Service (RDS) is a managed service provided by AWS to set up, operate, and scale a relational database in the cloud. It simplifies database management for several popular database engines.

1. **Managed Service**: Amazon RDS handles routine database tasks such as provisioning, patching, backup, recovery, failure detection, and repair.

2. **Database Engines**: RDS supports several popular database engines, including Amazon Aurora, PostgreSQL, MySQL, MariaDB, Oracle Database, and SQL Server.

3. **Scalability**: It allows you to scale your database's compute and storage resources with minimal downtime. This is ideal for applications with variable workloads.

4. **Availability and Durability**: RDS facilitates high availability and durability through features like Multi-AZ deployments for failover and Read Replicas for improved read scaling.

   - **Multi-AZ Deployments**: For high availability, RDS can automatically replicate the data in a primary database to a secondary database in a different Availability Zone (AZ).

   - **Read Replicas**: They enhance performance by offloading read traffic from the primary database instance. This is especially useful for read-heavy database workloads.

5. **Automated Backups**: RDS automatically backs up your database and transaction logs, enabling point-in-time recovery.

6. **Security**: It offers encryption at rest and in transit. RDS also integrates with AWS Identity and Access Management (IAM) for access control.

# DynamoDB

Amazon DynamoDB is a fully managed NoSQL database service provided by AWS. It's a key-value and document database that delivers single-digit millisecond performance at any scale.

## Key Concepts

1. **Tables**: A table is a collection of data. It stores items, which are similar to rows in a relational database. Each item has a primary key, which uniquely identifies it in the table.
2. **Attributes**: An attribute is a piece of data stored in an item. It's similar to a column in a relational database. Each attribute has a name and a value.
3. **Item**: An item is a collection of attributes. It's similar to a row in a relational database.
4. Simple Key: A simple key is a primary key that consists of one attribute.
5. **Composite Key**: A composite key is a primary key that consists of two attributes. The two attributes are a partition key and a sort key.
6. **Partition Key**: A partition key defines how data is distributed across partitions.
7. **Sort Key**: A sort key is used to sort items with the same partition key.

## DynamoDB JSON

Each attribute in DynamoDB has an associated type. All types can be categorized into three categories: Scalar, Document, and Set.

They are used for specifying the data type of an attribute when creating a table or adding an item to a table. DynamoDB is a schema-less NoSQL database, but it still enforces data types for each attribute in an item. These type designations ensure that the data stored in each attribute is of the expected type, which is crucial for operations like querying and data processing.

- "S" stands for String.
- "N" for Number.
- "B" for Binary.
- "L" for List.
- "M" for Map.

## Queries and Scans

Scan operations examine every item in a table. They are less efficient than query operations because they process the entire table. However, they are useful for operations that don't require a specific item.

Query operations are more efficient than scan operations because they only process items that match a given key condition expression. They are useful for operations that require a specific item.

## Pricing

DynamoDB charges you based on Read Capacity Units (RCU) and Write Capacity Units
(WCU).

## Backup

It's built-in backup and restore feature allows you to create full backups of your tables for long-term retention and archival for regulatory compliance needs. It also enables point-in-time recovery (PITR) for your DynamoDB tables, helping you protect against accidental writes or deletes.

## Streams

DynamoDB Streams is a feature in Amazon DynamoDB that captures changes (such as inserts, updates, and deletes) to items in a DynamoDB table in near real-time. Each record in the stream details a single data modification in the table.

The purpose of DynamoDB Streams is to enable real-time processing of changes in your DynamoDB table. This feature allows you to:

- Respond immediately to changes in your data.
- Synchronize data changes with other databases or services.
- Implement event-driven architectures.

**When to Use**:

1. **Real-Time Data Replication**: If you need to replicate data changes from a DynamoDB table to another data store.
2. **Triggering Automated Actions**: For triggering AWS Lambda functions based on table changes. This is useful for various automated workflows like sending notifications, updating indexes, or real-time analytics.
3. **Event-Driven Architectures**: If your application is built on an event-driven model where actions depend on certain data changes.
4. **Maintaining Audit Trails**: To log and monitor changes in data for compliance or auditing purposes.
5. **Aggregating or Filtering Data**: When you want to process data streams for summarizing, transforming, or filtering data as it changes.

## TTL

You can enable TTL (Time to Live) on a table to automatically delete expired items. This is useful for removing old data from your tables.

## Tips

Think about your access patterns first- When designing your database, don't start
by thinking about your keys and attributes first. Instead, start by thinking about your access patterns. For example, if you're building a project management tool, your access
patterns could include:

Getting users by user ID
Getting users by project
Getting projects by user Note down the access patterns and discuss them with

Always prefer queries over scans - Always think about how you can leverage a query
over a scan. Scans won't scale and are very expensive.

Make use of global tables - Global tables allow you to create a single table that is
replicated to multiple AWS regions. Use this feature right from the beginning.

Activate point-in-time recovery - This will allow you to restore your database to
points in the last 30 days.

Monitor usage for your tables - Use common metrics in CloudWatch and build a
dashboard for DynamoDB. There are automatic dashboards for DynamoDB already
available. This will help you understand how your application behaves.

# S3

**What**: Amazon S3 (Simple Storage Service) is a scalable object storage service by AWS for storing and retrieving any amount of data.

**Event Notifications**: Automatically sends messages or triggers functions in response to specific events in an S3 bucket, like object creation or deletion.

**Lifecycle Policies**: Automatically manages objects by defining rules for transitioning objects to less expensive storage classes or deleting them after a set period.

**Batch Operations**: Performs large-scale batch operations on S3 objects, like copying, tagging, or applying access controls, reducing manual effort for bulk actions.

**Versioning**: Maintains multiple versions of an object within an S3 bucket, allowing you to retrieve and restore previous versions of an object.

**Multi-Region Access Points**: Provides a way to manage data access across multiple geographic regions, optimizing for performance and resilience.

**Pricing**: Based on storage used, number of requests, data transfer, and additional features like data transfer acceleration or lifecycle management. Pricing can vary by region and storage class.

# SQS

**What**: Amazon SQS (Simple Queue Service) is a fully managed message queuing service by AWS that enables the decoupling and scaling of microservices, distributed systems, and serverless applications.

**Poll-Based**: Consumers poll SQS to retrieve and process messages, as opposed to push-based systems.

**Event Source Mapping**: Allows automatic triggering of AWS Lambda functions in response to messages in an SQS queue.

**Exactly Once vs At Least Once Delivery**:

- **Exactly Once**: Each message is delivered only once (typically associated with FIFO queues).
- **At Least Once**: Messages may be delivered more than once; consumers must handle duplicate messages (common in standard queues).

**FIFO vs Standard Queues**:

- **FIFO (First-In-First-Out)**:
  - **Pros**: Guarantees the order of messages and exactly-once processing.
  - **Cons**: Limited throughput (300 messages per second with batching, or 10 messages per second without).
- **Standard Queues**:
  - **Pros**: Higher throughput, unlimited number of transactions per second.
  - **Cons**: Messages might be delivered in a different order and more than once.

**DLQ (Dead Letter Queue)**: Used to collect messages that can’t be processed successfully, allowing separate handling of these messages.

**Redriving from DLQ Back to SQS**: Involves manually or automatically moving messages from the DLQ back to the original queue for reprocessing.

**Retention Period**: The time a message stays in the queue before being automatically deleted, ranging from 1 minute to 14 days.

**Visibility Timeout**: The period during which SQS prevents other consumers from receiving and processing the message, ensuring that a message being processed isn’t received by another consumer.

**Long Polling vs Short Polling**:

- **Long Polling**: Waits for a message to become available if the queue is empty, reducing the number of empty responses and lowering costs.
- **Short Polling**: Returns immediately, even if the queue is empty, which might lead to more frequent polling.

**Three Common Message Lifecycles Within SQS**:

1. **The Happy Path**: Message is successfully processed and deleted from the queue.
2. **Consumer Failures**: Message isn't processed successfully and becomes visible again for reprocessing.
3. **Too-Short Retention Periods**: Messages are automatically deleted if they aren’t processed within the retention period.

**Server-Side Encryption**: Provides the ability to secure messages by encrypting them as they are stored in the queue.

**Pricing**: Based on the number of requests (each 64KB chunk of payload is billed as one request). Also includes additional costs for optional features.

**Using Partial Batch Responses**: Allows consumers to process and delete a subset of messages from a batch, reducing the likelihood of reprocessing the same message multiple times.

**Good Use Cases**: Ideal for applications requiring decoupling of component processes, handling sporadic traffic, and ensuring the reliability and scalability of message processing.

# SNS

**What**: Amazon SNS (Simple Notification Service) is a fully managed messaging service by AWS for both application-to-application (A2A) and application-to-person (A2P) communication.

**Pub/Sub**: SNS follows a publish/subscribe model where messages are published to topics and immediately delivered to subscribers.

**Difference from SQS**:

- SQS is a message queue service used for decoupling components of a system.
- SNS is a notification service designed for high-throughput, push-based messaging.

**When to Use SNS over SQS and Vice Versa**:

- **Use SNS** when you need to send the same message to multiple subscribers or for broadcasting notifications.
- **Use SQS** for simple queuing, decoupling of processes, or if you need to process messages in a particular order.

**Application to Application vs Application to Person**:

- **A2A**: SNS facilitates communication between distributed software systems.
- **A2P**: SNS can send messages to users via SMS, email, or mobile push notifications.

**Fanout Pattern**: In SNS, this involves a single message being published to a topic and then delivered to multiple SQS queues, Lambda functions, or HTTP endpoints.

**FIFO/Standard**:

- SNS supports FIFO (First-In-First-Out) topics for messages that need strict order and deduplication.
- Standard topics offer higher throughput with at-least-once delivery.

**Deduplication IDs**: For FIFO topics, deduplication IDs prevent the same message from being delivered multiple times (useful in scenarios where multiple identical messages might be published).

**Message Archive with Kinesis Firehose**: SNS can integrate with Kinesis Firehose to archive messages for compliance or analytical purposes.

**Error Handling in SNS vs SQS**:

- SNS doesn't have built-in awareness of consumer errors. If a Lambda function triggered by SNS fails, SNS won't retry.
- To handle failures, implement error handling in the consumer (like Lambda) itself or use DLQs to capture failed messages.

**Backoff Functions**: These are retry strategies that progressively increase the wait time between retries, useful in handling temporary failures in consumers.

**Handling DLQ Messages from SNS**:

- With SNS, the DLQ is for storing failed notification deliveries, not message processing failures.
- Redriving messages isn’t straightforward as there's no source queue. You may need to manually replay messages on SNS or send them directly to the consumer.

**Pricing**: SNS charges are based on the number of messages published, the number of notification deliveries, and optional features like SMS or mobile push notifications. Pricing can vary based on the region and the specific service used (SMS, HTTP, email, etc.).

# EventBridge

**What**: AWS EventBridge is a serverless event bus service that facilitates event-driven architecture by enabling software components to communicate with each other through events.

**Problem It Solves**: EventBridge helps in connecting applications with data from a variety of sources and routes that data to targets for processing. It simplifies the architecture for event ingestion, delivery, security, authorization, and error handling.

**Main Components**:

1. **Event Bus**: The central hub where events are sent.
2. **Event Rules**: Define the criteria for how incoming events are handled and routed.
3. **Targets**: The destinations where events are sent for processing.

**Event Bus in Depth**:

- Acts as the receiver of events from AWS services, SaaS applications, and custom applications.
- Supports different types of event buses like the default event bus for AWS services, partner event buses for SaaS, and custom event buses.

**Event Rules in Depth**:

- Rules match incoming events and route them to targets.
- Can filter events based on specific attributes, patterns, or content.

**Targets in Depth**:

- AWS services like Lambda functions, SNS topics, SQS queues, or even another EventBridge event bus.
- When a rule is met, the event is sent to the specified target(s) for processing.

**Custom Event Bus**:

- Allows you to create your own event bus for custom or third-party application events.
- Useful for isolating and managing events specific to your application or organization.

**Schedule Tasks with EventBridge Scheduler**:

- Enables scheduling of automated tasks or workflows at specific times using cron or rate expressions.

**Archive & Replay**:

- Archive: Save events for a specified period for auditing or analysis.
- Replay: Resend events from the archive to the event bus for reprocessing.

**Handle Failures with DLQs**:

- If an event fails to reach a target, it can be sent to a DLQ.
- DLQs allow you to diagnose and understand the failure, and then reprocess the failed events.

**Design for Failures**:

- Anticipate and handle component failures in an event-driven architecture.
- Implement retry policies, DLQs, and monitor events to ensure system resilience.

**Subscription Pattern**:

- Each consumer (service or application) subscribes to specific events via rules.
- Ensures that consumers process only the events relevant to them, reducing unnecessary processing.

**Schema Bindings**:

- Define the structure of event data (objects and attributes).
- Helps in validating the format of incoming events and assists in the development process by providing clear contracts for event data.
