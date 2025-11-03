Questa guida descrive i passaggi per configurare l’ambiente `Wordpress` su Kubernetes.

---

## 1️⃣ Creazione dell'ingress controller

utilizzare questo comando

```bash
helm install ingress-nginx ingress-nginx/ingress-nginx   --namespace ingress-nginx --create-namespace   --set controller.service.loadBalancerIP=<IL_TUO_IP_STATICO>
```


## 1️⃣ Creazione del namespace

Creare il namespace dedicato alle applicazioni:

```bash
kubectl create ns wordpress
```

---

## 2️⃣ Creazione dei singoli con kustomize

ma prima bisognera configurare il service con il load balancer o senno l'ingress successivamente avviare l'installazione con quest'ordine di creazione usando kustomize "GRAFANA-METRICS-PROMETHEUS-LOKI-PROMTAIL-TEMPO" qui sotto il comando:

```bash
kubectl apply -k "path assoluto in locale"
```

## 3️⃣ credenziali per accedere

le credenziali base per accedere sono 

id user

la password da cambiare internalmente al pod mysql

una volta eseguito l'accesso e cambiato la password si avra tutto lo stack grafana configurato


