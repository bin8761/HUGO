---
title: "Chuáº©n bá»‹ network vĂ  RDS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

## Chuáº©n bá»‹ network vĂ  RDS

BÆ°á»›c nĂ y chuáº©n bá»‹ database MySQL cho backend. Vá»›i mĂ´i trÆ°á»ng demo, cĂ³ thá»ƒ dĂ¹ng VPC máº·c Ä‘á»‹nh hoáº·c VPC Ä‘Ă£ cĂ³ sáºµn, miá»…n lĂ  Elastic Beanstalk backend cĂ³ thá»ƒ káº¿t ná»‘i Ä‘áº¿n Amazon RDS qua port `3306`.

## MĂ´ hĂ¬nh káº¿t ná»‘i má»¥c tiĂªu

{{< mermaid >}}
flowchart LR
    APIGW["Amazon API Gateway"] --> EB["Elastic Beanstalk Backend"]
    EB --> SGBackend["Backend Security Group"]
    SGBackend --> RDS["Amazon RDS MySQL"]
    RDS --> SGRDS["RDS Security Group"]
{{< /mermaid >}}

## BÆ°á»›c 1: Chá»n VPC

DĂ¹ng má»™t VPC cá»‘ Ä‘á»‹nh cho Elastic Beanstalk vĂ  RDS. VPC nĂªn cĂ³:

- Subnet cho Elastic Beanstalk environment.
- Subnet group cho RDS.
- Route Internet phĂ¹ há»£p Ä‘á»ƒ backend cĂ³ thá»ƒ nháº­n request public qua Elastic Beanstalk.
- Security group tĂ¡ch riĂªng cho backend vĂ  database.

Náº¿u workshop chá»‰ phá»¥c vá»¥ demo ngáº¯n háº¡n, cĂ³ thá»ƒ dĂ¹ng cáº¥u hĂ¬nh Ä‘Æ¡n giáº£n hÆ¡n so vá»›i kiáº¿n trĂºc production nhiá»u subnet.

![VPC Ä‘Æ°á»£c sá»­ dá»¥ng cho Elastic Beanstalk vĂ  RDS](/HUGO/images/5-Workshop/5.3-Network-RDS/5.3.1-vpc-subnets.png)

*HĂ¬nh 5.3.1. VPC Ä‘Æ°á»£c sá»­ dá»¥ng cho Elastic Beanstalk vĂ  RDS.*

VPC vĂ  CIDR trong áº£nh cáº§n khá»›p vá»›i mĂ´i trÆ°á»ng dĂ¹ng cho backend vĂ  database. Backend Elastic Beanstalk vĂ  RDS cáº§n náº±m trong cĂ¹ng VPC hoáº·c cĂ³ Ä‘á»‹nh tuyáº¿n phĂ¹ há»£p Ä‘á»ƒ káº¿t ná»‘i an toĂ n.

## BÆ°á»›c 2: Táº¡o security group

Táº¡o hoáº·c kiá»ƒm tra cĂ¡c security group sau:

| Security group | Inbound rule | Má»¥c Ä‘Ă­ch |
| --- | --- | --- |
| `eam-backend-sg` | HTTP tá»« Internet hoáº·c tá»« cáº¥u hĂ¬nh Elastic Beanstalk Ä‘Æ°á»£c chá»n | Cho phĂ©p API Gateway gá»i backend endpoint. |
| `eam-rds-sg` | MySQL `3306` tá»« `eam-backend-sg` | Chá»‰ cho backend káº¿t ná»‘i database. |

Äiá»ƒm quan trá»ng nháº¥t lĂ  RDS khĂ´ng nĂªn má»Ÿ `3306` cho toĂ n bá»™ Internet. Chá»‰ cho phĂ©p backend security group truy cáº­p database.

![Security group cá»§a backend Elastic Beanstalk](/HUGO/images/5-Workshop/5.3-Network-RDS/5.3.2-backend-security-group.png)

*HĂ¬nh 5.3.2. Security group cá»§a backend Elastic Beanstalk.*

Security group ID cá»§a backend cáº§n Ä‘Æ°á»£c ghi láº¡i Ä‘á»ƒ dĂ¹ng lĂ m source cho rule inbound cá»§a RDS.

![Security group cá»§a RDS cho phĂ©p backend truy cáº­p MySQL](/HUGO/images/5-Workshop/5.3-Network-RDS/5.3.3-rds-security-group.png)

*HĂ¬nh 5.3.3. Security group cá»§a RDS cho phĂ©p backend truy cáº­p port 3306.*

