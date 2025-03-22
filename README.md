# Project:  Performing a Basic Audit of an AWS Environment

Date: 2025-02-25

## Description

This project goes through the steps to perform basic audits of core AWS resources. It will use the AWS Management Console to understand how to audit the use of multiple AWS services, ...

## Objectives

- Review user permissions in AWS IAM
- Capture audit evidence using AWS IAM Policy Simulator
- Review Inbound and Outbound networking rules for Amazon EC2 Security Groups
...

## AWS Services Used

- Amazon Elastic Compute Cloud (Amazon EC2)
- Amazon Virtual Private Cloud (Amazon VPC)
...

## Task 1: Audit user permissions in IAM

AWS Identity and Access Management (IAM) enables the engineer to securely control access to AWS services and resources for end users. Using IAM, the engineer can create and manage AWS users and groups and use permissions to allow and deny their access to AWS resources.

In this project, the auditor will launch IAM secure AWS Access Control in order to review permissions, group assignments and roles associated with the auditing instance:

Launch the AWS Console:

<img src="https://imgur.com/4znV30l.jpg" height="80%" width="80%" alt="Open AWS Console"/>

### Review permissions

1. At the top of the AWS Management Console, in the search bar, search for and choose IAM.

<img src="https://imgur.com/UwO7osv.jpg" height="80%" width="80%" alt="Open IAM Console"/>

2. In the navigation pane at the left of the page, under Access management, choose Users.

<img src="https://imgur.com/zFDjtUM.jpg" height="80%" width="80%" alt="Select Users"/>

3. On the Users page, choose the link for user-1 to view its details.
...

### Run the IAM Policy Simulator

...

12. Choose Run Simulation.

<img src="https://imgur.com/6KZqGzF.jpg" height="80%" width="80%" alt="Policy Simulator Run"/>

> Expected output: The Action Settings and Results section displays the effective permissions for user-1, similar to this:

...

### Collecting audit evidence

From an audit evidence standpoint, the auditor can capture the IAM settings and the IAM Policy Simulator output to be used as support evidence in user access reviews (UARs).

## Task 2: Review the security configuration of Amazon EC2 instances

### What is Amazon EC2?

Amazon Elastic Compute Cloud (Amazon EC2) is a web service that provides resizable compute capacity...

### What is a security group?

A security group acts as a virtual firewall for your instance to control inbound and outbound traffic...

The following are basic characteristics of security groups:

- Can specify allow rules, but not deny rules.
- Can specify separate rules for inbound and outbound traffic.
- By default, no inbound traffic is allowed until the engineer adds inbound rules to the security group.
...

### Review running Amazon EC2 instances

14. At the top of the AWS Management Console, in the search bar, search for and choose EC2.

<img src="https://imgur.com/KlJqESy.jpg" height="80%" width="80%" alt="Launch EC2 Console"/>

...

### Review the web server security group

16. In the navigation pane at the left of the page, under Network & Security, choose Security Groups.

<img src="https://imgur.com/4pt917g.jpg" height="80%" width="80%" alt="EC2 WebServer Sec Group"/>

17. Select WebServerSG.

<img src="https://imgur.com/fGr08Po.jpg" height="80%" width="80%" alt="Web Server WebServerSG"/>

...

19. Review the Inbound rules.

> Note: The engineer can specify a number of different sources in security group rules, such as anywhere, a custom IP address or CIDR, My IP (the IP address of your current workstation), or specific security groups. The rules chosen to implement are a critical step towards running instances and services within Amazon EC2.

### Review the bastion host security group

...

22. To review the inbound and outbound rules, choose the Inbound rules and Outbound rules tabs respectively.

### Review the SQL server security group

23. Clear BastionSG.
24. Select SQLSG.
...

### Collecting audit evidence

From an audit evidence standpoint, these findings can support resource access isolation and data protection from internal or external threats. All access to the SQL Server instance is restricted via a jump box (Bastion Host); therefore, no internal user has direct access to it. Externally, the SQL Server only communicates with the web service via the WebServerSG and SQLSG security groups.

## Task 3: Review Amazon VPC security configurations

### What is Amazon VPC?

Amazon Virtual Private Cloud (Amazon VPC) permits the organization to launch AWS resources into a virtual network that the engineer has defined...

Amazon VPC provides two features that can be used to increase security for a VPC:
...

When the engineer launches an instance in a VPC, they can associate one or more security groups...

### Locate Amazon EC2 instance VPC configurations

...

29. In the Instance summary section, locate the VPC ID value and copy it to your favorite text editor.

<img src="https://imgur.com/5P4yeRn.jpg" height="80%" width="80%" alt="VPC Instance ID"/>

> Note: The VPC ID should look similar to: `vpc-0385934dd2bef2354`. Every VPC is associated with a VPC ID. In the next section, you identify the VPC that is associated with this VPC ID.

### Review existing VPCs, subnets, and NACLs

...

## Task 4: Audit CloudWatch metrics and alarms

In this task, the auditor reviews built-in CloudWatch metrics, alarms, and service health associated with...

### What is Amazon CloudWatch?

Amazon CloudWatch is a monitoring and management service...

### Audit CloudWatch metrics and alarms

...

43. Choose the Graphed metrics tab.
   
> Note: You can change the Statistic and the Period settings to customize the view to your liking.

<img src="https://imgur.com/bSSzpsH.jpg" height="80%" width="80%" alt="SQL Graphed metrics"/>

### Review CloudWatch data for EBS volumes

In addition to viewing Amazon CloudWatch metrics and alarms via the CloudWatch dashboard, one can also view the data in other locations. In this section, the auditor will review Amazon CloudWatch data for Amazon EBS volumes.

44. At the top of the AWS Management Console, in the search bar, search for and choose EC2.

<img src="https://imgur.com/voBWnol.jpg" height="80%" width="80%" alt="EC2 launch"/>

...

## Task 5: Audit CloudTrail logs

### What is AWS CloudTrail?

AWS CloudTrail is a service that enables governance, compliance, operational auditing, and risk auditing of an AWS account...

### Find CloudTrail logs

...

55. Choose the AWSLogs/ link.

<img src="https://imgur.com/LpWidxv.jpg" height="80%" width="80%" alt="S3 Object details"/>

...

An alternate approach to viewing Amazon CloudTrail logs is to download them locally and use a text editor along with the JSON Viewer plug-in.

### 3rd Party Solutions

...

## End project

Follow these steps to close the console and end the project.

...

## Conclusion

The following actions were taken:
- Reviewed user permissions in AWS IAM.
- Captured audit evidence using AWS IAM Policy Simulator.
...

## Additional Resources

- [Testing IAM policies with the IAM policy simulator](https://aws.amazon.com/iam/policy-simulator/)
- [AWS Security Center](https://aws.amazon.com/security/)
