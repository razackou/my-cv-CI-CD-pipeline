my-cv-CI-CD-pipeline

install eksctl to be able to create and manage AWS EKS Kubernetes cluster

then create a cluster with the command eksctl create cluster and check the cluster <add screen0 here>

Do an initial deployment of the application by running kubectl apply -f deployment.yaml Right after, run kubectl get all to get the LoadBalancer link and test it in a web brwoser. Please, add http:// before. It not working, allow few minutes and try again. <add screen1 here>

Then in GitHub, create three secrets: DOCKER_HUB_USERNAME ; DOCKER_HUB_TOKEN and KUBECONFIG which will contain docker username/password and a last variable which will contain .kube/config file content as on below screenshot. <Add screen2 here>

[CI/CD]

on Commit via GitHub

job 1 Build Docker image (docker build -t cv_site .)

job 2 Tag Docker image (docker tag cv_site razackou/cv_site)

job 3 Push docker image to razackou/cv_site repository (on DockerHub)(docker push razackou/cv_site:latest)

job 4 Update image in Kubernetes deployment  (kubectl set image deployment/my-deployment my-container=razackou/cv_site)



[DOC]
https://eksctl.io/usage/creating-and-managing-clusters/

https://eksctl.io/
