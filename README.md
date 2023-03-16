# UKS Beta

This repository contains sample configurations for Terraform and Kubernetes manifests to get started with our UpCloud Kubernetes Service (UKS).

Note that this repository is still evolving. Please check back during the beta period and also familiarise yourself with [the known issues](KNOWN_ISSUES.md).

## Creating your first cluster

### UI
The simplest way to create a cluster is to use our Control Panel. You can do so by following these steps:

* Log in to the [UpCloud Control Panel](https://hub.upcloud.com).
* Go to `Kubernetes` page using the left-hand side menu.
* Click `Create new cluster`.
* The beta is being run on a two zones: 🇩🇪 `de-fra1` and 🇫🇮 `fi-hel2`.
* Select a Private Network for your Worker Nodes. This network should be in the same zone as the cluster you are creating. The network can not be connected to an existing cluster, can not have an attached router, and should have DHCP enabled with default route from DHCP disabled. For IP network of your SDN network, you can use for example `172.24.1.0/24`.
* Create a node group or use the default node-group; node group is a group of workers with identical image templates.
* Name your cluster.
* Click `Create` button.
* Cluster creation will take a few minutes as worker nodes are being provisioned and a DNS record is prepared.
* When the cluster is running, you can download your cluster's kubeconfig file; it allows you to access your cluster easily via command line with [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl). See [Exposing Services](#exposing-services) for example on deploying an _Hello UKS_ application to your newly created cluster.

### Alternatives
You can also create a cluser using the following ways:
* Terraform - see [terraform/README.md](terraform/README.md) for more precise instructions
* Direct API access - see [openapi/openapi.yaml](openapi/openapi.yaml) for UKS Beta API documentation; authentication can be achieved with [these](https://developers.upcloud.com/1.3/2-architecture/#authentication) instructions

### Kubeconfig

You can get your kubeconfig by going to your cluster details page in [Control Panel](https://hub.upcloud.com/kubernetes).
Alternatively, if you use Terraform you can leverage `local_file` provider to create kubeconfig file after the cluster is deleted ([see terraform example](terraform/main.tf))

## Exposing Services

See [ccm/README.md](ccm/README.md).

## Persistent storage

See [storage/README.md](storage/README.md).  

## Troubleshooting

See [KNOWN_ISSUES.md](KNOWN_ISSUES.md)

