Most of the documentation is from https://cloud.google.com/kubernetes-engine/docs/quickstart

# Create a GKE cluster
To create a cluster on the specified network and subnetwork, run:

```shell
gcloud container clusters create hello-cluster --num-nodes=1 --network=hello-net --subnetwork=hello-net-us-west1-01
```

If you want to create a GKE cluster on the default network, run:

```shell
gcloud container clusters create hello-cluster --num-nodes=1
```

# List to see if the cluster shows up
Run:
```shell
gcloud container clusters list
```

Sample output:

```sql
NAME           LOCATION    MASTER_VERSION   MASTER_IP     MACHINE_TYPE  NODE_VERSION     NUM_NODES  STATUS
hello-cluster  us-west1-b  1.19.9-gke.1900  35.197.90.43  e2-medium     1.19.9-gke.1900  1          RUNNING
```

# Download kubectl

* Install `kubectl` (reads _kube control_), it is a tool for controlling Kubernetes clusters in general.

```shell
gcloud components install kubectl
```

# Configure kubectl to talk to the newly created cluster

```shell
gcloud container clusters get-credentials hello-cluster
```

# Verify the nodes via kubectl

Run:

```shell
kubectl get nodes
```

Sample output:

```shell
gke-hello-cluster-default-pool-97ba9700-tdx6   Ready    <none>   62m   v1.19.9-gke.1900
```