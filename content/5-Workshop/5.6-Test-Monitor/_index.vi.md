---
title: "Kiá»ƒm thá»­, monitoring vĂ  xá»­ lĂ½ lá»—i"
date: 2024-01-01
weight: 6
chapter: false
pre: " <b> 5.6. </b> "
---

## Kiá»ƒm thá»­, monitoring vĂ  xá»­ lĂ½ lá»—i

Sau khi frontend, API Gateway vĂ  backend Ä‘Ă£ deploy, cáº§n kiá»ƒm thá»­ toĂ n bá»™ há»‡ thá»‘ng vĂ  kiá»ƒm tra log váº­n hĂ nh.

## Test 1: Backend health

Kiá»ƒm tra theo tá»«ng lá»›p:

```text
http://<elastic-beanstalk-domain>/api/health
https://<api-gateway-endpoint>/api/health
https://<amplify-domain>/api/health
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

Náº¿u lá»—i, kiá»ƒm tra theo thá»© tá»±: Elastic Beanstalk logs, API Gateway route/integration/stage, rá»“i Amplify rewrite rule.

## Test 2: Admin login

Má»Ÿ URL Amplify vĂ  Ä‘Äƒng nháº­p báº±ng tĂ i khoáº£n admin tá»« seed data.

![Trang Ä‘Äƒng nháº­p trĂªn Amplify domain](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.1-login-page.png)

*HĂ¬nh 5.6.1. Trang Ä‘Äƒng nháº­p trĂªn Amplify domain.*

á»¨ng dá»¥ng frontend cáº§n má»Ÿ Ä‘Æ°á»£c tá»« domain Amplify vĂ  form Ä‘Äƒng nháº­p pháº£i hiá»ƒn thá»‹ Ä‘áº§y Ä‘á»§. ÄĂ¢y lĂ  Ä‘iá»ƒm báº¯t Ä‘áº§u Ä‘á»ƒ kiá»ƒm thá»­ luá»“ng ngÆ°á»i dĂ¹ng.

Káº¿t quáº£ mong Ä‘á»£i:

- User Ä‘Æ°á»£c redirect Ä‘áº¿n `/admin/dashboard`.
- Dashboard metrics hiá»ƒn thá»‹.
- Sidebar vĂ  navigation hoáº¡t Ä‘á»™ng.
- API call tráº£ `200` hoáº·c response nghiá»‡p vá»¥ mong Ä‘á»£i.

![Admin dashboard sau khi Ä‘Äƒng nháº­p thĂ nh cĂ´ng](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.2-admin-dashboard.png)

*HĂ¬nh 5.6.2. Admin dashboard sau khi Ä‘Äƒng nháº­p thĂ nh cĂ´ng.*

Sau khi Ä‘Äƒng nháº­p admin, dashboard cáº§n hiá»ƒn thá»‹ dá»¯ liá»‡u tá»•ng quan. Äiá»u nĂ y xĂ¡c nháº­n authentication, API backend vĂ  database Ä‘ang hoáº¡t Ä‘á»™ng cĂ¹ng nhau.

## Test 3: Workflow admin chĂ­nh

Kiá»ƒm thá»­ Ă­t nháº¥t má»™t workflow tá»« má»—i module admin lá»›n:

| Module | HĂ nh Ä‘á»™ng kiá»ƒm thá»­ |
| --- | --- |
| Categories | Táº¡o hoáº·c tĂ¬m kiáº¿m danh má»¥c tĂ i sáº£n. |
| Assets | Táº¡o, cáº­p nháº­t hoáº·c tĂ¬m kiáº¿m tĂ i sáº£n. |
| Employees | Xem danh sĂ¡ch nhĂ¢n viĂªn vĂ  chi tiáº¿t nhĂ¢n viĂªn. |
| Departments | Xem hoáº·c cáº­p nháº­t thĂ´ng tin phĂ²ng ban. |
| Assignments | BĂ n giao tĂ i sáº£n kháº£ dá»¥ng cho nhĂ¢n viĂªn. |
| Maintenance | Táº¡o hoáº·c cáº­p nháº­t yĂªu cáº§u há»— trá»£/báº£o trĂ¬. |
| Inventory | Xem hoáº·c táº¡o phiĂªn kiá»ƒm kĂª. |
| Reports | Má»Ÿ bĂ¡o cĂ¡o tá»•ng quan hoáº·c bĂ¡o cĂ¡o tĂ i sáº£n. |

![MĂ n hĂ¬nh quáº£n lĂ½ tĂ i sáº£n](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.3-admin-assets.png)

*HĂ¬nh 5.6.3. MĂ n hĂ¬nh quáº£n lĂ½ tĂ i sáº£n.*

Danh sĂ¡ch tĂ i sáº£n cáº§n hiá»ƒn thá»‹ Ä‘Ăºng, Ä‘á»“ng thá»i cĂ¡c thao tĂ¡c chĂ­nh nhÆ° xem, sá»­a, xĂ³a hoáº·c nháº­p Excel pháº£i xuáº¥t hiá»‡n theo Ä‘Ăºng quyá»n admin.

![Workflow quáº£n lĂ½ bĂ n giao tĂ i sáº£n](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.4-assignment-maintenance.png)

*HĂ¬nh 5.6.4. Workflow quáº£n lĂ½ bĂ n giao tĂ i sáº£n.*

á» workflow bĂ n giao, cáº§n kiá»ƒm tra tráº¡ng thĂ¡i tĂ i sáº£n, nhĂ¢n viĂªn nháº­n tĂ i sáº£n vĂ  lá»‹ch sá»­ bĂ n giao. ÄĂ¢y lĂ  luá»“ng nghiá»‡p vá»¥ quan trá»ng cá»§a há»‡ thá»‘ng EAM Workspace.

## Test 4: Workflow nhĂ¢n viĂªn

ÄÄƒng nháº­p báº±ng tĂ i khoáº£n nhĂ¢n viĂªn vĂ  kiá»ƒm tra:

- Employee dashboard.
- Trang tĂ i sáº£n Ä‘Æ°á»£c bĂ n giao.
- Trang chi tiáº¿t tĂ i sáº£n.
- Táº¡o yĂªu cáº§u há»— trá»£.
- Trang FAQ.
- Trang há»“ sÆ¡ vĂ  lá»‹ch sá»­.

![Employee dashboard](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.5-employee-dashboard.png)

*HĂ¬nh 5.6.5. Employee dashboard sau khi Ä‘Äƒng nháº­p.*

Táº¡i dashboard nhĂ¢n viĂªn, cáº§n kiá»ƒm tra dá»¯ liá»‡u hiá»ƒn thá»‹ theo Ä‘Ăºng quyá»n cá»§a tĂ i khoáº£n nhĂ¢n viĂªn. NgÆ°á»i dĂ¹ng chá»‰ nĂªn tháº¥y tĂ i sáº£n, yĂªu cáº§u há»— trá»£ vĂ  thĂ´ng tin cĂ¡ nhĂ¢n liĂªn quan Ä‘áº¿n mĂ¬nh.

## Test 5: Upload vĂ  tráº¡ng thĂ¡i tĂ i khoáº£n

Kiá»ƒm tra thĂªm cĂ¡c case Ä‘Ă£ gáº·p trong quĂ¡ trĂ¬nh deploy:

- Upload áº£nh/avatar Ä‘i qua backend/API vĂ  áº£nh tráº£ `200`.
- TĂ i khoáº£n inactive khĂ´ng thá»ƒ Ä‘Äƒng nháº­p.
- Response lá»—i inactive tráº£ Ä‘Ăºng mĂ£ nghiá»‡p vá»¥, vĂ­ dá»¥ `AUTH_ACCOUNT_INACTIVE`.
- Browser DevTools khĂ´ng cĂ³ lá»—i CORS.

![DevTools Network hiá»ƒn thá»‹ API request thĂ nh cĂ´ng](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.6-devtools-network.png)

*HĂ¬nh 5.6.6. DevTools Network hiá»ƒn thá»‹ cĂ¡c API request thĂ nh cĂ´ng.*

Táº¡i tab Network, cáº§n lá»c cĂ¡c request `/api/...` vĂ  kiá»ƒm tra status tráº£ vá» `200` hoáº·c mĂ£ nghiá»‡p vá»¥ mong Ä‘á»£i. Náº¿u xuáº¥t hiá»‡n lá»—i CORS hoáº·c request tráº£ HTML, cáº§n kiá»ƒm tra láº¡i Amplify rewrite vĂ  backend CORS.

![TĂ i khoáº£n inactive bá»‹ cháº·n Ä‘Äƒng nháº­p](/HUGO/images/5-Workshop/5.6-Test-Monitor/5.6.7-inactive-account.png)

*HĂ¬nh 5.6.7. TĂ i khoáº£n inactive bá»‹ cháº·n Ä‘Äƒng nháº­p.*

Khi Ä‘Äƒng nháº­p báº±ng tĂ i khoáº£n inactive, há»‡ thá»‘ng cáº§n tá»« chá»‘i truy cáº­p. Káº¿t quáº£ nĂ y xĂ¡c nháº­n backend cĂ³ kiá»ƒm tra tráº¡ng thĂ¡i tĂ i khoáº£n trÆ°á»›c khi cáº¥p quyá»n vĂ o há»‡ thá»‘ng.

## Monitoring vá»›i CloudWatch

Má»Ÿ CloudWatch Logs vĂ  kiá»ƒm tra log group cá»§a Elastic Beanstalk.

Cáº§n kiá»ƒm tra:

- Log startup backend.
- Request log.
- Lá»—i authentication.
- Lá»—i káº¿t ná»‘i database.
- Exception chÆ°a Ä‘Æ°á»£c xá»­ lĂ½.

CĂ¡c endpoint há»¯u Ă­ch:

```text
GET /api/health
POST /api/auth/login
GET /api/assets
GET /api/reports/summary
```

## Alarm Ä‘á» xuáº¥t

Vá»›i mĂ´i trÆ°á»ng demo, cĂ³ thá»ƒ táº¡o cĂ¡c CloudWatch alarm Ä‘Æ¡n giáº£n:

| Alarm | Má»¥c Ä‘Ă­ch |
| --- | --- |
| EC2 high CPU | PhĂ¡t hiá»‡n backend instance quĂ¡ táº£i. |
| Elastic Beanstalk health degraded | PhĂ¡t hiá»‡n environment khĂ´ng á»•n Ä‘á»‹nh. |
| RDS CPU hoáº·c storage | PhĂ¡t hiá»‡n váº¥n Ä‘á» capacity cá»§a database. |
| 5xx errors | PhĂ¡t hiá»‡n lá»—i application hoáº·c infrastructure. |

## HÆ°á»›ng dáº«n xá»­ lĂ½ lá»—i

| Váº¥n Ä‘á» | NguyĂªn nhĂ¢n thÆ°á»ng gáº·p | CĂ¡ch xá»­ lĂ½ |
| --- | --- | --- |
| `502` hoáº·c backend khĂ´ng pháº£n há»“i | Backend crash hoáº·c sai port | Kiá»ƒm tra `PORT=8080`, EB logs vĂ  health endpoint trá»±c tiáº¿p. |
| API Gateway tráº£ `404` | Route, stage, integration hoáº·c path forwarding sai | Kiá»ƒm tra route proxy, endpoint integration, stage Ä‘Ă£ deploy vĂ  Ä‘áº£m báº£o backend nháº­n Ä‘Ăºng path `/api/...`. |
| CORS error | `FRONTEND_ORIGIN` hoáº·c `FRONTEND_ORIGINS` sai | Set Ä‘Ăºng URL Amplify vĂ  redeploy backend. |
| KhĂ´ng káº¿t ná»‘i Ä‘Æ°á»£c database | RDS endpoint hoáº·c security group sai | Kiá»ƒm tra `DATABASE_URL` vĂ  cho phĂ©p `3306` tá»« backend SG. |
| `/api/...` tráº£ frontend HTML | Thá»© tá»± Amplify rewrite sai | ÄÆ°a `/api/<*>` lĂªn trĂªn SPA fallback rule. |
| áº¢nh/avatar upload tráº£ `404` | Amplify chÆ°a rewrite `/uploads/<*>` hoáº·c backend chÆ°a phá»¥c vá»¥ Ä‘Ăºng thÆ° má»¥c upload | ThĂªm `/uploads/<*>` rewrite Ä‘áº¿n API Gateway, Ä‘áº·t trĂªn SPA fallback vĂ  kiá»ƒm tra URL áº£nh trá»±c tiáº¿p. |
| Static JS/CSS lá»—i MIME type | Rewrite rule báº¯t nháº§m static assets | Chá»‰ rewrite `/api/<*>` vĂ  `/uploads/<*>` Ä‘áº¿n API Gateway, Ä‘á»ƒ SPA fallback xá»­ lĂ½ route frontend. |
| Login fail | Seed data hoáº·c JWT config cĂ³ váº¥n Ä‘á» | Kiá»ƒm tra seed data, `JWT_SECRET` vĂ  backend logs. |
| Upload khĂ´ng bá»n vá»¯ng | Äang dĂ¹ng local instance storage | Chuyá»ƒn nÆ¡i lÆ°u file upload sang S3 cho hÆ°á»›ng triá»ƒn khai sáºµn sĂ ng production. |

## Checklist xĂ¡c nháº­n

- [ ] Frontend má»Ÿ Ä‘Æ°á»£c tá»« Amplify URL.
- [ ] `GET /api/health` tráº£ success qua Elastic Beanstalk.
- [ ] `GET /api/health` tráº£ success qua API Gateway.
- [ ] `GET /api/health` tráº£ success qua Amplify rewrite.
- [ ] Admin login hoáº¡t Ä‘á»™ng.
- [ ] Employee login hoáº¡t Ä‘á»™ng.
- [ ] Workflow CRUD chĂ­nh hoáº¡t Ä‘á»™ng.
- [ ] Workflow bĂ n giao tĂ i sáº£n hoáº¡t Ä‘á»™ng.
- [ ] Workflow yĂªu cáº§u há»— trá»£ hoáº¡t Ä‘á»™ng.
- [ ] TĂ i khoáº£n inactive bá»‹ cháº·n Ä‘Äƒng nháº­p.
- [ ] KhĂ´ng cĂ³ lá»—i CORS trong browser DevTools.


