---
title: "Dá»n dáº¹p tĂ i nguyĂªn"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---


Sau khi hoĂ n thĂ nh workshop triá»ƒn khai **EAM Workspace** trĂªn AWS, cáº§n dá»n dáº¹p cĂ¡c tĂ i nguyĂªn khĂ´ng cĂ²n sá»­ dá»¥ng Ä‘á»ƒ trĂ¡nh phĂ¡t sinh chi phĂ­ ngoĂ i dá»± kiáº¿n. á» workshop nĂ y, cĂ¡c tĂ i nguyĂªn chĂ­nh Ä‘Ă£ sá»­ dá»¥ng gá»“m **AWS Amplify Hosting**, **Amazon API Gateway**, **AWS Elastic Beanstalk**, **Amazon RDS for MySQL**, **Amazon SES**, security group vĂ  má»™t sá»‘ log/metric liĂªn quan.

TrÆ°á»›c khi xĂ³a tĂ i nguyĂªn, cáº§n chá»¥p láº¡i cĂ¡c mĂ n hĂ¬nh quan trá»ng Ä‘á»ƒ Ä‘Æ°a vĂ o bĂ¡o cĂ¡o. CĂ¡c áº£nh nĂ y giĂºp chá»©ng minh project Ä‘Ă£ Ä‘Æ°á»£c triá»ƒn khai, kiá»ƒm thá»­ vĂ  cĂ³ káº¿ hoáº¡ch cleanup rĂµ rĂ ng.

### Tá»•ng káº¿t ná»™i dung Ä‘Ă£ thá»±c hiá»‡n

Trong workshop nĂ y, há»‡ thá»‘ng EAM Workspace Ä‘Ă£ Ä‘Æ°á»£c triá»ƒn khai theo mĂ´ hĂ¬nh web full-stack trĂªn AWS:

- Frontend React/Vite Ä‘Æ°á»£c build vĂ  host báº±ng **AWS Amplify Hosting**.
- Request `/api/*` tá»« frontend Ä‘Æ°á»£c chuyá»ƒn Ä‘áº¿n **Amazon API Gateway**.
- API Gateway chuyá»ƒn tiáº¿p request Ä‘áº¿n backend cháº¡y trĂªn **AWS Elastic Beanstalk**.
- Backend káº¿t ná»‘i Ä‘áº¿n **Amazon RDS for MySQL** Ä‘á»ƒ lÆ°u dá»¯ liá»‡u nghiá»‡p vá»¥.
- Chá»©c nÄƒng gá»­i email/OTP sá»­ dá»¥ng **Amazon SES** thĂ´ng qua SMTP credential.
- Káº¿t quáº£ triá»ƒn khai Ä‘Æ°á»£c kiá»ƒm tra báº±ng health endpoint, giao diá»‡n Ä‘Äƒng nháº­p, dashboard vĂ  cĂ¡c mĂ n hĂ¬nh nghiá»‡p vá»¥ chĂ­nh.

Sau khi Ä‘Ă£ hoĂ n táº¥t pháº§n kiá»ƒm thá»­ vĂ  ghi nháº­n áº£nh minh há»a, cĂ¡c tĂ i nguyĂªn demo cĂ³ thá»ƒ Ä‘Æ°á»£c xĂ³a theo thá»© tá»± bĂªn dÆ°á»›i.

## BÆ°á»›c 1: Ghi láº¡i danh sĂ¡ch tĂ i nguyĂªn cáº§n dá»n dáº¹p

TrÆ°á»›c khi xĂ³a, nĂªn ghi láº¡i tĂªn cĂ¡c tĂ i nguyĂªn Ä‘Ă£ táº¡o trong workshop:

| NhĂ³m tĂ i nguyĂªn | TĂªn hoáº·c ná»™i dung cáº§n kiá»ƒm tra |
| --- | --- |
| Amplify app | App frontend `quanlidoanhnghiep` hoáº·c branch deploy `aws-architecture` |
| API Gateway | HTTP API `eam-backend-http-api` |
| Elastic Beanstalk | Environment backend, vĂ­ dá»¥ `eam-backend-prod-v8` |
| RDS | MySQL database dĂ¹ng cho EAM Workspace |
| SES | Email identity vĂ  SMTP credential dĂ¹ng Ä‘á»ƒ gá»­i email |
| CloudWatch | Log/metric liĂªn quan Ä‘áº¿n Elastic Beanstalk hoáº·c API |
| EC2/Security Group | Security group cá»§a Elastic Beanstalk vĂ  RDS |

