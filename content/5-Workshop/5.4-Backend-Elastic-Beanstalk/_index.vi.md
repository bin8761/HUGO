---
title: "Triá»ƒn khai backend báº±ng Elastic Beanstalk"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

## Triá»ƒn khai backend báº±ng Elastic Beanstalk

BÆ°á»›c nĂ y Ä‘Ă³ng gĂ³i backend Node.js/Express vĂ  deploy lĂªn AWS Elastic Beanstalk. Backend sáº½ nháº­n request tá»« API Gateway vĂ  káº¿t ná»‘i Ä‘áº¿n Amazon RDS for MySQL.

## BÆ°á»›c 1: Kiá»ƒm tra backend local

Tá»« thÆ° má»¥c backend, cĂ i dependency vĂ  kiá»ƒm tra backend cĂ³ thá»ƒ start:

```bash
cd backend
npm ci
npm start
```

Entry point cá»§a backend:

```text
src/app/server.js
```

á»¨ng dá»¥ng cáº§n Ä‘á»c port tá»« biáº¿n mĂ´i trÆ°á»ng `PORT`. Khi deploy lĂªn Elastic Beanstalk, dĂ¹ng:

```env
PORT=8080
```

## BÆ°á»›c 2: Táº¡o backend source bundle

Táº¡o file ZIP tá»« ná»™i dung bĂªn trong thÆ° má»¥c `backend/`. Root cá»§a file ZIP pháº£i chá»©a trá»±c tiáº¿p `package.json`.

Cáº¥u trĂºc ZIP Ä‘Ăºng:

```text
backend-eb-source.zip
  package.json
  package-lock.json
  src/
  prisma/
```

Cáº¥u trĂºc ZIP sai:

```text
backend-eb-source.zip
  backend/
    package.json
```

KhĂ´ng Ä‘Æ°a `.env`, `node_modules` hoáº·c secret tháº­t vĂ o file ZIP.

![Backend source bundle Ä‘Ăºng cáº¥u trĂºc Ä‘á»ƒ deploy lĂªn Elastic Beanstalk](/HUGO/images/5-Workshop/5.4-Backend-Elastic-Beanstalk/5.4.1-source-bundle.png)

*HĂ¬nh 5.4.1. Backend source bundle Ä‘Ăºng cáº¥u trĂºc Ä‘á»ƒ deploy lĂªn Elastic Beanstalk.*

File ZIP cáº§n cĂ³ `package.json`, `package-lock.json`, `src/` vĂ  `prisma/` náº±m trá»±c tiáº¿p á»Ÿ root. Náº¿u ZIP chá»©a thĂªm thÆ° má»¥c `backend/` bĂªn ngoĂ i, Elastic Beanstalk cĂ³ thá»ƒ khĂ´ng start Ä‘Æ°á»£c á»©ng dá»¥ng.

## BÆ°á»›c 3: Táº¡o Elastic Beanstalk application

Má»Ÿ Elastic Beanstalk console:

1. Chá»n **Create application**.
2. Application name: `eam-backend`.
3. Platform: **Node.js**.
4. Application code: upload file ZIP cá»§a backend.
5. Environment name: vĂ­ dá»¥ `eam-backend-prod`.
6. Chá»n VPC vĂ  subnet phĂ¹ há»£p.
7. Gáº¯n backend security group.
8. Táº¡o environment vĂ  chá» quĂ¡ trĂ¬nh provision hoĂ n táº¥t.

Náº¿u environment cÅ© bá»‹ káº¹t á»Ÿ tráº¡ng thĂ¡i `Severe`, `No Data`, `CREATE_FAILED` hoáº·c `DELETE_FAILED`, cĂ³ thá»ƒ táº¡o environment má»›i vĂ  trá» vá» cĂ¹ng RDS Ä‘á»ƒ giáº£m thá»i gian xá»­ lĂ½.

![Trang táº¡o Elastic Beanstalk environment cho backend](/HUGO/images/5-Workshop/5.4-Backend-Elastic-Beanstalk/5.4.2-create-eb-environment.png)

*HĂ¬nh 5.4.2. Trang táº¡o Elastic Beanstalk environment cho backend.*

Pháº§n táº¡o environment cáº§n thá»ƒ hiá»‡n Ä‘Ăºng application name, environment name, platform Node.js vĂ  file source bundle Ä‘Ă£ upload. ÄĂ¢y lĂ  cáº¥u hĂ¬nh ná»n táº£ng Ä‘á»ƒ backend cháº¡y trĂªn Elastic Beanstalk.

## BÆ°á»›c 4: Cáº¥u hĂ¬nh environment properties

Trong Elastic Beanstalk environment properties, Ä‘áº·t:

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

`FRONTEND_ORIGIN` vĂ  `FRONTEND_ORIGINS` cĂ³ thá»ƒ cáº­p nháº­t sau khi Amplify táº¡o URL frontend.

![Environment properties cá»§a Elastic Beanstalk](/HUGO/images/5-Workshop/5.4-Backend-Elastic-Beanstalk/5.4.4-eb-env-properties.png)

*HĂ¬nh 5.4.4. Environment properties cá»§a Elastic Beanstalk sau khi che thĂ´ng tin nháº¡y cáº£m.*

CĂ¡c biáº¿n quan trá»ng cáº§n Ä‘Æ°á»£c kiá»ƒm tra gá»“m `DATABASE_URL`, `JWT_SECRET`, `MAIL_HOST`, `MAIL_USER`, `MAIL_PASSWORD`, `FRONTEND_ORIGIN` vĂ  `PORT=8080`. Khi Ä‘Æ°a vĂ o bĂ¡o cĂ¡o, cĂ¡c secret pháº£i Ä‘Æ°á»£c che Ä‘á»ƒ trĂ¡nh lá»™ thĂ´ng tin nháº¡y cáº£m.

