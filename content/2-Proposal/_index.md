---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# Enterprise Asset Management Proposal
## Unified AWS platform for asset tracking, assignment, maintenance, and reporting

### 1. Executive Summary
The Enterprise Asset Management proposal describes an internal system for admin and employee users to manage assets in a single centralized workflow. The platform covers asset tracking, assignment, return, transfer, maintenance, reporting, attachment uploads, OTP email notifications, and auditable history in one place.

The solution uses React + Vite on AWS Amplify Hosting for the frontend, Node.js + Express on AWS Elastic Beanstalk behind an Application Load Balancer for the backend, and Amazon RDS for MySQL through Prisma for persistent data. Supporting services include Amazon S3 private buckets for files, Amazon SES for OTP and notifications, AWS Secrets Manager and Systems Manager Parameter Store for configuration, plus CloudWatch, CloudTrail, and Session Manager for operations and audit.

### 2. Problem Statement
### What's the Problem?
Asset operations are currently fragmented across manual processes, ad hoc files, and separate communication channels. Admin and employee workflows need clear role separation, but without a single system it is difficult to track who owns which asset, who received it, when it was returned, or whether maintenance is still pending.

### The Solution
The platform centralizes asset records, assignment, return, transfer, maintenance, feedback, notifications, and attachment handling in one internal system. Role-aware screens let admins manage the full asset lifecycle while employees can focus on self-service actions such as viewing assigned assets, submitting requests, and checking status updates. This removes duplicated records and makes the workflow auditable from end to end.

### Benefits and Return on Investment
The result is faster asset processing, fewer handoff mistakes, and a single source of truth for operational history. Centralized records improve reporting quality, make file attachments and audit trails easier to retrieve, and reduce the time spent reconciling scattered spreadsheets or chat messages. The internal team also gets a more stable MVP foundation for future expansion without changing the core workflow.

### 3. Solution Architecture
The solution uses a layered AWS architecture built for internal asset operations. React + Vite is hosted on AWS Amplify Hosting, the public API entry point is an Application Load Balancer, and the backend runs on AWS Elastic Beanstalk with Node.js + Express. Persistent business data is stored in Amazon RDS for MySQL and accessed through Prisma. The architecture is detailed below:

![Enterprise Asset Management Architecture Overview](/images/2-Proposal/enterprise-asset-management-architecture-overview.svg)

![Enterprise Asset Management Request Flow](/images/2-Proposal/enterprise-asset-management-request-flow.svg)

### AWS Services Used
- **AWS Amplify Hosting**: Hosts the React + Vite frontend.
- **Application Load Balancer**: Receives API traffic and routes it to the backend.
- **AWS Elastic Beanstalk**: Runs the Node.js + Express application.
- **Amazon RDS for MySQL Single-AZ**: Stores assets, assignments, maintenance history, and reports.
- **Amazon S3 private bucket**: Stores attachments, uploaded files, and exported documents.
- **Amazon SES**: Sends OTP and internal notification emails.
- **AWS Secrets Manager**: Stores sensitive secrets such as database credentials and mail credentials.
- **AWS Systems Manager Parameter Store**: Stores environment-specific configuration.
- **Amazon CloudWatch**: Collects logs and alarms for application health.
- **AWS CloudTrail**: Records AWS-level audit activity.
- **AWS Systems Manager Session Manager**: Supports secure administration without public SSH.

### Component Design
- **Frontend**: React + Vite provides admin and employee screens for asset workflows.
- **API entry**: The Application Load Balancer forwards API requests into the backend tier.
- **Application tier**: Node.js + Express implements authentication, role checks, and business rules.
- **Data storage**: Amazon RDS for MySQL stores the core relational model through Prisma.
- **File handling**: Amazon S3 private bucket stores attachments, evidence files, and exports.
- **Notifications**: Amazon SES sends OTP and notification emails from backend actions.
- **Secrets and config**: Secrets Manager and Parameter Store keep runtime values out of source code.
- **Observability**: CloudWatch, CloudTrail, and Session Manager support monitoring, audit, and operations.

### 4. Technical Implementation
**Implementation Phases**
This project moves through four practical implementation phases that match the actual asset management workflow:
- Frontend and user-role foundation: set up React + Vite screens for admin and employee access, route structure, shared layout, and basic auth-aware UI behavior.
- Backend foundation, auth, and database schema: implement Node.js + Express APIs, JWT authentication, role-based access control, Prisma models, and MySQL schema setup.
- Asset lifecycle flows: build asset, assignment, return, transfer, maintenance, inventory, reporting, attachment, and notification flows end to end.
- Deployment, QA, documentation, and demo hardening: validate AWS deployment, stabilize error handling, prepare seed data, write docs, and polish the demo path.

**Technical Requirements**
- Frontend stack: React + Vite with role-aware admin and employee screens.
- Backend stack: Node.js + Express with JWT, bcrypt, Prisma, and MySQL.
- Testing stack: Playwright for end-to-end checks and Jest for backend or service-level tests where applicable.
- Deployment stack: AWS Amplify Hosting, AWS Elastic Beanstalk, Amazon RDS for MySQL, Amazon S3 private bucket, Amazon SES, AWS Secrets Manager, AWS Systems Manager Parameter Store, Amazon CloudWatch, AWS CloudTrail, and AWS Systems Manager Session Manager.
- Operational requirements: keep the schema aligned between local development and production, preserve role-based access control, and make the demo flow stable enough for presentation.

