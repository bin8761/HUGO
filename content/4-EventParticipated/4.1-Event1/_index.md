---
title: "AWS First Cloud Journey Community Day"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

## Event Information

| Information | Details |
| --- | --- |
| Date | June 6, 2026 |
| Location | 26th Floor, Bitexco Financial Tower |
| Participation format | On-site participation |
| Role | Attendee |
| Main topics | Cloud Computing, DevOps, Security, AI, WebSocket, Teamwork, and career orientation in information technology |
| Speakers | Tran Trung Vinh - System Administrator at Central Retail Group; Bao Huynh - Junior Cloud Native Developer, Endava Vietnam; Le Hoang Gia Dai; Nguyen Quoc Bao; Truong Huy Phuoc; Viet Phat |

## 1. Purpose of participating in the event

AWS First Cloud Journey Community Day was a good opportunity to hear practical experience from speakers who are working directly in cloud-related roles. Instead of focusing only on theory, the event connected AWS, Docker, Machine Learning, WebSocket, GraphRAG, and DevOps with actual engineering use cases.

I joined the event to widen my view beyond classroom learning. What I wanted most was to understand how people in the industry talk about deployment, security, real-time systems, and career development in Cloud and DevOps. It was also helpful to see how they approach tradeoffs, explain technical decisions, and relate those decisions to enterprise work.

## 2. Main content of the event

The event was divided into several sessions, and each one covered a different part of the cloud learning path. Together, they gave a useful picture of the skills that matter for AWS learners, from deployment basics and security to teamwork and career growth.

### 2.1. Docker - A Containerization Technology

The Docker session explained containerization and why Docker has become a core part of modern software delivery. The speaker compared containers with virtual machines and highlighted that containers are lighter, more portable, and more suitable for cloud-native systems.

What stood out to me was that Docker is not only a runtime tool. It also helps bundle application code, libraries, configuration, and runtime dependencies together, which reduces the familiar problem of an application working on one machine but failing in another environment. That is why Docker appears so often in DevOps pipelines.

For AWS learning, Docker matters because many modern services, including Amazon ECS, Amazon EKS, and CI/CD workflows, rely heavily on containers. Understanding Docker gives a stronger base before moving on to those services.

### 2.2. Machine Learning-based Network Intrusion Detection System (NIDS) on AWS

The security session focused on web protection and network intrusion detection. AWS WAF was introduced as a defense layer for HTTP and HTTPS applications, able to block common threats such as SQL injection, cross-site scripting, bot traffic, brute-force attempts, and abnormal requests.

The speaker also showed the limitation of fixed rule-based security. Traditional rules work well for known attack patterns, but they struggle when threats are new, behave differently, or fall outside existing definitions. That led into the Machine Learning-based NIDS idea, where network data can be analyzed to detect signals that do not look normal.

The main lesson from this session was that cloud security is layered. It is not enough to configure a firewall and stop there. A stronger approach combines rules, monitoring, and behavior-based detection.

### 2.3. From IT Helpdesk to Senior Sysadmin

The career session about moving from IT Helpdesk to Senior Sysadmin was very practical. The speaker described how support work can lead into Linux administration, networking, infrastructure management, home lab practice, and eventually system administration.

One important point was the discipline required in infrastructure roles. These roles need calm troubleshooting, documentation, monitoring habits, and a careful mindset that avoids testing directly in production without a safe plan. The transition from on-premise to cloud also changes the way you think about scale, cost, managed services, and Infrastructure as Code.

For me, this session connected Sysadmin, Cloud, and DevOps more clearly. Growth in cloud is not only about knowing service names. It also depends on operating systems, networking, security, and automation fundamentals.

### 2.4. Multiplayer in the Cloud

The Multiplayer in the Cloud session showed how Godot clients can stay connected through AWS WebSockets. The speaker compared different communication methods such as UDP/ENet, WebSocket, and HTTP Polling, and explained when each one is appropriate.

The proposed architecture used API Gateway WebSocket to manage client connections, AWS Lambda to process events, DynamoDB to store connection state, and CloudWatch for logging and monitoring. That made serverless architecture feel more concrete because it showed how a real-time system can work without a traditional always-on server.

This session helped me understand where AWS fits in chat systems, game lobbies, matchmaking, and other applications that need continuous data exchange.

### 2.5. The Art of Effective Teamwork

The teamwork session focused on practical habits that improve collaboration inside a team. The speaker emphasized four important factors: shared goals, assigning the right work to the right person, open communication with active listening, and personal accountability.

The tools mentioned, such as ClickUp, Trello, Slack, Google Workspace, and Discord, were examples of how teams can keep tasks visible, exchange updates, and store information more systematically.

For internship and project work, this session was relevant because technology projects usually require cooperation among several members. I realized that technical skill matters, but communication, work management, and responsibility also have a direct impact on results.

### 2.6. GraphRAG - Build GraphRAG Applications Using Amazon Bedrock and Amazon Neptune

The final session introduced GraphRAG, which combines Retrieval-Augmented Generation with graph data. Traditional RAG helps language models retrieve information from external sources to produce better answers. GraphRAG goes further when questions require reasoning over multiple entities and their relationships.

The speaker presented how GraphRAG applications can be built using Amazon Bedrock and Amazon Neptune. Bedrock provides the generative AI layer, while Neptune stores and processes graph data. Together they allow systems to search by content and by relationship, which makes reasoning more effective for complex questions.

This session reminded me that AWS is not only about infrastructure. It also provides building blocks for intelligent systems, knowledge search, and more advanced AI applications.

## 3. What I took away

The event gave me lessons on both technical knowledge and career development. On the technical side, I better understood Docker in deployment pipelines, layered cloud security, serverless real-time systems, and the role AWS is taking in AI-enabled use cases. On the career side, the helpdesk-to-sysadmin session reinforced the need for a strong base in Linux, networking, troubleshooting, monitoring, and documentation.

The teamwork session also made a simple but important point: communication is not an extra skill, it is part of how technical work succeeds. Good communication makes it much easier for a team to move work forward without confusion.

## 4. How I used the event

I took notes during the sessions and focused on the parts that were relevant to my internship report: AWS, Docker, security, serverless systems, AI, and teamwork. I also compared the examples from the speakers with what I had already learned in AWS Study Group sessions so I could connect the event content with my own study path.

After the event, I adjusted my learning plan. The sessions made it clear that I should keep practicing Docker, deepen my AWS serverless knowledge, strengthen cloud security basics, and continue studying real deployment patterns instead of only isolated services.

## 5. Closing note

AWS First Cloud Journey Community Day gave me a practical view of how cloud, DevOps, security, and AI fit together in real work. It also showed that career growth in technology comes from more than technical knowledge. It requires consistency, communication, and the habit of learning from people who are already doing the job.
