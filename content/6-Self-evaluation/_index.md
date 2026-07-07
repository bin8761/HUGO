---
title: "Self-Assessment"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

My internship ran from **17/04/2026 to 10/07/2026** at **Amazon Web Services Vietnam Company Limited**, within the **Workforce Bootcamp - First Cloud AI Journey** program. Over that period, the most useful part for me was not a single task, but the way the entire workflow connected: self-study, event participation, AWS Blog reading, deployment work, and workshop writing. Together, those activities helped me understand what it takes to bring a backend system from local development to a real cloud environment.

The report is based on **EAM Workspace - Enterprise Asset Management System**. From my perspective, the most important learning was not the UI itself, but the backend path behind it: API design, database connectivity, authentication flow, deployment configuration, and runtime monitoring. That is the part of the internship that shaped my thinking the most.

## 1. What I Learned

### 1.1. Understanding the AWS Foundation

Early on, I focused on the basics: **Cloud Computing**, **AWS Global Infrastructure**, **AWS Management Console**, **AWS Free Tier**, and **AWS Budgets**. These topics gave me the context I needed to understand AWS as a platform for operating backend systems, not just a place to create resources.

From there, I moved into the service groups that mattered most for backend work:

- **IAM** for users, roles, policies, and least-privilege access.
- **Networking** for VPC, subnets, route tables, Internet Gateway, NAT Gateway, Security Groups, and Network ACLs.
- **Compute** for EC2, AMIs, and instance types.
- **Database** for Amazon RDS for MySQL, endpoints, and connectivity from the backend.
- **Storage** for Amazon S3 and file handling.
- **Deployment** for Elastic Beanstalk and API Gateway.
- **Monitoring and Security** for CloudWatch, CloudTrail, WAF, KMS, and Secrets Manager.

After working through these topics, I stopped looking at AWS services as isolated tools. I started seeing them as parts of a backend delivery flow: build the API, connect the database, secure access, deploy the service, and observe it in production-like conditions.

### 1.2. Working Through the EAM Workspace Backend Flow

The project helped me connect theory with implementation. I could see how the backend path was assembled instead of only reading about it:

- **Amazon API Gateway** exposed `/api/*` requests.
- **AWS Elastic Beanstalk** hosted the Node.js/Express backend.
- **Amazon RDS for MySQL** stored application data.
- **Amazon SES** supported email and OTP delivery through SMTP credentials.
- **CloudWatch** handled logs, status checks, and troubleshooting.

That was the point where I understood the real difference between a local backend and a deployed backend. Once the application moves into AWS, details like environment variables, runtime health, routing, database access, and network settings become part of the backend itself.

### 1.3. Deployment and Debugging from a Backend Perspective

The most practical experience I gained was in deployment and debugging. I had to check Elastic Beanstalk environment variables, verify SES SMTP credentials, confirm that API Gateway could reach the backend, and make sure the deployment configuration was consistent from end to end.

The biggest lesson was about troubleshooting discipline. When something failed, I learned not to focus only on the source code. A backend issue can come from the API route, the environment configuration, the database connection, the IAM permissions, or the cloud setup itself. Because of that, I trained myself to trace the problem layer by layer until I found the real cause.

### 1.4. Reading Technical Material with a Backend Mindset

Another useful part of the internship was reading AWS Blog articles about EKS, Istio Ambient Mesh, EKS Control Plane Egress, and AWS Continuum. These articles helped me understand how AWS explains operational concerns, architecture choices, and service tradeoffs in real systems.

The events I attended also broadened my perspective. They gave me a wider view of cloud engineering, security, containers, automation, and how teams think about backend reliability and career development.

Because of that, I became more careful in how I study technical material. I do not just ask what a service does. I also ask when a backend should use it, what problem it solves, and how it affects the overall system behavior.

### 1.5. Writing Workshop Content

Writing the workshop was another area where I improved. It forced me to explain backend work in a way that someone else could repeat without guessing. For each step, I had to think about the purpose, the backend service involved, the configuration required, the validation result, and how the step fit into the full deployment flow.

