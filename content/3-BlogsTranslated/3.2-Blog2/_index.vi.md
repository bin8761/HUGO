---
title: "Blog 2"
date: 2026-06-25
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---
# Amazon EKS Auto Mode vĂ  Istio Ambient Mesh

**Nguá»“n:** [AWS Containers Blog - Better Together: Amazon EKS Auto Mode and Istio Ambient Mesh](https://aws.amazon.com/blogs/containers/better-together-amazon-eks-auto-mode-and-istio-ambient-mesh/)

## Amazon EKS Auto Mode vĂ  Istio Ambient Mesh

BĂ i blog giá»›i thiá»‡u cĂ¡ch káº¿t há»£p Amazon EKS Auto Mode vá»›i Istio Ambient Mesh nháº±m giáº£m gĂ¡nh náº·ng váº­n hĂ nh Kubernetes vĂ  service mesh trong mĂ´i trÆ°á»ng cloud-native. EKS Auto Mode há»— trá»£ tá»± Ä‘á»™ng hĂ³a nhiá»u thĂ nh pháº§n váº­n hĂ nh cá»§a cluster, trong khi Istio Ambient Mesh cung cáº¥p kháº£ nÄƒng báº£o máº­t, quan sĂ¡t vĂ  kiá»ƒm soĂ¡t lÆ°u lÆ°á»£ng mĂ  khĂ´ng cáº§n triá»ƒn khai sidecar proxy cho tá»«ng pod.

Äiá»ƒm ná»•i báº­t cá»§a bĂ i viáº¿t lĂ  mĂ´ hĂ¬nh nĂ y cho phĂ©p doanh nghiá»‡p triá»ƒn khai service mesh theo hÆ°á»›ng nháº¹ hÆ¡n, dá»… má»Ÿ rá»™ng hÆ¡n vĂ  phĂ¹ há»£p vá»›i cĂ¡c há»‡ thá»‘ng microservices trĂªn Amazon EKS. Thay vĂ¬ pháº£i quáº£n lĂ½ nhiá»u node, sidecar vĂ  cáº¥u hĂ¬nh phá»©c táº¡p, Ä‘á»™i ngÅ© váº­n hĂ nh cĂ³ thá»ƒ táº­n dá»¥ng EKS Auto Mode káº¿t há»£p ambient mode Ä‘á»ƒ táº­p trung vĂ o á»©ng dá»¥ng vĂ  chĂ­nh sĂ¡ch báº£o máº­t.

## CĂ¡c Ä‘iá»ƒm chĂ­nh cáº§n náº¯m

- EKS Auto Mode tá»± Ä‘á»™ng hĂ³a nhiá»u cĂ´ng viá»‡c váº­n hĂ nh cluster nhÆ° node provisioning, autoscaling, patching vĂ  quáº£n lĂ½ háº¡ táº§ng, giĂºp giáº£m operational overhead cho Ä‘á»™i ngÅ© DevOps.
- CĂ¡c node trong EKS Auto Mode cháº¡y trĂªn EC2 managed instances, sá»­ dá»¥ng há»‡ Ä‘iá»u hĂ nh container-optimized vĂ  Ä‘Æ°á»£c AWS quáº£n lĂ½ nhiá»u pháº§n ná»n táº£ng, giĂºp viá»‡c váº­n hĂ nh cluster á»•n Ä‘á»‹nh vĂ  Ä‘Æ¡n giáº£n hÆ¡n.
- Istio Ambient Mesh lĂ  mĂ´ hĂ¬nh service mesh khĂ´ng sá»­ dá»¥ng sidecar truyá»n thá»‘ng. Thay vĂ¬ gáº¯n proxy vĂ o tá»«ng pod, ambient mesh dĂ¹ng thĂ nh pháº§n ztunnel cháº¡y á»Ÿ cáº¥p node Ä‘á»ƒ xá»­ lĂ½ báº£o máº­t vĂ  lÆ°u lÆ°á»£ng Layer 4.
- Khi cáº§n cĂ¡c tĂ­nh nÄƒng á»Ÿ Layer 7 nhÆ° HTTP routing, retries, timeouts, circuit breaking hoáº·c authorization policy chi tiáº¿t hÆ¡n, há»‡ thá»‘ng cĂ³ thá»ƒ triá»ƒn khai thĂªm waypoint proxy cho service hoáº·c namespace cá»¥ thá»ƒ.
- ztunnel táº¡o secure overlay giá»¯a cĂ¡c workload thĂ´ng qua HBONE, giĂºp lÆ°u lÆ°á»£ng service-to-service Ä‘Æ°á»£c báº£o vá»‡ báº±ng mTLS mĂ  khĂ´ng cáº§n sá»­a Ä‘á»•i mĂ£ nguá»“n á»©ng dá»¥ng.
- Viá»‡c báº­t Ambient Mesh cĂ³ thá»ƒ thá»±c hiá»‡n báº±ng cĂ¡ch gáº¯n nhĂ£n `istio.io/dataplane-mode=ambient` cho namespace, tá»« Ä‘Ă³ cĂ¡c workload trong namespace sáº½ tá»± Ä‘á»™ng tham gia vĂ o mesh.
- MĂ´ hĂ¬nh nĂ y giĂºp giáº£m operational overhead vĂ¬ khĂ´ng cáº§n quáº£n lĂ½ sidecar cho tá»«ng pod, Ä‘á»“ng thá»i váº«n giá»¯ Ä‘Æ°á»£c cĂ¡c lá»£i Ă­ch quan trá»ng cá»§a service mesh nhÆ° encryption, observability vĂ  traffic policy.
- BĂ i blog cÅ©ng minh há»a cĂ¡ch sá»­ dá»¥ng Kiali vĂ  Prometheus Ä‘á»ƒ quan sĂ¡t traffic graph, xĂ¡c minh mTLS thĂ´ng qua ztunnel vĂ  kiá»ƒm tra luá»“ng giao tiáº¿p giá»¯a cĂ¡c service trong á»©ng dá»¥ng máº«u.
- Trong pháº§n thá»±c hĂ nh, bĂ i viáº¿t hÆ°á»›ng dáº«n táº¡o EKS Auto Mode cluster, cĂ i Ä‘áº·t Istio Ambient Mesh, triá»ƒn khai á»©ng dá»¥ng máº«u retail store, báº­t ambient mode, kiá»ƒm tra mTLS vĂ  Ă¡p dá»¥ng AuthorizationPolicy á»Ÿ cáº£ Layer 4 vĂ  Layer 7.
- Äá»‘i vá»›i mĂ´i trÆ°á»ng production, cáº§n lÆ°u Ă½ chi phĂ­ tĂ i nguyĂªn AWS, quyá»n IAM phĂ¹ há»£p, báº£o máº­t ingress gateway, chĂ­nh sĂ¡ch phĂ¢n quyá»n giá»¯a cĂ¡c service vĂ  quy trĂ¬nh cleanup tĂ i nguyĂªn sau khi thá»­ nghiá»‡m.

## HĂ¬nh áº£nh

DÆ°á»›i Ä‘Ă¢y lĂ  hai hĂ¬nh minh há»a kiáº¿n trĂºc gá»‘c tá»« bĂ i AWS Blog, thá»ƒ hiá»‡n cĂ¡ch Istio Ambient Mesh hoáº¡t Ä‘á»™ng trĂªn Amazon EKS Auto Mode á»Ÿ hai má»©c Layer 4 vĂ  Layer 7.

![Kiáº¿n trĂºc Istio Ambient Mesh Layer 4 trĂªn Amazon EKS Auto Mode](/HUGO/images/3-BlogsPosted/3.1-Blog1/c-170-1.jpg)

*HĂ¬nh 1. Kiáº¿n trĂºc Istio Ambient Mesh vá»›i cĂ¡c tĂ­nh nÄƒng Layer 4 trĂªn Amazon EKS Auto Mode. Nguá»“n: AWS Blog, Figure 1.*

![Kiáº¿n trĂºc Istio Ambient Mesh Layer 7 vá»›i waypoint proxy](/HUGO/images/3-BlogsPosted/3.1-Blog1/c-170-2.jpg)

*HĂ¬nh 2. Kiáº¿n trĂºc Istio Ambient Mesh vá»›i waypoint proxy cho cĂ¡c tĂ­nh nÄƒng Layer 7. Nguá»“n: AWS Blog, Figure 2.*

## HÆ°á»›ng dáº«n

CĂ³ thá»ƒ tĂ¡i hiá»‡n ná»™i dung bĂ i blog theo cĂ¡c bÆ°á»›c tá»•ng quĂ¡t sau:

- Chuáº©n bá»‹ mĂ´i trÆ°á»ng: cĂ i Ä‘áº·t AWS CLI, `kubectl`, Helm, Terraform vĂ  `envsubst`. TĂ i khoáº£n AWS cáº§n cĂ³ quyá»n táº¡o EKS, EC2, IAM, VPC vĂ  cĂ¡c tĂ i nguyĂªn liĂªn quan.
- Clone repository máº«u cá»§a AWS vĂ  chuyá»ƒn vĂ o thÆ° má»¥c Terraform dĂ¹ng cho ambient mode.
- Cháº¡y `terraform init`, `terraform plan` vĂ  `terraform apply --auto-approve` Ä‘á»ƒ táº¡o EKS Auto Mode cluster, node pool, Istio control plane vĂ  cĂ¡c thĂ nh pháº§n cáº§n thiáº¿t.
- Cáº¥u hĂ¬nh `kubectl` báº±ng lá»‡nh `aws eks update-kubeconfig`, sau Ä‘Ă³ kiá»ƒm tra cĂ¡c pod trong namespace `istio-system` Ä‘á»ƒ báº£o Ä‘áº£m Istio Ä‘Ă£ hoáº¡t Ä‘á»™ng.
- CĂ i Ä‘áº·t Prometheus vĂ  Kiali Ä‘á»ƒ quan sĂ¡t traffic trong mesh, sau Ä‘Ă³ port-forward Kiali vá» mĂ¡y local Ä‘á»ƒ theo dĂµi service graph.
- Triá»ƒn khai á»©ng dá»¥ng retail store máº«u báº±ng Helm, bao gá»“m cĂ¡c service nhÆ° cart, catalog, checkout, orders vĂ  ui.
- CĂ i Gateway API CRDs náº¿u cluster chÆ°a cĂ³ sáºµn, sau Ä‘Ă³ táº¡o Gateway vĂ  HTTPRoute Ä‘á»ƒ cho phĂ©p truy cáº­p á»©ng dá»¥ng tá»« bĂªn ngoĂ i.
- Báº­t ambient mode cho namespace `default` báº±ng cĂ¡ch gáº¯n nhĂ£n `istio.io/dataplane-mode=ambient`, sau Ä‘Ă³ táº£i láº¡i workload Ä‘á»ƒ cĂ¡c pod tham gia mesh.
- Ăp PeerAuthentication á»Ÿ cháº¿ Ä‘á»™ `STRICT` Ä‘á»ƒ báº¯t buá»™c mTLS trong mesh vĂ  kiá»ƒm tra request tá»« pod ngoĂ i mesh Ä‘á»ƒ xĂ¡c minh chĂ­nh sĂ¡ch báº£o máº­t.
- Táº¡o AuthorizationPolicy á»Ÿ Layer 4 Ä‘á»ƒ giá»›i háº¡n service nĂ o Ä‘Æ°á»£c phĂ©p gá»i service catalog.
- Triá»ƒn khai waypoint proxy cho service catalog náº¿u cáº§n kiá»ƒm soĂ¡t Layer 7, sau Ä‘Ă³ dĂ¹ng `targetRefs` trong AuthorizationPolicy Ä‘á»ƒ giá»›i háº¡n truy cáº­p theo HTTP method hoáº·c path.
- Sau khi thá»±c hĂ nh xong, cáº§n cleanup cĂ¡c tĂ i nguyĂªn AWS Ä‘á»ƒ trĂ¡nh phĂ¡t sinh chi phĂ­ khĂ´ng cáº§n thiáº¿t.

## Má»™t sá»‘ lá»‡nh tham kháº£o

```bash
git clone https://github.com/aws-samples/sample-istio-ambient-eks-automode.git
cd sample-istio-ambient-eks-automode/terraform-blueprint/ambient

terraform init
terraform plan
terraform apply --auto-approve

aws eks --region us-west-2 update-kubeconfig --name ambient
kubectl get pods -A
kubectl label namespace default istio.io/dataplane-mode=ambient
kubectl port-forward svc/kiali 20001:20001 -n istio-system
```

## Káº¿t luáº­n

BĂ i blog cho tháº¥y EKS Auto Mode vĂ  Istio Ambient Mesh lĂ  hai cĂ´ng nghá»‡ bá»• trá»£ tá»‘t cho nhau trong quĂ¡ trĂ¬nh triá»ƒn khai Kubernetes hiá»‡n Ä‘áº¡i trĂªn AWS. EKS Auto Mode giĂºp Ä‘Æ¡n giáº£n hĂ³a váº­n hĂ nh háº¡ táº§ng, cĂ²n Istio Ambient Mesh cung cáº¥p kháº£ nÄƒng báº£o máº­t vĂ  kiá»ƒm soĂ¡t lÆ°u lÆ°á»£ng theo hÆ°á»›ng nháº¹ hÆ¡n so vá»›i mĂ´ hĂ¬nh sidecar truyá»n thá»‘ng. ÄĂ¢y lĂ  má»™t hÆ°á»›ng tiáº¿p cáº­n phĂ¹ há»£p cho cĂ¡c há»‡ thá»‘ng microservices cáº§n tĂ­nh báº£o máº­t, kháº£ nÄƒng quan sĂ¡t vĂ  kháº£ nÄƒng má»Ÿ rá»™ng cao trong mĂ´i trÆ°á»ng cloud-native.

