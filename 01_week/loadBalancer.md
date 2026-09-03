# ⚖️ Load Balancer in AWS

A **Load Balancer** distributes incoming traffic across multiple servers/EC2 instances.

### Simple Example

Without Load Balancer:

```text
Users
  │
  ▼
EC2 ─── 💥 Overloaded
```

With Load Balancer:

```text
             Users
               │
               ▼
        Load Balancer
          /    |    \
         ▼     ▼     ▼
       EC2    EC2    EC2
```

So, the main purpose is:

> **Load Balancer = Distribute traffic + Improve availability + Prevent one server from getting overloaded.**

---

# Types of AWS Load Balancers

AWS mainly provides **4 types**:

| Type     | Full Name                 | Mainly Used For             |
| -------- | ------------------------- | --------------------------- |
| **ALB**  | Application Load Balancer | HTTP/HTTPS applications     |
| **NLB**  | Network Load Balancer     | TCP/UDP, high performance   |
| **GWLB** | Gateway Load Balancer     | Network/security appliances |
| **CLB**  | Classic Load Balancer     | Older/legacy applications   |

### 1. ALB — Application Load Balancer ⭐

Used mainly for **web applications**.

```text
User
 ↓ HTTPS
ALB
 ↓
EC2 / EKS
```

It works at **Layer 7 (Application Layer)** and can route based on things like:

```text
/example
/api
/admin
```

**Most common choice for modern web applications.**

---

### 2. NLB — Network Load Balancer

Used when you need **very high performance and low latency**.

Works mainly at **Layer 4 (TCP/UDP/TLS)**.

```text
Client
  ↓
NLB
  ↓
EC2
```

Common for TCP/UDP workloads and applications requiring high throughput.

---

### 3. GWLB — Gateway Load Balancer

Used for **network/security appliances**.

```text
Traffic
   ↓
GWLB
   ↓
Firewall / Security Appliance
   ↓
Application
```

---

### 4. CLB — Classic Load Balancer

Older generation load balancer.

```text
CLB
 ↓
EC2
```

For new applications, you would generally choose **ALB or NLB** instead.

---

### 🧠 Easy way to remember

```text
ALB → Web applications → HTTP/HTTPS
NLB → Network traffic → TCP/UDP
GWLB → Security appliances
CLB → Old/legacy
```

**For your Node.js application, start by learning ALB first.**



### Script that install the Appache web server and that create on dummy html page 

```
#!/bin/bash

# Update packages
dnf update -y

# Install Apache web server
dnf install -y httpd

# Start Apache
systemctl start httpd

# Enable Apache to start automatically after reboot
systemctl enable httpd

# Create a dummy HTML page
cat > /var/www/html/index.html <<'EOF'
<!DOCTYPE html>
<html>
<head>
    <title>My AWS EC2 Server</title>
</head>
<body>
    <h1>Hello from AWS EC2!</h1>
    <p>Apache Web Server is working successfully.</p>
</body>
</html>
EOF

```