Viá»‡c ghi láº¡i danh sĂ¡ch nĂ y giĂºp trĂ¡nh xĂ³a nháº§m tĂ i nguyĂªn khĂ´ng thuá»™c workshop.

## BÆ°á»›c 2: XĂ³a hoáº·c disconnect AWS Amplify app

AWS Amplify Hosting Ä‘ang dĂ¹ng Ä‘á»ƒ build vĂ  public frontend. Náº¿u khĂ´ng cĂ²n cáº§n demo giao diá»‡n, cĂ³ thá»ƒ xĂ³a app hoáº·c disconnect branch deploy.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **AWS Amplify** console.
2. Chá»n app frontend cá»§a project, vĂ­ dá»¥ `quanlidoanhnghiep`.
3. Chá»n branch deploy Ä‘ang dĂ¹ng, vĂ­ dá»¥ `aws-architecture`.
4. Chá»¥p láº¡i mĂ n hĂ¬nh app/branch trÆ°á»›c khi xĂ³a.
5. Náº¿u muá»‘n dá»n hoĂ n toĂ n, chá»n **App settings** hoáº·c **General settings** vĂ  thá»±c hiá»‡n xĂ³a app.
6. XĂ¡c nháº­n domain Amplify khĂ´ng cĂ²n Ä‘Æ°á»£c sá»­ dá»¥ng cho demo.

Náº¿u váº«n cáº§n giá»¯ frontend Ä‘á»ƒ trĂ¬nh bĂ y bĂ¡o cĂ¡o, cĂ³ thá»ƒ táº¡m thá»i chÆ°a xĂ³a Amplify, nhÆ°ng cáº§n ghi chĂº ráº±ng tĂ i nguyĂªn nĂ y váº«n cĂ²n tá»“n táº¡i.

![Amplify app cleanup](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.1-amplify-cleanup.png)

*HĂ¬nh 5.7.1. AWS Amplify app `quanlidoanhnghiep` vĂ  branch `aws-architecture` Ä‘Æ°á»£c kiá»ƒm tra trÆ°á»›c khi cleanup. áº¢nh nĂ y ghi nháº­n frontend Ä‘Ă£ Ä‘Æ°á»£c deploy thĂ nh cĂ´ng, cĂ³ domain Amplify Ä‘ang hoáº¡t Ä‘á»™ng vĂ  lĂ  tĂ i nguyĂªn cáº§n xá»­ lĂ½ náº¿u khĂ´ng tiáº¿p tá»¥c duy trĂ¬ báº£n demo.*

Sau khi ghi nháº­n áº£nh nĂ y, thá»±c hiá»‡n cleanup Amplify theo hÆ°á»›ng:

1. Náº¿u khĂ´ng cáº§n giá»¯ frontend demo, vĂ o **App settings** -> **General settings** -> **Delete app**.
2. Náº¿u chá»‰ muá»‘n dá»«ng branch deploy, chá»n branch `aws-architecture` vĂ  disconnect/delete branch.
3. Kiá»ƒm tra láº¡i domain Amplify sau khi xĂ³a Ä‘á»ƒ báº£o Ä‘áº£m URL public khĂ´ng cĂ²n truy cáº­p Ä‘Æ°á»£c.
4. Náº¿u váº«n giá»¯ app Ä‘á»ƒ trĂ¬nh bĂ y bĂ¡o cĂ¡o, cáº§n ghi chĂº láº¡i ráº±ng Amplify váº«n Ä‘ang Ä‘Æ°á»£c duy trĂ¬ vĂ  tiáº¿p tá»¥c theo dĂµi chi phĂ­ trong Billing.

## BÆ°á»›c 3: XĂ³a Amazon API Gateway

API Gateway lĂ  lá»›p public endpoint Ä‘á»ƒ frontend gá»i backend. Náº¿u API khĂ´ng cĂ²n dĂ¹ng, nĂªn xĂ³a Ä‘á»ƒ trĂ¡nh endpoint váº«n tiáº¿p tá»¥c nháº­n request.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **Amazon API Gateway** console.
2. Chá»n HTTP API cá»§a project, vĂ­ dá»¥ `eam-backend-http-api`.
3. Kiá»ƒm tra route `ANY /{proxy+}` vĂ  integration Ä‘ang trá» Ä‘áº¿n Elastic Beanstalk backend.
4. Chá»¥p láº¡i mĂ n hĂ¬nh danh sĂ¡ch API hoáº·c trang route/integration.
5. Chá»n **Delete** Ä‘á»ƒ xĂ³a API náº¿u khĂ´ng cĂ²n cáº§n sá»­ dá»¥ng.
6. Kiá»ƒm tra láº¡i danh sĂ¡ch API Ä‘á»ƒ xĂ¡c nháº­n API Ä‘Ă£ Ä‘Æ°á»£c xĂ³a.

