---
title: "Blog 1"
date: 2026-06-25
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Amazon EKS now supports control plane egress through your VPC

**Nguá»“n:** [Amazon EKS now supports control plane egress through your VPC](https://aws.amazon.com/blogs/containers/amazon-eks-now-supports-control-plane-egress-through-your-vpc/)

Amazon EKS Ä‘Ă£ bá»• sung kháº£ nÄƒng customer-routed control plane egress, cho phĂ©p Ä‘á»‹nh tuyáº¿n má»™t sá»‘ lÆ°u lÆ°á»£ng outbound tá»« Kubernetes API Server Ä‘i qua chĂ­nh Amazon VPC cá»§a ngÆ°á»i dĂ¹ng. TĂ­nh nÄƒng nĂ y giĂºp doanh nghiá»‡p kiá»ƒm soĂ¡t tá»‘t hÆ¡n Ä‘Æ°á»ng Ä‘i cá»§a cĂ¡c request do control plane khá»Ÿi táº¡o, cháº³ng háº¡n nhÆ° admission webhook callback, truy váº¥n OIDC provider vĂ  aggregate API server request.

Thay vĂ¬ Ä‘á»ƒ cĂ¡c luá»“ng nĂ y Ä‘i theo Ä‘Æ°á»ng máº¡ng do EKS quáº£n lĂ½, ngÆ°á»i dĂ¹ng cĂ³ thá»ƒ Ă¡p dá»¥ng cĂ¡c cÆ¡ cháº¿ kiá»ƒm soĂ¡t quen thuá»™c trong VPC nhÆ° route table, security group, VPC endpoint, AWS PrivateLink, NAT Gateway hoáº·c AWS Network Firewall. ÄĂ¢y lĂ  cáº£i tiáº¿n quan trá»ng Ä‘á»‘i vá»›i cĂ¡c há»‡ thá»‘ng Kubernetes yĂªu cáº§u báº£o máº­t cao, Ä‘áº·c biá»‡t trong mĂ´i trÆ°á»ng doanh nghiá»‡p, tĂ i chĂ­nh, y táº¿ hoáº·c cĂ¡c tá»• chá»©c cĂ³ yĂªu cáº§u tuĂ¢n thá»§ nghiĂªm ngáº·t.


## CĂ¡c Ä‘iá»ƒm chĂ­nh cáº§n náº¯m

- Customer-routed control plane egress cho phĂ©p cĂ¡c luá»“ng outbound "customer-controllable" tá»« Kubernetes API Server Ä‘i qua Elastic Network Interface (ENI) náº±m trong VPC cá»§a ngÆ°á»i dĂ¹ng.
- CĂ¡c loáº¡i lÆ°u lÆ°á»£ng Ä‘Æ°á»£c há»— trá»£ bao gá»“m admission webhook callback, truy váº¥n tĂ i liá»‡u khĂ¡m phĂ¡ OIDC, yĂªu cáº§u Ä‘áº¿n aggregate API server vĂ  DNS resolution phá»¥c vá»¥ cho cĂ¡c luá»“ng nĂ y.
- Khi báº­t tĂ­nh nÄƒng nĂ y, ngÆ°á»i dĂ¹ng cĂ³ thá»ƒ Ă¡p dá»¥ng route table, security group, endpoint policy, NAT Gateway, AWS PrivateLink, VPC endpoint, AWS Network Firewall vĂ  cĂ¡c quy táº¯c egress control sáºµn cĂ³ trong VPC.
- TĂ­nh nÄƒng Ä‘áº·c biá»‡t há»¯u Ă­ch cho cĂ¡c há»‡ thá»‘ng cáº§n private networking, private OIDC provider hoáº·c admission webhook chá»‰ cĂ³ thá»ƒ truy cáº­p bĂªn trong máº¡ng riĂªng.
- Control plane egress qua VPC khĂ¡c vá»›i EKS private endpoint: private endpoint kiá»ƒm soĂ¡t chiá»u inbound Ä‘áº¿n Kubernetes API Server, cĂ²n customer-routed egress kiá»ƒm soĂ¡t chiá»u outbound tá»« API Server ra cĂ¡c dá»‹ch vá»¥ liĂªn quan.
- NgÆ°á»i dĂ¹ng cĂ³ thá»ƒ báº­t khi táº¡o cluster má»›i hoáº·c cáº­p nháº­t cluster hiá»‡n cĂ³ báº±ng cĂ¡ch Ä‘áº·t `controlPlaneEgressMode = CUSTOMER_ROUTED` trong `resourcesVpcConfig`.
- Sau khi cluster chuyá»ƒn sang `CUSTOMER_ROUTED`, thiáº¿t láº­p nĂ y lĂ  cá»‘ Ä‘á»‹nh trong suá»‘t vĂ²ng Ä‘á»i cluster vĂ  khĂ´ng thá»ƒ chuyá»ƒn ngÆ°á»£c vá» `AWS_MANAGED`.
- CĂ³ thá»ƒ dĂ¹ng IAM condition key `eks:controlPlaneEgressMode` káº¿t há»£p vá»›i AWS Organizations Service Control Policies Ä‘á»ƒ báº¯t buá»™c cĂ¡c cluster trong tá»• chá»©c pháº£i sá»­ dá»¥ng cháº¿ Ä‘á»™ `CUSTOMER_ROUTED`.
- VPC Flow Logs cĂ³ thá»ƒ Ä‘Æ°á»£c sá»­ dá»¥ng Ä‘á»ƒ quan sĂ¡t vĂ  xĂ¡c minh cĂ¡c káº¿t ná»‘i tá»« EKS-managed cross-account ENI Ä‘áº¿n cĂ¡c endpoint ná»™i bá»™, há»— trá»£ kiá»ƒm toĂ¡n vĂ  tuĂ¢n thá»§.
- Má»™t sá»‘ luá»“ng khĂ´ng thuá»™c Kubernetes API Server, vĂ­ dá»¥ EKS Capabilities hoáº·c AWS STS call tá»« IAM Authenticator, váº«n tiáº¿p tá»¥c Ä‘i theo Ä‘Æ°á»ng EKS-managed vĂ  khĂ´ng Ä‘i qua VPC cá»§a ngÆ°á»i dĂ¹ng.

## HĂ¬nh áº£nh

HĂ¬nh minh há»a kiáº¿n trĂºc khi Private Control Plane Networking Ä‘Æ°á»£c báº­t. LÆ°u lÆ°á»£ng customer-controllable tá»« `kube-apiserver` Ä‘i qua ENI trong VPC cá»§a ngÆ°á»i dĂ¹ng, sau Ä‘Ă³ chá»‹u sá»± kiá»ƒm soĂ¡t bá»Ÿi cĂ¡c thĂ nh pháº§n máº¡ng nhÆ° VPC endpoint, NAT Gateway, Transit Gateway hoáº·c AWS PrivateLink trÆ°á»›c khi Ä‘i Ä‘áº¿n customer destinations.

![Control plane egress Ä‘i qua VPC cá»§a ngÆ°á»i dĂ¹ng khi báº­t Private Control Plane Networking](/HUGO/images/3-BlogsPosted/3.2-Blog2/CONTAINERS-269-1.png)

*HĂ¬nh 1. Control plane egress Ä‘i qua VPC cá»§a ngÆ°á»i dĂ¹ng khi báº­t Private Control Plane Networking. Nguá»“n: AWS Blog.*


## HÆ°á»›ng dáº«n

Äá»ƒ tĂ¬m hiá»ƒu vĂ  Ă¡p dá»¥ng tĂ­nh nÄƒng nĂ y, cĂ³ thá»ƒ thá»±c hiá»‡n theo cĂ¡c bÆ°á»›c chĂ­nh sau:

1. XĂ¡c Ä‘á»‹nh cluster EKS cáº§n sá»­ dá»¥ng private control plane networking vĂ  kiá»ƒm tra cĂ¡c subnet, security group, route table, DNS resolver trong VPC.
2. Khi táº¡o cluster má»›i, cáº¥u hĂ¬nh `resources-vpc-config` vĂ  thĂªm `controlPlaneEgressMode=CUSTOMER_ROUTED` Ä‘á»ƒ báº­t Ä‘á»‹nh tuyáº¿n egress qua VPC.
3. Vá»›i cluster hiá»‡n cĂ³, sá»­ dá»¥ng lá»‡nh `update-cluster-config` Ä‘á»ƒ chuyá»ƒn sang cháº¿ Ä‘á»™ `CUSTOMER_ROUTED`, Ä‘á»“ng thá»i lÆ°u Ă½ ráº±ng thiáº¿t láº­p nĂ y khĂ´ng thá»ƒ quay láº¡i `AWS_MANAGED`.
4. Äáº£m báº£o cĂ¡c endpoint mĂ  Kubernetes API Server cáº§n gá»i, cháº³ng háº¡n admission webhook, OIDC provider hoáº·c aggregate API server, cĂ³ thá»ƒ truy cáº­p Ä‘Æ°á»£c tá»« subnet cá»§a cluster thĂ´ng qua private DNS, internal load balancer, VPC endpoint hoáº·c PrivateLink.
5. Kiá»ƒm tra security group, route table vĂ  NAT/PrivateLink path Ä‘á»ƒ trĂ¡nh trÆ°á»ng há»£p API Server khĂ´ng gá»i Ä‘Æ°á»£c webhook hoáº·c OIDC endpoint.
6. Sá»­ dá»¥ng `aws eks describe-cluster` Ä‘á»ƒ xĂ¡c minh giĂ¡ trá»‹ `controlPlaneEgressMode` vĂ  báº­t VPC Flow Logs Ä‘á»ƒ theo dĂµi Ä‘Æ°á»ng Ä‘i cá»§a lÆ°u lÆ°á»£ng phá»¥c vá»¥ kiá»ƒm toĂ¡n.
7. Náº¿u quáº£n lĂ½ nhiá»u tĂ i khoáº£n AWS, cĂ³ thá»ƒ dĂ¹ng AWS Organizations SCP vá»›i condition key `eks:controlPlaneEgressMode` Ä‘á»ƒ yĂªu cáº§u cĂ¡c cluster pháº£i báº­t `CUSTOMER_ROUTED` theo chuáº©n báº£o máº­t cá»§a tá»• chá»©c.

### VĂ­ dá»¥ lá»‡nh AWS CLI tham kháº£o

```bash
# Táº¡o cluster má»›i vá»›i customer-routed control plane egress
aws eks create-cluster \
  --name my-cluster \
  --kubernetes-version 1.36 \
  --role-arn arn:aws:iam::111122223333:role/eks-cluster-role \
  --resources-vpc-config subnetIds=subnet-aaa,subnet-bbb,securityGroupIds=sg-xxx,controlPlaneEgressMode=CUSTOMER_ROUTED

# Báº­t trĂªn cluster hiá»‡n cĂ³
aws eks update-cluster-config \
  --name my-cluster \
  --resources-vpc-config controlPlaneEgressMode=CUSTOMER_ROUTED

# Kiá»ƒm tra cáº¥u hĂ¬nh
aws eks describe-cluster --name my-cluster \
  --query "cluster.resourcesVpcConfig.controlPlaneEgressMode"
```

## Káº¿t luáº­n 

TĂ­nh nÄƒng customer-routed control plane egress giĂºp Amazon EKS phĂ¹ há»£p hÆ¡n vá»›i cĂ¡c mĂ´i trÆ°á»ng yĂªu cáº§u kiá»ƒm soĂ¡t máº¡ng nghiĂªm ngáº·t. Thay vĂ¬ chá»‰ quáº£n lĂ½ lÆ°u lÆ°á»£ng cá»§a worker nodes vĂ  workloads, ngÆ°á»i dĂ¹ng cĂ³ thĂªm kháº£ nÄƒng kiá»ƒm soĂ¡t má»™t pháº§n lÆ°u lÆ°á»£ng outbound tá»« Kubernetes API Server. Äiá»u nĂ y giĂºp tÄƒng tĂ­nh riĂªng tÆ°, há»— trá»£ kiá»ƒm toĂ¡n, giáº£m rá»§i ro khi sá»­ dá»¥ng webhook hoáº·c OIDC provider ná»™i bá»™ vĂ  giĂºp triá»ƒn khai EKS trong cĂ¡c há»‡ thá»‘ng doanh nghiá»‡p cĂ³ yĂªu cáº§u báº£o máº­t cao.

