---
title: "Tá»•ng quan workshop"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

## Tá»•ng quan workshop

Má»¥c tiĂªu cá»§a workshop lĂ  triá»ƒn khai EAM Workspace lĂªn AWS vĂ  kiá»ƒm thá»­ luá»“ng end-to-end tá»« trĂ¬nh duyá»‡t Ä‘áº¿n database. Ná»™i dung Ä‘Æ°á»£c viáº¿t theo Ä‘Ăºng mĂ´ hĂ¬nh Ä‘Ă£ triá»ƒn khai trong project: Amplify Hosting cho frontend, API Gateway cho route `/api`, Elastic Beanstalk cho backend vĂ  RDS MySQL cho dá»¯ liá»‡u.

EAM Workspace cĂ³ hai tráº£i nghiá»‡m ngÆ°á»i dĂ¹ng chĂ­nh:

- **Admin Portal**: quáº£n lĂ½ nhĂ¢n viĂªn, phĂ²ng ban, danh má»¥c, tĂ i sáº£n, bĂ n giao, thu há»“i, báº£o trĂ¬, kiá»ƒm kĂª, bĂ¡o cĂ¡o, feedback, FAQ, cháº¥m cĂ´ng, lá»‹ch sá»­ Ä‘Äƒng nháº­p vĂ  support chat.
- **Employee Portal**: xem tĂ i sáº£n Ä‘Æ°á»£c bĂ n giao, gá»­i yĂªu cáº§u há»— trá»£, Ä‘á»c FAQ, cáº­p nháº­t há»“ sÆ¡, Ä‘á»•i máº­t kháº©u vĂ  xem lá»‹ch sá»­ cĂ¡ nhĂ¢n.

Backend cung cáº¥p REST API dÆ°á»›i prefix `/api`. Frontend gá»i API báº±ng Ä‘Æ°á»ng dáº«n tÆ°Æ¡ng Ä‘á»‘i `/api`, Amplify rewrite request Ä‘áº¿n API Gateway, sau Ä‘Ă³ API Gateway chuyá»ƒn tiáº¿p Ä‘áº¿n backend Elastic Beanstalk. CĂ¡c file upload nhÆ° avatar hoáº·c hĂ¬nh áº£nh tĂ i sáº£n Ä‘Æ°á»£c truy cáº­p qua prefix `/uploads`, vĂ¬ váº­y mĂ´i trÆ°á»ng Amplify cÅ©ng cáº§n rewrite `/uploads/*` Ä‘áº¿n API Gateway Ä‘á»ƒ áº£nh khĂ´ng bá»‹ tráº£ vá» `404`.

## Káº¿t quáº£ má»¥c tiĂªu

Sau khi hoĂ n thĂ nh workshop, há»‡ thá»‘ng cĂ³:

- Frontend React Ä‘Æ°á»£c host trĂªn AWS Amplify Hosting.
- Backend Node.js/Express cháº¡y trĂªn AWS Elastic Beanstalk.
- Amazon API Gateway HTTP API lĂ m Ä‘iá»ƒm vĂ o cho backend.
- Database MySQL cháº¡y trĂªn Amazon RDS.
- Endpoint `/api/health` hoáº¡t Ä‘á»™ng qua cáº£ API Gateway vĂ  Amplify domain.
- Luá»“ng Ä‘Äƒng nháº­p admin, user vĂ  cĂ¡c quy trĂ¬nh chĂ­nh cĂ³ thá»ƒ kiá»ƒm thá»­ trĂªn trĂ¬nh duyá»‡t.
- CloudWatch Logs há»— trá»£ kiá»ƒm tra lá»—i backend.

## Luá»“ng triá»ƒn khai

Luá»“ng triá»ƒn khai cá»§a workshop Ä‘Æ°á»£c xĂ¢y dá»±ng theo thá»© tá»± tá»« háº¡ táº§ng dá»¯ liá»‡u, backend, lá»›p API trung gian Ä‘áº¿n frontend. CĂ¡ch triá»ƒn khai nĂ y giĂºp kiá»ƒm tra tá»«ng thĂ nh pháº§n riĂªng láº» trÆ°á»›c khi káº¿t ná»‘i thĂ nh má»™t há»‡ thá»‘ng hoĂ n chá»‰nh.