### 5. Timeline & Milestones
**Project Timeline**
The timeline is organized by dependency over five weeks so the team can build the foundation first and then layer the lifecycle flows on top.

- Week 1: Foundation and contracts
  - Build the backend foundation, core schema, API contracts, frontend shell, and QA outline.
  - Milestone: schema, API contract, app skeleton, login flow.
- Week 2: Core management features
  - Finish JWT login, complete core CRUD, connect admin CRUD screens, and prepare the employee profile shell.
  - Milestone: core CRUD complete.
- Week 3: Asset lifecycle features
  - Implement assignment APIs and screens, employee asset detail, and the broken-asset report flow.
  - Milestone: assignment, employee views, broken asset report complete.
- Week 4: Maintenance, inventory, reports, and AWS trial
  - Implement maintenance, inventory, and report APIs, build the remaining admin screens, and run the first AWS deployment trial.
  - Milestone: maintenance, inventory, reports, first AWS deployment complete.
- Week 5: Final deployment, QA, and presentation
  - Finalize deployment, verify data and auth stability, prepare seed data, QA checklist, screenshots, and the demo script.
  - Milestone: final deployment, demo data, QA, presentation complete.

### 6. Budget Estimation
The budget is based on the current AWS architecture and should be recalculated in AWS Pricing Calculator once the final instance sizes are locked.

### Estimated Infrastructure Costs
- Application Load Balancer + Elastic Beanstalk compute: UNCONFIRMED, roughly $28-40/month combined for the current demo-sized stack.
- Amazon RDS for MySQL Single-AZ: UNCONFIRMED, roughly $12-19/month including modest storage and backup usage.
- Amazon S3 private bucket: UNCONFIRMED, usually low single-digit monthly cost for attachments and exports.
- Amazon SES: UNCONFIRMED, usually low single-digit monthly cost for OTP and internal email volume.
- Amazon CloudWatch: UNCONFIRMED, usually low single-digit monthly cost for logs and alarms.
- AWS Secrets Manager, Systems Manager Parameter Store, CloudTrail, and Session Manager: UNCONFIRMED or near-zero for baseline usage.

### Total Estimate
- Estimated monthly operating cost: UNCONFIRMED, roughly $46-60/month for the current architecture.
- Estimated annual operating cost: UNCONFIRMED, roughly $552-720/year.
- One-time hardware cost: no dedicated hardware purchase is required beyond existing development devices.

### 7. Risk Assessment
#### Risk Matrix
- Single-instance availability risk: Medium impact, medium probability.
- File upload durability risk: High impact, medium probability.
- Auth or permission leakage risk: High impact, low probability.
- Database backup and restore risk: High impact, low probability.
- SSE or realtime notification state risk: Medium impact, medium probability.
- Cost overrun risk: Medium impact, medium probability.
- Deployment or rollback risk: Medium impact, medium probability.
- Audit and history integrity risk: High impact, low probability.

#### Mitigation Strategies
- Single-instance availability: keep the deployment small and documented, then upgrade only after the workflow is stable.
- File uploads: store attachments in a private S3 bucket and keep upload validation on the backend.
- Auth and permissions: enforce JWT, role checks, and server-side authorization on every protected route.
- Backup and restore: keep database backups and document restore steps before production use.
- SSE and realtime state: treat in-memory notification state as a baseline constraint and review scaling strategy before multi-instance rollout.
- Cost: use budget alerts, small instance sizes, and monthly cost reviews.
- Deployment and rollback: keep deployment notes, versioned releases, and a rollback path ready before demo day.
- Audit and history: keep operational history in MySQL and write cloud audit events through CloudTrail and CloudWatch.

#### Contingency Plans
- Revert to a manual process only if the AWS deployment is unavailable during demo preparation.
- Restore from database backup if data corruption or failed deployment affects the main dataset.
- Roll back the last deployment version if the release introduces blocking bugs.
- Revisit notification design if multi-instance scaling breaks in-memory SSE assumptions.

### 8. Expected Outcomes
#### Technical Improvements:
Centralized asset visibility replaces scattered spreadsheets and manual follow-up.
Faster assignment, return, and transfer flows reduce handoff delays.
Better maintenance handling keeps request status, repair cost, and history in one place.
Employee self-service screens let users track assets and requests without asking admins for every update.
Improved reporting and auditability make summaries, attachments, and history easier to review.
#### Long-term Value
A stable internal MVP foundation supports future expansion without changing the core workflow.
Reusable asset, maintenance, and inventory data supports future reporting and process improvements.
The team can keep using the project as a demo-ready internal system for later iterations.
### 9. Final Conclusion
The proposed Enterprise Asset Management solution is a practical internal MVP that matches the current team scope and the actual AWS stack in use.
React + Vite on Amplify, Node.js + Express on Elastic Beanstalk, and MySQL through Prisma provide a clear path from local development to a deployable demo.
The supporting AWS services give the project enough structure for asset tracking, maintenance, reporting, file handling, notifications, audit, and secure operations without adding unnecessary complexity.