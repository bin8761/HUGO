---
title: "FCAJ Community Day"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# Event 2 - FC Community Day

## Event Information

| Item | Details |
| --- | --- |
| Event name | FC Community Day |
| Format | In-person event with livestream |
| Location | 26th and 36th floors, Bitexco Financial Tower |
| Role | Attendee |
| Main topics | Cloud Computing, AI Agents, Voice AI, DevOps AI Agents, AI in Human Resources, and secure enterprise AI deployment |

## Overview

FC Community Day was less like a lecture and more like a practical conversation about how cloud and AI show up in real enterprises. The sessions moved between operations, cost, automation, customer support, HR, and deployment security, so the event covered both the technical side and the business side of the same problem.

What made it useful was the mix of production stories and architecture decisions. The speakers did not stay at the level of “what this service is.” They showed how organizations actually use it, what breaks, what scales, and where human judgment still matters.

## Key Topics

### Cloud Thinker and the Cloud Engineering Career Path

Steve Tran opened with a cloud engineering career story that started from server work and gradually moved toward cloud certifications and cloud-native practice. The message was straightforward: the cloud market in Vietnam and ASEAN is expanding because businesses keep pushing digital transformation, and that shift has made cloud literacy more valuable than ever.

The talk also connected AI to the expectations of cloud engineers. The bar is rising. It is no longer enough to know service names; engineers are now expected to use AI tools, understand architecture, and solve operational problems with better speed and judgment.

Cloud Thinker was presented as an AI-assisted cloud operations platform that can help with incident investigation, FinOps, security testing, and controlled decisions in sensitive production systems.

### Voice AI for Vietnamese Users

The Voice AI session described the basic voice-agent pipeline: audio input, speech-to-text, language model processing, and text-to-speech output. The Vietnamese angle made the topic feel more real because accents, tones, rhythm, and conversational timing create extra complexity.

The speakers made the case for a staged pipeline instead of a single black box. That structure gives better control over accuracy, latency, and the business rules that the voice assistant must respect.

Examples included banking assistants, customer support automation, card-blocking flows, and tool calling so the system can perform a workflow instead of just giving a generic answer.

### DevOps AI Agent

The DevOps AI Agent talk addressed a problem every operations team knows well: when a cloud system has too many services, too many logs, and too many possible failure points, root-cause analysis gets slow. That slowness pushes MTTD and MTTR up.

The proposed workflow was to receive an alert, collect logs, form hypotheses, test those hypotheses, suggest mitigation steps, and recommend follow-up improvements. The key point was that the AI Agent is not there to replace engineers. It is there to reduce the manual work that slows them down.

The examples showed that AI becomes much more useful when observability is good, the operational data is complete, and permissions are designed with clear boundaries.

### AI in Enterprise Human Resources

The HR session shifted the focus to hiring. It described the usual pain points: screening too many CVs manually, slow hiring cycles, subjective review, and the need to protect candidate data carefully.

AI can help by extracting CV data, matching skills to job descriptions, generating candidate summaries, and supporting interview scheduling. Amazon Q-style agents can also be tailored to a department so teams can process internal documents and automate repetitive tasks.

The important warning was not to over-automate strategic decisions. AI can assist with filtering and analysis, but the final decision still belongs to people who can judge fairness, context, and cultural fit.

### Secure Enterprise AI Deployment

The last topic looked at security. If an organization has sensitive internal data, AI should not reach those systems through the public Internet without strong controls.

The suggested design used VPC Interface Endpoints, AWS PrivateLink, and MCP servers to connect AI agents to internal systems through private networking. That approach reduces exposure, limits man-in-the-middle risk, and gives enterprises the access control they need.

## Key Takeaways

- Cloud and AI are becoming intertwined in everyday enterprise work, especially in incident response, FinOps, DevOps, and customer support.
- AI Agents should operate inside clear permission boundaries and support human review for critical actions.
- Vietnamese Voice AI has extra challenges around accents, tone, and latency.
- DevOps AI Agents work best when the system already has logs, metrics, and topology data in place.
- AI can speed up recruitment, but human judgment is still necessary.
- Enterprise AI deployments need security and governance first, not last.

## Connection to the EAM Workspace Project

The event content lines up well with the EAM Workspace project. An enterprise asset management system needs reliable backend services, logging, authorization, data control, and room to grow as users and assets increase.

From the DevOps side, the project can benefit from better logs, health checks, monitoring, and alerts. From the AI side, future versions could include internal assistants for asset lookup, support request classification, maintenance suggestions, or natural-language reporting.

## Conclusion

FC Community Day showed how cloud and AI are being used in production-minded ways. The common thread across the sessions was simple: technology only matters when it is secure, observable, and useful in a real business context.

## Event Images

Some images recorded during the event:

![FC Community Day](../../images/4-EventParticipated/4.2-Event2/Screenshot%202026-06-27%20234244.png)

![FC Community Day](../../images/4-EventParticipated/4.2-Event2/Screenshot%202026-06-27%20234457.png)
