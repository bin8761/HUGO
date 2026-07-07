---
title: "Chuáº©n bá»‹"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---

## Chuáº©n bá»‹

TrÆ°á»›c khi triá»ƒn khai, cáº§n chuáº©n bá»‹ AWS account, cĂ´ng cá»¥ local, source code vĂ  cĂ¡c biáº¿n mĂ´i trÆ°á»ng cáº§n dĂ¹ng cho backend/frontend.

## AWS account

Sá»­ dá»¥ng má»™t AWS Region cá»‘ Ä‘á»‹nh cho toĂ n bá»™ tĂ i nguyĂªn trong workshop. IAM user hoáº·c role cáº§n cĂ³ quyá»n táº¡o vĂ  quáº£n lĂ½:

- AWS Amplify Hosting
- Amazon API Gateway
- Amazon EC2 vĂ  Security Groups
- AWS Elastic Beanstalk
- Amazon RDS
- Amazon S3
- Amazon SES
- AWS Secrets Manager
- AWS Systems Manager Parameter Store
- Amazon CloudWatch
- AWS CloudTrail

Sau khi chá»n Region, kiá»ƒm tra láº¡i gĂ³c pháº£i trĂªn cá»§a AWS Console Ä‘á»ƒ Ä‘áº£m báº£o toĂ n bá»™ thao tĂ¡c Ä‘Æ°á»£c thá»±c hiá»‡n trong cĂ¹ng má»™t Region.

![Region AWS Ä‘Æ°á»£c sá»­ dá»¥ng cho workshop](/HUGO/images/5-Workshop/5.2-Prerequisites/5.2.1-aws-region.png)

*HĂ¬nh 5.2.1. Region AWS Ä‘Æ°á»£c sá»­ dá»¥ng cho workshop.*

Region Ä‘ang chá»n pháº£i lĂ  Region Ä‘Æ°á»£c dĂ¹ng xuyĂªn suá»‘t workshop. Viá»‡c thá»‘ng nháº¥t Region giĂºp trĂ¡nh lá»—i káº¿t ná»‘i giá»¯a Elastic Beanstalk, API Gateway, RDS vĂ  SES.

## CĂ´ng cá»¥ local

CĂ i Ä‘áº·t vĂ  kiá»ƒm tra cĂ¡c cĂ´ng cá»¥ sau:

| CĂ´ng cá»¥ | Má»¥c Ä‘Ă­ch |
| --- | --- |
| Node.js 20+ | Cháº¡y backend vĂ  frontend local. |
| npm | CĂ i dependency vĂ  cháº¡y build script. |
| Git | Quáº£n lĂ½ source code vĂ  káº¿t ná»‘i GitHub. |
| MySQL client hoáº·c database tool | TĂ¹y chá»n, há»¯u Ă­ch khi kiá»ƒm tra database. |
| Postman hoáº·c browser DevTools | Kiá»ƒm thá»­ API endpoint. |

Kiá»ƒm tra Node.js vĂ  npm:

```bash
node -v
npm -v
```

Káº¿t quáº£ cáº§n hiá»ƒn thá»‹ phiĂªn báº£n Node.js vĂ  npm trĂªn mĂ¡y local.

![Kiá»ƒm tra Node.js vĂ  npm trĂªn mĂ¡y local](/HUGO/images/5-Workshop/5.2-Prerequisites/5.2.3-local-tools.png)

*HĂ¬nh 5.2.3. Kiá»ƒm tra Node.js vĂ  npm trĂªn mĂ¡y local.*

Náº¿u hai lá»‡nh trĂªn tráº£ vá» version há»£p lá»‡, mĂ´i trÆ°á»ng local Ä‘Ă£ sáºµn sĂ ng Ä‘á»ƒ cĂ i dependency, build frontend vĂ  kiá»ƒm tra backend trÆ°á»›c khi Ä‘Ă³ng gĂ³i triá»ƒn khai lĂªn AWS.

## Cáº¥u trĂºc source code

Project cĂ³ hai thÆ° má»¥c á»©ng dá»¥ng:

```text
quanlidoanhnghiep/
  backend/
  frontend/
```

Entry runtime cá»§a backend:

```text
backend/src/app/server.js
```

Output build cá»§a frontend:

```text
frontend/dist
```

## Kiá»ƒm tra branch triá»ƒn khai

TrÆ°á»›c khi káº¿t ná»‘i AWS Amplify, cáº§n xĂ¡c Ä‘á»‹nh branch GitHub Ä‘Æ°á»£c dĂ¹ng Ä‘á»ƒ triá»ƒn khai frontend.

![GitHub branch dĂ¹ng Ä‘á»ƒ triá»ƒn khai frontend báº±ng Amplify](/HUGO/images/5-Workshop/5.2-Prerequisites/5.2.2-github-branch.png)

*HĂ¬nh 5.2.2. GitHub branch dĂ¹ng Ä‘á»ƒ triá»ƒn khai frontend báº±ng Amplify.*

Cáº§n ghi láº¡i Ä‘Ăºng branch deploy, vĂ­ dá»¥ `aws-architecture`, vĂ¬ Amplify sáº½ láº¥y source code tá»« branch nĂ y Ä‘á»ƒ build vĂ  deploy frontend.

## Biáº¿n mĂ´i trÆ°á»ng backend

Chuáº©n bá»‹ cĂ¡c giĂ¡ trá»‹ sau trÆ°á»›c khi táº¡o hoáº·c cáº­p nháº­t Elastic Beanstalk environment:

