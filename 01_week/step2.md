


### **EC2 (Elastic Compute Cloud)**

> **EC2 is a virtual server that you rent from AWS to run your applications.**

* **Instance:** A virtual server that you launch.

* **AMI (Amazon Machine Image):** A pre-configured template for your instance.

* **Instance Type:** Different configurations of CPU, memory, storage, and network capacity.

* **EBS (Elastic Block Store):** Persistent storage that can be attached to your instance.

* **Security Group:** A virtual firewall that controls traffic to and from your instance.

* **Elastic IP:** A static IP address designed for dynamic cloud computing.

* **Key Pair:** Secure login credentials used to access your instance.

* **Spot Instance** Unused instance i.




### how to do SSH 

```
 ssh -i awsec2key.pem ec2-user@43.204.147.224

 ```


 ### Security group and how to create and edit and delete the 
  

### VPC (Vitual private cloud):
. What is VPC?

VPC = Virtual Private Cloud

A VPC is your own isolated virtual network inside AWS where you can launch AWS resources such as:

EC2
RDS
Load Balancers
ECS
Lambda
etc.

Think of a VPC as the network of a company, but created virtually inside AWS.


### What are Private IP, Public IP, and Elastic IP?

**🔹 Private IP**

* Used for communication **inside the VPC/private network**.
* Example: `10.0.1.10`
* Not directly accessible from the internet.

**🔹 Public IP**

* Used for communication **over the internet**.
* Example: `13.234.56.78`
* Can change when an EC2 instance is stopped and started.

**🔹 Elastic IP**

* A **fixed (static) public IP address**.
* Stays the same even when you stop/start an EC2 instance.
* Useful when you need a permanent public IP.

### Easy way to remember

```text
Private IP  → Inside VPC
Public IP   → Internet + Can change
Elastic IP  → Internet + Fixed
```




### how to Allocate and Associate Elastic IP 
first Allocate and and the Associte this Elatice IP to the instance



### how to install the packages or the run some script when the ec2 instance luanch 

