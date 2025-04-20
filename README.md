my-cv-CI-CD-pipeline

install eksctl to be able to create and manage AWS EKS Kubernetes cluster

[CI/CD]

on Commit via GitHub

job 1 Build Docker image (docker build -t cv_site .)

job 2 Tag Docker image (docker tag cv_site razackou/cv_site)

job 3 Push docker image to razackou/cv_site repository (on DockerHub)(docker push razackou/cv_site:latest)

job 4 Update image in Kubernetes deployment  (kubectl set image deployment/my-deployment my-container=razackou/cv_site)



[DOC]
https://eksctl.io/usage/creating-and-managing-clusters/

https://eksctl.io/
