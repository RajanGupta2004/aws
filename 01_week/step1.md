### ⏱️ 1 week

Before jumping deeply into AWS, understand these concepts:

* What is Cloud Computing?
* IaaS vs PaaS vs SaaS
* Region
* Availability Zone
* Scalability
* Elasticity
* High Availability
* Fault Tolerance
* Disaster Recovery
* Load Balancing
* Horizontal vs Vertical Scaling
* Stateless vs Stateful applications


### cloud computing

```
On-demand delivery of IT
resources over the Internet
with pay-as-you-go
pricing..

Access computing resources (like servers,
storage, databases, and software) over the
internet, rather than owning and
maintaining physical hardware.

Amazon Web Services (AWS)
Microsoft Azure
Google Cloud Platform (GCP)
IBM Cloud
Oracle Cloud
Alibaba Cloud
DigitalOcean
Salesfor

```


### 3. What is a Region?
```
A Region is a geographical area where AWS has data centers.
Examples:

Mumbai Region
Singapore Region

```


### 4. What is an Availability Zone?

An Availability Zone (AZ) is a separate data-center location inside an AWS Region.

For example:

Mumbai Region
│
├── Availability Zone 1
├── Availability Zone 2
└── Availability Zone 3


### 6. What is Elasticity?

Elasticity is similar to scalability, but there's an important difference.

Elasticity means automatically increasing or decreasing resources based on demand.

Example:

During normal time:

2 EC2 Servers

During a traffic spike:

10 EC2 Servers

After traffic decreases:

2 EC2 Servers


### 7. What is High Availability?

High Availability means your application should remain available even if something fails.

Bad design:

User
 ↓
ONE Server

Server fails:

User
 ↓
❌ Application Down

High Availability design:

              Load Balancer
              /           \
             ↓             ↓
           Server 1      Server 2
             AZ1           AZ2

If Server 1 fails:

              Load Balancer
                    |
                    ↓
                 Server 2

Users can still access the application.

👉 Remember:

High Availability = Keep the application running despite failures.


### 10. What is Load Balancing?

Imagine you have:

1000 users
    ↓
ONE Server

That server can become overloaded.

Instead:

             Users
               ↓
         Load Balancer
          /    |    \
         ↓     ↓     ↓
      Server Server Server
        1      2      3

The Load Balancer distributes incoming traffic between servers.

AWS provides Elastic Load Balancing (ELB), including Application Load Balancers.

Simple example

User 1 → Server 1

User 2 → Server 2

User 3 → Server 3

User 4 → Server 1

And so on.

👉 Remember:

Load Balancer = Traffic manager that distributes requests across servers.



### How to create the Usage threse hold and See the billing 
```
Billing and Cost Management
bugget and billing service
```