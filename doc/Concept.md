# Comparison of Minikube, Kind, and K3d

|   Tool         |Description             |Pros                                             |Cons          |How-To Install          |
|----------------|------------------------|-------------------------------------------------|--------------|--------------
|minicube|Minikube is software that allows users to run a k8s cluster of just a single node and on a local machine. It is fast to set up and good testing environment for developers to see how their containerized application will run on Kubernetes.<br> It is not meant for production, but to test applications and deployment settings to see how they fare before sending them to a production environment. Has >25.8k stars on GitHub.|- easy to setup and use;<br> - GUI availability;<br> - mounts code from the developer’s machine directly into the running k8s node;<br> - SIG (special interest group) support;<br> - platform-agnostic;<br> - kubectl context automatically set to the newly created cluster;<br> - addons;<br> - allows creating multiple instances in parallel;|- running on Podman is considered experimental;<br> - high resource demands;<br> - poor automation options - no configuration file;<br> - poor multi-node support;<br> - cannot be deployed in the cloud by default;<br> - unavailable as a managed service;<br> - not intended for hosting production-grade workloads;<br> - does not support IoT/edge;<br> - approach of spawning a VM which decreases the startup speed.|[minikube](https://minikube.sigs.k8s.io/docs/) | 
|kind|Kind is an acronym for “Kubernetes in Docker'' and was born from the idea to run Kubernetes on a container runtime (instead of a VM). Has >11.1k stars on GitHub.            |- solid Podman support;<br> - CNCF certified;<br> - platform-agnostic;<br> - faster startup speed:<br> - allows creating multiple instances in parallel;<br> - provides configuration files;<br> - ability to load a local images directly into the cluster;|- requires Docker to run Kubernetes clusters, which can impact performance.<br> - harder to learn and operate from the start| [kind](https://kind.sigs.k8s.io/docs/user/quick-start/) |
|k3d|k3d is a lightweight wrapper to run k3s (Rancher Lab’s minimal Kubernetes distribution) in docker. k3d makes it very easy to create single- and multi-node k3s clusters in docker, e.g. for local development on Kubernetes. Has >4.1k stars on GitHub.|- quickly installed and runs on a local machine;<br> - ingress out of the box;<br> - platform-agnostic;<br> - lower resource consumption compared to minikube;<br> - fully CNCF (Cloud Native Computing Foundation);<br> - provides the capability to mount code from the developer’s machine directly into the running Kubernetes node;<br> - designed to run production-level Kubernetes on local machines;<br> - a single binary of less than 50MB;<br> - kubectl context automatically set to the newly created cluster;<br> - provides a cluster configuration file in YAML;<br> - allows quickly deploy production-level Kubernetes in a local environments without much storage or network requirements;<br> - easily to create single and multi-node k3s clusters for seamless local development and testing;<br> - more suitable for Raspberry Pi, IoT, and Edge devices;<br> - provides the ability to create multi-node Kubernetes clusters, allowing testing of more complex scenarios.|- some features supported by official Kubernetes may be limited or not fully supported;<br> - VM based Kubernetes environment;<br> - more limited when it comes to deploying it on a development machine;<br> - has a smaller community and ecosystem compared to Minikube or Kind;<br>| [k3d](https://k3d.io/#getting-started) |

## Conclusions

Considering the risks that may arise with Docker licensing and considering the possibility of using an alternative to Podman, only one Kind provides solid Podman support. Thus, I recommend Kind as a further development tool of AsciiArtify.  

## Setup demo

![kind create cluster](https://github.com/ibayro/devops/assets/104074570/3ee1c07f-9858-49e2-9d3a-69edb060dc63)
![scratch demo](https://github.com/ibayro/devops/assets/104074570/84fe6968-fec6-4c9c-9705-8a8c2129bc87)

1. Install kind on a local machine
2. Create a Kubernetes cluster using `kind create cluster` command
3. Verify that the cluster is running using the `kubectl cluster-info` command
4. Deploy an example application using `kubectl create deployment` and `kubectl expose deployment` commands
5. Access the application using the `kubectl port-forward` command or `kubectl proxy` command

