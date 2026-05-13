---
title: "Event 2"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.2. </b> "
---

# BĂ i thu hoáº¡ch â€œGenAI-powered App-DB Modernization workshopâ€

### Má»¥c ÄĂ­ch Cá»§a Sá»± Kiá»‡n

- Chia sáº» best practices trong thiáº¿t káº¿ á»©ng dá»¥ng hiá»‡n Ä‘áº¡i
- Giá»›i thiá»‡u phÆ°Æ¡ng phĂ¡p DDD vĂ  event-driven architecture
- HÆ°á»›ng dáº«n lá»±a chá»n compute services phĂ¹ há»£p
- Giá»›i thiá»‡u cĂ´ng cá»¥ AI há»— trá»£ development lifecycle

### Danh SĂ¡ch Diá»…n Giáº£

- **Jignesh Shah** - Director, Open Source Databases
- **Erica Liu** - Sr. GTM Specialist, AppMod
- **Fabrianne Effendi** - Assc. Specialist SA, Serverless Amazon Web Services

### Ná»™i Dung Ná»•i Báº­t

#### ÄÆ°a ra cĂ¡c áº£nh hÆ°á»Ÿng tiĂªu cá»±c cá»§a kiáº¿n trĂºc á»©ng dá»¥ng cÅ©

- Thá»i gian release sáº£n pháº©m lĂ¢u â†’ Máº¥t doanh thu/bá» lá»¡ cÆ¡ há»™i
- Hoáº¡t Ä‘á»™ng kĂ©m hiá»‡u quáº£ â†’ Máº¥t nÄƒng suáº¥t, tá»‘n kĂ©m chi phĂ­
- KhĂ´ng tuĂ¢n thá»§ cĂ¡c quy Ä‘á»‹nh vá» báº£o máº­t â†’ Máº¥t an ninh, uy tĂ­n

#### Chuyá»ƒn Ä‘á»•i sang kiáº¿n trĂºc á»©ng dá»¥ng má»›i - Microservice Architecture

Chuyá»ƒn Ä‘á»•i thĂ nh há»‡ thá»‘ng modular â€“ tá»«ng chá»©c nÄƒng lĂ  má»™t **dá»‹ch vá»¥ Ä‘á»™c láº­p** giao tiáº¿p vá»›i nhau qua **sá»± kiá»‡n** vá»›i 3 trá»¥ cá»™t cá»‘t lĂµi:

- **Queue Management**: Xá»­ lĂ½ tĂ¡c vá»¥ báº¥t Ä‘á»“ng bá»™
- **Caching Strategy:** Tá»‘i Æ°u performance
- **Message Handling:** Giao tiáº¿p linh hoáº¡t giá»¯a services

#### Domain-Driven Design (DDD)

- **PhÆ°Æ¡ng phĂ¡p 4 bÆ°á»›c**: XĂ¡c Ä‘á»‹nh domain events â†’ sáº¯p xáº¿p timeline â†’ identify actors â†’ xĂ¡c Ä‘á»‹nh bounded contexts
- **Case study bookstore**: Minh há»a cĂ¡ch Ă¡p dá»¥ng DDD thá»±c táº¿
- **Context mapping**: 7 patterns tĂ­ch há»£p bounded contexts

#### Event-Driven Architecture

- **3 patterns tĂ­ch há»£p**: Publish/Subscribe, Point-to-point, Streaming
- **Lá»£i Ă­ch**: Loose coupling, scalability, resilience
- **So sĂ¡nh sync vs async**: Hiá»ƒu rĂµ trade-offs (sá»± Ä‘Ă¡nh Ä‘á»•i)

#### Compute Evolution

- **Shared Responsibility Model**: Tá»« EC2 â†’ ECS â†’ Fargate â†’ Lambda
- **Serverless benefits**: No server management, auto-scaling, pay-for-value
- **Functions vs Containers**: Criteria lá»±a chá»n phĂ¹ há»£p

#### Amazon Q Developer

- **SDLC automation**: Tá»« planning Ä‘áº¿n maintenance
- **Code transformation**: Java upgrade, .NET modernization
- **AWS Transform agents**: VMware, Mainframe, .NET migration

