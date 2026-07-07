---
title: "Káº¿t ná»‘i API Gateway vĂ  Amplify Hosting"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

## Káº¿t ná»‘i API Gateway vĂ  Amplify Hosting

BÆ°á»›c nĂ y táº¡o Amazon API Gateway HTTP API cho backend, sau Ä‘Ă³ deploy frontend React lĂªn AWS Amplify Hosting vĂ  cáº¥u hĂ¬nh rewrite `/api/*`.

## BÆ°á»›c 1: Táº¡o API Gateway HTTP API

Má»Ÿ Amazon API Gateway console:

1. Chá»n **Create API**.
2. Chá»n **HTTP API**.
3. Äáº·t tĂªn, vĂ­ dá»¥ `eam-backend-api`.
4. Táº¡o integration trá» Ä‘áº¿n backend Elastic Beanstalk endpoint.
5. Táº¡o route proxy Ä‘á»ƒ nháº­n request Ä‘Æ°á»£c Amplify chuyá»ƒn Ä‘áº¿n:

```text
ANY /{proxy+}
```

Route nĂ y cho phĂ©p API Gateway nháº­n cĂ¡c path nhÆ° `/api/health`, `/api/auth/login`, `/uploads/...` vĂ  chuyá»ƒn tiáº¿p nguyĂªn path Ä‘áº¿n backend.

6. Táº¡o stage, vĂ­ dá»¥ `$default` hoáº·c `prod`.
7. Deploy API.

Endpoint API Gateway sáº½ cĂ³ dáº¡ng:

```text
https://<api-id>.execute-api.<region>.amazonaws.com
```

![Tá»•ng quan HTTP API trong Amazon API Gateway](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.1-api-gateway-overview.png)

*HĂ¬nh 5.5.1. Tá»•ng quan HTTP API trong Amazon API Gateway.*

API cáº§n Ä‘Æ°á»£c táº¡o Ä‘Ăºng tĂªn vĂ  cĂ³ endpoint public. Endpoint nĂ y sáº½ Ä‘Æ°á»£c dĂ¹ng trong Amplify rewrite Ä‘á»ƒ chuyá»ƒn tiáº¿p cĂ¡c request `/api/*` vĂ  `/uploads/*`.

![Route proxy cá»§a API Gateway](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.2-api-gateway-route.png)

*HĂ¬nh 5.5.2. Route `ANY /{proxy+}` cá»§a API Gateway.*

Táº¡i pháº§n Routes, cáº§n Ä‘áº£m báº£o route `ANY /{proxy+}` Ä‘Ă£ Ä‘Æ°á»£c táº¡o. Route nĂ y giĂºp API Gateway nháº­n má»i path cáº§n chuyá»ƒn Ä‘áº¿n backend, bao gá»“m `/api/health`, `/api/assets` vĂ  `/uploads/...`.

![Integration cá»§a API Gateway trá» Ä‘áº¿n Elastic Beanstalk](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.3-api-gateway-integration.png)

*HĂ¬nh 5.5.3. Integration cá»§a API Gateway trá» Ä‘áº¿n Elastic Beanstalk backend.*

Táº¡i pháº§n Integration, cáº§n kiá»ƒm tra URI Ä‘ang trá» Ä‘áº¿n domain Elastic Beanstalk vĂ  cĂ³ giá»¯ biáº¿n `{proxy}`. Náº¿u integration khĂ´ng giá»¯ path, backend cĂ³ thá»ƒ nháº­n sai endpoint vĂ  tráº£ lá»—i `404`.

## BÆ°á»›c 2: Kiá»ƒm tra API Gateway

Má»Ÿ health endpoint qua API Gateway:

```text
https://<api-gateway-endpoint>/api/health
```

Náº¿u tráº£ 404, kiá»ƒm tra láº¡i:

