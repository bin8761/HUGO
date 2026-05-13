---
title: "Báº£n Ä‘á» xuáº¥t"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---
Táº¡i pháº§n nĂ y, báº¡n cáº§n tĂ³m táº¯t cĂ¡c ná»™i dung trong workshop mĂ  báº¡n **dá»± tĂ­nh** sáº½ lĂ m.

# IoT Weather Platform for Lab Research  
## Giáº£i phĂ¡p AWS Serverless há»£p nháº¥t cho giĂ¡m sĂ¡t thá»i tiáº¿t thá»i gian thá»±c  

### 1. TĂ³m táº¯t Ä‘iá»u hĂ nh  
IoT Weather Platform Ä‘Æ°á»£c thiáº¿t káº¿ dĂ nh cho nhĂ³m *ITea Lab* táº¡i TP. Há»“ ChĂ­ Minh nháº±m nĂ¢ng cao kháº£ nÄƒng thu tháº­p vĂ  phĂ¢n tĂ­ch dá»¯ liá»‡u thá»i tiáº¿t. Ná»n táº£ng há»— trá»£ tá»‘i Ä‘a 5 tráº¡m thá»i tiáº¿t, cĂ³ kháº£ nÄƒng má»Ÿ rá»™ng lĂªn 10â€“15 tráº¡m, sá»­ dá»¥ng thiáº¿t bá»‹ biĂªn Raspberry Pi káº¿t há»£p cáº£m biáº¿n ESP32 Ä‘á»ƒ truyá»n dá»¯ liá»‡u qua MQTT. Ná»n táº£ng táº­n dá»¥ng cĂ¡c dá»‹ch vá»¥ AWS Serverless Ä‘á»ƒ cung cáº¥p giĂ¡m sĂ¡t thá»i gian thá»±c, phĂ¢n tĂ­ch dá»± Ä‘oĂ¡n vĂ  tiáº¿t kiá»‡m chi phĂ­, vá»›i quyá»n truy cáº­p giá»›i háº¡n cho 5 thĂ nh viĂªn phĂ²ng lab thĂ´ng qua Amazon Cognito.  

### 2. TuyĂªn bá»‘ váº¥n Ä‘á»  
*Váº¥n Ä‘á» hiá»‡n táº¡i*  
CĂ¡c tráº¡m thá»i tiáº¿t hiá»‡n táº¡i yĂªu cáº§u thu tháº­p dá»¯ liá»‡u thá»§ cĂ´ng, khĂ³ quáº£n lĂ½ khi cĂ³ nhiá»u tráº¡m. KhĂ´ng cĂ³ há»‡ thá»‘ng táº­p trung cho dá»¯ liá»‡u hoáº·c phĂ¢n tĂ­ch thá»i gian thá»±c, vĂ  cĂ¡c ná»n táº£ng bĂªn thá»© ba thÆ°á»ng tá»‘n kĂ©m vĂ  quĂ¡ phá»©c táº¡p.  

*Giáº£i phĂ¡p*  
Ná»n táº£ng sá»­ dá»¥ng AWS IoT Core Ä‘á»ƒ tiáº¿p nháº­n dá»¯ liá»‡u MQTT, AWS Lambda vĂ  API Gateway Ä‘á»ƒ xá»­ lĂ½, Amazon S3 Ä‘á»ƒ lÆ°u trá»¯ (bao gá»“m data lake), vĂ  AWS Glue Crawlers cĂ¹ng cĂ¡c tĂ¡c vá»¥ ETL Ä‘á»ƒ trĂ­ch xuáº¥t, chuyá»ƒn Ä‘á»•i, táº£i dá»¯ liá»‡u tá»« S3 data lake sang má»™t S3 bucket khĂ¡c Ä‘á»ƒ phĂ¢n tĂ­ch. AWS Amplify vá»›i Next.js cung cáº¥p giao diá»‡n web, vĂ  Amazon Cognito Ä‘áº£m báº£o quyá»n truy cáº­p an toĂ n. TÆ°Æ¡ng tá»± nhÆ° Thingsboard vĂ  CoreIoT, ngÆ°á»i dĂ¹ng cĂ³ thá»ƒ Ä‘Äƒng kĂ½ thiáº¿t bá»‹ má»›i vĂ  quáº£n lĂ½ káº¿t ná»‘i, nhÆ°ng ná»n táº£ng nĂ y hoáº¡t Ä‘á»™ng á»Ÿ quy mĂ´ nhá» hÆ¡n vĂ  phá»¥c vá»¥ má»¥c Ä‘Ă­ch sá»­ dá»¥ng ná»™i bá»™. CĂ¡c tĂ­nh nÄƒng chĂ­nh bao gá»“m báº£ng Ä‘iá»u khiá»ƒn thá»i gian thá»±c, phĂ¢n tĂ­ch xu hÆ°á»›ng vĂ  chi phĂ­ váº­n hĂ nh tháº¥p.  

