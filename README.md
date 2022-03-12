# Readme

[![DigitalOcean Referral Badge](https://web-platforms.sfo2.digitaloceanspaces.com/WWW/Badge%202.svg)](https://www.digitalocean.com/?refcode=b69d53aaa3a0&utm_campaign=Referral_Invite&utm_medium=Referral_Program&utm_source=badge)

docker-compose up

## Cloudflare

```bash
cloudflared tunnel login
kubectl create secret generic tunnel-credentials \
--from-file=credentials.json=/home/levi/.cloudflared/uuid-from-above.json

kubectl logs $(kubectl get pod -l app=cloudflared -o jsonpath="{.items[0].metadata.name}")
```

https://developers.cloudflare.com/cloudflare-one/tutorials/many-cfd-one-tunnel/

## DigitalOcean

```bash
doctl kubernetes cluster create --region=nyc3 --node-pool=my_pool;size=s-1vcpu-2gb;auto-scale=true
doctl kubernetes cluster kubeconfig save uuid-from-above
```

## Docker

### nginx

pg-nginx (playground-nginx).

```bash
docker build -t levidurfee/pg-nginx -f ./docker/nginx/Dockerfile .
docker push levidurfee/pg-nginx
```

### app

pg-app (playground-app).

```bash
docker build -t levidurfee/pg-app -f ./docker/app/Dockerfile .
docker push levidurfee/pg-app
```

## Kubernetes

```bash
kubectl rollout restart deployment/app
kubectl rollout restart deployment/nginx

kubectl rollout restart deployment/{app,nginx,cloudflared}
```

## Kube State Metrics

```bash
git clone --depth=1 https://github.com/kubernetes/kube-state-metrics.git ./kubernetes/ksm
kubectl create -f ./kubernetes/ksm/examples/standard/
```

## Links

* https://docs.digitalocean.com/products/kubernetes/how-to/monitor-advanced/