- Route `ANY /{proxy+}`.
- Integration target Ä‘áº¿n Ä‘Ăºng backend Elastic Beanstalk endpoint.
- Stage Ä‘Ă£ deploy.
- Parameter mapping hoáº·c path forwarding khĂ´ng lĂ m máº¥t prefix `/api`.
- Backend pháº£i nháº­n Ä‘Ăºng Ä‘Æ°á»ng dáº«n gá»‘c nhÆ° `/api/health`, `/api/auth/login` hoáº·c `/api/assets`.
- Integration URI cĂ³ thá»ƒ dĂ¹ng `http://<elastic-beanstalk-domain>/{proxy}` khi route cĂ³ biáº¿n `{proxy+}`.

![Health endpoint qua API Gateway](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.4-api-gateway-health.png)

*HĂ¬nh 5.5.4. Health endpoint qua API Gateway tráº£ káº¿t quáº£ thĂ nh cĂ´ng.*

Khi gá»i `/api/health` qua API Gateway, response cáº§n tráº£ `success: true` vĂ  `status: ok`. Káº¿t quáº£ nĂ y xĂ¡c nháº­n route, integration vĂ  stage cá»§a API Gateway hoáº¡t Ä‘á»™ng Ä‘Ăºng.

## BÆ°á»›c 3: Kiá»ƒm tra frontend build local

Tá»« thÆ° má»¥c frontend:

```bash
cd frontend
npm ci
npm run build
```

Output build production:

```text
dist/
```

## BÆ°á»›c 4: Kiá»ƒm tra Amplify build settings

Repository cĂ³ thá»ƒ dĂ¹ng file `amplify.yml` cho cáº¥u trĂºc monorepo:

```yaml
version: 1
applications:
  - appRoot: frontend
    frontend:
      phases:
        preBuild:
          commands:
            - npm ci
        build:
          commands:
            - npm run build
      artifacts:
        baseDirectory: dist
        files:
          - '**/*'
```

![Build settings cá»§a Amplify](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.6-amplify-build-settings.png)

*HĂ¬nh 5.5.6. Build settings cá»§a Amplify vá»›i app root vĂ  output directory.*

Build settings cáº§n khá»›p vá»›i cáº¥u trĂºc project: `appRoot` lĂ  `frontend`, build command lĂ  `npm ci && npm run build` vĂ  output directory lĂ  `dist`.

## BÆ°á»›c 5: Táº¡o Amplify app

Má»Ÿ AWS Amplify console:

1. Chá»n **New app** hoáº·c **Host web app**.
2. Káº¿t ná»‘i GitHub repository.
3. Chá»n branch triá»ƒn khai, vĂ­ dá»¥ `aws-architecture`.
4. Äáº·t monorepo root lĂ  `frontend` náº¿u Amplify yĂªu cáº§u.
5. Kiá»ƒm tra build command:

```bash
npm ci && npm run build
```

6. Kiá»ƒm tra output directory:

```text
dist
```

![Amplify app káº¿t ná»‘i branch aws-architecture](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.5-amplify-branch.png)

*HĂ¬nh 5.5.5. Amplify app káº¿t ná»‘i Ä‘Ăºng branch triá»ƒn khai.*

Branch deploy pháº£i lĂ  branch chá»©a source frontend má»›i nháº¥t. Sau khi káº¿t ná»‘i, Amplify sáº½ tá»± Ä‘á»™ng build vĂ  publish frontend theo cáº¥u hĂ¬nh Ä‘Ă£ chá»n.

![Amplify deployment thĂ nh cĂ´ng](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.8-amplify-build-success.png)

*HĂ¬nh 5.5.8. Amplify deployment thĂ nh cĂ´ng.*

Khi deployment á»Ÿ tráº¡ng thĂ¡i `Deployed`, frontend Ä‘Ă£ Ä‘Æ°á»£c build vĂ  xuáº¥t báº£n thĂ nh cĂ´ng trĂªn Amplify domain. ÄĂ¢y lĂ  Ä‘iá»u kiá»‡n trÆ°á»›c khi kiá»ƒm thá»­ giao diá»‡n vĂ  rewrite API.

## BÆ°á»›c 6: Äáº·t biáº¿n mĂ´i trÆ°á»ng frontend

Trong Amplify, Ä‘áº·t:

```env
VITE_API_BASE_URL=/api
```

