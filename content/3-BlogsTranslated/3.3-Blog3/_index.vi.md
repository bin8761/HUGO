---
title: "Blog 3"
date: 2026-06-25
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

# AWS Continuum: Báº£o máº­t á»Ÿ tá»‘c Ä‘á»™ mĂ¡y

**Nguá»“n:** [AWS Security Blog - Introducing AWS Continuum: Security at machine speed](https://aws.amazon.com/vi/blogs/security/introducing-aws-continuum-security-at-machine-speed/)

BĂ i blog giá»›i thiá»‡u AWS Continuum, má»™t hÆ°á»›ng tiáº¿p cáº­n má»›i cá»§a AWS nháº±m há»— trá»£ cĂ¡c Ä‘á»™i ngÅ© báº£o máº­t xá»­ lĂ½ lá»— há»•ng mĂ£ nguá»“n á»Ÿ tá»‘c Ä‘á»™ mĂ¡y. Thay vĂ¬ chá»‰ thu tháº­p telemetry, lÆ°u trá»¯, truy váº¥n vĂ  xĂ¢y dá»±ng dashboard Ä‘á»ƒ theo dĂµi, AWS nháº¥n máº¡nh mĂ´ hĂ¬nh má»›i gá»“m telemetry, context, reasoning vĂ  actions.

AWS Continuum for code vulnerabilities hiá»‡n Ä‘Æ°á»£c cĂ´ng bá»‘ á»Ÿ dáº¡ng gated preview, táº­p trung vĂ o toĂ n bá»™ vĂ²ng Ä‘á»i cá»§a lá»— há»•ng: tá»« phĂ¡t hiá»‡n, Æ°u tiĂªn, xĂ¡c thá»±c cho Ä‘áº¿n Ä‘á» xuáº¥t giáº£m thiá»ƒu vĂ  kháº¯c phá»¥c. Äiá»ƒm Ä‘Ă¡ng chĂº Ă½ lĂ  há»‡ thá»‘ng cĂ³ thá»ƒ káº¿t há»£p nhiá»u mĂ´ hĂ¬nh AI khĂ¡c nhau, phĂ¢n tĂ­ch bá»‘i cáº£nh doanh nghiá»‡p vĂ  Ä‘Æ°a ra khuyáº¿n nghá»‹ cĂ³ cÆ¡ sá»Ÿ thay vĂ¬ Ă¡p dá»¥ng má»™t bá»™ quy táº¯c chung cho má»i mĂ´i trÆ°á»ng.

## CĂ¡c Ä‘iá»ƒm chĂ­nh cáº§n náº¯m

- AWS Continuum for code vulnerabilities Ä‘Æ°á»£c AWS cĂ´ng bá»‘ á»Ÿ dáº¡ng gated preview, hÆ°á»›ng Ä‘áº¿n viá»‡c xá»­ lĂ½ vĂ²ng Ä‘á»i lá»— há»•ng mĂ£ nguá»“n tá»« discovery Ä‘áº¿n action.
- Continuum khĂ´ng chá»‰ phĂ¡t hiá»‡n lá»— há»•ng mĂ  cĂ²n phĂ¢n tĂ­ch bá»‘i cáº£nh thá»±c táº¿ cá»§a mĂ´i trÆ°á»ng nhÆ° háº¡ táº§ng AWS, quyá»n truy cáº­p, network topology, mĂ£ nguá»“n, tĂ i liá»‡u ná»™i bá»™, quy trĂ¬nh váº­n hĂ nh vĂ  má»©c Ä‘á»™ rá»§i ro cá»§a tá»• chá»©c.
- Quy trĂ¬nh hoáº¡t Ä‘á»™ng gá»“m 4 giai Ä‘oáº¡n liĂªn tá»¥c: Discovery, Prioritization, Validation, Mitigation and Remediation.
- á» giai Ä‘oáº¡n Discovery, há»‡ thá»‘ng tiáº¿p nháº­n backlog lá»— há»•ng hiá»‡n cĂ³ vĂ  cĂ³ thá»ƒ thá»±c hiá»‡n quĂ©t mĂ´i trÆ°á»ng Ä‘á»ƒ táº¡o cĂ¡i nhĂ¬n toĂ n diá»‡n hÆ¡n vá» cĂ¡c lá»— há»•ng cĂ¹ng Ä‘Æ°á»ng táº¥n cĂ´ng liĂªn quan.
- á» giai Ä‘oáº¡n Prioritization, Continuum Ä‘Ă¡nh giĂ¡ má»©c Ä‘á»™ quan trá»ng dá»±a trĂªn cĂ¢u há»i nhÆ° thĂ nh pháº§n cĂ³ Ä‘ang Ä‘Æ°á»£c triá»ƒn khai hay khĂ´ng, cĂ³ thá»ƒ truy cáº­p Ä‘Æ°á»£c khĂ´ng, cĂ³ náº±m trĂªn luá»“ng production khĂ´ng vĂ  tĂ¡c Ä‘á»™ng kinh doanh náº¿u bá»‹ khai thĂ¡c lĂ  gĂ¬.
- á» giai Ä‘oáº¡n Validation, há»‡ thá»‘ng giĂºp giáº£m false positives báº±ng cĂ¡ch xĂ¡c thá»±c lá»— há»•ng theo bá»‘i cáº£nh mĂ´i trÆ°á»ng vĂ  cĂ³ thá»ƒ táº¡o vĂ­ dá»¥ khai thĂ¡c trong mĂ´i trÆ°á»ng sandbox Ä‘á»ƒ cung cáº¥p báº±ng chá»©ng cĂ³ thá»ƒ tĂ¡i láº­p.
- á» giai Ä‘oáº¡n Mitigation and Remediation, Continuum Ä‘á» xuáº¥t cĂ¡c biá»‡n phĂ¡p nhÆ° thay Ä‘á»•i network, Ä‘iá»u chá»‰nh policy hoáº·c táº¡o code patch; Ä‘á»“ng thá»i xem xĂ©t blast radius vĂ  rollback path khi kháº£ thi.
- CĂ¡ch tiáº¿p cáº­n cá»§a AWS Continuum theo hÆ°á»›ng "graduated trust": ban Ä‘áº§u cháº¡y á»Ÿ learn mode vá»›i human-in-the-loop, sau Ä‘Ă³ cĂ³ thá»ƒ chuyá»ƒn dáº§n sang enforce mode khi tá»• chá»©c Ä‘Ă£ Ä‘á»§ tin tÆ°á»Ÿng vĂ o cĂ¡c khuyáº¿n nghá»‹.
- NgoĂ i code vulnerabilities, AWS cÅ©ng Ä‘Æ°a cĂ¡c kháº£ nÄƒng nhÆ° Continuum pen testing, Continuum code scanning vĂ  Continuum threat modeling vĂ o cĂ¹ng vĂ²ng láº·p báº£o máº­t.
- TĂ­nh nÄƒng nĂ y Ä‘áº·c biá»‡t há»¯u Ă­ch vá»›i cĂ¡c tá»• chá»©c cĂ³ sá»‘ lÆ°á»£ng lá»— há»•ng lá»›n, nhiá»u há»‡ thá»‘ng phá»©c táº¡p vĂ  cáº§n Æ°u tiĂªn xá»­ lĂ½ theo rá»§i ro thá»±c táº¿ thay vĂ¬ chá»‰ dá»±a trĂªn má»©c Ä‘á»™ nghiĂªm trá»ng chung.

## HĂ¬nh áº£nh

HĂ¬nh minh há»a vĂ²ng láº·p hoáº¡t Ä‘á»™ng cá»§a AWS Continuum, dá»±a trĂªn cĂ¡c giai Ä‘oáº¡n Discovery, Prioritization, Validation, Mitigation and Remediation Ä‘Æ°á»£c mĂ´ táº£ trong bĂ i blog.

![SÆ¡ Ä‘á»“ minh há»a vĂ²ng Ä‘á»i xá»­ lĂ½ lá»— há»•ng cá»§a AWS Continuum](/HUGO/images/3-BlogsPosted/3.3-Blog3/aws-continuum-1.png)

*HĂ¬nh 1. SÆ¡ Ä‘á»“ minh há»a vĂ²ng Ä‘á»i xá»­ lĂ½ lá»— há»•ng cá»§a AWS Continuum. Nguá»“n ná»™i dung: AWS Security Blog.*


## HÆ°á»›ng dáº«n

1. Äá»c pháº§n "What we believe" Ä‘á»ƒ hiá»ƒu vĂ¬ sao mĂ´ hĂ¬nh báº£o máº­t truyá»n thá»‘ng dá»±a nhiá»u vĂ o telemetry vĂ  dashboard khĂ´ng cĂ²n Ä‘á»§ nhanh trÆ°á»›c tá»‘c Ä‘á»™ phĂ¡t hiá»‡n lá»— há»•ng báº±ng AI.
2. Ghi nhá»› 4 giai Ä‘oáº¡n chĂ­nh cá»§a AWS Continuum: Discovery, Prioritization, Validation, Mitigation and Remediation.
3. Khi phĂ¢n tĂ­ch má»™t há»‡ thá»‘ng thá»±c táº¿, cĂ³ thá»ƒ liĂªn há»‡ bĂ i blog vá»›i cĂ¡c nguá»“n dá»¯ liá»‡u nhÆ° code repository, IAM permissions, network topology, tĂ i liá»‡u thiáº¿t káº¿ há»‡ thá»‘ng vĂ  má»©c Ä‘á»™ quan trá»ng cá»§a workload.
4. AWS Continuum nhÆ° má»™t vĂ­ dá»¥ vá» xu hÆ°á»›ng Agentic AI trong báº£o máº­t: AI khĂ´ng chá»‰ phĂ¡t hiá»‡n váº¥n Ä‘á» mĂ  cĂ²n há»— trá»£ suy luáº­n, Æ°u tiĂªn vĂ  Ä‘á» xuáº¥t hĂ nh Ä‘á»™ng kháº¯c phá»¥c.
5. Do AWS Continuum for code vulnerabilities Ä‘ang á»Ÿ dáº¡ng gated preview, pháº§n thá»±c hĂ nh cĂ³ thá»ƒ dá»«ng á»Ÿ má»©c tĂ¬m hiá»ƒu kiáº¿n trĂºc, quy trĂ¬nh váº­n hĂ nh vĂ  Ä‘Äƒng kĂ½ request access náº¿u tá»• chá»©c cĂ³ nhu cáº§u tráº£i nghiá»‡m.

## Káº¿t luáº­n ngáº¯n

AWS Continuum thá»ƒ hiá»‡n Ä‘á»‹nh hÆ°á»›ng má»›i trong lÄ©nh vá»±c cloud security, nÆ¡i AI Ä‘Æ°á»£c sá»­ dá»¥ng Ä‘á»ƒ tÄƒng tá»‘c quĂ¡ trĂ¬nh phĂ¡t hiá»‡n, Ä‘Ă¡nh giĂ¡ vĂ  kháº¯c phá»¥c lá»— há»•ng. Thay vĂ¬ chá»‰ cung cáº¥p thĂ´ng tin cho con ngÆ°á»i quan sĂ¡t, há»‡ thá»‘ng hÆ°á»›ng Ä‘áº¿n viá»‡c táº¡o ra cĂ¡c hĂ nh Ä‘á»™ng cĂ³ cÄƒn cá»©, cĂ³ thá»ƒ kiá»ƒm chá»©ng vĂ  tá»«ng bÆ°á»›c tá»± Ä‘á»™ng hĂ³a dÆ°á»›i sá»± kiá»ƒm soĂ¡t cá»§a Ä‘á»™i ngÅ© báº£o máº­t.


