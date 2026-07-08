---
title: "Self-Assessment"
date: 2026-07-05
weight: 6
chapter: false
pre: " <b> 6. </b> "
---

During the internship period from 17/04/2026 to 10/07/2026 at Amazon Web Services Vietnam Company Limited in the Workforce Bootcamp - First Cloud AI Journey program, I built a more concrete understanding of cloud work by combining self-study, event participation, technical reading, implementation practice, and report writing.

The main project in this report is EAM Workspace - Enterprise Asset Management System. My direct contribution was focused on the frontend side, but the broader value of the internship came from learning how a complete web system is assembled, deployed, observed, and explained in an AWS environment.

---

## 1. Achievements

### 1.1. Building a Practical AWS Baseline
At the start of the internship, I focused on the essential concepts that appear again and again in cloud projects: Cloud Computing, AWS Global Infrastructure, AWS Management Console, AWS Free Tier, AWS Budgets, and the habit of watching cost impact early instead of late.

From there, I moved through the core service groups in a more structured way:
* **Identity and access:** Role-based access control (RBAC), IAM Policy Simulator, cross-account roles, and Cognito user pools.
* **Networking:** Transit Gateway, VPC peering, flow logs, Bastion hosts, Application Load Balancers, and Route 53 DNS routing.
* **Compute:** Auto Scaling Groups, Launch Templates, Spot Instances, AWS Lambda for serverless tasks, and containerized layers.
* **Data layer:** Amazon RDS Read Replicas, Multi-AZ deployment for high availability, connection pooling, and automated snapshot policies.
* **Storage:** S3 Lifecycle Policies, Glacier deep archive, cross-region replication, CloudFront CDN integration, and signed URLs.
* **Deployment:** AWS CodePipeline, CodeBuild, CodeDeploy for automated CI/CD, and infrastructure provisioning patterns.
* **Operations and protection:** GuardDuty threats, AWS Config compliance, Inspector vulnerabilities, Systems Manager, and proactive alerting mechanisms.

This gave me a clearer view of AWS as an integrated platform rather than a set of isolated tools.

### 1.2. Understanding the Project Through Its Cloud Architecture
The most valuable part of the internship was seeing how AWS services map to a real application architecture instead of learning them in isolation.

In EAM Workspace, I observed the role of each service in the end-to-end flow:
* **Amazon CloudFront** accelerated asset delivery and served the static frontend globally.
* **AWS WAF** inspected incoming traffic at the edge to block malicious SQL injections.
* **Application Load Balancer** distributed user requests across multiple availability zones.
* **Amazon ElastiCache (Redis)** reduced database stress by caching frequent asset queries.
* **AWS Secrets Manager** rotated database credentials automatically without code redeployment.
* **Amazon SNS** managed notification fan-outs for critical enterprise asset alerts.

This project made the dependencies between layers much more tangible. A deployment is not finished when the code runs locally; the real work also includes routing, environment variables, permissions, database access, build configuration, and service health.

### 1.3. Deployment Discipline and Debugging Habits
Working through deployment issues helped me develop a more disciplined troubleshooting process. I learned to break a failure into smaller checks instead of treating it as one vague problem.

Some of the operational lessons I gained were:
* Analyzing CloudFront custom error responses before modifying asset distribution settings.
* Debugging security group ingress rules when container instances fail to reach the cache layer.
* Decoding IAM permission denied errors using the AWS CLI to locate missing actions.
* Inspecting database connection timeout configurations within the target group settings.
* Identifying whether a latency spike belongs to network serialization or unindexed database queries.
* Writing deployment steps in a way that another person could repeat them later.

That workflow trained me to inspect configuration first, code second, and symptoms in context rather than in isolation.

### 1.4. Reading AWS Content and Extracting the Useful Parts
Another meaningful part of the internship was reading AWS Blog articles and turning them into short, useful notes. I studied topics such as EKS, Istio Ambient Mesh, EKS Control Plane Egress, and AWS Continuum.

This practice improved two skills at once. First, it helped me understand how AWS explains architecture and operational trade-offs. Second, it trained me to compress a technical article into the ideas that matter for learning and implementation.

