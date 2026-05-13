---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Äáº£m báº£o truy cáº­p Hybrid an toĂ n Ä‘áº¿n S3 báº±ng cĂ¡ch sá»­ dá»¥ng VPC endpoint

#### Tá»•ng quan

**AWS PrivateLink** cung cáº¥p káº¿t ná»‘i riĂªng tÆ° Ä‘áº¿n cĂ¡c dá»‹ch vá»¥ aws tá»« VPCs hoáº·c trung tĂ¢m dá»¯ liá»‡u (on-premise) mĂ  khĂ´ng lĂ m lá»™ lÆ°u lÆ°á»£ng truy cáº­p ra ngoĂ i public internet.

Trong bĂ i lab nĂ y, chĂºng ta sáº½ há»c cĂ¡ch táº¡o, cáº¥u hĂ¬nh, vĂ  kiá»ƒm tra VPC endpoints Ä‘á»ƒ cho phĂ©p workload cá»§a báº¡n tiáº¿p cáº­n cĂ¡c dá»‹ch vá»¥ AWS mĂ  khĂ´ng cáº§n Ä‘i qua Internet cĂ´ng cá»™ng.

ChĂºng ta sáº½ táº¡o hai loáº¡i endpoints Ä‘á»ƒ truy cáº­p Ä‘áº¿n Amazon S3: gateway vpc endpoint vĂ  interface vpc endpoint. Hai loáº¡i vpc endpoints nĂ y mang Ä‘áº¿n nhiá»u lá»£i Ă­ch tĂ¹y thuá»™c vĂ o viá»‡c báº¡n truy cáº­p Ä‘áº¿n S3 tá»« mĂ´i trÆ°á»ng cloud hay tá»« trung tĂ¢m dá»¯ liá»‡u (on-premise).
+ **Gateway** - Táº¡o gateway endpoint Ä‘á»ƒ gá»­i lÆ°u lÆ°á»£ng Ä‘áº¿n Amazon S3 hoáº·c DynamoDB using private IP addresses. Báº¡n Ä‘iá»u hÆ°á»›ng lÆ°u lÆ°á»£ng tá»« VPC cá»§a báº¡n Ä‘áº¿n gateway endpoint báº±ng cĂ¡c báº£ng Ä‘á»‹nh tuyáº¿n (route tables)
+ **Interface** - Táº¡o interface endpoint Ä‘á»ƒ gá»­i lÆ°u lÆ°á»£ng Ä‘áº¿n cĂ¡c dá»‹ch vá»¥ Ä‘iá»ƒm cuá»‘i (endpoints) sá»­ dá»¥ng Network Load Balancer Ä‘á»ƒ phĂ¢n phá»‘i lÆ°u lÆ°á»£ng. LÆ°u lÆ°á»£ng dĂ nh cho dá»‹ch vá»¥ Ä‘iá»ƒm cuá»‘i Ä‘Æ°á»£c resolved báº±ng DNS.

#### Ná»™i dung

1. [Tá»•ng quan vá» workshop](5.1-Workshop-overview/)
2. [Chuáº©n bá»‹](5.2-Prerequiste/)
3. [Truy cáº­p Ä‘áº¿n S3 tá»« VPC](5.3-S3-vpc/)
4. [Truy cáº­p Ä‘áº¿n S3 tá»« TTDL On-premises](5.4-S3-onprem/)
5. [VPC Endpoint Policies (lĂ m thĂªm)](5.5-Policy/)
6. [Dá»n dáº¹p tĂ i nguyĂªn](5.6-Cleanup/)