Biáº¿n nĂ y giĂºp browser gá»i API qua cĂ¹ng Amplify domain:

```text
https://<amplify-domain>/api/...
```

## BÆ°á»›c 7: Cáº¥u hĂ¬nh Amplify rewrite

Sau khi app Ä‘Æ°á»£c táº¡o, má»Ÿ **Rewrites and redirects**.

ThĂªm rule nĂ y á»Ÿ phĂ­a trĂªn SPA fallback rule:

| Source address | Target address | Type |
| --- | --- | --- |
| `/api/<*>` | `https://<api-gateway-endpoint>/api/<*>` | `200 (Rewrite)` |
| `/uploads/<*>` | `https://<api-gateway-endpoint>/uploads/<*>` | `200 (Rewrite)` |

Sau Ä‘Ă³ giá»¯ SPA fallback rule cho React Router:

| Source address | Target address | Type |
| --- | --- | --- |
| `/<*>` | `/index.html` | `404 (Rewrite)` hoáº·c `404-200` |

Náº¿u rule `/api/<*>` hoáº·c `/uploads/<*>` Ä‘áº·t sai thá»© tá»±, request API hoáº·c áº£nh upload cĂ³ thá»ƒ bá»‹ tráº£ vá» HTML cá»§a frontend, gĂ¢y lá»—i `404`, lá»—i áº£nh khĂ´ng hiá»ƒn thá»‹ hoáº·c static assets bá»‹ lá»—i MIME type.

![Rewrite rules cá»§a Amplify](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.7-amplify-rewrite-rules.png)

*HĂ¬nh 5.5.7. Rewrite rules cá»§a Amplify chuyá»ƒn tiáº¿p `/api/<*>` vĂ  `/uploads/<*>` Ä‘áº¿n API Gateway.*

Hai rule `/api/<*>` vĂ  `/uploads/<*>` pháº£i náº±m phĂ­a trĂªn rule fallback `/index.html`. Thá»© tá»± nĂ y Ä‘áº£m báº£o request API vĂ  file upload Ä‘i Ä‘áº¿n API Gateway thay vĂ¬ bá»‹ React Router xá»­ lĂ½ nhÆ° route frontend.

## BÆ°á»›c 8: Cáº­p nháº­t backend CORS origin

Sau khi Amplify deploy xong, copy URL máº·c Ä‘á»‹nh cá»§a Amplify:

```text
https://main.xxxxx.amplifyapp.com
```

Náº¿u deploy tá»« branch khĂ¡c, hĂ£y dĂ¹ng Ä‘Ăºng domain cá»§a branch Ä‘Ă³, vĂ­ dá»¥:

```text
https://aws-architecture.xxxxx.amplifyapp.com
```

Cáº­p nháº­t biáº¿n mĂ´i trÆ°á»ng backend:

```env
FRONTEND_ORIGIN=https://main.xxxxx.amplifyapp.com
FRONTEND_ORIGINS=https://main.xxxxx.amplifyapp.com
```

Redeploy hoáº·c restart Elastic Beanstalk environment sau khi cáº­p nháº­t giĂ¡ trá»‹ nĂ y.

## Káº¿t quáº£ cá»§a bÆ°á»›c nĂ y

Ghi láº¡i:

- API Gateway endpoint.
- Amplify app URL.
- GiĂ¡ trá»‹ `FRONTEND_ORIGIN`.
- Tráº¡ng thĂ¡i frontend build.
- Káº¿t quáº£ test `https://<amplify-domain>/api/health`.

![Health endpoint qua Amplify domain](/HUGO/images/5-Workshop/5.5-Frontend-Amplify/5.5.9-amplify-health.png)

*HĂ¬nh 5.5.9. Health endpoint qua Amplify domain tráº£ káº¿t quáº£ thĂ nh cĂ´ng.*

Táº¡i bÆ°á»›c kiá»ƒm thá»­ cuá»‘i, gá»i `https://<amplify-domain>/api/health`. Request sáº½ Ä‘i qua Amplify rewrite, API Gateway vĂ  Elastic Beanstalk trÆ°á»›c khi tráº£ vá» response thĂ nh cĂ´ng.


