# Helm
helm repo for lab

# install helm 
$ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
$ chmod 700 get_helm.sh
$ ./get_helm.sh

# $ helm version   ----version check

# create helm chart firstly 

$ helm create my-first-chart

#go created folder or go with editer 

#click >--- in left side >file>open workspace>open created chart 

#chart folder used for require depiciency

#template folder ---where all kubernets object present that you want to deploy 

#chart.yaml ---information about baseic components object

#values.yaml  ---where we specifi variable  regarding of kubernets object [template]

# Generate yaml through command line 
$ kubectl create deployment my-deploy --image=nginx --dry-run=client -o yaml > deploy.yaml
$ kubectl create service nodeport my-svc --tcp=80:80 --dry-run=client -o yaml >svc.yaml
#add selector  in this yaml or take another yaml files.

#to apply this yaml files
$ helm install my-first-relaese  .    ----[we can give any name but should be unserastanderble of first application]

# to check created deployment

$ kubectl get svc.deploy       ---or can access with port number

# we can not create same application with second release name chart 

#we should have second deployment and second release   --Tocreate second application just we need to pass values in deployment through the variable 

# for e.g  we have add new deployment so  specify values in values.yaml

#deployment:
  name: my-new-deploy
  image: abhijitramteke/myhtml-site:01   
  replicas: 1

# service:
  name: my-new-service 

# template >  deploy.yaml   enter path of object in deployment files

name: {{. values.deployment.name }}
image : {{ .values.deployment.image }}
replicas: {{ .values.deployment.replicas }}


# helm list  ----for deploied application 

#helm install relese2 . ----for apply secod deploymnt 

# kubectl get svc,deploy

#helm uninstall my-first-relaese ---to delete first appliation 





