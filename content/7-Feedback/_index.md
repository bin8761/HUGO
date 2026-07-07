---
title: "Sharing and Feedback"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

The First Cloud AI Journey program gave me a backend-oriented view of AWS that I did not get from classroom learning alone. What stood out most was that the program did not treat deployment as a final step. Instead, it forced me to think about the full backend path: how the API is routed, how the database is connected, how runtime variables are managed, how logs are checked, and how the system is verified after deployment.

That approach made the internship feel practical. I was not only learning AWS service names. I was learning how those services behave together in a real architecture.

## 1. Overall Impression

My overall impression of the program is very positive. The program helped me understand that backend work on AWS is not only about writing code. It also includes deployment setup, access control, service integration, monitoring, and troubleshooting.

For me, that was the biggest value of the internship. It connected the technical concepts I had learned before with the reality of running an application on cloud infrastructure.

## 2. Backend Learning Experience

From a backend perspective, the most useful part of the program was learning how a request flows through the system.

- The client sends a request.
- API Gateway receives and forwards it.
- Elastic Beanstalk runs the backend service.
- RDS stores the application data.
- SES handles email and OTP delivery.
- CloudWatch helps with inspection and debugging.

This flow made AWS much easier to understand. I no longer saw each service as an isolated tool. Instead, I saw how they support the backend in different layers.

The program also helped me understand why backend systems need environment variables, database credentials, network rules, and runtime checks. These are not optional details. They are part of the backend itself.

## 3. Deployment Experience

The most practical part of the internship was deployment. I had to care about details that do not appear in local development, such as:

- whether the backend reads environment variables correctly
- whether the API Gateway route points to the right service
- whether the database connection string is valid
- whether SES credentials match the SMTP setup
- whether the health endpoint responds as expected
- whether logs in CloudWatch show the real cause of an issue

This made me more careful when working on backend systems. I learned that a deployment problem is often not a single error, but a chain of small configuration issues.

Another useful lesson was that backend debugging on AWS requires patience. Sometimes the issue is in the code, but sometimes it is in the route, the environment, the database, the security group, or the service configuration. The internship helped me build a more systematic way of checking those layers.

## 4. Support From Mentor and Team

The support from the mentor and the team was one of the strongest parts of the program. I appreciated that I was not simply given the final answer. I was usually guided to inspect the problem step by step so I could understand the cause myself.

That style of support was useful for backend learning because backend issues are rarely solved well by guessing. I needed to inspect the flow, validate assumptions, and verify each service one by one.

The team also helped by sharing context around the project architecture and the deployment workflow. That made it easier for me to connect the report content with the actual system behavior.

## 5. Most Valuable Part

The most valuable part for me was understanding how a backend system becomes operational on AWS. I could see the difference between a project that only runs locally and a project that is ready to be deployed, monitored, and checked in a cloud environment.

The model that stayed in my mind most clearly was:

`API Gateway -> Elastic Beanstalk -> RDS -> SES / CloudWatch`

That is the point where the internship became truly meaningful for me. It was no longer just about learning AWS features. It was about understanding backend architecture as a working system.

## 6. Difficulties During the Program

The main difficulty I faced was not the lack of information, but the number of moving parts. Backend deployment on AWS requires attention to many details at the same time:

- backend routing
- environment configuration
- database access
- email credentials
- logging
- health checks

At first, this was overwhelming. But over time, it trained me to think more carefully and troubleshoot more methodically. I also realized that writing clear documentation is part of the solution, because it makes the system easier to reproduce and debug later.

## 7. Suggestions for the Program

If I were to suggest one improvement, it would be to provide more backend-focused deployment checklists. A short checklist for API Gateway, Elastic Beanstalk, RDS, SES, and CloudWatch would help students verify their setup faster.

I also think a small troubleshooting guide would be useful, especially for common issues such as environment variables, health checks, routing, and database connectivity. Those are the places where beginners usually spend the most time.

Another helpful addition would be a sample backend deployment flow that clearly shows what should be checked before and after deployment. That would make the learning path more practical for future interns.

## 8. Expectations After the Program

After the program, I would like to keep moving in a backend and cloud direction. The areas I want to study further include:

- AWS CDK or Terraform for infrastructure as code
- CloudWatch Logs and alerting
- VPC, private subnets, NAT Gateway, and VPC Endpoints
- IAM policies and secrets management
- RDS backup and restore workflows
- more production-like backend deployment patterns

Overall, the program gave me a more realistic view of backend engineering on AWS. It showed me that a backend system is not complete until it can be deployed, monitored, debugged, and maintained with confidence.