Sau khi xĂ³a API Gateway, cĂ¡c URL dáº¡ng `https://...execute-api.ap-southeast-1.amazonaws.com/...` sáº½ khĂ´ng cĂ²n hoáº¡t Ä‘á»™ng.

![API Gateway cleanup](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.2-api-gateway-cleanup.png)

*HĂ¬nh 5.7.2. HTTP API `eam-backend-http-api` trong Amazon API Gateway trÆ°á»›c khi xĂ³a. MĂ n hĂ¬nh nĂ y giĂºp xĂ¡c nháº­n Ä‘Ăºng API public endpoint cá»§a backend, trĂ¡nh xĂ³a nháº§m API khĂ´ng thuá»™c project.*

Sau khi chá»¥p láº¡i API, thá»±c hiá»‡n cleanup nhÆ° sau:

1. Chá»n Ä‘Ăºng HTTP API `eam-backend-http-api`.
2. Kiá»ƒm tra láº¡i route `ANY /{proxy+}` vĂ  integration Ä‘ang trá» vá» Elastic Beanstalk backend.
3. Náº¿u khĂ´ng cĂ²n dĂ¹ng frontend/backend demo, chá»n **Delete** Ä‘á»ƒ xĂ³a API.
4. Sau khi xĂ³a, thá»­ truy cáº­p láº¡i API endpoint hoáº·c kiá»ƒm tra danh sĂ¡ch API Ä‘á»ƒ xĂ¡c nháº­n API khĂ´ng cĂ²n tá»“n táº¡i.
5. Náº¿u frontend Amplify váº«n cĂ²n giá»¯, cáº§n cáº­p nháº­t láº¡i cáº¥u hĂ¬nh rewrite hoáº·c ghi chĂº ráº±ng cĂ¡c request `/api/*` sáº½ khĂ´ng cĂ²n hoáº¡t Ä‘á»™ng.

## BÆ°á»›c 4: Terminate Elastic Beanstalk environment

Elastic Beanstalk quáº£n lĂ½ mĂ´i trÆ°á»ng cháº¡y backend Node.js/Express. ÄĂ¢y lĂ  tĂ i nguyĂªn cĂ³ thá»ƒ táº¡o EC2 instance, load balancer, Auto Scaling resource vĂ  security group liĂªn quan, vĂ¬ váº­y cáº§n terminate khi khĂ´ng cĂ²n sá»­ dá»¥ng.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **Elastic Beanstalk** console.
2. Chá»n environment backend, vĂ­ dá»¥ `eam-backend-prod-v8`.
3. Chá»¥p láº¡i mĂ n hĂ¬nh environment trÆ°á»›c khi terminate, gá»“m health, platform vĂ  domain.
4. Chá»n **Actions** -> **Terminate environment**.
5. Nháº­p tĂªn environment Ä‘á»ƒ xĂ¡c nháº­n náº¿u AWS yĂªu cáº§u.
6. Chá» Ä‘áº¿n khi environment chuyá»ƒn sang tráº¡ng thĂ¡i terminated.
7. Kiá»ƒm tra EC2 console Ä‘á»ƒ báº£o Ä‘áº£m instance do Elastic Beanstalk táº¡o Ä‘Ă£ Ä‘Æ°á»£c dá»«ng/xĂ³a.

Náº¿u Elastic Beanstalk chÆ°a terminate Ä‘Æ°á»£c do dependency, cáº§n kiá»ƒm tra thĂªm security group, load balancer hoáº·c EC2 resource liĂªn quan.

![Elastic Beanstalk cleanup](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.3-eb-cleanup.png)

*HĂ¬nh 5.7.3. Elastic Beanstalk environment `eam-backend-prod-v8` trÆ°á»›c khi terminate. áº¢nh thá»ƒ hiá»‡n environment backend Ä‘ang á»Ÿ tráº¡ng thĂ¡i hoáº¡t Ä‘á»™ng á»•n Ä‘á»‹nh, cĂ³ domain riĂªng vĂ  lĂ  tĂ i nguyĂªn cĂ³ thá»ƒ phĂ¡t sinh chi phĂ­ náº¿u tiáº¿p tá»¥c cháº¡y.*

