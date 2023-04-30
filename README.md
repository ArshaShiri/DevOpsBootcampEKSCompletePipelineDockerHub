# Complete CI/CD Pipeline Using Dockerhub and EKS

The Jenkinsfile is modified to deploy using the `deployment` and `service` yaml files. The app name and image name are also fed to these files via environment variables and `envsubst` command-line tool.