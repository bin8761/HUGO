# Proposal Rewrite TODO

Muc tieu: thay Proposal mau hien tai bang noi dung dung cua du an **Enterprise Asset Management** trong `C:\Users\yasuo\Desktop\appquanlidoanhnghiep`.

## Nguon chuan

- `content/2-Proposal/_index.md`
- `content/2-Proposal/_index.vi.md`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\docs\codebase\enterprise-asset-management-aws-presentation.md`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\docs\codebase\fullstack-aws-final-architecture.md`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\docs\codebase\backend-aws-final-be-architecture.md`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\frontend\src\routes\AppRoutes.jsx`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\backend\prisma\schema.prisma`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\docs\plans\2026-06-02-enterprise-asset-management-design.md`
- `C:\Users\yasuo\Desktop\appquanlidoanhnghiep\docs\plans\2026-06-02-enterprise-asset-management-implementation-plan.md`

## Sections To Replace

### 1. Executive Summary

- Replace the weather/IoT summary with the real project summary:
  - enterprise asset management for admin and employee users
  - asset tracking, assignment, return, transfer, maintenance, reporting, attachments, OTP email, centralized data
  - frontend React/Vite on Amplify
  - backend Node.js/Express on Elastic Beanstalk behind ALB
  - MySQL via Prisma

### 2. Problem Statement

- Replace the weather-station pain points with the real project pain points:
  - asset workflows are fragmented
  - admin and employee actions need clear roles and permissions
  - maintenance requests, feedback, notifications, and history need centralized handling
  - file uploads and reporting need durable storage and auditability

### 3. Solution Architecture

- Replace all IoT/weather architecture text with the real AWS architecture:
  - AWS Amplify Hosting
  - Application Load Balancer
  - AWS Elastic Beanstalk
  - Amazon RDS for MySQL Single-AZ
  - Amazon S3 private bucket
  - Amazon SES
  - AWS Secrets Manager
  - AWS Systems Manager Parameter Store
  - Amazon CloudWatch
  - AWS CloudTrail
  - AWS Systems Manager Session Manager
- Replace the two weather images with new architecture diagrams for the enterprise asset management stack.

### 4. Technical Implementation

- Replace the weather phases with the real development phases of this project:
  - frontend/admin-employee foundation
  - backend foundation auth and database schema
  - asset / assignment / maintenance / inventory / reports flows
  - deployment, QA, documentation, demo hardening
- Replace technical requirements with the actual repo stack:
  - React + Vite
  - Node.js + Express
  - Prisma + MySQL
  - Playwright / Jest where applicable

### 5. Timeline & Milestones

- Replace the weather timeline with a project timeline sourced from the repo docs.
- Use these sources:
  - `docs/plans/2026-06-02-enterprise-asset-management-design.md`
  - `docs/plans/2026-06-02-enterprise-asset-management-implementation-plan.md`
- Synthesis rule:
  - use `design.md` for dependency order and team sequencing
  - use `implementation-plan.md` for concrete milestone labels and phase structure
  - if the two docs differ in wording, keep the milestone meaning and normalize the wording into a single Proposal timeline
- Do not leave this section as `UNCONFIRMED`.

### 6. Budget Estimation

- Replace the weather budget with a budget estimate for the real architecture.
- Use the backend architecture docs as the main source for service choices and cost framing.
- If exact numbers are not yet confirmed, mark the values as `UNCONFIRMED` instead of importing the weather pricing numbers.

### 7. Risk Assessment

- Replace weather risks with project-relevant risks:
  - single-instance availability
  - file upload durability
  - auth / permission leakage
  - database backup / restore
  - SSE / realtime notification state
  - cost guardrails
  - deployment / rollback risk
  - audit / history integrity

### 8. Expected Outcomes

- Replace weather outcomes with enterprise asset management outcomes:
  - centralized asset visibility
  - faster assignment / return / transfer flows
  - better maintenance handling
  - employee self-service portal
  - better reporting and auditability
  - stable internal MVP / demo foundation

## Cross-file Sync Tasks

- Keep Vietnamese and English Proposal files structurally aligned.
- Remove every mention of:
  - IoT weather
  - Raspberry Pi
  - ESP32
  - MQTT
  - Cognito
  - Glue
  - Lambda serverless weather flow
- Replace image paths and captions so they match the enterprise asset management architecture.
- Keep the section order consistent across both language files.

## Review Checklist

- Header and subtitle match the real project.
- All section text matches the project architecture and repo docs.
- Timeline uses the design and implementation plan docs.
- Budget uses the real AWS stack, not the weather calculator.
- Risk and outcome sections reflect enterprise asset management.
- No weather-specific wording remains.