The events I attended also widened my perspective. They covered subjects like security, AI, containers, automation, recruiting, and how cloud platforms are used in enterprise workflows.

### 1.5. Turning Work Into Clear Documentation
Writing the workshop was a separate skill from building the system, and I improved by treating it that way. The workshop required me to describe a technical process in a sequence that others could follow without guessing.

While preparing the deployment guide, I had to think about:
* The purpose of each step.
* Which AWS service was being configured.
* What inputs or settings were required.
* What screenshot or proof should be captured.
* What the expected result should look like.
* How to confirm that the step succeeded.

This showed me that good documentation is not a transcript of actions. It is a guided explanation of intent, setup, validation, and outcome.

---

## 2. Self-Evaluation Table

| No. | Criteria | Description | Self-rating |
| :--- | :--- | :--- | :--- |
| 1 | AWS foundation | Understand the main ideas behind IAM, VPC, EC2, RDS, S3, CloudWatch, and AWS cost awareness | Fair |
| 2 | AWS deployment | Able to support a demo deployment covering frontend, backend, API Gateway, RDS, and SES | Fair |
| 3 | Cloud architecture understanding | Understand how traffic moves from Amplify to API Gateway, Elastic Beanstalk, and RDS | Fair |
| 4 | Deployment troubleshooting | Able to inspect endpoints, environment variables, health checks, rewrite rules, and database connectivity | Fair |
| 5 | AWS documentation reading | Able to read AWS Blog and technical documentation and restate the ideas more clearly | Good |
| 6 | Workshop writing | Able to explain deployment steps, add screenshots, and document validation results | Good |
| 7 | Cloud self-learning | Proactively explore AWS services based on what the project requires | Good |
| 8 | Teamwork | Coordinate with the team to understand frontend, backend, database, and deployment details | Fair |
| 9 | Progress management | Keep worklog, proposal, blogs, events, workshop, and self-assessment organized by stage | Fair |
| 10 | Overall | Complete an individual report connected to both the project and the AWS learning process | Good |

---

## 3. Strengths

* I kept learning independently and did not wait for tasks to be fully explained before researching AWS services.
* I could connect cloud concepts with the actual deployment flow used by EAM Workspace.
* I became more effective at reading technical material and rewriting it into clearer report language.
* I gained a better understanding of how the frontend, API, backend, and database interact in an AWS deployment.
* I improved my ability to document steps, capture evidence, and explain verification results.

---

## 4. Areas For Improvement

* I still need more hands-on practice with AWS CLI and Infrastructure as Code so that I rely less on manual console actions.
* I need to sharpen my skill in reading logs and tracing backend failures through CloudWatch.
* I want a deeper understanding of network isolation, private subnets, NAT Gateway behavior, VPC Endpoints, and secure connectivity patterns.
* I should spend more time on IAM design, secret handling, and separating environments such as development, staging, and production.
* I need to think more systematically about cost control when designing cloud deployments.

---

## 5. Lessons Learned

This internship changed how I think about cloud work. I no longer see AWS only as a place to deploy an app. I see it as a set of decisions about structure, access, monitoring, data flow, and operational reliability.

I also learned that theory becomes much easier to remember once it is attached to a working project. Services like Amplify, API Gateway, Elastic Beanstalk, RDS, and SES make more sense when they are used together in one system rather than studied one by one.

The workshop writing process was especially useful because it forced me to turn experience into reusable knowledge. That is important in cloud engineering, where clear steps and clear evidence matter just as much as the final result.

---

## 6. Direction After The Internship

After the internship, I want to keep developing in practical AWS directions:
* Learn AWS CDK or Terraform and use them for repeatable infrastructure work.
* Study VPC design, private networking, load balancing, Security Groups, and IAM more deeply.
* Add stronger monitoring with CloudWatch Logs, metrics, and alarms.
* Practice S3 upload patterns, CloudFront, custom domains, and HTTPS configuration.
* Improve database backup and restore skills and apply AWS cost optimization more deliberately.
* Continue refining EAM Workspace so it looks closer to a production-ready application.

Overall, the internship gave me a more grounded view of cloud computing. I learned not only how to use AWS services, but also how to combine them into a deployable system and document that system in a way that others can follow.
