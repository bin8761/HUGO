---
title: "Blog 6"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.6. </b> "
---

# Báº¯t Ä‘áº§u vá»›i healthcare data lakes: Sá»­ dá»¥ng microservices

CĂ¡c data lake cĂ³ thá»ƒ giĂºp cĂ¡c bá»‡nh viá»‡n vĂ  cÆ¡ sá»Ÿ y táº¿ chuyá»ƒn dá»¯ liá»‡u thĂ nh nhá»¯ng thĂ´ng tin chi tiáº¿t vá» doanh nghiá»‡p vĂ  duy trĂ¬ hoáº¡t Ä‘á»™ng kinh doanh liĂªn tá»¥c, Ä‘á»“ng thá»i báº£o vá»‡ quyá»n riĂªng tÆ° cá»§a bá»‡nh nhĂ¢n. **Data lake** lĂ  má»™t kho lÆ°u trá»¯ táº­p trung, Ä‘Æ°á»£c quáº£n lĂ½ vĂ  báº£o máº­t Ä‘á»ƒ lÆ°u trá»¯ táº¥t cáº£ dá»¯ liá»‡u cá»§a báº¡n, cáº£ á»Ÿ dáº¡ng ban Ä‘áº§u vĂ  Ä‘Ă£ xá»­ lĂ½ Ä‘á»ƒ phĂ¢n tĂ­ch. data lake cho phĂ©p báº¡n chia nhá» cĂ¡c kho chá»©a dá»¯ liá»‡u vĂ  káº¿t há»£p cĂ¡c loáº¡i phĂ¢n tĂ­ch khĂ¡c nhau Ä‘á»ƒ cĂ³ Ä‘Æ°á»£c thĂ´ng tin chi tiáº¿t vĂ  Ä‘Æ°a ra cĂ¡c quyáº¿t Ä‘á»‹nh kinh doanh tá»‘t hÆ¡n.

BĂ i Ä‘Äƒng trĂªn blog nĂ y lĂ  má»™t pháº§n cá»§a loáº¡t bĂ i lá»›n hÆ¡n vá» viá»‡c báº¯t Ä‘áº§u cĂ i Ä‘áº·t data lake dĂ nh cho lÄ©nh vá»±c y táº¿. Trong bĂ i Ä‘Äƒng blog cuá»‘i cĂ¹ng cá»§a tĂ´i trong loáº¡t bĂ i, *â€œBáº¯t Ä‘áº§u vá»›i data lake dĂ nh cho lÄ©nh vá»±c y táº¿: ÄĂ o sĂ¢u vĂ o Amazon Cognitoâ€*, tĂ´i táº­p trung vĂ o cĂ¡c chi tiáº¿t cá»¥ thá»ƒ cá»§a viá»‡c sá»­ dá»¥ng Amazon Cognito vĂ  Attribute Based Access Control (ABAC) Ä‘á»ƒ xĂ¡c thá»±c vĂ  á»§y quyá»n ngÆ°á»i dĂ¹ng trong giáº£i phĂ¡p data lake y táº¿. Trong blog nĂ y, tĂ´i trĂ¬nh bĂ y chi tiáº¿t cĂ¡ch giáº£i phĂ¡p Ä‘Ă£ phĂ¡t triá»ƒn á»Ÿ cáº¥p Ä‘á»™ cÆ¡ báº£n, bao gá»“m cĂ¡c quyáº¿t Ä‘á»‹nh thiáº¿t káº¿ mĂ  tĂ´i Ä‘Ă£ Ä‘Æ°a ra vĂ  cĂ¡c tĂ­nh nÄƒng bá»• sung Ä‘Æ°á»£c sá»­ dá»¥ng. Báº¡n cĂ³ thá»ƒ truy cáº­p cĂ¡c code samples cho giáº£i phĂ¡p táº¡i Git repo nĂ y Ä‘á»ƒ tham kháº£o.

---

## HÆ°á»›ng dáº«n kiáº¿n trĂºc