That process taught me that documentation is part of backend work. A backend engineer does not only build APIs and connect databases. A backend engineer also has to explain how the system is deployed, verified, and maintained.

## 2. Self-Evaluation Table

| No. | Criteria | Description | Self-rating |
| --- | --- | --- | --- |
| 1 | AWS foundation | Understand core concepts of IAM, VPC, EC2, RDS, S3, CloudWatch, and AWS cost control | Fair |
| 2 | Backend deployment | Able to help deploy and verify the backend flow with API Gateway, Elastic Beanstalk, RDS, and SES | Fair |
| 3 | Backend architecture understanding | Understand how requests move from the client to API Gateway, backend services, and the database | Fair |
| 4 | Backend troubleshooting | Able to check endpoints, environment variables, logs, health checks, and database connectivity | Fair |
| 5 | AWS documentation reading | Able to read AWS Blog articles and technical documentation, then rewrite them in a clearer way | Good |
| 6 | Workshop writing | Able to describe deployment steps, add screenshots, and record validation results | Good |
| 7 | Cloud self-learning | Proactively learn AWS services based on project needs | Good |
| 8 | Teamwork | Coordinate with the team to understand backend, database, and deployment content | Fair |
| 9 | Progress management | Maintain worklog, proposal, blog, event, workshop, and self-assessment in stages | Fair |
| 10 | Overall | Complete an individual report connected to the project and the AWS learning process | Good |

## 3. Strengths

My strongest habit during the internship was initiative. When I ran into something unfamiliar, I did not wait for it to become a blocker. I usually tried to understand it early so I could keep moving. That made my learning process more structured and more useful.

I also became better at thinking in backend terms. Instead of seeing the application as a collection of screens, I started looking at request flow, API behavior, database access, runtime configuration, and deployment status. That shift made the project much easier to understand from a system perspective.

Another strength was documentation. I became more comfortable reading technical material, extracting the useful parts, and rewriting them into something clearer for a report or workshop. That mattered a lot because backend work is not only about making things run; it is also about making the system understandable and maintainable.

## 4. Areas for Improvement

There is still a gap between being able to use AWS services and being able to operate them confidently in a backend environment. I need more hands-on practice with AWS CLI and Infrastructure as Code so I can rely less on manual console work.

I also want to become faster at reading CloudWatch Logs and tracking backend issues in the cloud. That is one of the most important skills for backend work, especially when the system moves beyond a simple demo.

On the architecture side, I still want to go deeper into private subnets, NAT Gateway, VPC Endpoints, and the security patterns that go with them. I also need more practice with secrets management, IAM permission design, and separating dev, staging, and production environments.

Finally, I want to be more deliberate about AWS cost control when designing backend systems. It is easy to ignore in a demo, but it becomes a real concern in production-like environments.

## 5. Key Takeaways

The biggest takeaway for me is that AWS changes the way backend work is done. Once the project moved to AWS, I had to think about permissions, connectivity, logs, runtime health, and scaling, not just endpoints and business logic.

I also learned that backend knowledge becomes much clearer when it is connected to a real project. Services that look separate on paper become much easier to understand when they are used together inside an actual deployment flow.

The most practical lesson was probably this: if I can explain the backend deployment process clearly, then I understand it much better myself. Documentation forced me to slow down, verify my assumptions, and describe each step in a way that another person could repeat.

## 6. Direction After the Internship

After the internship, I want to keep growing in a backend-oriented direction:

- Practice infrastructure deployment with AWS CDK or Terraform.
- Study VPC, private subnets, load balancers, security groups, and IAM policies in more depth.
- Add CloudWatch Logs, metrics, and alarms for the backend.
- Learn more about S3 uploads, CloudFront, custom domains, and HTTPS.
- Practice backup and restore workflows for databases.
- Continue improving EAM Workspace toward a more production-ready backend architecture.

Overall, the internship gave me a more realistic view of backend engineering on AWS. I learned how AWS services work individually, but more importantly, I learned how to combine them into a system that can be deployed, monitored, and maintained with more confidence.
