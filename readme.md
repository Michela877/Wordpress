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

ma prima bisognera configurare il service con il load balancer o senno l'ingress successivamente avviare l'installazione con quest'ordine di creazione usando kustomize qui sotto il comando:

```bash
kubectl apply -k "path assoluto in locale"
```

## 3️⃣ credenziali per accedere

Bisognera cambiare la password tramite pod mysql 
```bash
kubectl exec -it mysql-deployment-6f49d8d57d-srgzq -n monitoring -- bash
```
Entrare nel mysql 
```bash
mysql -u root -prootpassword
```
```bash
use wordpress;
```
```bash
UPDATE wp_users 
SET user_pass = MD5('nuovapassword') 
WHERE user_login = 'user';
```
le credenziali base per accedere sono al wp-admin 

id user
password nuovapassword

una volta eseguito l'accesso e cambiato la password si avra tutto il sito wordpress configurato