*Lá»£i Ă­ch vĂ  hoĂ n vá»‘n Ä‘áº§u tÆ° (ROI)*  
Giáº£i phĂ¡p táº¡o ná»n táº£ng cÆ¡ báº£n Ä‘á»ƒ cĂ¡c thĂ nh viĂªn phĂ²ng lab phĂ¡t triá»ƒn má»™t ná»n táº£ng IoT lá»›n hÆ¡n, Ä‘á»“ng thá»i cung cáº¥p nguá»“n dá»¯ liá»‡u cho nhá»¯ng ngÆ°á»i nghiĂªn cá»©u AI phá»¥c vá»¥ huáº¥n luyá»‡n mĂ´ hĂ¬nh hoáº·c phĂ¢n tĂ­ch. Ná»n táº£ng giáº£m bá»›t bĂ¡o cĂ¡o thá»§ cĂ´ng cho tá»«ng tráº¡m thĂ´ng qua há»‡ thá»‘ng táº­p trung, Ä‘Æ¡n giáº£n hĂ³a quáº£n lĂ½ vĂ  báº£o trĂ¬, Ä‘á»“ng thá»i cáº£i thiá»‡n Ä‘á»™ tin cáº­y dá»¯ liá»‡u. Chi phĂ­ hĂ ng thĂ¡ng Æ°á»›c tĂ­nh 0,66 USD (theo AWS Pricing Calculator), tá»•ng cá»™ng 7,92 USD cho 12 thĂ¡ng. Táº¥t cáº£ thiáº¿t bá»‹ IoT Ä‘Ă£ Ä‘Æ°á»£c trang bá»‹ tá»« há»‡ thá»‘ng tráº¡m thá»i tiáº¿t hiá»‡n táº¡i, khĂ´ng phĂ¡t sinh chi phĂ­ phĂ¡t triá»ƒn thĂªm. Thá»i gian hoĂ n vá»‘n 6â€“12 thĂ¡ng nhá» tiáº¿t kiá»‡m Ä‘Ă¡ng ká»ƒ thá»i gian thao tĂ¡c thá»§ cĂ´ng.  

### 3. Kiáº¿n trĂºc giáº£i phĂ¡p  
Ná»n táº£ng Ă¡p dá»¥ng kiáº¿n trĂºc AWS Serverless Ä‘á»ƒ quáº£n lĂ½ dá»¯ liá»‡u tá»« 5 tráº¡m dá»±a trĂªn Raspberry Pi, cĂ³ thá»ƒ má»Ÿ rá»™ng lĂªn 15 tráº¡m. Dá»¯ liá»‡u Ä‘Æ°á»£c tiáº¿p nháº­n qua AWS IoT Core, lÆ°u trá»¯ trong S3 data lake vĂ  xá»­ lĂ½ bá»Ÿi AWS Glue Crawlers vĂ  ETL jobs Ä‘á»ƒ chuyá»ƒn Ä‘á»•i vĂ  táº£i vĂ o má»™t S3 bucket khĂ¡c cho má»¥c Ä‘Ă­ch phĂ¢n tĂ­ch. Lambda vĂ  API Gateway xá»­ lĂ½ bá»• sung, trong khi Amplify vá»›i Next.js cung cáº¥p báº£ng Ä‘iá»u khiá»ƒn Ä‘Æ°á»£c báº£o máº­t bá»Ÿi Cognito.  