Thay Ä‘á»•i chĂ­nh ká»ƒ tá»« láº§n trĂ¬nh bĂ y cuá»‘i cĂ¹ng cá»§a kiáº¿n trĂºc tá»•ng thá»ƒ lĂ  viá»‡c tĂ¡ch dá»‹ch vá»¥ Ä‘Æ¡n láº» thĂ nh má»™t táº­p há»£p cĂ¡c dá»‹ch vá»¥ nhá» Ä‘á»ƒ cáº£i thiá»‡n kháº£ nÄƒng báº£o trĂ¬ vĂ  tĂ­nh linh hoáº¡t. Viá»‡c tĂ­ch há»£p má»™t lÆ°á»£ng lá»›n dá»¯ liá»‡u y táº¿ khĂ¡c nhau thÆ°á»ng yĂªu cáº§u cĂ¡c trĂ¬nh káº¿t ná»‘i chuyĂªn biá»‡t cho tá»«ng Ä‘á»‹nh dáº¡ng; báº±ng cĂ¡ch giá»¯ chĂºng Ä‘Æ°á»£c Ä‘Ă³ng gĂ³i riĂªng biá»‡t vá»›i microservices, chĂºng ta cĂ³ thá»ƒ thĂªm, xĂ³a vĂ  sá»­a Ä‘á»•i tá»«ng trĂ¬nh káº¿t ná»‘i mĂ  khĂ´ng áº£nh hÆ°á»Ÿng Ä‘áº¿n nhá»¯ng káº¿t ná»‘i khĂ¡c. CĂ¡c microservices Ä‘Æ°á»£c káº¿t ná»‘i rá»i thĂ´ng qua tin nháº¯n publish/subscribe táº­p trung trong cĂ¡i mĂ  tĂ´i gá»i lĂ  â€œpub/sub hubâ€.

Giáº£i phĂ¡p nĂ y Ä‘áº¡i diá»‡n cho nhá»¯ng gĂ¬ tĂ´i sáº½ coi lĂ  má»™t láº§n láº·p nÆ°á»›c rĂºt há»£p lĂ½ khĂ¡c tá»« last post cá»§a tĂ´i. Pháº¡m vi váº«n Ä‘Æ°á»£c giá»›i háº¡n trong viá»‡c nháº­p vĂ  phĂ¢n tĂ­ch cĂº phĂ¡p Ä‘Æ¡n giáº£n cá»§a cĂ¡c **HL7v2 messages** Ä‘Æ°á»£c Ä‘á»‹nh dáº¡ng theo **Quy táº¯c mĂ£ hĂ³a 7 (ER7)** thĂ´ng qua giao diá»‡n REST.

**Kiáº¿n trĂºc giáº£i phĂ¡p bĂ¢y giá» nhÆ° sau:**

> *HĂ¬nh 1. Kiáº¿n trĂºc tá»•ng thá»ƒ; nhá»¯ng Ă´ mĂ u thá»ƒ hiá»‡n nhá»¯ng dá»‹ch vá»¥ riĂªng biá»‡t.*

---

Máº·c dĂ¹ thuáº­t ngá»¯ *microservices* cĂ³ má»™t sá»‘ sá»± mÆ¡ há»“ cá»‘ há»¯u, má»™t sá»‘ Ä‘áº·c Ä‘iá»ƒm lĂ  chung:  
- ChĂºng nhá», tá»± chá»§, káº¿t há»£p rá»i ráº¡c  
- CĂ³ thá»ƒ tĂ¡i sá»­ dá»¥ng, giao tiáº¿p thĂ´ng qua giao diá»‡n Ä‘Æ°á»£c xĂ¡c Ä‘á»‹nh rĂµ  
- ChuyĂªn biá»‡t Ä‘á»ƒ giáº£i quyáº¿t má»™t viá»‡c  
- ThÆ°á»ng Ä‘Æ°á»£c triá»ƒn khai trong **event-driven architecture**

Khi xĂ¡c Ä‘á»‹nh vá»‹ trĂ­ táº¡o ranh giá»›i giá»¯a cĂ¡c microservices, cáº§n cĂ¢n nháº¯c:  
- **Ná»™i táº¡i**: cĂ´ng nghá»‡ Ä‘Æ°á»£c sá»­ dá»¥ng, hiá»‡u suáº¥t, Ä‘á»™ tin cáº­y, kháº£ nÄƒng má»Ÿ rá»™ng  
- **BĂªn ngoĂ i**: chá»©c nÄƒng phá»¥ thuá»™c, táº§n suáº¥t thay Ä‘á»•i, kháº£ nÄƒng tĂ¡i sá»­ dá»¥ng  
- **Con ngÆ°á»i**: quyá»n sá»Ÿ há»¯u nhĂ³m, quáº£n lĂ½ *cognitive load*

---

## Lá»±a chá»n cĂ´ng nghá»‡ vĂ  pháº¡m vi giao tiáº¿p

