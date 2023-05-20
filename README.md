# kubernetes-full-cycle

## Instalations
    - kubectl: curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
    - sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
    - test: kubectl version --client

    - kind: go install sigs.k8s.io/kind@v0.19.0
    - test: kind --version
    - kind documentation: https://kind.sigs.k8s.io/docs/user/configuration/

## Docker
    - docker build -t mrpsousa/k8s-pratice:latest -f Dockerfile .
    - docker run --rm -p 8000:8000 mrpsousa/k8s-pratice:latest
    - docker push mrpsousa/k8s-pratice:latest


## Kind 
    - kind create cluster --config=./k8s/kind.yaml --name=fullcycle
    - kubectl cluster-info --context kind-{cluster_name}
    - docker ps - to verify
    - kubectl get nodes
    ----------------------------------------------------------------
    - kind get clusters
    - kind delete clusters {cluster_name}

## Run
    - kubectl apply -f k8s/deployment.yaml
        - (creating pod) kubectl apply -f k8s/pod.yaml
        - (creating pod com replicaset) kubectl apply -f k8s/replicaset.yaml
    - kubectl apply -f k8s/service_loadbalance.yaml
    - kubectl get pod
    - kubectl describe pod {pod_name}
    - (deleting pod) kubectl delete pod {pod_name}
    - (deleting replicaset) kubectl delete replicaset {replicaset_name}
    - kubectl rollout undo deployment {deployment_name} (back to last "version")
    - kubectl rollout undo deployment {deployment_name} --to-revision={revision_number} (back to last "version")

    


<!-- spec:
  containers:
  - name: goserver
    image: "mrpsousa/k8s-pratice:latest"
    # env:
    # - name: KUBE_CACHE_MUTATION_DETECTOR
    #   value: "true" -->
 
 