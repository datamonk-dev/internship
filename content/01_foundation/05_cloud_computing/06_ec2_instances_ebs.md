
---

# EC2 — Your Personal Computer in the Cloud

Imagine you need a laptop — just for a few hours — to run a program or host a website.

Instead of buying one, what if you could **borrow a powerful virtual machine** from Amazon, pay by the hour, and return it when you're done?

That’s what **EC2** does.

---

## What Are EC2 Instances?

EC2 stands for **Elastic Compute Cloud** — a service that lets you **run virtual machines on demand**.

These virtual machines are called **instances**. And just like real machines, they have:

* CPUs (vCPUs)
* RAM
* Storage (temporary or permanent)
* Operating systems (Linux, Windows, etc.)

But here's the twist — they live in Amazon's data centers, and you can spin them up or shut them down in **minutes**, from anywhere.

---

## Separation of Compute and Storage

Let’s break it down:

* **Compute** = The power to run applications (like CPU + RAM)
* **Storage** = Where your files live (like SSDs or disks)

In EC2, these are separate on purpose. Why?

* You can stop or replace your compute instance without touching your data.
* You can attach storage to multiple instances.
* It gives you **flexibility** and **fault tolerance**.

This separation is what makes cloud computing so powerful.

---

## Block Storage vs Object Storage

Two types of storage you’ll often use:

| Storage Type            | Used With | Acts Like     | Good For                      |
| ----------------------- | --------- | ------------- | ----------------------------- |
| **Block Storage (EBS)** | EC2       | Hard disk/SSD | OS, databases, app files      |
| **Object Storage (S3)** | Any app   | Online drive  | Images, videos, backups, logs |

Think of **block storage** like your laptop's SSD — tightly coupled with the OS.

While **S3 object storage** is like Google Drive — store anything, retrieve it anytime, not tied to any specific machine.

---

##  How to Persist Data After Instance Stops?

By default, EC2 gives you **ephemeral storage** — like RAM, it’s wiped out when you stop the instance.

To persist data, use:

* **EBS Volumes** — attach them to EC2 like external hard drives
* **S3** — for larger files, backups, or less frequently accessed data

And you can:

* Detach the EBS volume before shutting down
* Take **snapshots** to back it up
* Attach it later to another EC2

So even if the instance dies, **your data lives on**.

---

##  On-Demand vs Reserved vs Spot Instances

You don’t always need the same pricing plan. AWS gives you 3 modes:

| Type          | Pricing             | Best Use                   | Gotcha                |
| ------------- | ------------------- | -------------------------- | --------------------- |
| **On-Demand** | Pay per hour/second | Short tasks, experiments   | Costliest             |
| **Reserved**  | 1–3 year commitment | Stable long-term apps      | Pay upfront           |
| **Spot**      | Up to 90% cheaper   | Batch jobs, stateless apps | Can be killed anytime |

 Spot = airline seat clearance sale. Great deals, but not guaranteed.

---

## Public IP vs Elastic IP vs Internal IP

EC2 instances come with 3 kinds of IPs:

| IP Type         | Visible To      | Changes?       | Purpose                        |
| --------------- | --------------- | -------------- | ------------------------------ |
| **Public IP**   | Internet        | Yes, on reboot | Temporary web access           |
| **Elastic IP**  | Internet        | No             | Static IP for production apps  |
| **Internal IP** | Private network | No             | For communication between EC2s |

Use **Elastic IP** when you want a **permanent domain or address** — like pointing your DNS to it.

---

## Monitoring and Alerts (a.k.a "Don’t Let It Burn Down")

You can’t sit and stare at your EC2 24/7.

Use **CloudWatch** to monitor:

* CPU usage
* Disk activity
* Network traffic
* Memory (with some setup)

And set **alarms** like:

> "If CPU > 80% for 5 minutes, send me an email"

It’s like having a smoke alarm for your cloud machines.

[ Learn more about CloudWatch here](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)

---

##  Firewall Rules — Meet the "Security Group"

In AWS, your EC2 lives inside a **VPC** (a private network), and access is controlled by:

* **Security Groups** = Firewalls for EC2
* **Subnet rules** = Network-level controls

By default, all incoming traffic is blocked.

You can allow specific traffic like:

```text
 Allow TCP port 22 from your IP (for SSH)
 Allow TCP port 80 or 443 (for web traffic)
 Block everything else
```

Think of it as giving people a key to a specific door in your house — not access to the whole building.

---

##  Using EC2: GUI vs CLI

### GUI (Console):

Easy to launch EC2:

1. Go to [EC2 Dashboard](https://console.aws.amazon.com/ec2)
2. Click “Launch Instance”
3. Choose OS, instance type, storage, and security
4. Done!

You’ll get an instance you can SSH into using your key.

---

### CLI (Command Line):

Install the [AWS CLI](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html) and run:

```bash
aws ec2 run-instances \
  --image-id ami-xxxx \
  --instance-type t2.micro \
  --key-name my-key \
  --security-group-ids sg-xxxx \
  --subnet-id subnet-xxxx
```

You can automate instance creation, scaling, and deletion.

CLI is essential for DevOps, scripting, and real-world automation.

---

##  Exercise Time

 Launch a new EC2 instance from AWS Console
 SSH into it using your terminal
 Install NGINX (`sudo apt install nginx`)
 Open the instance’s public IP in your browser — Hello Web!
 Now stop the instance and relaunch — notice public IP changes
 Allocate and attach an **Elastic IP** — make it permanent

Bonus:

* Create a **CloudWatch alarm** for high CPU
* Try creating an **EBS volume**, attach it, format it, and mount it

---

