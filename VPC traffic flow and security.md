<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** Cody Chinothai  
**Email:** cchinothai@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is your own delegated space within the cloud where you can control your resources and the traffic that flows into them. It's useful to control client/user requests from a cloud security perspective to ensure that you are safely transferring data to and from your resources. 

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to configure our own route tables, security groups, and network ACLs.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was the default route tables, security groups, and network ACLs that were already setup for our existing VPC. 

### This project took me...

// Project time: ~1-2 hours. 

---

## Route tables

Route tables map the expected traffic from our resources within our subnet. Think of it like a GPS. Just like a GPS helps people get to their destination in a city, a route table is a table of rules, called routes, that decide where the data in your network should go.

Every subnet in your VPC needs to be linked to a route table, because the table tells your subnet's traffic where to travel to send and receive data. For example, if you have a web server (i.e. an EC2 instance) hosting a website, the EC2 instance's subnet needs a route table that knows how to direct incoming traffic to the website.



Routes tables are needed to make a subnet public because there must be a defined route from your resources to your internet gateway if you have internet-bound trafiic. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target. The destination refers to the IP address it wants to reach, whereas the target is the means that they use to reach that destination. For example, you may want to end up at a destination with a certain IP on the internet, so you target the internet gateway in order to do so. 

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 with the target being the internet gateway that we setup for our current VPC.

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups define the allowable inbound/outbound traffic for each resource in your subnet. 

If VPCs are cities and subnets are neighbourhoods, a security group is a security checkpoint, or security guard, at the entrance for each building (resource) in that neighbourhood (subnet).

### Inbound vs Outbound rules

Inbound rules are the protocol specifications that are allowed to access your resource. 

If you need your resource to be accessible to the public, you may want to allow inbound connection from any IPV-4 address via an HTTP protocol. 

You can make this more restrictive depending on the use case of your resource. 

Outbound rules are the data that your resources send out. 

Examples of outbound data: Your server requests data from another service; your app sends out an email notification.

By default, AWS allows actions for all outbound data from your resource.  

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are similar to security groups but they operate at the VPC level. 

Think of Network ACLs as traffic cops stationed at every entry and exit point of your subnet, checking each data packet against a table of ACL rules before allowing them through.

### Security groups vs. network ACLs

Security groups operate at a narrower scope - the actual resources themselves. This means that it's within the subnet level. Network ACLs on the other hand will apply to all of the subnets in the current VPC. 

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic, denoted by the (*) rule number. 

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all traffic, until you specify by adding a new inbound/outbound rule. 

![Image](http://learn.nextwork.org/enthusiastic_turquoise_radiant_monstera_deliciosa/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

---

---
