---
title: "AWS First Cloud Journey Community Day"
date: 2026-06-06
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

# Event 1 - AWS First Cloud Journey Community Day

| Information | Details |
| --- | --- |
| Date | June 6, 2026 |
| Location | 26th Floor, Bitexco Financial Tower |
| Role | Participant in the First Cloud Journey program |
| Participation format | On-site participation |
| Main topics | Cloud Computing, DevOps, Security, AI, WebSocket, Teamwork, and career orientation in information technology |
| Speakers | Tran Trung Vinh - System Administrator at Central Retail Group; Bao Huynh - Junior Cloud Native Developer, Endava Vietnam; Le Hoang Gia Dai; Nguyen Quoc Bao; Truong Huy Phuoc; Viet Phat |

## 1. Why I joined this event

AWS First Cloud Journey Community Day brought together speakers who were already working with cloud systems, so the event felt practical from the start. Instead of staying at the level of theory, it showed how AWS, Docker, machine learning, WebSocket, GraphRAG, and DevOps show up in real projects and real operations.

I joined to get a clearer picture of what lies beyond classroom material. In particular, I wanted to hear how practitioners talk about cloud deployment, security, real-time systems, and career growth. The event was also useful because it showed how professionals explain tradeoffs, break down problems, and connect technology choices to day-to-day work.

## 2. What the sessions covered

The program was split into several talks, and each one covered a different angle of the cloud journey. Taken together, they formed a useful map of the skills a cloud learner needs, from deployment basics and security to collaboration and career mindset.

### 2.1. Docker as a packaging layer

The Docker session focused on containerization and why it has become a standard part of modern software delivery. The speaker contrasted containers with traditional virtualization and made a simple point: containers are lighter, easier to move, and a better fit for cloud-native workflows.

What I took from this session was that Docker is not just a runtime tool. It also helps teams package code, dependencies, configuration, and execution environment together, which reduces the “it works on my machine” problem. That is one of the reasons Docker shows up so often in DevOps and deployment pipelines.

From an AWS perspective, this matters because services like Amazon ECS, Amazon EKS, and CI/CD flows all connect naturally to container-based delivery. Understanding Docker gives me a more stable base for those services later.

### 2.2. AWS WAF and machine-learning-based NIDS

The security session looked at web application protection and network intrusion detection. AWS WAF was introduced as a first layer of defense for HTTP and HTTPS applications, with the ability to block common threats such as SQL injection, cross-site scripting, brute-force attempts, bots, and unusual request patterns.

The speaker also pointed out the weakness of rule-only protection. Static rules work well for known attack patterns, but they are less useful when the threat is new or behaves differently from the patterns already defined. That led into the machine-learning-based NIDS approach, where network data is used to detect behavior that does not look normal.

This session stood out because it made cloud security feel layered rather than single-purpose. It was not just “set a firewall and move on.” The stronger model combines rules, monitoring, and behavior-based detection.

### 2.3. The road from helpdesk to sysadmin

One of the most practical sessions traced a career path from IT Helpdesk to Senior Sysadmin. The speaker showed how support work can grow into Linux administration, networking, infrastructure management, home lab practice, and eventually system administration.

The part that stayed with me was the emphasis on operating discipline. Infrastructure roles require more than technical knowledge. They need calm troubleshooting, documentation, monitoring habits, and a habit of checking before touching production. The shift from on-premise to cloud also changes how you think about scale, cost, managed services, and Infrastructure as Code.

For me, this session connected the dots between Sysadmin, Cloud, and DevOps. The cloud path is not built only on service names. It also depends on operating systems, networking, security, and automation fundamentals.

### 2.4. Multiplayer systems in the cloud

The multiplayer session showed how Godot clients can stay connected through AWS WebSockets. The speaker compared several communication models, including UDP/ENet, WebSocket, and HTTP polling, and explained when each one makes sense.

The architecture used API Gateway WebSocket to manage client connections, AWS Lambda to process events, DynamoDB to store connection state, and CloudWatch for logs and monitoring. That example made serverless feel concrete rather than abstract, because it showed how a system can handle real-time communication without a traditional always-on server.

This section was useful because it linked backend systems, cloud design, and real-time application patterns. I left with a better understanding of where AWS fits in chat systems, game lobbies, matchmaking, and other always-connected use cases.

### 2.5. Teamwork as an engineering skill

The teamwork session focused on the habits that make collaboration work in practice. The speaker highlighted four essentials: shared goals, putting the right person on the right task, open communication with active listening, and personal accountability.

The tools mentioned, such as ClickUp, Trello, Slack, Google Workspace, and Discord, were not the main story. They were examples of how teams keep work visible, divide tasks, exchange updates, and store information without relying on memory alone.

That session felt relevant to internship work because technical projects are rarely solo efforts. Good results usually depend on how well the team communicates and how clearly people handle responsibility.

### 2.6. GraphRAG with Bedrock and Neptune

The final technical session introduced GraphRAG, which extends Retrieval-Augmented Generation with graph structures. Traditional RAG improves answer quality by pulling information from external sources, but GraphRAG goes further when the problem requires reasoning over connected entities and relationships.

The speaker showed how Amazon Bedrock and Amazon Neptune can be combined to build this kind of system. Bedrock provides the generative AI layer, while Neptune stores and processes graph data. Together they let the system search by content and by relationship, which makes reasoning more useful for complex questions.

This was a strong reminder that AWS is not only for infrastructure. It also provides building blocks for intelligent systems, knowledge search, and applications that need more than simple keyword retrieval.

## 3. What I took away

The event left me with both technical and career lessons. On the technical side, I came away with a clearer view of Docker in delivery pipelines, layered cloud security, serverless real-time systems, and the way AWS is moving into AI-enabled use cases. On the career side, the helpdesk-to-sysadmin talk reinforced the need for a strong foundation in Linux, networking, troubleshooting, monitoring, and documentation.

The teamwork session also made an obvious point that is easy to ignore: communication is not a soft extra, it is part of how technical work succeeds. The better a team communicates, the easier it is to move work forward without confusion.

## 4. How I used the event

I took notes during the sessions and focused on the parts that were relevant to my internship report: AWS, Docker, security, serverless systems, AI, and teamwork. I also compared the speakers’ examples with what I had already learned in AWS Study Group sessions so I could connect the talk content to my own study path.

After the event, I adjusted my learning plan a bit. The topics made it clear that I should keep practicing Docker, deepen my AWS serverless knowledge, strengthen cloud security basics, and keep looking at real deployment patterns rather than only isolated services.

## 5. Closing note

AWS First Cloud Journey Community Day gave me a practical look at how cloud, DevOps, security, and AI fit together in real work. It also showed that career growth in tech comes from more than technical knowledge alone. You need consistency, communication, and a habit of learning from people who are already doing the job.

## Event Images

Some images recorded during the event:

![AWS First Cloud Journey Community Day](../../images/4-EventParticipated/4.1-Event1/z7976498940486_4005b6c6d8361abe3f1b76bdf4dd74ef.jpg)
