 # Repo to learn Aws with practice. Contributions are most welcome.
 # # AWS Learning Guide

This repository serves as a guide for learning Infra designing,cost optimization,fault tolerant,scalabillity and security  

## Table of Contents

Introduction to AWS
- 1-EC2
  
  
  
          |-----------------|-----------------|-----------------|
          |     AMI         |      SG         |     ENI         |
          |     Template    |      On-demand   |Reseved Instance|
          |Schedule instance| Spot Instance   |Dedicated Instanc|
          |capacity reserve | Saving plan     |placement group  |
          |Ec2 troubleshot  |networking seting|Moniter and trobl|
          |Ec2 status check |

- 2-EBS STORAGE
- 3-VPC
- 4-Load-balancer
- 5-Auto-scalling
- 6-Route53
- 7-S3 bucket
- 8-IAM User
- 9-RDS
- 10-Terraform
- 11-ECS

# Ami
before Ami

1- ec2 instance don't backup

after Ami

1- ec2 instance backup

# Ec2 troubleshuting 
1- Attach with auto-scalling
2- change protection termination
3 - change stop & start protection 
4 - change shutdown behavior
5 - change auto-recovery behavior

# Ec2 Networking setting

1 - Attach network interface 

## why we need interface card

1 - more than workload and  NIC attach to ec2 instance

2- It works like a load balancer 

2 - Connect RDS database

3 - change source /destination

4 - Diassociate elastic Ip


# How to check status

1 - system status check

2 - instance status check 

## system status check 
if this check fail,there might issue with infrastructure that is hosting such as Aws power,Networking software system

## Instance status check 
Ec2 instance to identify hardware/software issue
Reboot
terminate
launch replacement

# Aws instance type
## General purpose: 
Normal purpose  (testing)
## Compute optimize:
High CPU
## Memory optimize
High memory
## Accerlated computing
High graphic
## Storage optimize
High storage 

# On-Demand
No capacity

High price 

Per hour payment

# Reserved instance 

Capacity guranty

Low price 

## payment plan:

1-No-upfront

2-Partial upfront

3-All upfront

1-3 year reserved

No, cancellation 

# Schedule instance 

capacity guranty

schdule instance available no every region

everyday  a running a instance 9:00am to 10:00pm


# Capacity reservation instance

On-demand ,capacity guranty reserved

# saving plan

On-demand price discount


# Dedicated Host

Complete rack buy 

High cost

Storage manage

Capacity gurantee

No, security issue

# spot instance

As a bids

90% discount 













  



