## 1. Install Docker

To install Docker, follow the instructions provided in the [official Docker documentation](https://docs.docker.com/get-docker/).

## 2. Install Installing Kind (Kubernetes in Docker) 
kind is a tool for running local Kubernetes clusters using Docker container “nodes”.
kind was primarily designed for testing Kubernetes itself, but may be used for local development or CI.

For detailed installation instructions and troubleshooting, refer to the [official Kind documentation](https://kind.sigs.k8s.io/docs/user/quick-start#installation).


## 3. Create Kubernetes cluster using Docker containers

When you run kind create cluster, Kind performs the following steps:

1. It sets up a new Kubernetes cluster using Docker containers as "nodes".
2. It creates a new Docker container for each Kubernetes node (master and worker nodes).
3. It configures networking between the containers to simulate a multi-node Kubernetes cluster.
4. It installs the necessary Kubernetes components inside the containers, such as kubelet, kube-proxy, and etcd.
5. Finally, it sets up kubeconfig files and context to allow kubectl to interact with the newly created Kind cluster.

To create a Kubernetes cluster using Kind, execute the following command:

```
kind create cluster
```

## 4. Deploy Kubeflow Pipelines

You can enter the commands above one line at a time. These will setup all the deployments and spin up the pods for the entire application. These will be found in the kubeflow namespace. After sending the last command, it will take a moment (around 30 minutes) for all the deployments to be ready. 

```
export PIPELINE_VERSION=1.8.5
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/cluster-scoped-resources?ref=$PIPELINE_VERSION"
kubectl wait --for condition=established --timeout=300s crd/applications.app.k8s.io
kubectl apply -k "github.com/kubeflow/pipelines/manifests/kustomize/env/platform-agnostic-pns?ref=$PIPELINE_VERSION"
```
You can send the command ``` kubectl get deploy -n kubeflow ``` a few times to check the status. You should see all deployments with the READY status before you can proceed to the next section.
