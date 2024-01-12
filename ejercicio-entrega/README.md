Estructura:

my-chart/
|-- Chart.yaml
|-- values.yaml
|-- templates/
|   |-- deployment.yaml
|   |-- service.yaml
|   |-- configmap.yaml
|-- charts/

juan@Portatil-Juan:~/HELM/ejercicio-entrega$ helm create microservice
juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice/charts$ helm create redis

Elimino en juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice/charts/redis/templates$ cat deployment.yaml:
image: "{{ .Values.image.repository }}:{{ .Values.image.tag | default .Chart.AppVersion }}"
imagePullPolicy: {{ .Values.image.pullPolicy }}

juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice$ helm lint .
==> Linting .
[INFO] Chart.yaml: icon is recommended

1 chart(s) linted, 0 chart(s) failed

 helm install my-release  . --dry-run --debug

# helm install my-release .

juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice$ helm install my-release014 .
NAME: my-release014
LAST DEPLOYED: Thu Jan 11 07:43:58 2024
NAMESPACE: default
STATUS: deployed
REVISION: 1

kubectl get pods
NAME                                   READY   STATUS             RESTARTS       AGE
my-release-app1-5689fc5954-7wfdn       1/1     Running            1 (112m ago)   10h
my-release-app1-5689fc5954-mgmwr       1/1     Running            1 (112m ago)   10h
my-release-app1-5689fc5954-mhv9n       1/1     Running            1 (112m ago)   10h
my-release002-redis-6547cd649f-8ds6l   1/1     Running            0              14m
my-release003-redis-6cc5c7f984-mlkxx   1/1     Running            0              9m10s
my-release004-redis-69f9898bb9-qt9ws   1/1     Running            0              8m31s
my-release005-redis-6fdd457b9d-cdnd8   1/1     Running            0              8m14s
my-release007-redis-55f454cdb8-5vzsb   1/1     Running            0              7m44s
my-release01-redis-dd49684b6-hnbnm     1/1     Running            0              59m
my-release011-redis-7f768f5f75-2zq58   1/1     Running            0              6m25s
my-release013-redis-65756bf9df-lg8f9   1/1     Running            0              66s
my-release014-redis-6fbf5868d-v6bwd    1/1     Running            0              37s
my-release02-redis-59575459c5-wc8dp    1/1     Running            0              54m
my-release07-redis-6b4687965b-grfj7    1/1     Running            0              50m
my-release1-redis-77b786578-ftrkp      1/1     Running            0              61m
my-release10-redis-567578cc4d-8ttd5    1/1     Running            0              47m
my-release14-redis-5d97c56fb4-hxlxg    1/1     Running            0              42m
my-release15-redis-749c75c5f-k9bhr     1/1     Running            0              42m
my-release16-redis-7cc95b4c7d-sqgcj    1/1     Running            0              41m
my-release17-redis-7c6d9696fc-2zbhb    1/1     Running            0              39m
my-release19-redis-7fdcdc5975-vq4vz    1/1     Running            0              34m
my-release2-app1-79bd6c4856-8jxgt      1/1     Running            1              9h
my-release2-app1-79bd6c4856-fwc5s      1/1     Running            1              9h
my-release2-app1-79bd6c4856-mdqfg      1/1     Running            1 (112m ago)   9h
my-release20-redis-bfb4944f9-f4zks     1/1     Running            0              32m
my-release21-redis-65d5447c64-d5s66    1/1     Running            0              31m
my-release22-redis-797df5f8d5-6phj9    1/1     Running            0              27m
my-release24-redis-5965b5854c-p5kcd    1/1     Running            0              24m
my-release25-redis-865457fcc6-fqtcd    0/1     InvalidImageName   0              23m
my-release26-redis-857f8656bf-f2wrc    0/1     InvalidImageName   0              22m
my-release27-redis-5c57f4bd66-674q6    1/1     Running            0              21m
my-release29-redis-c55d48556-m87bv     1/1     Running            1 (112m ago)   9h
my-release3-redis-ccdc64c89-n24s8      1/1     Running            1 (112m ago)   9h
my-release30-redis-cccf6b47d-f6snx     1/1     Running            1              9h
my-release31-redis-657f598f85-slt4k    1/1     Running            1 (112m ago)   8h
my-release4-redis-77865cf954-vsvnq     1/1     Running            1 (112m ago)   9h
my-release5-redis-5b6b8558f5-99px7     1/1     Running            1 (112m ago)   9h
my-release7-redis-6b85cdc54f-8hdhd     1/1     Running            1 (112m ago)   9h
my-release8-redis-56696bfc74-nrz5t     1/1     Running            1 (112m ago)   9h
my-release9-redis-d896f44c-xkt5x       1/1     Running            1 (112m ago)   9h
prueba1-redis-b8657677f-jfhs2          1/1     Running            0              88m
prueba10-redis-7dddf4fdb7-5r429        1/1     Running            0              76m
prueba11-redis-54bbd846dd-twzj5        1/1     Running            0              75m
prueba12-redis-67548fd76f-j5xxx        1/1     Running            0              72m
prueba13-redis-686f478558-ffcnp        1/1     Running            0              71m
prueba14-redis-69644f9dc-vx4g2         1/1     Running            0              69m
prueba2-redis-bcbdbc6cd-g2kbp          1/1     Running            0              87m
prueba4-redis-589bfb7484-5mvpm         1/1     Running            0              83m
prueba5-redis-86cf476b59-f9tp6         1/1     Running            0              83m
prueba6-redis-6d5f59bdbb-qbbrj         1/1     Running            0              81m
prueba7-redis-6c44b654d5-hpbz6         1/1     Running            0              78m
prueba8-redis-7897747bbd-ccllr         1/1     Running            0              77m
prueba9-redis-fc5595c7f-9nk54          1/1     Running            0              77m

juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice$ kubectl get svc
NAME                  TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
kubernetes            ClusterIP   10.96.0.1        <none>        443/TCP          6d18h
my-release-app1       NodePort    10.100.222.211   <none>        5000:30001/TCP   10h
my-release-redis      ClusterIP   10.105.113.133   <none>        80/TCP           10h
my-release002-redis   ClusterIP   10.96.47.240     <none>        80/TCP           15m
my-release003-redis   ClusterIP   10.102.45.191    <none>        80/TCP           10m
my-release004-app1    NodePort    10.97.210.107    <none>        5000:30018/TCP   9m27s
my-release004-redis   ClusterIP   10.103.106.103   <none>        80/TCP           9m27s
my-release005-redis   ClusterIP   10.110.3.91      <none>        80/TCP           9m12s
my-release007-app1    NodePort    10.106.181.206   <none>        5000:30071/TCP   8m40s
my-release007-redis   ClusterIP   10.107.142.9     <none>        80/TCP           8m40s
my-release01-app1     NodePort    10.101.173.109   <none>        5000:30077/TCP   60m
my-release01-redis    ClusterIP   10.108.183.20    <none>        80/TCP           60m
my-release011-redis   ClusterIP   10.103.54.2      <none>        80/TCP           7m22s
my-release013-redis   ClusterIP   10.108.50.211    <none>        80/TCP           2m2s
my-release014-app1    NodePort    10.106.34.30     <none>        5000:30012/TCP   93s
my-release014-redis   ClusterIP   10.96.4.28       <none>        80/TCP           93s
my-release02-redis    ClusterIP   10.106.105.111   <none>        80/TCP           55m
my-release07-redis    ClusterIP   10.97.77.220     <none>        80/TCP           51m
my-release1-redis     ClusterIP   10.107.154.70    <none>        80/TCP           62m
my-release10-redis    ClusterIP   10.97.118.29     <none>        80/TCP           48m
my-release14-redis    ClusterIP   10.104.254.57    <none>        80/TCP           43m
my-release15-redis    ClusterIP   10.96.37.90      <none>        80/TCP           42m
my-release16-redis    ClusterIP   10.99.176.20     <none>        80/TCP           42m
my-release17-redis    ClusterIP   10.97.163.229    <none>        80/TCP           40m
my-release19-redis    ClusterIP   10.100.130.117   <none>        80/TCP           35m
my-release2-redis     ClusterIP   10.102.252.246   <none>        80/TCP           9h
my-release20-redis    ClusterIP   10.110.71.147    <none>        80/TCP           33m
my-release21-redis    ClusterIP   10.108.68.236    <none>        80/TCP           32m
my-release22-redis    ClusterIP   10.101.92.3      <none>        80/TCP           28m
my-release24-redis    ClusterIP   10.96.194.114    <none>        80/TCP           25m
my-release25-redis    ClusterIP   10.96.84.151     <none>        80/TCP           24m
my-release26-redis    ClusterIP   10.101.34.164    <none>        80/TCP           23m
my-release27-app1     NodePort    10.108.253.148   <none>        5000:30022/TCP   22m
my-release27-redis    ClusterIP   10.107.243.73    <none>        80/TCP           22m
my-release29-app1     NodePort    10.109.150.28    <none>        5000:30080/TCP   9h
my-release3-app1      NodePort    10.108.183.240   <none>        5000:30002/TCP   9h
my-release3-redis     ClusterIP   10.109.24.141    <none>        80/TCP           9h
my-release31-app1     NodePort    10.105.163.136   <none>        5000:30081/TCP   9h
my-release4-redis     ClusterIP   10.108.52.223    <none>        80/TCP           9h
my-release5-app1      NodePort    10.109.66.217    <none>        5000:30003/TCP   9h
my-release5-redis     ClusterIP   10.107.243.246   <none>        80/TCP           9h
my-release7-redis     ClusterIP   10.96.182.175    <none>        80/TCP           9h
my-release8-redis     ClusterIP   10.110.230.30    <none>        80/TCP           9h
my-release9-app1      NodePort    10.101.20.51     <none>        5000:30004/TCP   9h
my-release9-redis     ClusterIP   10.109.253.230   <none>        80/TCP           9h
prueba10-app1         NodePort    10.97.142.170    <none>        5000:30100/TCP   77m
prueba10-redis        NodePort    10.108.113.36    <none>        1:30320/TCP      77m
prueba11-redis        NodePort    10.103.90.32     <none>        1:30713/TCP      76m
prueba12-redis        NodePort    10.96.54.73      <none>        1:32224/TCP      73m
prueba13-app1         NodePort    10.106.211.61    <none>        5000:30088/TCP   72m
prueba13-redis        NodePort    10.97.158.85     <none>        1:32658/TCP      72m
prueba14-redis        NodePort    10.100.129.70    <none>        1:30448/TCP      70m
prueba2-app1          NodePort    10.97.107.190    <none>        5000:30010/TCP   88m
prueba4-redis         NodePort    10.111.140.224   <none>        1:30790/TCP      84m
prueba5-redis         NodePort    10.97.11.112     <none>        1:30982/TCP      84m
prueba6-app1          NodePort    10.111.181.168   <none>        5000:30020/TCP   82m
prueba6-redis         NodePort    10.104.200.55    <none>        1:30345/TCP      82m
prueba7-redis         NodePort    10.99.84.235     <none>        1:31872/TCP      79m
prueba8-redis         NodePort    10.108.164.135   <none>        1:32591/TCP      78m
prueba9-redis         NodePort    10.109.254.237   <none>        1:30090/TCP      78m

juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice$ kubectl get deploy
NAME                  READY   UP-TO-DATE   AVAILABLE   AGE
my-release-app1       3/3     3            3           10h
my-release002-redis   1/1     1            1           15m
my-release003-redis   1/1     1            1           10m
my-release004-redis   1/1     1            1           9m53s
my-release005-redis   1/1     1            1           9m36s
my-release007-redis   1/1     1            1           9m6s
my-release01-redis    1/1     1            1           60m
my-release011-redis   1/1     1            1           7m48s
my-release013-redis   1/1     1            1           2m28s
my-release014-redis   1/1     1            1           119s
my-release02-redis    1/1     1            1           56m
my-release07-redis    1/1     1            1           52m
my-release1-redis     1/1     1            1           62m
my-release10-redis    1/1     1            1           49m
my-release14-redis    1/1     1            1           43m
my-release15-redis    1/1     1            1           43m
my-release16-redis    1/1     1            1           42m
my-release17-redis    1/1     1            1           41m
my-release19-redis    1/1     1            1           35m
my-release2-app1      3/3     3            3           9h
my-release20-redis    1/1     1            1           34m
my-release21-redis    1/1     1            1           32m
my-release22-redis    1/1     1            1           29m
my-release24-redis    1/1     1            1           26m
my-release25-redis    0/1     1            0           24m
my-release26-redis    0/1     1            0           23m
my-release27-redis    1/1     1            1           23m
my-release29-redis    1/1     1            1           9h
my-release3-redis     1/1     1            1           9h
my-release30-redis    1/1     1            1           9h
my-release31-redis    1/1     1            1           9h
my-release4-redis     1/1     1            1           9h
my-release5-redis     1/1     1            1           9h
my-release7-redis     1/1     1            1           9h
my-release8-redis     1/1     1            1           9h
my-release9-redis     1/1     1            1           9h
prueba1-redis         1/1     1            1           90m
prueba10-redis        1/1     1            1           78m
prueba11-redis        1/1     1            1           77m
prueba12-redis        1/1     1            1           74m
prueba13-redis        1/1     1            1           73m
prueba14-redis        1/1     1            1           70m
prueba2-redis         1/1     1            1           88m
prueba4-redis         1/1     1            1           85m
prueba5-redis         1/1     1            1           84m
prueba6-redis         1/1     1            1           82m
prueba7-redis         1/1     1            1           80m
prueba8-redis         1/1     1            1           79m
prueba9-redis         1/1     1            1           78m


juan@Portatil-Juan:~/HELM/ejercicio-entrega/microservice$ curl -s 127.0.0.1:30001/
<!doctype html>
<html lang=en>
<title>500 Internal Server Error</title>
<h1>Internal Server Error</h1>
<p>The server encountered an internal error and was unable to complete your request. Either the server is overloaded or there is an error in the application.</p>

kubectl logs my-release25-redis-865457fcc6-fqtcd
Error from server (BadRequest): container "redis" in pod "my-release25-redis-865457fcc6-fqtcd" is waiting to start: InvalidImageName