![IoT Weather Station Architecture](/images/2-Proposal/edge_architecture.jpeg)

![IoT Weather Platform Architecture](/images/2-Proposal/platform_architecture.jpeg)

*Dá»‹ch vá»¥ AWS sá»­ dá»¥ng*  
- *AWS IoT Core*: Tiáº¿p nháº­n dá»¯ liá»‡u MQTT tá»« 5 tráº¡m, má»Ÿ rá»™ng lĂªn 15.  
- *AWS Lambda*: Xá»­ lĂ½ dá»¯ liá»‡u vĂ  kĂ­ch hoáº¡t Glue jobs (2 hĂ m).  
- *Amazon API Gateway*: Giao tiáº¿p vá»›i á»©ng dá»¥ng web.  
- *Amazon S3*: LÆ°u trá»¯ dá»¯ liá»‡u thĂ´ (data lake) vĂ  dá»¯ liá»‡u Ä‘Ă£ xá»­ lĂ½ (2 bucket).  
- *AWS Glue*: Crawlers láº­p chá»‰ má»¥c dá»¯ liá»‡u, ETL jobs chuyá»ƒn Ä‘á»•i vĂ  táº£i dá»¯ liá»‡u.  
- *AWS Amplify*: LÆ°u trá»¯ giao diá»‡n web Next.js.  
- *Amazon Cognito*: Quáº£n lĂ½ quyá»n truy cáº­p cho ngÆ°á»i dĂ¹ng phĂ²ng lab.  

*Thiáº¿t káº¿ thĂ nh pháº§n*  
- *Thiáº¿t bá»‹ biĂªn*: Raspberry Pi thu tháº­p vĂ  lá»c dá»¯ liá»‡u cáº£m biáº¿n, gá»­i tá»›i IoT Core.  
- *Tiáº¿p nháº­n dá»¯ liá»‡u*: AWS IoT Core nháº­n tin nháº¯n MQTT tá»« thiáº¿t bá»‹ biĂªn.  
- *LÆ°u trá»¯ dá»¯ liá»‡u*: Dá»¯ liá»‡u thĂ´ lÆ°u trong S3 data lake; dá»¯ liá»‡u Ä‘Ă£ xá»­ lĂ½ lÆ°u á»Ÿ má»™t S3 bucket khĂ¡c.  
- *Xá»­ lĂ½ dá»¯ liá»‡u*: AWS Glue Crawlers láº­p chá»‰ má»¥c dá»¯ liá»‡u; ETL jobs chuyá»ƒn Ä‘á»•i Ä‘á»ƒ phĂ¢n tĂ­ch.  
- *Giao diá»‡n web*: AWS Amplify lÆ°u trá»¯ á»©ng dá»¥ng Next.js cho báº£ng Ä‘iá»u khiá»ƒn vĂ  phĂ¢n tĂ­ch thá»i gian thá»±c.  
- *Quáº£n lĂ½ ngÆ°á»i dĂ¹ng*: Amazon Cognito giá»›i háº¡n 5 tĂ i khoáº£n hoáº¡t Ä‘á»™ng.  