Rule inbound MySQL/Aurora `3306` cá»§a RDS chá»‰ nĂªn cho phĂ©p source lĂ  security group cá»§a backend, khĂ´ng má»Ÿ `0.0.0.0/0`.

## BÆ°á»›c 3: Táº¡o Amazon RDS for MySQL

Má»Ÿ Amazon RDS console vĂ  táº¡o database:

1. Chá»n **Create database**.
2. Chá»n **Standard create**.
3. Chá»n engine **MySQL**.
4. Chá»n template **Dev/Test** hoáº·c cáº¥u hĂ¬nh chi phĂ­ tháº¥p.
5. Äáº·t DB instance identifier, vĂ­ dá»¥ `eam-mysql-demo`.
6. Äáº·t master username, vĂ­ dá»¥ `asset_app`.
7. Äáº·t máº­t kháº©u máº¡nh vĂ  lÆ°u á»Ÿ nÆ¡i an toĂ n.
8. Chá»n instance class nhá» cho mĂ´i trÆ°á»ng demo.
9. Chá»n dung lÆ°á»£ng storage phĂ¹ há»£p Ä‘á»ƒ test.
10. Trong **Connectivity**, chá»n VPC má»¥c tiĂªu.
11. Chá»n DB subnet group phĂ¹ há»£p.
12. Náº¿u cĂ³ thá»ƒ, Ä‘áº·t **Public access** lĂ  **No**.
13. Gáº¯n `eam-rds-sg`.
14. Báº­t storage encryption náº¿u cáº§n.
15. Äáº·t initial database name:

```text
enterprise_asset_management
```

Chá» database chuyá»ƒn sang tráº¡ng thĂ¡i **Available**.

![RDS database á»Ÿ tráº¡ng thĂ¡i Available](/HUGO/images/5-Workshop/5.3-Network-RDS/5.3.4-rds-available.png)

*HĂ¬nh 5.3.4. RDS database á»Ÿ tráº¡ng thĂ¡i Available.*

Khi tráº¡ng thĂ¡i database lĂ  `Available`, RDS Ä‘Ă£ sáºµn sĂ ng nháº­n káº¿t ná»‘i. Chá»‰ nĂªn tiáº¿p tá»¥c cáº¥u hĂ¬nh backend sau khi tráº¡ng thĂ¡i nĂ y hiá»ƒn thá»‹ á»•n Ä‘á»‹nh.

## BÆ°á»›c 4: Ghi láº¡i thĂ´ng tin káº¿t ná»‘i

Sau khi RDS available, ghi láº¡i:

- RDS endpoint
- Port, thÆ°á»ng lĂ  `3306`
- Database name
- Username
- Password

Táº¡o backend `DATABASE_URL`:

```env
DATABASE_URL=mysql://asset_app:<password>@<rds-endpoint>:3306/enterprise_asset_management
```

![ThĂ´ng tin káº¿t ná»‘i vĂ  security cá»§a RDS](/HUGO/images/5-Workshop/5.3-Network-RDS/5.3.5-rds-connectivity.png)

*HĂ¬nh 5.3.5. ThĂ´ng tin káº¿t ná»‘i vĂ  security cá»§a RDS.*

Táº¡i pháº§n Connectivity & security, cáº§n láº¥y Ä‘Ăºng endpoint, port, VPC vĂ  security group. CĂ¡c giĂ¡ trá»‹ nĂ y Ä‘Æ°á»£c dĂ¹ng Ä‘á»ƒ táº¡o `DATABASE_URL` cho Elastic Beanstalk.

## BÆ°á»›c 5: Kiá»ƒm tra báº£o máº­t

TrÆ°á»›c khi tiáº¿p tá»¥c, kiá»ƒm tra:

- RDS khĂ´ng má»Ÿ database port cho toĂ n bá»™ Internet.
- Inbound rule cá»§a RDS chá»‰ cho `3306` tá»« backend security group.
- Backend vĂ  RDS náº±m trong cĂ¹ng VPC hoáº·c cĂ³ route phĂ¹ há»£p.
- Username/password database Ä‘Ă£ Ä‘Æ°á»£c lÆ°u an toĂ n vĂ  khĂ´ng commit vĂ o source code.

## Káº¿t quáº£ mong Ä‘á»£i

Káº¿t thĂºc bÆ°á»›c nĂ y, project cĂ³ má»™t MySQL database sáºµn sĂ ng Ä‘á»ƒ backend Elastic Beanstalk káº¿t ná»‘i thĂ´ng qua `DATABASE_URL`.