Äá»ƒ cleanup backend trĂªn Elastic Beanstalk:

1. VĂ o environment `eam-backend-prod-v8`.
2. Chá»n **Actions** -> **Terminate environment**.
3. Nháº­p chĂ­nh xĂ¡c tĂªn environment náº¿u AWS yĂªu cáº§u xĂ¡c nháº­n.
4. Chá» tráº¡ng thĂ¡i chuyá»ƒn sang terminated, sau Ä‘Ă³ kiá»ƒm tra EC2 Ä‘á»ƒ báº£o Ä‘áº£m instance/load balancer do environment táº¡o Ä‘Ă£ Ä‘Æ°á»£c xĂ³a.
5. Náº¿u terminate bá»‹ lá»—i do dependency, kiá»ƒm tra thĂªm Load Balancer, Auto Scaling group, network interface vĂ  security group liĂªn quan.

## BÆ°á»›c 5: XĂ³a hoáº·c táº¡m dá»«ng Amazon RDS for MySQL

Amazon RDS lĂ  tĂ i nguyĂªn quan trá»ng vĂ¬ cĂ³ thá»ƒ phĂ¡t sinh chi phĂ­ khi database instance váº«n cháº¡y. TrÆ°á»›c khi xĂ³a, cáº§n xĂ¡c Ä‘á»‹nh cĂ³ cáº§n giá»¯ dá»¯ liá»‡u demo hay khĂ´ng.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **Amazon RDS** console.
2. Chá»n database MySQL cá»§a project EAM Workspace.
3. Chá»¥p láº¡i mĂ n hĂ¬nh database list hoáº·c database detail.
4. Náº¿u cáº§n giá»¯ dá»¯ liá»‡u, táº¡o snapshot trÆ°á»›c khi xĂ³a.
5. Náº¿u khĂ´ng cáº§n giá»¯ dá»¯ liá»‡u, chá»n **Delete**.
6. Vá»›i mĂ´i trÆ°á»ng demo, cĂ³ thá»ƒ chá»n khĂ´ng táº¡o final snapshot náº¿u dá»¯ liá»‡u khĂ´ng cĂ²n cáº§n thiáº¿t.
7. XĂ¡c nháº­n database Ä‘Ă£ chuyá»ƒn sang tráº¡ng thĂ¡i deleting/deleted.

Náº¿u chÆ°a muá»‘n xĂ³a RDS ngay, cáº§n táº¡m dá»«ng database náº¿u phĂ¹ há»£p vĂ  tiáº¿p tá»¥c theo dĂµi chi phĂ­ trong Billing.

![RDS cleanup](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.4-rds-cleanup.png)

*HĂ¬nh 5.7.4. Amazon RDS database `eam-mysql` Ä‘Æ°á»£c kiá»ƒm tra trÆ°á»›c khi cleanup. ÄĂ¢y lĂ  tĂ i nguyĂªn cáº§n chĂº Ă½ vĂ¬ database instance váº«n cĂ³ thá»ƒ phĂ¡t sinh chi phĂ­ khi cĂ²n á»Ÿ tráº¡ng thĂ¡i available.*

Äá»‘i vá»›i RDS, cáº§n cleanup cáº©n tháº­n hÆ¡n vĂ¬ dá»¯ liá»‡u cĂ³ thá»ƒ bá»‹ máº¥t:

1. Náº¿u cáº§n giá»¯ dá»¯ liá»‡u demo, táº¡o snapshot trÆ°á»›c khi xĂ³a database.
2. Náº¿u dá»¯ liá»‡u khĂ´ng cĂ²n cáº§n thiáº¿t, chá»n database `eam-mysql` -> **Actions** -> **Delete**.
3. Vá»›i mĂ´i trÆ°á»ng demo, cĂ³ thá»ƒ bá» chá»n final snapshot náº¿u Ä‘Ă£ cháº¯c cháº¯n khĂ´ng cáº§n khĂ´i phá»¥c dá»¯ liá»‡u.
4. XĂ¡c nháº­n database chuyá»ƒn sang tráº¡ng thĂ¡i deleting/deleted.
5. Sau khi RDS bá»‹ xĂ³a, kiá»ƒm tra láº¡i security group liĂªn quan vĂ¬ cĂ³ thá»ƒ khĂ´ng cĂ²n dependency vĂ  cĂ³ thá»ƒ xĂ³a tiáº¿p.

