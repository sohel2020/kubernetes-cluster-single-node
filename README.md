# Kubernetes Single Machine Cluster on Vagrant on top of CoreOS

# Install kubectl

```bash
curl -O https://storage.googleapis.com/kubernetes-release/release/v1.2.4/bin/linux/amd64/kubectl
bash

After downloading the binary, ensure it is executable and move it into your PATH:

```bash
$ sudo chmod +x kubectl
$ sudo mv kubectl /usr/local/bin/kubectl
bash

```bash
$ vagrant up --provider=virtualbox
```

# Configure kubectl

```bash
$ kubectl config set-cluster vagrant-single-cluster --server=https://172.17.4.99:443 --certificate-authority=${PWD}/ssl/ca.pem
$ kubectl config set-credentials vagrant-single-admin --certificate-authority=${PWD}/ssl/ca.pem --client-key=${PWD}/ssl/admin-key.pem --client-certificate=${PWD}/ssl/admin.pem
$ kubectl config set-context vagrant-single --cluster=vagrant-single-cluster --user=vagrant-single-admin
$ kubectl config use-context vagrant-single

```
Check that your client is configured properly by using kubectl to inspect your cluster:

```bash
$ kubectl get nodes
bash

NOTE: When the cluster is first being launched, it must download all container images for the cluster components (Kubernetes, dns, heapster, etc). Depending on the speed of your connection, it can take a few minutes before the Kubernetes api-server is available. Before the api-server is running, the kubectl command above may show output similar to:

```text
The connection to the server 172.17.4.99:443 was refused - did you specify the right host or port?
```




