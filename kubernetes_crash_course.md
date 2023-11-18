# Introduction to Kubernetes

*Notes taken in reference to: [TechWorld with Nana](https://www.youtube.com/watch?v=s_o8dwzRlu4)*

I DO NOT OWN THE ORIGINAL CONTENT.

*[Git repo to follow along with demos](https://gitlab.com/nanuchi/k8s-in-1-hour)*

*[MiniKube installation Guide](https://minikube.sigs.k8s.io/docs/start/)*

The rough notes were made readable using ChatGPT.

In the dynamic landscape of modern software development, the use of containers has become ubiquitous. Managing hundreds of thousands of containers individually through scripts can be impractical. Kubernetes, an open-source container orchestration framework initially developed by Google, addresses this challenge. It enables the efficient management of applications composed of numerous containers across various deployment environments, including physical machines, virtual machines (VMs), cloud, or hybrid setups.

## Key Features of Kubernetes:

Kubernetes offers essential features that make it a powerful tool for container orchestration:

1. **High Availability:** Ensures applications experience no downtime by maintaining continuous availability.

2. **Scalability:** Allows quick scaling of resources to meet increased demand or vice versa.

3. **Disaster Recovery:** Facilitates backup and restoration from the latest state of containers, enhancing resilience.

## Basic Architecture:

The core architecture of Kubernetes consists of two main components:

- **Master Node:** Responsible for running Kubernetes processes and includes components such as the API server (facilitating cluster access), controller manager (managing cluster state), scheduler (scheduling containers on worker nodes), and etcd (key-value storage for cluster state).

- **Worker Nodes:** These nodes host the containers where the actual application workloads run. Each worker node runs the Kubelet process, facilitating communication and task execution within the cluster.

## Main Kubernetes Components:

1. **Nodes and Pods:**
   - A **Node** represents a physical or virtual machine.
   - A **Pod** is an abstraction over containers, creating a running environment atop containers. Best practice is to run one application container per Pod.

2. **Communication:**
   - Pods have unique IP addresses for communication, and **Services** are used to provide a static/permanent IP address for each Pod.
   - **External Service:** Enables communication from external sources.
   - **Internal Service:** Restricts external access, useful for sensitive services like databases.
   - **Ingress:** Resolves URL issues arising from impractical IP addresses.

3. **Configuration:**
   - **ConfigMap:** For external configuration to applications, excluding confidential data.
   - **Secret:** For handling sensitive information like passwords using Base64 encryption.

4. **Data Persistence:**
   - **Volumes:** Attaches physical storage to Pods, ensuring data persistence across Pod restarts.

## Scaling and Replication:

- **Deployments:** Blueprints for Pods, allowing the specification of replica scales. Services provide permanent IPs and load balancing.
  
- **StatefulSet:** Ensures synchronization for stateful applications (e.g., databases) to prevent inconsistencies.

## Creation and Configuration of Kubernetes Cluster:

- Kubernetes clients (UI, API, or K8s CLI) communicate with the API server, the entry point to the server, using .yaml or .json files.
  
- Configuration files include metadata, specification, and automatically generated status.
  
- Continuous updates and checks ensure the desired state matches the actual state, triggering adjustments if needed.

- Store configuration files with code or in a dedicated Git repository for version control.

## Minikube:

Minikube is a powerful tool designed to simplify the deployment of Kubernetes clusters for local development and testing purposes. It streamlines the process of working with Kubernetes in a smaller, controlled environment.

### Production Cluster Setup:

In a production environment, setting up a Kubernetes cluster typically involves multiple Master nodes (at least 2) and Worker nodes, each with distinct responsibilities. However, when aiming to test something on a local environment swiftly, configuring such a cluster can be complex.

Minikube presents an alternative by providing a single-node cluster where both the master and worker processes run on the same node. This approach is conducive to rapid testing without the complexities associated with a multi-node setup. Additionally, Minikube comes preinstalled with Docker containers, further simplifying the setup process.

### Interacting with Minikube:

To interact with the Minikube cluster, you need to perform various tasks such as creating pods and components on the node. The primary tool for this interaction is `kubectl`. This versatile command-line utility enables you to create, destroy, and configure pods, among other Kubernetes components.

**Key Points:**
- Minikube operates as a 1-node cluster with combined master and worker processes.
- It is equipped with preinstalled Docker containers for ease of use.
- Interaction with the Minikube cluster, including pod creation and configuration, is accomplished through `kubectl`.
- `kubectl` can be utilized for interacting with any Kubernetes cluster, not limited to Minikube.

Next task: [Deploy a WebApp using MongoDB]()