## BÆ°á»›c 6: Kiá»ƒm tra Amazon SES

Amazon SES trong workshop Ä‘Æ°á»£c dĂ¹ng Ä‘á»ƒ xĂ¡c thá»±c email identity vĂ  táº¡o SMTP credential cho backend gá»­i email/OTP. SES thÆ°á»ng khĂ´ng phĂ¡t sinh chi phĂ­ lá»›n náº¿u khĂ´ng gá»­i email nhiá»u, nhÆ°ng váº«n nĂªn kiá»ƒm tra láº¡i cáº¥u hĂ¬nh.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **Amazon SES** console.
2. Kiá»ƒm tra email identity Ä‘Ă£ xĂ¡c thá»±c.
3. Kiá»ƒm tra SMTP credential/IAM user Ä‘Ă£ táº¡o cho SES.
4. Náº¿u khĂ´ng cĂ²n sá»­ dá»¥ng, xĂ³a IAM user hoáº·c credential liĂªn quan Ä‘áº¿n SMTP.
5. KhĂ´ng Ä‘Æ°a SMTP password vĂ o áº£nh chá»¥p hoáº·c bĂ¡o cĂ¡o.

Náº¿u váº«n giá»¯ SES Ä‘á»ƒ tiáº¿p tá»¥c demo chá»©c nÄƒng email, cáº§n báº£o quáº£n credential cáº©n tháº­n vĂ  khĂ´ng commit vĂ o GitHub.

![SES cleanup](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.5-ses-cleanup.png)

*HĂ¬nh 5.7.5. Amazon SES email identity Ä‘Ă£ Ä‘Æ°á»£c xĂ¡c thá»±c táº¡i region Singapore. áº¢nh nĂ y dĂ¹ng Ä‘á»ƒ ghi nháº­n cáº¥u hĂ¬nh gá»­i email/OTP cá»§a backend, Ä‘á»“ng thá»i nháº¯c ráº±ng SMTP credential cáº§n Ä‘Æ°á»£c quáº£n lĂ½ riĂªng vĂ  khĂ´ng Ä‘Æ°a thĂ´ng tin nháº¡y cáº£m vĂ o bĂ¡o cĂ¡o.*

Vá»›i SES, pháº§n cleanup táº­p trung vĂ o identity vĂ  credential:

1. Náº¿u khĂ´ng cĂ²n dĂ¹ng chá»©c nÄƒng gá»­i email/OTP, cĂ³ thá»ƒ xĂ³a email identity trong Amazon SES.
2. VĂ o IAM Ä‘á»ƒ tĂ¬m SMTP user/credential Ä‘Ă£ táº¡o cho SES.
3. XĂ³a access key hoáº·c IAM user náº¿u khĂ´ng cĂ²n sá»­ dá»¥ng.
4. Kiá»ƒm tra láº¡i biáº¿n mĂ´i trÆ°á»ng trĂªn Elastic Beanstalk hoáº·c file `.env` local, khĂ´ng Ä‘á»ƒ `MAIL_USER`, `MAIL_PASSWORD` hoáº·c SMTP secret bá»‹ commit lĂªn GitHub.
5. KhĂ´ng chá»¥p hoáº·c Ä‘Æ°a SMTP password vĂ o bĂ¡o cĂ¡o.

## BÆ°á»›c 7: XĂ³a security group vĂ  tĂ i nguyĂªn phá»¥ thuá»™c

Sau khi Elastic Beanstalk vĂ  RDS Ä‘Ă£ Ä‘Æ°á»£c xĂ³a, kiá»ƒm tra láº¡i cĂ¡c security group khĂ´ng cĂ²n sá»­ dá»¥ng.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **EC2** console.
2. VĂ o **Security Groups**.
3. TĂ¬m cĂ¡c security group liĂªn quan Ä‘áº¿n Elastic Beanstalk backend vĂ  RDS.
4. Chá»‰ xĂ³a security group khi khĂ´ng cĂ²n resource nĂ o phá»¥ thuá»™c.
5. Náº¿u AWS bĂ¡o lá»—i dependency, kiá»ƒm tra láº¡i EC2 instance, load balancer, RDS hoáº·c network interface.