### 4. Triá»ƒn khai ká»¹ thuáº­t  
*CĂ¡c giai Ä‘oáº¡n triá»ƒn khai*  
Dá»± Ă¡n gá»“m 2 pháº§n â€” thiáº¿t láº­p tráº¡m thá»i tiáº¿t biĂªn vĂ  xĂ¢y dá»±ng ná»n táº£ng thá»i tiáº¿t â€” má»—i pháº§n tráº£i qua 4 giai Ä‘oáº¡n:  
1. *NghiĂªn cá»©u vĂ  váº½ kiáº¿n trĂºc*: NghiĂªn cá»©u Raspberry Pi vá»›i cáº£m biáº¿n ESP32 vĂ  thiáº¿t káº¿ kiáº¿n trĂºc AWS Serverless (1 thĂ¡ng trÆ°á»›c ká»³ thá»±c táº­p).  
2. *TĂ­nh toĂ¡n chi phĂ­ vĂ  kiá»ƒm tra tĂ­nh kháº£ thi*: Sá»­ dá»¥ng AWS Pricing Calculator Ä‘á»ƒ Æ°á»›c tĂ­nh vĂ  Ä‘iá»u chá»‰nh (ThĂ¡ng 1).  
3. *Äiá»u chá»‰nh kiáº¿n trĂºc Ä‘á»ƒ tá»‘i Æ°u chi phĂ­/giáº£i phĂ¡p*: Tinh chá»‰nh (vĂ­ dá»¥ tá»‘i Æ°u Lambda vá»›i Next.js) Ä‘á»ƒ Ä‘áº£m báº£o hiá»‡u quáº£ (ThĂ¡ng 2).  
4. *PhĂ¡t triá»ƒn, kiá»ƒm thá»­, triá»ƒn khai*: Láº­p trĂ¬nh Raspberry Pi, AWS services vá»›i CDK/SDK vĂ  á»©ng dá»¥ng Next.js, sau Ä‘Ă³ kiá»ƒm thá»­ vĂ  Ä‘Æ°a vĂ o váº­n hĂ nh (ThĂ¡ng 2â€“3).  

*YĂªu cáº§u ká»¹ thuáº­t*  
- *Tráº¡m thá»i tiáº¿t biĂªn*: Cáº£m biáº¿n (nhiá»‡t Ä‘á»™, Ä‘á»™ áº©m, lÆ°á»£ng mÆ°a, tá»‘c Ä‘á»™ giĂ³), vi Ä‘iá»u khiá»ƒn ESP32, Raspberry Pi lĂ m thiáº¿t bá»‹ biĂªn. Raspberry Pi cháº¡y Raspbian, sá»­ dá»¥ng Docker Ä‘á»ƒ lá»c dá»¯ liá»‡u vĂ  gá»­i 1 MB/ngĂ y/tráº¡m qua MQTT qua Wi-Fi.  
- *Ná»n táº£ng thá»i tiáº¿t*: Kiáº¿n thá»©c thá»±c táº¿ vá» AWS Amplify (lÆ°u trá»¯ Next.js), Lambda (giáº£m thiá»ƒu do Next.js xá»­ lĂ½), AWS Glue (ETL), S3 (2 bucket), IoT Core (gateway vĂ  rules), vĂ  Cognito (5 ngÆ°á»i dĂ¹ng). Sá»­ dá»¥ng AWS CDK/SDK Ä‘á»ƒ láº­p trĂ¬nh (vĂ­ dá»¥ IoT Core rules tá»›i S3). Next.js giĂºp giáº£m táº£i Lambda cho á»©ng dá»¥ng web fullstack.  

### 5. Lá»™ trĂ¬nh & Má»‘c triá»ƒn khai  
- *TrÆ°á»›c thá»±c táº­p (ThĂ¡ng 0)*: 1 thĂ¡ng lĂªn káº¿ hoáº¡ch vĂ  Ä‘Ă¡nh giĂ¡ tráº¡m cÅ©.  
- *Thá»±c táº­p (ThĂ¡ng 1â€“3)*:  
    - ThĂ¡ng 1: Há»c AWS vĂ  nĂ¢ng cáº¥p pháº§n cá»©ng.  
    - ThĂ¡ng 2: Thiáº¿t káº¿ vĂ  Ä‘iá»u chá»‰nh kiáº¿n trĂºc.  
    - ThĂ¡ng 3: Triá»ƒn khai, kiá»ƒm thá»­, Ä‘Æ°a vĂ o sá»­ dá»¥ng.  
- *Sau triá»ƒn khai*: NghiĂªn cá»©u thĂªm trong vĂ²ng 1 nÄƒm.  

