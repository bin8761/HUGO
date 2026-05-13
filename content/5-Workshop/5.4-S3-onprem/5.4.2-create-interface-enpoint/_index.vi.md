---
title : "Táº¡o má»™t S3 Interface endpoint"
date : 2024-01-01
weight : 2
chapter : false
pre : " <b> 5.4.2 </b> "
---

Trong pháº§n nĂ y, báº¡n sáº½ táº¡o vĂ  kiá»ƒm tra Interface Endpoint  S3 báº±ng cĂ¡ch sá»­ dá»¥ng mĂ´i trÆ°á»ng truyá»n thá»‘ng mĂ´ phá»ng.

1. Quay láº¡i Amazon VPC menu. Trong thanh Ä‘iá»u hÆ°á»›ng bĂªn trĂ¡i, chá»n Endpoints, sau Ä‘Ă³ click Create Endpoint.

2. Trong Create endpoint console:
+ Äáº·t tĂªn interface endpoint
+ Trong Service category, chá»n **aws services** 

![name](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint1.png)

3.  Trong Search box, gĂµ S3 vĂ  nháº¥n Enter. Chá»n endpoint cĂ³ tĂªn com.amazonaws.us-east-1.s3. Äáº£m báº£o ráº±ng cá»™t Type cĂ³ giĂ¡ trá»‹ Interface.

![service](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint2.png)

4. Äá»‘i vá»›i VPC, chá»n VPC Cloud tá»« drop-down.
+ Má»Ÿ rá»™ng **Additional settings** vĂ  Ä‘áº£m báº£o ráº±ng Enable DNS name *khĂ´ng* Ä‘Æ°á»£c chá»n (sáº½ sá»­ dá»¥ng Ä‘iá»u nĂ y trong pháº§n tiáº¿p theo cá»§a workshop)

![vpc](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint3.png)

5. Chá»n 2 subnets trong AZs sau: us-east-1a and us-east-1b

![subnets](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint4.png)

6. Äá»‘i vá»›i Security group, chá»n SGforS3Endpoint:

![sg](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint5.png)

7. Giá»¯ default policy - full access vĂ  click Create endpoint

![success](/images/5-Workshop/5.4-S3-onprem/s3-interface-endpoint-success.png)

ChĂºc má»«ng báº¡n Ä‘Ă£ táº¡o thĂ nh cĂ´ng S3 interface endpoint. á» bÆ°á»›c tiáº¿p theo, chĂºng ta sáº½ kiá»ƒm tra interface endpoint.
