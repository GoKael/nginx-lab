# nginx-lab

1.kubectl apply -f configmap.yaml
2.kubectl apply -f nodeport.yaml
3.kubectl apply -f controller.yaml
4.kubectl apply -f nginx.yaml
5.kubectl apply -f ingress.yaml

SET STATIC IP
gcloud compute addresses create kubernetes-ingress --global             # not working
gcloud compute addresses create kubernetes-ingress --region=asia-east1	# working

Check config inside alpine
kubectl exec `kubectl get pods -l run=my-nginx -o=name|cut -d "/" -f2` cat /tmp/log_level		  
kubectl exec `kubectl get pods -l run=my-nginx -o=name|cut -d "/" -f2` cat /etc/nginx/extra/proxy.conf

SOME COMMAND AND TIPS
gcloud auth list
gcloud config list project
gcloud config list zones
gcloud config set compute/zone asia-east1-a
gcloud container clusters create [CLUSTER-NAME]
gcloud container clusters get-credentials [CLUSTER-NAME] --zone asia-east1-a --project multi-k8s-ict
kubectl get pod --all-namespaces
kubectl describe pod [POD-NAME] -n [NameSpace]


SET SSH TO GCP INSTANCE
ssh instance-1.asia-east1-b.multi-k8s-ict  # can config in ./ssh

Build image using Cloud-Build
gcloud builds submit --config cloudbuild.yaml .

2019/02/08
1.Basic port 80 route external traffic to local backend successfully.

TODO:
1.SSL
2.HELM
3.SECURITY