### 6. Æ¯á»›c tĂ­nh ngĂ¢n sĂ¡ch  
CĂ³ thá»ƒ xem chi phĂ­ trĂªn [AWS Pricing Calculator](https://calculator.aws/#/estimate?id=621f38b12a1ef026842ba2ddfe46ff936ed4ab01)  
Hoáº·c táº£i [tá»‡p Æ°á»›c tĂ­nh ngĂ¢n sĂ¡ch](../attachments/budget_estimation.pdf).  

*Chi phĂ­ háº¡ táº§ng*  
- AWS Lambda: 0,00 USD/thĂ¡ng (1.000 request, 512 MB lÆ°u trá»¯).  
- S3 Standard: 0,15 USD/thĂ¡ng (6 GB, 2.100 request, 1 GB quĂ©t).  
- Truyá»n dá»¯ liá»‡u: 0,02 USD/thĂ¡ng (1 GB vĂ o, 1 GB ra).  
- AWS Amplify: 0,35 USD/thĂ¡ng (256 MB, request 500 ms).  
- Amazon API Gateway: 0,01 USD/thĂ¡ng (2.000 request).  
- AWS Glue ETL Jobs: 0,02 USD/thĂ¡ng (2 DPU).  
- AWS Glue Crawlers: 0,07 USD/thĂ¡ng (1 crawler).  
- MQTT (IoT Core): 0,08 USD/thĂ¡ng (5 thiáº¿t bá»‹, 45.000 tin nháº¯n).  

*Tá»•ng*: 0,7 USD/thĂ¡ng, 8,40 USD/12 thĂ¡ng  
- *Pháº§n cá»©ng*: 265 USD má»™t láº§n (Raspberry Pi 5 vĂ  cáº£m biáº¿n).  

### 7. ÄĂ¡nh giĂ¡ rá»§i ro  
*Ma tráº­n rá»§i ro*  
- Máº¥t máº¡ng: áº¢nh hÆ°á»Ÿng trung bĂ¬nh, xĂ¡c suáº¥t trung bĂ¬nh.  
- Há»ng cáº£m biáº¿n: áº¢nh hÆ°á»Ÿng cao, xĂ¡c suáº¥t tháº¥p.  
- VÆ°á»£t ngĂ¢n sĂ¡ch: áº¢nh hÆ°á»Ÿng trung bĂ¬nh, xĂ¡c suáº¥t tháº¥p.  

*Chiáº¿n lÆ°á»£c giáº£m thiá»ƒu*  
- Máº¡ng: LÆ°u trá»¯ cá»¥c bá»™ trĂªn Raspberry Pi vá»›i Docker.  
- Cáº£m biáº¿n: Kiá»ƒm tra Ä‘á»‹nh ká»³, dá»± phĂ²ng linh kiá»‡n.  
- Chi phĂ­: Cáº£nh bĂ¡o ngĂ¢n sĂ¡ch AWS, tá»‘i Æ°u dá»‹ch vá»¥.  

*Káº¿ hoáº¡ch dá»± phĂ²ng*  
- Quay láº¡i thu tháº­p thá»§ cĂ´ng náº¿u AWS gáº·p sá»± cá»‘.  
- Sá»­ dá»¥ng CloudFormation Ä‘á»ƒ khĂ´i phá»¥c cáº¥u hĂ¬nh liĂªn quan Ä‘áº¿n chi phĂ­.  

### 8. Káº¿t quáº£ ká»³ vá»ng  
*Cáº£i tiáº¿n ká»¹ thuáº­t*: Dá»¯ liá»‡u vĂ  phĂ¢n tĂ­ch thá»i gian thá»±c thay tháº¿ quy trĂ¬nh thá»§ cĂ´ng. CĂ³ thá»ƒ má»Ÿ rá»™ng tá»›i 10â€“15 tráº¡m.  
*GiĂ¡ trá»‹ dĂ i háº¡n*: Ná»n táº£ng dá»¯ liá»‡u 1 nÄƒm cho nghiĂªn cá»©u AI, cĂ³ thá»ƒ tĂ¡i sá»­ dá»¥ng cho cĂ¡c dá»±Â Ă¡nÂ tÆ°Æ¡ngÂ lai.
