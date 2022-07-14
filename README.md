# Airflow no k8s

### Abrindo a porta para acessar o dashboard do airflow
kubectl port-forward --namespace airflow svc/v1-airflow 8080:8080 &
    echo "Airflow URL: http://127.0.0.1:8080"

### Instala o airflow
helm install -n airflow v1 bitnami/airflow -f values.yaml

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