### Nhá»¯ng GĂ¬ Há»c ÄÆ°á»£c

#### TÆ° Duy Thiáº¿t Káº¿

- **Business-first approach**: LuĂ´n báº¯t Ä‘áº§u tá»« business domain, khĂ´ng pháº£i technology
- **Ubiquitous language**: Importance cá»§a common vocabulary giá»¯a business vĂ  tech teams
- **Bounded contexts**: CĂ¡ch identify vĂ  manage complexity trong large systems

#### Kiáº¿n TrĂºc Ká»¹ Thuáº­t

- **Event storming technique**: PhÆ°Æ¡ng phĂ¡p thá»±c táº¿ Ä‘á»ƒ mĂ´ hĂ¬nh hĂ³a quy trĂ¬nh kinh doanh
- Sá»­ dá»¥ng **Event-driven communication** thay vĂ¬ synchronous calls
- **Integration patterns**: Hiá»ƒu khi nĂ o dĂ¹ng sync, async, pub/sub, streaming
- **Compute spectrum**: Criteria chá»n tá»« VM â†’ containers â†’ serverless

#### Chiáº¿n LÆ°á»£c Hiá»‡n Äáº¡i HĂ³a

- **Phased approach**: KhĂ´ng rush, pháº£i cĂ³ roadmap rĂµ rĂ ng
- **7Rs framework**: Nhiá»u con Ä‘Æ°á»ng khĂ¡c nhau tĂ¹y thuá»™c vĂ o Ä‘áº·c Ä‘iá»ƒm cá»§a má»—i á»©ng dá»¥ng
- **ROI measurement**: Cost reduction + business agility

### á»¨ng Dá»¥ng VĂ o CĂ´ng Viá»‡c

- **Ăp dá»¥ng DDD** cho project hiá»‡n táº¡i: Event storming sessions vá»›i business team
- **Refactor microservices**: Sá»­ dá»¥ng bounded contexts Ä‘á»ƒ identify service boundaries
- **Implement event-driven patterns**: Thay tháº¿ má»™t sá»‘ sync calls báº±ng async messaging
- **Serverless adoption**: Pilot AWS Lambda cho má»™t sá»‘ use cases phĂ¹ há»£p
- **Try Amazon Q Developer**: Integrate vĂ o development workflow Ä‘á»ƒ boost productivity

### Tráº£i nghiá»‡m trong event

Tham gia workshop **â€œGenAI-powered App-DB Modernizationâ€** lĂ  má»™t tráº£i nghiá»‡m ráº¥t bá»• Ă­ch, giĂºp tĂ´i cĂ³ cĂ¡i nhĂ¬n toĂ n diá»‡n vá» cĂ¡ch hiá»‡n Ä‘áº¡i hĂ³a á»©ng dá»¥ng vĂ  cÆ¡ sá»Ÿ dá»¯ liá»‡u báº±ng cĂ¡c phÆ°Æ¡ng phĂ¡p vĂ  cĂ´ng cá»¥ hiá»‡n Ä‘áº¡i. Má»™t sá»‘ tráº£i nghiá»‡m ná»•i báº­t:

#### Há»c há»i tá»« cĂ¡c diá»…n giáº£ cĂ³ chuyĂªn mĂ´n cao
- CĂ¡c diá»…n giáº£ Ä‘áº¿n tá»« AWS vĂ  cĂ¡c tá»• chá»©c cĂ´ng nghá»‡ lá»›n Ä‘Ă£ chia sáº» **best practices** trong thiáº¿t káº¿ á»©ng dá»¥ng hiá»‡n Ä‘áº¡i.
- Qua cĂ¡c case study thá»±c táº¿, tĂ´i hiá»ƒu rĂµ hÆ¡n cĂ¡ch Ă¡p dá»¥ng **Domain-Driven Design (DDD)** vĂ  **Event-Driven Architecture** vĂ o cĂ¡c project lá»›n.

