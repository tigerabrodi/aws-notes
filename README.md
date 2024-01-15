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
