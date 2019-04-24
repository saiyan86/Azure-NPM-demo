# Azure-NPM Demo for ONUG
This demo showcases how can k8s operators leverage Azure-NPM to secure their clusters and applications.

## Create namespaces
```
kubectl create ns firewall 
kubectl label ns/firewall purpose=firewall
kubectl create ns expressroute
kubectl label ns/expressroute purpose=expressroute
```

## Create nginx web server deployments in each namespace
```
kubectl run firewall --image=azurecontnw/firewall:onug -n firewall --replicas=3 --labels=app=firewall-content --expose --port 80
kubectl run expressroute --image=azurecontnw/expressroute:onug -n --replicas=3 --labels=app=expressroute-content --expose --port 80
```

## Apply network policy
```
kubectl apply -f https://raw.githubusercontent.com/saiyan86/Azure-NPM-demo/master/ONUG/policy.yaml
```
policy.yaml:
```
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: firewall-content-policy
  namespace: firewall
spec:
  podSelector:
    matchLabels:
      app: firewall-content
  policyTypes:
  - Ingress
  ingress:
  - from:
    - namespaceSelector:
        matchLabels:
          purpose: firewall
    - namespaceSelector:
        matchLabels:
          purpose: expressroute
      podSelector:
        matchLabels:
          status: exception
```