#### Tráº£i nghiá»‡m ká»¹ thuáº­t thá»±c táº¿
- Tham gia cĂ¡c phiĂªn trĂ¬nh bĂ y vá» **event storming** giĂºp tĂ´i hĂ¬nh dung cĂ¡ch **mĂ´ hĂ¬nh hĂ³a quy trĂ¬nh kinh doanh** thĂ nh cĂ¡c domain events.
- Há»c cĂ¡ch **phĂ¢n tĂ¡ch microservices** vĂ  xĂ¡c Ä‘á»‹nh **bounded contexts** Ä‘á»ƒ quáº£n lĂ½ sá»± phá»©c táº¡p cá»§a há»‡ thá»‘ng lá»›n.
- Hiá»ƒu rĂµ trade-offs giá»¯a **synchronous vĂ  asynchronous communication** cÅ©ng nhÆ° cĂ¡c pattern tĂ­ch há»£p nhÆ° **pub/sub, point-to-point, streaming**.

#### á»¨ng dá»¥ng cĂ´ng cá»¥ hiá»‡n Ä‘áº¡i
- Trá»±c tiáº¿p tĂ¬m hiá»ƒu vá» **Amazon Q Developer**, cĂ´ng cá»¥ AI há»— trá»£ SDLC tá»« láº­p káº¿ hoáº¡ch Ä‘áº¿n maintenance.
- Há»c cĂ¡ch **tá»± Ä‘á»™ng hĂ³a code transformation** vĂ  pilot serverless vá»›i **AWS Lambda**, tá»« Ä‘Ă³ nĂ¢ng cao nÄƒng suáº¥t phĂ¡t triá»ƒn.

#### Káº¿t ná»‘i vĂ  trao Ä‘á»•i
- Workshop táº¡o cÆ¡ há»™i trao Ä‘á»•i trá»±c tiáº¿p vá»›i cĂ¡c chuyĂªn gia, Ä‘á»“ng nghiá»‡p vĂ  team business, giĂºp **nĂ¢ng cao ngĂ´n ngá»¯ chung (ubiquitous language)** giá»¯a business vĂ  tech.
- Qua cĂ¡c vĂ­ dá»¥ thá»±c táº¿, tĂ´i nháº­n ra táº§m quan trá»ng cá»§a **business-first approach**, luĂ´n báº¯t Ä‘áº§u tá»« nhu cáº§u kinh doanh thay vĂ¬ chá»‰ táº­p trung vĂ o cĂ´ng nghá»‡.

#### BĂ i há»c rĂºt ra
- Viá»‡c Ă¡p dá»¥ng DDD vĂ  event-driven patterns giĂºp giáº£m **coupling**, tÄƒng **scalability** vĂ  **resilience** cho há»‡ thá»‘ng.
- Chiáº¿n lÆ°á»£c hiá»‡n Ä‘áº¡i hĂ³a cáº§n **phased approach** vĂ  Ä‘o lÆ°á»ng **ROI**, khĂ´ng nĂªn vá»™i vĂ ng chuyá»ƒn Ä‘á»•i toĂ n bá»™ há»‡ thá»‘ng.
- CĂ¡c cĂ´ng cá»¥ AI nhÆ° Amazon Q Developer cĂ³ thá»ƒ **boost productivity** náº¿u Ä‘Æ°á»£c tĂ­ch há»£p vĂ o workflow phĂ¡t triá»ƒn hiá»‡n táº¡i.

#### Má»™t sá»‘ hĂ¬nh áº£nh khi tham gia sá»± kiá»‡n
* ThĂªm cĂ¡c hĂ¬nh áº£nh cá»§a cĂ¡c báº¡n táº¡i Ä‘Ă¢y
> Tá»•ng thá»ƒ, sá»± kiá»‡n khĂ´ng chá»‰ cung cáº¥p kiáº¿n thá»©c ká»¹ thuáº­t mĂ  cĂ²n giĂºp tĂ´i thay Ä‘á»•i cĂ¡ch tÆ° duy vá» thiáº¿t káº¿ á»©ng dá»¥ng, hiá»‡n Ä‘áº¡i hĂ³a há»‡ thá»‘ng vĂ  phá»‘i há»£p hiá»‡u quáº£ hÆ¡n giá»¯a cĂ¡c team.

