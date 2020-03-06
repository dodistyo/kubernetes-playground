You have to set secret for private registry authentication authentication

Step :
1. make sure you're logged in to docker registry (docker hub) in your host computer. command : "docker login"
2. run command : "
    kubectl create secret generic regcred \
    --from-file=.dockerconfigjson=<home_path/to/.docker/config.json> \
    --type=kubernetes.io/dockerconfigjson
"
3. to confirm, run command : "
    kubectl get secret regcred --output="jsonpath={.data.\.dockerconfigjson}" | base64 --decode
"
