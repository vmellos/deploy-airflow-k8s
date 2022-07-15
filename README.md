# Airflow no k8s

### Abrindo a porta para acessar o dashboard do airflow
kubectl port-forward --namespace airflow svc/v1-airflow 8080:8080 &
    echo "Airflow URL: http://127.0.0.1:8080"

### Instala o Apache Airflow
helm install v1 bitnami/airflow -n airflow -f values.yaml

### Atualiza o deploy do Apache Airflow
helm upgrade --install v1 bitnami/airflow -n airflow -f values.yaml


### Remover o airflow
helm delete v1 --namespace airflow

### k8s dashboard
kubectl dashboard

### Referencia
https://towardsdatascience.com/setting-up-data-pipelines-using-apache-airflow-on-kubernetes-4506baea3ce0
https://github.com/bitnami/charts/tree/master/bitnami/airflow/#installing-the-chart
https://github.com/bitnami/charts/tree/master/bitnami

### Referencia para configuração do postgres
https://github.com/bitnami/charts/blob/master/bitnami/postgresql/values.yaml

# cmd
kubectl get pod -n airflow
kubectl get pvc -n airflow
kubectl exec --stdin --tty airflow-webserver_POD_NAME -n airflow -- /bin/bash
kubectl create secret generic airflow-ssh-git-secret --from-file=gitSshKey=/home/user/.ssh/id_rsa -n airflow
kubectl delete secret -n airflow airflow-ssh-git-secret
kubectl get secret -n airflow 
kubectl logs -n airflow POD_NAME
kubectl config set-context default

minikube ssh docker container ls
minikube ssh "docker container exec -it -u 0 <Container ID> /bin/bash"


# kubectl - Cheat Sheet 
https://kubernetes.io/pt-br/docs/reference/kubectl/cheatsheet/ 