KhĂ´ng nĂªn xĂ³a default security group hoáº·c security group khĂ´ng thuá»™c workshop.

## BÆ°á»›c 8: Kiá»ƒm tra CloudWatch vĂ  Billing

Sau khi dá»n cĂ¡c tĂ i nguyĂªn chĂ­nh, cáº§n kiá»ƒm tra láº¡i log vĂ  chi phĂ­.

CĂ¡c bÆ°á»›c thá»±c hiá»‡n:

1. Má»Ÿ **CloudWatch** console.
2. Kiá»ƒm tra log groups liĂªn quan Ä‘áº¿n Elastic Beanstalk hoáº·c backend.
3. XĂ³a log group khĂ´ng cĂ²n cáº§n sá»­ dá»¥ng hoáº·c giáº£m retention náº¿u muá»‘n giá»¯ log.
4. Má»Ÿ **Billing and Cost Management**.
5. Kiá»ƒm tra Cost Explorer hoáº·c Bills Ä‘á»ƒ xĂ¡c nháº­n khĂ´ng cĂ²n tĂ i nguyĂªn phĂ¡t sinh chi phĂ­ báº¥t thÆ°á»ng.

CĂ¡c tĂ i nguyĂªn cáº§n chĂº Ă½ nháº¥t vá» chi phĂ­ gá»“m RDS database, EC2/Elastic Beanstalk, Load Balancer, NAT Gateway, Elastic IP vĂ  CloudWatch Logs.

![Billing check](/HUGO/images/5-Workshop/5.7-Cleanup/5.7.6-billing-check.png)

*HĂ¬nh 5.7.6. Billing and Cost Management Ä‘Æ°á»£c dĂ¹ng Ä‘á»ƒ theo dĂµi chi phĂ­ sau quĂ¡ trĂ¬nh triá»ƒn khai AWS. MĂ n hĂ¬nh Cost summary vĂ  Cost breakdown giĂºp kiá»ƒm tra cĂ¡c khoáº£n phĂ¡t sinh theo dá»‹ch vá»¥ nhÆ° RDS, EC2, VPC vĂ  Amplify.*

Sau khi cleanup cĂ¡c tĂ i nguyĂªn chĂ­nh, cáº§n kiá»ƒm tra chi phĂ­:

1. Má»Ÿ **Billing and Cost Management**.
2. Kiá»ƒm tra **Cost summary** Ä‘á»ƒ xem chi phĂ­ thĂ¡ng hiá»‡n táº¡i vĂ  dá»± bĂ¡o cuá»‘i thĂ¡ng.
3. Xem **Cost breakdown** theo service Ä‘á»ƒ phĂ¡t hiá»‡n dá»‹ch vá»¥ nĂ o váº«n cĂ²n phĂ¡t sinh chi phĂ­.
4. CĂ¡c service cáº§n chĂº Ă½ gá»“m Amazon RDS, EC2, Elastic Load Balancing, VPC, API Gateway, Amplify vĂ  CloudWatch.
5. Náº¿u váº«n tháº¥y chi phĂ­ tÄƒng báº¥t thÆ°á»ng sau khi cleanup, quay láº¡i tá»«ng service Ä‘á»ƒ kiá»ƒm tra tĂ i nguyĂªn cĂ²n sĂ³t.

## Checklist dá»n dáº¹p cuá»‘i cĂ¹ng

- [ ] ÄĂ£ ghi láº¡i danh sĂ¡ch tĂ i nguyĂªn Ä‘Æ°á»£c táº¡o trong workshop.
- [ ] ÄĂ£ chá»¥p áº£nh Amplify app/branch trÆ°á»›c khi xĂ³a hoáº·c disconnect.
- [ ] ÄĂ£ xĂ³a API Gateway khĂ´ng cĂ²n sá»­ dá»¥ng.
- [ ] ÄĂ£ terminate Elastic Beanstalk environment.
- [ ] ÄĂ£ xĂ³a hoáº·c táº¡m dá»«ng RDS database theo nhu cáº§u demo.
- [ ] ÄĂ£ kiá»ƒm tra SES identity vĂ  SMTP credential.
- [ ] ÄĂ£ xĂ³a security group khĂ´ng cĂ²n dependency.
- [ ] ÄĂ£ kiá»ƒm tra CloudWatch log groups.
- [ ] ÄĂ£ kiá»ƒm tra Billing/Cost Explorer sau cleanup.


