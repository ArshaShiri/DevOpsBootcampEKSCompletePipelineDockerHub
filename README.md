# Complete CI/CD Pipeline Using Dockerhub and EKS

The Jenkinsfile is modified to deploy using the `deployment` and `service` yaml files. The app name and image name are also fed to these files via environment variables and `envsubst` command-line tool.

## Installing "gettext-base" Tool on Jenkins
    
    # Where the Jenkins container is running
    docker exec -u 0 -it {jenkins-container-id} bash
    
    apt-get update
    
    # This package includes the tool for substituting env varibles which is called in the Jenkinsfile
    apt-get install gettext-base
    