Äáº§u tiĂªn, mĂ´i trÆ°á»ng AWS, source code vĂ  cĂ¡c biáº¿n cáº¥u hĂ¬nh cáº§n Ä‘Æ°á»£c chuáº©n bá»‹ Ä‘áº§y Ä‘á»§. Sau Ä‘Ă³, Amazon RDS for MySQL Ä‘Æ°á»£c cáº¥u hĂ¬nh lĂ m database chĂ­nh cho há»‡ thá»‘ng. Khi database sáºµn sĂ ng, backend Node.js/Express Ä‘Æ°á»£c Ä‘Ă³ng gĂ³i vĂ  triá»ƒn khai lĂªn AWS Elastic Beanstalk, Ä‘á»“ng thá»i cáº¥u hĂ¬nh cĂ¡c biáº¿n mĂ´i trÆ°á»ng nhÆ° `DATABASE_URL`, `JWT_SECRET`, thĂ´ng tin SES SMTP vĂ  CORS origin.

Sau khi backend hoáº¡t Ä‘á»™ng á»•n Ä‘á»‹nh vĂ  endpoint `/api/health` tráº£ káº¿t quáº£ thĂ nh cĂ´ng, Amazon API Gateway Ä‘Æ°á»£c táº¡o Ä‘á»ƒ lĂ m Ä‘iá»ƒm truy cáº­p public cho backend. Frontend React/Vite Ä‘Æ°á»£c triá»ƒn khai lĂªn AWS Amplify Hosting, sau Ä‘Ă³ cáº¥u hĂ¬nh rewrite Ä‘á»ƒ cĂ¡c request `/api/*` vĂ  `/uploads/*` tá»« Amplify domain Ä‘Æ°á»£c chuyá»ƒn tiáº¿p Ä‘áº¿n API Gateway. Cuá»‘i cĂ¹ng, há»‡ thá»‘ng Ä‘Æ°á»£c kiá»ƒm thá»­ báº±ng cĂ¡c luá»“ng chĂ­nh nhÆ° Ä‘Äƒng nháº­p admin, Ä‘Äƒng nháº­p nhĂ¢n viĂªn, quáº£n lĂ½ tĂ i sáº£n, bĂ n giao tĂ i sáº£n, kiá»ƒm tra API request trĂªn DevTools vĂ  xĂ¡c nháº­n tĂ i khoáº£n inactive bá»‹ cháº·n Ä‘Äƒng nháº­p.

{{< mermaid >}}
flowchart TD
    A["Chuáº©n bá»‹ AWS account, source code vĂ  biáº¿n mĂ´i trÆ°á»ng"] --> B["Táº¡o hoáº·c cáº¥u hĂ¬nh RDS MySQL"]
    B --> C["ÄĂ³ng gĂ³i backend source bundle"]
    C --> D["Deploy backend lĂªn Elastic Beanstalk"]
    D --> E["Cáº¥u hĂ¬nh Environment Properties vĂ  kiá»ƒm tra health"]
    E --> F["Táº¡o API Gateway HTTP API"]
    F --> G["Deploy frontend lĂªn Amplify Hosting"]
    G --> H["ThĂªm rewrite rule /api/* vĂ  /uploads/* Ä‘áº¿n API Gateway"]
    H --> I["Kiá»ƒm thá»­ login, upload vĂ  workflow chĂ­nh"]
    I --> J["Kiá»ƒm tra CloudWatch Logs vĂ  dá»n dáº¹p tĂ i nguyĂªn"]
{{< /mermaid >}}

## Dá»‹ch vá»¥ AWS trong pháº¡m vi