```env
NODE_ENV=production
PORT=8080
DATABASE_URL=mysql://<db_user>:<db_password>@<rds-endpoint>:3306/enterprise_asset_management
JWT_SECRET=<long-random-secret>
JWT_EXPIRES_IN=1h
DEFAULT_USER_PASSWORD=<default-demo-password>
OTP_EXPIRES_SECONDS=60
OTP_MAX_ATTEMPTS=3
RATE_LIMIT_BUCKET_CAPACITY=60
RATE_LIMIT_REFILL_TOKENS_PER_SECOND=1
RATE_LIMIT_TOKENS_PER_REQUEST=1
MAIL_HOST=<smtp-host>
MAIL_PORT=<smtp-port>
MAIL_SECURE=false
MAIL_USER=<mail-user>
MAIL_PASSWORD=<mail-password>
MAIL_FROM=<mail-from-address>
FRONTEND_ORIGIN=https://<amplify-domain>
FRONTEND_ORIGINS=https://<amplify-domain>
```

## Chuáº©n bá»‹ SES/SMTP

Backend sá»­ dá»¥ng email Ä‘á»ƒ gá»­i OTP hoáº·c thĂ´ng bĂ¡o, vĂ¬ váº­y cáº§n chuáº©n bá»‹ thĂ´ng tin SMTP trÆ°á»›c khi cáº¥u hĂ¬nh Elastic Beanstalk. Trong mĂ´i trÆ°á»ng demo, cĂ³ thá»ƒ xĂ¡c thá»±c má»™t email identity thay vĂ¬ xĂ¡c thá»±c domain riĂªng.

CĂ¡c bÆ°á»›c chuáº©n bá»‹:

1. Má»Ÿ **Amazon SES** trong cĂ¹ng Region Ä‘ang dĂ¹ng cho workshop.
2. VĂ o **Verified identities** vĂ  táº¡o identity loáº¡i **Email address**.
3. Nháº­p email gá»­i, vĂ­ dá»¥ email cĂ¡ nhĂ¢n hoáº·c email dĂ¹ng cho demo.
4. Má»Ÿ há»™p thÆ° vĂ  báº¥m link xĂ¡c thá»±c do Amazon SES gá»­i Ä‘áº¿n.
5. Sau khi email á»Ÿ tráº¡ng thĂ¡i **Verified**, táº¡o **SMTP credentials** trong SES.
6. LÆ°u láº¡i SMTP username vĂ  SMTP password Ä‘á»ƒ Ä‘iá»n vĂ o Elastic Beanstalk.

CĂ¡c biáº¿n mĂ´i trÆ°á»ng tÆ°Æ¡ng á»©ng:

```env
MAIL_HOST=email-smtp.<region>.amazonaws.com
MAIL_PORT=587
MAIL_SECURE=false
MAIL_USER=<ses-smtp-username>
MAIL_PASSWORD=<ses-smtp-password>
MAIL_FROM=<verified-email-address>
```

Náº¿u SES váº«n á»Ÿ sandbox mode, email chá»‰ gá»­i Ä‘Æ°á»£c Ä‘áº¿n cĂ¡c Ä‘á»‹a chá»‰ Ä‘Ă£ verified. Vá»›i workshop demo, Ä‘iá»u nĂ y váº«n Ä‘á»§ Ä‘á»ƒ kiá»ƒm thá»­ OTP hoáº·c email thĂ´ng bĂ¡o.

## Biáº¿n mĂ´i trÆ°á»ng frontend

Khi deploy báº±ng Amplify, dĂ¹ng API path tÆ°Æ¡ng Ä‘á»‘i:

```env
VITE_API_BASE_URL=/api
```

CĂ¡ch nĂ y giĂºp browser gá»i cĂ¹ng origin cá»§a Amplify, cĂ²n Amplify sáº½ rewrite `/api/*` Ä‘áº¿n endpoint Amazon API Gateway.

## Checklist Ä‘Ă³ng gĂ³i backend

Khi Ä‘Ă³ng gĂ³i backend Ä‘á»ƒ deploy lĂªn Elastic Beanstalk, file ZIP nĂªn chá»©a cĂ¡c file vĂ  thÆ° má»¥c sau ngay á»Ÿ root cá»§a ZIP:

- `package.json`
- `package-lock.json`
- `src/`
- `prisma/`
- cĂ¡c file cáº¥u hĂ¬nh runtime cáº§n thiáº¿t cho backend

KhĂ´ng nĂªn Ä‘Æ°a vĂ o:

- `node_modules/`
- `.env`
- secret tháº­t
- file upload local khĂ´ng cáº§n thiáº¿t

## Checklist sáºµn sĂ ng

- [ ] ÄĂ£ chá»n AWS Region.
- [ ] AWS account cĂ³ quyá»n phĂ¹ há»£p.
- [ ] ÄĂ£ cĂ³ source code backend vĂ  frontend.
- [ ] ÄĂ£ chuáº©n bá»‹ biáº¿n mĂ´i trÆ°á»ng backend.
- [ ] ÄĂ£ chuáº©n bá»‹ `VITE_API_BASE_URL=/api` cho Amplify.
- [ ] ÄĂ£ xĂ¡c Ä‘á»‹nh endpoint RDS hoáº·c káº¿ hoáº¡ch táº¡o RDS.
- [ ] Thá»‘ng nháº¥t dĂ¹ng hÆ°á»›ng demo khĂ´ng cĂ³ Route 53 hoáº·c custom domain.