| Pháº¡m vi giao tiáº¿p                        | CĂ¡c cĂ´ng nghá»‡ / mĂ´ hĂ¬nh cáº§n xem xĂ©t                                                        |
| ---------------------------------------- | ------------------------------------------------------------------------------------------ |
| Trong má»™t microservice                   | Amazon Simple Queue Service (Amazon SQS), AWS Step Functions                               |
| Giá»¯a cĂ¡c microservices trong má»™t dá»‹ch vá»¥ | AWS CloudFormation cross-stack references, Amazon Simple Notification Service (Amazon SNS) |
| Giá»¯a cĂ¡c dá»‹ch vá»¥                         | Amazon EventBridge, AWS Cloud Map, Amazon API Gateway                                      |

---

## The pub/sub hub

Viá»‡c sá»­ dá»¥ng kiáº¿n trĂºc **hub-and-spoke** (hay message broker) hoáº¡t Ä‘á»™ng tá»‘t vá»›i má»™t sá»‘ lÆ°á»£ng nhá» cĂ¡c microservices liĂªn quan cháº·t cháº½.  
- Má»—i microservice chá»‰ phá»¥ thuá»™c vĂ o *hub*  
- Káº¿t ná»‘i giá»¯a cĂ¡c microservice chá»‰ giá»›i háº¡n á»Ÿ ná»™i dung cá»§a message Ä‘Æ°á»£c xuáº¥t  
- Giáº£m sá»‘ lÆ°á»£ng synchronous calls vĂ¬ pub/sub lĂ  *push* khĂ´ng Ä‘á»“ng bá»™ má»™t chiá»u

NhÆ°á»£c Ä‘iá»ƒm: cáº§n **phá»‘i há»£p vĂ  giĂ¡m sĂ¡t** Ä‘á»ƒ trĂ¡nh microservice xá»­ lĂ½ nháº§m message.

---

## Core microservice

Cung cáº¥p dá»¯ liá»‡u ná»n táº£ng vĂ  lá»›p truyá»n thĂ´ng, gá»“m:  
- **Amazon S3** bucket cho dá»¯ liá»‡u  
- **Amazon DynamoDB** cho danh má»¥c dá»¯ liá»‡u  
- **AWS Lambda** Ä‘á»ƒ ghi message vĂ o data lake vĂ  danh má»¥c  
- **Amazon SNS** topic lĂ m *hub*  
- **Amazon S3** bucket cho artifacts nhÆ° mĂ£ Lambda

> Chá»‰ cho phĂ©p truy cáº­p ghi giĂ¡n tiáº¿p vĂ o data lake qua hĂ m Lambda â†’ Ä‘áº£m báº£o nháº¥t quĂ¡n.

---

## Front door microservice

- Cung cáº¥p API Gateway Ä‘á»ƒ tÆ°Æ¡ng tĂ¡c REST bĂªn ngoĂ i  
- XĂ¡c thá»±c & á»§y quyá»n dá»±a trĂªn **OIDC** thĂ´ng qua **Amazon Cognito**  
- CÆ¡ cháº¿ *deduplication* tá»± quáº£n lĂ½ báº±ng DynamoDB thay vĂ¬ SNS FIFO vĂ¬:
  1. SNS deduplication TTL chá»‰ 5 phĂºt
  2. SNS FIFO yĂªu cáº§u SQS FIFO
  3. Chá»§ Ä‘á»™ng bĂ¡o cho sender biáº¿t message lĂ  báº£n sao

---

## Staging ER7 microservice

- Lambda â€œtriggerâ€ Ä‘Äƒng kĂ½ vá»›i pub/sub hub, lá»c message theo attribute  
- Step Functions Express Workflow Ä‘á»ƒ chuyá»ƒn ER7 â†’ JSON  
- Hai Lambda:
  1. Sá»­a format ER7 (newline, carriage return)
  2. Parsing logic  
- Káº¿t quáº£ hoáº·c lá»—i Ä‘Æ°á»£c Ä‘áº©y láº¡i vĂ o pub/sub hub

---

## TĂ­nh nÄƒng má»›i trong giáº£i phĂ¡p

### 1. AWS CloudFormation cross-stack references
VĂ­ dá»¥ *outputs* trong core microservice:
```yaml
Outputs:
  Bucket:
    Value: !Ref Bucket
    Export:
      Name: !Sub ${AWS::StackName}-Bucket
  ArtifactBucket:
    Value: !Ref ArtifactBucket
    Export:
      Name: !Sub ${AWS::StackName}-ArtifactBucket
  Topic:
    Value: !Ref Topic
    Export:
      Name: !Sub ${AWS::StackName}-Topic
  Catalog:
    Value: !Ref Catalog
    Export:
      Name: !Sub ${AWS::StackName}-Catalog
  CatalogArn:
    Value: !GetAtt Catalog.Arn
    Export:
      Name: !Sub ${AWS::StackName}-CatalogArn

