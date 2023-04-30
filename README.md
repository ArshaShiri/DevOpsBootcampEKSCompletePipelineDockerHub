# Complete CI/CD Pipeline Using Dockerhub and EKS

The Jenkinsfile is modified to deploy using the `deployment` and `service` yaml files. The app name and image name are also fed to these files via environment variables and `envsubst` command-line tool.

## Installing "gettext-base" Tool on Jenkins
    
    # Where the Jenkins container is running
    docker exec -u 0 -it {jenkins-container-id} bash
    
    apt-get update
    
    # This package includes the tool for substituting env varibles which is called in the Jenkinsfile
    apt-get install gettext-base
    
## Create Secret for DockerHub Credentials

We need authentication from inside of the k8s cluster to be able to access docker hub. Having the kubectl connected to our EKS cluster, we can create this secret file once.

    kubectl create secret docker-registry my-registry-key \
    --docker-server=docker.io \
    --docker-username={username} \
    --docker-password={password}
    
    kubectl get secret
     # NAME              TYPE                             DATA   AGE
     # my-registry-key   kubernetes.io/dockerconfigjson   1      36s
     
Now that the secret is available, we can use it in our deployment file. (`imagePullSecrets` section in `deployment.yaml`)