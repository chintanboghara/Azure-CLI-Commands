# Azure Kubernetes Service (AKS)

Azure Kubernetes Service (AKS) is a managed Kubernetes service that you can use to deploy and manage containerized applications. You need minimal container orchestration expertise to use AKS. AKS reduces the complexity and operational overhead of managing Kubernetes by offloading much of that responsibility to Azure.

AKS is an ideal platform for:
- Deploying and managing containerized applications that require high availability, scalability, and portability.
- Deploying applications to multiple regions.
- Using open-source tools.
- Integrating with existing DevOps tools.

## Overview of AKS

AKS reduces the complexity and operational overhead of managing Kubernetes by shifting that responsibility to Azure. When you create an AKS cluster, Azure automatically creates and configures a control plane for you at no cost. The Azure platform manages the AKS control plane, which is responsible for the Kubernetes objects and worker nodes that you deploy to run your applications. Azure takes care of critical operations like health monitoring and maintenance, and you only pay for the AKS nodes that run your applications.

## When to Use AKS

The following list describes some common use cases for AKS:

- **Lift and shift to containers with AKS**: Migrate existing applications to containers and run them in a fully managed Kubernetes environment.
- **Microservices with AKS**: Simplify the deployment and management of microservices-based applications with streamlined horizontal scaling, self-healing, load balancing, and secret management.
- **Secure DevOps for AKS**: Efficiently balance speed and security by implementing secure DevOps with Kubernetes.
- **Bursting from AKS with ACI**: Use virtual nodes to provision pods inside Azure Container Instances (ACI) that start in seconds and scale to meet demand.
- **Machine learning model training with AKS**: Train models using large datasets with familiar tools, such as TensorFlow and Kubeflow.
- **Data streaming with AKS**: Ingest and process real-time data streams with millions of data points collected via sensors, and perform fast analyses and computations to develop insights into complex scenarios.
- **Using Windows containers on AKS**: Run Windows Server containers on AKS to modernize your Windows applications and infrastructure.

## Features of AKS

### Identity and Security Management
- Enforce regulatory compliance controls using Azure Policy with built-in guardrails and internet security benchmarks.
- Integrate with Kubernetes RBAC to limit access to cluster resources.
- Use Microsoft Entra ID to set up Kubernetes access based on existing identity and group membership.

### Logging and Monitoring
- Integrate with Container Insights, a feature in Azure Monitor, to monitor the health and performance of your clusters and containerized applications.
- Set up Advanced Container Networking Services to collect and visualize network traffic data from your clusters.

### Streamlined Deployments
- Use prebuilt cluster configurations for Kubernetes with smart defaults.
- Autoscale your applications using the Kubernetes Event Driven Autoscaler (KEDA).
- Use Draft for AKS to ready source code and prepare your applications for production.

### Clusters and Nodes
- Connect storage to nodes and pods, upgrade cluster components, and use GPUs.
- Create clusters that run multiple node pools to support mixed operating systems and Windows Server containers.
- Configure automatic scaling using the cluster autoscaler and horizontal pod autoscaler.
- Deploy clusters with confidential computing nodes to allow containers to run in a hardware-based trusted execution environment.

### Storage Volume Support
- Mount static or dynamic storage volumes for persistent data.
- Use Azure Container Storage for fully managed, cloud-based volume management and orchestration of block storage. Azure Container Storage integrates with Kubernetes, allowing dynamic and automatic provisioning of persistent volumes.
- Use Azure Disks CSI driver for single pod access and Azure Files CSI driver for multiple, concurrent pod access.
- Use Azure NetApp Files for high-performance, high-throughput, and low-latency file shares.

### Networking
- Leverage our networking options for your needs.
- Bring your own Container Network Interface (CNI) to use a third-party CNI plugin.
- Easily access applications deployed to your clusters using the application routing add-on with nginx.

### Development Tooling Integration
- Develop on AKS with Helm.
- Install the Kubernetes extension for Visual Studio Code to manage your workloads.
- Leverage the features of Istio with the Istio-based service mesh add-on.