## BÆ°á»›c 5: Deploy vĂ  kiá»ƒm tra health

Sau khi deploy, kiá»ƒm tra endpoint trá»±c tiáº¿p cá»§a backend:

```text
http://<elastic-beanstalk-domain>/api/health
```

Káº¿t quáº£ mong Ä‘á»£i:

```json
{
  "success": true,
  "message": "OK",
  "data": {
    "status": "ok"
  }
}
```

![Elastic Beanstalk environment á»Ÿ tráº¡ng thĂ¡i OK](/HUGO/images/5-Workshop/5.4-Backend-Elastic-Beanstalk/5.4.3-eb-health-ok.png)

*HĂ¬nh 5.4.3. Elastic Beanstalk environment á»Ÿ tráº¡ng thĂ¡i OK.*

MĂ n hĂ¬nh nĂ y cáº§n hiá»ƒn thá»‹ environment health á»Ÿ tráº¡ng thĂ¡i OK. ÄĂ¢y lĂ  dáº¥u hiá»‡u Elastic Beanstalk Ä‘Ă£ provision tĂ i nguyĂªn vĂ  backend khĂ´ng gáº·p lá»—i startup nghiĂªm trá»ng.

![Health endpoint cá»§a backend trĂªn Elastic Beanstalk](/HUGO/images/5-Workshop/5.4-Backend-Elastic-Beanstalk/5.4.5-eb-health-endpoint.png)

*HĂ¬nh 5.4.5. Health endpoint cá»§a backend trĂªn Elastic Beanstalk tráº£ káº¿t quáº£ thĂ nh cĂ´ng.*

Káº¿t quáº£ `/api/health` cáº§n tráº£ `success: true` vĂ  `status: ok`. Náº¿u endpoint nĂ y hoáº¡t Ä‘á»™ng, cĂ³ thá»ƒ tiáº¿p tá»¥c Ä‘Æ°a backend ra ngoĂ i thĂ´ng qua API Gateway.

Náº¿u health check lá»—i, kiá»ƒm tra:

- Backend cĂ³ listen Ä‘Ăºng `PORT=8080`.
- `DATABASE_URL` Ä‘Ăºng.
- Backend security group cĂ³ thá»ƒ káº¿t ná»‘i RDS port `3306`.
- `JWT_SECRET` Ä‘á»§ dĂ i vĂ  khĂ´ng rá»—ng.
- Biáº¿n mĂ´i trÆ°á»ng mail/OTP/rate limit Ä‘Ă£ Ä‘Æ°á»£c cáº¥u hĂ¬nh.
- Elastic Beanstalk logs khĂ´ng cĂ³ startup error.

## BÆ°á»›c 6: Cháº¡y Prisma migration vĂ  seed

Sau khi backend cĂ³ thá»ƒ káº¿t ná»‘i RDS, cháº¡y migration tá»« mĂ´i trÆ°á»ng cĂ³ quyá»n truy cáº­p database. TrÆ°á»›c khi cháº¡y lá»‡nh, cáº§n kiá»ƒm tra file `.env` hoáº·c biáº¿n mĂ´i trÆ°á»ng local Ä‘ang trá» Ä‘áº¿n Ä‘Ăºng RDS endpoint, khĂ´ng pháº£i `localhost:3306`.

```bash
cd backend
npx prisma generate
npx prisma migrate deploy
```

Náº¿u mĂ¡y local khĂ´ng truy cáº­p Ä‘Æ°á»£c RDS do security group, network hoáº·c VPN, khĂ´ng nĂªn cháº¡y migration trá»±c tiáº¿p tá»« local. Khi Ä‘Ă³ cáº§n cháº¡y lá»‡nh tá»« má»™t mĂ´i trÆ°á»ng cĂ³ quyá»n truy cáº­p database, vĂ­ dá»¥ EC2/bastion trong cĂ¹ng VPC, mĂ´i trÆ°á»ng CI/CD Ä‘Ă£ Ä‘Æ°á»£c cáº¥p quyá»n, hoáº·c táº¡m thá»i cáº¥u hĂ¬nh network phĂ¹ há»£p cho quĂ¡ trĂ¬nh migration.

Vá»›i database demo, cĂ³ thá»ƒ seed dá»¯ liá»‡u máº«u sau khi migration cháº¡y thĂ nh cĂ´ng:

```bash
npx prisma db seed
```

Náº¿u lá»‡nh Prisma bĂ¡o lá»—i khĂ´ng káº¿t ná»‘i Ä‘Æ°á»£c `localhost:3306`, nguyĂªn nhĂ¢n thÆ°á»ng lĂ  `DATABASE_URL` váº«n Ä‘ang dĂ¹ng cáº¥u hĂ¬nh local. Cáº§n cáº­p nháº­t láº¡i `DATABASE_URL` theo dáº¡ng:

```env
DATABASE_URL=mysql://asset_app:<password>@<rds-endpoint>:3306/enterprise_asset_management
```

## Káº¿t quáº£ cá»§a bÆ°á»›c nĂ y

Ghi láº¡i cĂ¡c giĂ¡ trá»‹:

- TĂªn Elastic Beanstalk application.
- TĂªn Elastic Beanstalk environment.
- Backend endpoint/domain.
- Backend security group.
- RDS endpoint.
- Káº¿t quáº£ health check `/api/health`.