| Dá»‹ch vá»¥ | Má»¥c Ä‘Ă­ch |
| --- | --- |
| AWS Amplify Hosting | Host vĂ  build frontend React/Vite. |
| Amazon API Gateway | Cung cáº¥p HTTP API public cho Ä‘Æ°á»ng dáº«n `/api/*`. |
| AWS Elastic Beanstalk | Cháº¡y vĂ  quáº£n lĂ½ backend Node.js. |
| Amazon RDS for MySQL | LÆ°u dá»¯ liá»‡u á»©ng dá»¥ng. |
| Amazon S3 | HÆ°á»›ng lÆ°u trá»¯ file sáºµn sĂ ng production. |
| Amazon SES | Gá»­i OTP vĂ  email thĂ´ng bĂ¡o náº¿u cáº¥u hĂ¬nh mail Ä‘Æ°á»£c báº­t. |
| Amazon CloudWatch | LÆ°u log vĂ  há»— trá»£ monitoring. |

## BÆ°á»›c 1: Quan sĂ¡t kiáº¿n trĂºc triá»ƒn khai

TrÆ°á»›c khi báº¯t Ä‘áº§u cáº¥u hĂ¬nh tá»«ng dá»‹ch vá»¥, cáº§n náº¯m Ä‘Æ°á»£c luá»“ng káº¿t ná»‘i tá»•ng thá»ƒ cá»§a há»‡ thá»‘ng.

![SÆ¡ Ä‘á»“ kiáº¿n trĂºc tá»•ng quan cá»§a workshop EAM Workspace](/HUGO/images/5-Workshop/5.1-Workshop-overview/5.1.1-architecture-overview.png)

*HĂ¬nh 5.1.1. SÆ¡ Ä‘á»“ kiáº¿n trĂºc tá»•ng quan cá»§a workshop.*

áº¢nh nĂ y giĂºp xĂ¡c nháº­n cĂ¡c thĂ nh pháº§n chĂ­nh trong kiáº¿n trĂºc: frontend Ä‘Æ°á»£c phá»¥c vá»¥ qua Amplify, request API Ä‘i qua API Gateway, backend cháº¡y trĂªn Elastic Beanstalk vĂ  dá»¯ liá»‡u Ä‘Æ°á»£c lÆ°u trong Amazon RDS MySQL.

## BÆ°á»›c 2: XĂ¡c Ä‘á»‹nh cĂ¡c dá»‹ch vá»¥ AWS Ä‘Æ°á»£c sá»­ dá»¥ng

Sau khi hiá»ƒu kiáº¿n trĂºc tá»•ng quan, Ä‘á»‘i chiáº¿u cĂ¡c thĂ nh pháº§n trong sÆ¡ Ä‘á»“ vá»›i cĂ¡c dá»‹ch vá»¥ AWS sáº½ Ä‘Æ°á»£c thao tĂ¡c trong workshop.

![Tá»•ng quan cĂ¡c dá»‹ch vá»¥ AWS Ä‘Æ°á»£c sá»­ dá»¥ng trong workshop](/HUGO/images/5-Workshop/5.1-Workshop-overview/5.1.2-aws-services-overview.png)

*HĂ¬nh 5.1.2. Tá»•ng quan cĂ¡c dá»‹ch vá»¥ AWS Ä‘Æ°á»£c sá»­ dá»¥ng trong workshop.*

Danh sĂ¡ch dá»‹ch vá»¥ cáº§n Ä‘á»‘i chiáº¿u vá»›i pháº¡m vi workshop, gá»“m Amplify, API Gateway, Elastic Beanstalk, RDS, SES vĂ  CloudWatch.

## Giá»›i háº¡n cá»§a mĂ´i trÆ°á»ng demo

Workshop nĂ y Ä‘Æ°á»£c giá»›i háº¡n cho mĂ´i trÆ°á»ng demo:

- RDS cĂ³ thá»ƒ dĂ¹ng Single-AZ Ä‘á»ƒ giáº£m chi phĂ­.
- Backend cĂ³ thá»ƒ cháº¡y vá»›i má»™t Elastic Beanstalk environment nhá».
- Amplify dĂ¹ng domain máº·c Ä‘á»‹nh.
- KhĂ´ng yĂªu cáº§u custom domain vá»›i Route 53.
- File upload cĂ³ thá»ƒ Ä‘i qua backend trong demo; S3 Ä‘Æ°á»£c Ä‘á»‹nh hÆ°á»›ng cho báº£n sáºµn sĂ ng production.


