# `kubectl` - kubernetes control
```bash
kubectl get vpa -n qa-blue --template '{{range .items}}{{.metadata.name}}{{"\n"}}{{end}}' | while read VPA; do echo $VPA; kubectl describe vpa -n qa-blue $VPA | grep -A 12 "Container Name"; done
kubectl get vpa -n qa-blue -o jsonpath='{.metadata.name}{.status.recommendation}'
kubectl get vpa -n qa-blue -o custom-columns='NAME:metadata.name,CPU RECC:status.recommendation.containerRecommendations[*].target.cpu,MEM RECC:status.recommendation.containerRecommendations[*].target.memory'
kubectl get svc -n qa-blue -o jsonpath='{.metadata.annotations.service\.beta\.kubernetes\.io/aws-load-balancer-type}'
```