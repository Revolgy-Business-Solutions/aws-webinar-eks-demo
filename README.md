# EKS demo

# guestbook
```
kubectl apply -f guestbook.yaml
kubectl apply -f redis.yaml
```
# kuard 
```
kubecl apply -f kuard.yaml
```
# helm
```
kubectl apply -f rbac.yaml
helm init --upgrade --service-account tiller
```
# heapster
```
helm install --namespace kube-system --name heapster stable/heapster
```
# ALB ingress
```
aws iam put-role-policy --role-name <EKS-CLUSTER-NAME-DefaultNodeGroup-NodeInstanceRole-ID>  --policy-name mab-test-alb-ingress-extra --policy-document file://iam-policy.json
kubectl apply -f albrbac.yaml
kubectl apply -f alb-ingress-controller.yaml
```

make sure to edit the `ingress.yaml`
and then:

```
kubectl apply -f ingress.yaml
```

