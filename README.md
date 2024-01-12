
Descargo el repo bitnami que indica el profesor donde hay un wordpress con base de datos

helm repo add bitnami https://charts.bitnami.com/bitnami

helm search -> dos comandos disponibles: hub y repo
helm search hub redis -> distribuciones disponibles de redis en helm
helm search repo wordpress -> ver en mis repositorios.  descargado antes

helm install solucion-lab4 bitnami/wordpress -> instala wordpress con base de datos
helm uninstall solucion-lab4 bitnami/wordpress  -> desinstala wordpress

helm create microservice -> crea microservice con helm

juan@Portatil-Juan:~/HELM/microservice$ helm lint-> verifica que no hay errores en .yaml

helm install --dry-run --debug -> instala el nuevo microservicio de helm, el nombre no está en su sitio

helm package . -> empaquete l microservicio

helm install testv1 microservice-0.1.0.tgz

helm install testv1 microservice-0.1.0.tgz --debug --dry-run

helm install --set replicaCount=4 testv1 microservice-0.1.0.tgz -> cambio replicaCount en microservice de helm

-----------------------

Ejemplo con los archivos configmap.yaml, service.yaml y values.yaml

helm lint -> ver errores .yaml todo OK
helm install testv1 . --dry-run --debug

-----------------

step4**********************

helm install --set app.name=otro testv1 . --dry-run --debug

juan@Portatil-Juan:~/HELM/step4/microservice/charts$ helm create redis

********

juan@Portatil-Juan:~/HELM/step4/microservice$ helm install testv1 . --dry-run --debug