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

## Azure Kubernetes Service (AKS) Automatic (Preview)

**Applies to: ✔️ AKS Automatic (preview)**

Azure Kubernetes Service (AKS) Automatic offers an experience that makes the most common tasks on Kubernetes fast and frictionless, while preserving the flexibility, extensibility, and consistency of Kubernetes. Azure takes care of your cluster setup, including node management, scaling, security, and preconfigured settings that follow AKS well-architected recommendations. Automatic clusters dynamically allocate compute resources based on your specific workload requirements and are tuned for running production applications.

### Features of AKS Automatic (Preview)

- **Production ready by default**: Clusters are preconfigured for optimal production use, suitable for most applications. They offer fully managed node pools that automatically allocate and scale resources based on your workload needs. Pods are bin packed efficiently, to maximize resource utilization.
  
- **Built-in best practices and safeguards**: AKS Automatic clusters have a hardened default configuration, with many cluster, application, and networking security settings enabled by default. AKS automatically patches your nodes and cluster components while adhering to any planned maintenance schedules.

- **Code to Kubernetes in minutes**: Go from a container image to a deployed application that adheres to best practices patterns within minutes, with access to the comprehensive capabilities of the Kubernetes API and its rich ecosystem.

## AKS Automatic and Standard Feature Comparison

The following table provides a comparison of options that are available, preconfigured, and default in both AKS Automatic and AKS Standard. For more information on whether specific features are available in Automatic, you may need to check the documentation for that feature.

| Feature                           | AKS Automatic               | AKS Standard                |
|-----------------------------------|-----------------------------|-----------------------------|
| Pre-configured features           | Always enabled, cannot be disabled or changed | Optional to configure, not enabled by default |
| Default features                  | Configured by default, can be changed | Configured by default, can be changed |
| Optional features                 | Not enabled by default, configurable | Not enabled by default, configurable |

Pre-configured features are always enabled and you can't disable or change their settings. Default features are configured for you but can be changed. Optional features are available for you to configure and are not enabled by default.

## Application Deployment, Monitoring, and Observability

Application deployment can be streamlined using automated deployments from source control, which creates Kubernetes manifests and generates CI/CD workflows. Additionally, the cluster is configured with monitoring tools such as Managed Prometheus for metrics, Managed Grafana for visualization, and Container Insights for log collection.

| Option                          | AKS Automatic                | AKS Standard                 |
|---------------------------------|------------------------------|------------------------------|
| **Application Deployment**      | Optional:                    | Optional:                    |
|                                 | - Use automated deployments to containerize applications from source control, create Kubernetes manifests, and CI/CD workflows. | - Use automated deployments to containerize applications from source control, create Kubernetes manifests, and CI/CD workflows. |
|                                 | - Create deployment pipelines using GitHub Actions for Kubernetes. | - Create deployment pipelines using GitHub Actions for Kubernetes. |
|                                 | - Bring your own CI/CD pipeline. | - Bring your own CI/CD pipeline. |
| **Monitoring, Logging, and Visualization** | Default:                      | Optional:                    |
|                                 | - Managed Prometheus for metric collection when using Azure CLI or the Azure portal. | - Managed Prometheus for metric collection. |
|                                 | - Managed Grafana for visualization when using Azure CLI or the Azure portal. | - Managed Grafana for visualization. |
|                                 | - Container insights for log collection when using Azure CLI or the Azure portal. | - Container insights for log collection. |

## Node Management, Scaling, and Cluster Operations

Node management is automatically handled without the need for manual node pool creation. Scaling is seamless, with nodes created based on workload requests. Additionally, features for workload scaling like Horizontal Pod Autoscaler (HPA), Kubernetes Event Driven Autoscaling (KEDA), and Vertical Pod Autoscaler (VPA) are enabled. Clusters are configured for automatic node repair, automatic cluster upgrades, and detection of deprecated Kubernetes standard API usage. You can also set a planned maintenance schedule for upgrades if needed.

| Option                          | AKS Automatic                | AKS Standard                 |
|---------------------------------|------------------------------|------------------------------|
| **Node Management**             | Pre-configured: AKS Automatic manages the node pools using Node Autoprovisioning. | Default: You create and manage system and user node pools |
|                                 |                              | Optional: AKS Standard manages user node pools using Node Autoprovisioning. |
| **Scaling**                     | Pre-configured: AKS Automatic creates nodes based on workload requests using Node Autoprovisioning. | Default: Manual scaling of node pools. |
|                                 | Horizontal Pod Autoscaler (HPA), Kubernetes Event Driven Autoscaling (KEDA), and Vertical Pod Autoscaler (VPA) are enabled on the cluster. | Optional: Cluster autoscaler, Node Autoprovisioning, Kubernetes Event Driven Autoscaling (KEDA), Vertical Pod Autoscaler (VPA) |
| **Cluster Tier**                | Pre-configured: Standard tier cluster with up to 5,000 nodes and a cluster uptime Service Level Agreement (SLA). | Default: Free tier cluster with 10 nodes but can support up to 1,000 nodes. |
|                                 |                              | Optional: Standard tier cluster with up to 5,000 nodes and a cluster uptime SLA, Premium tier cluster with up to 5,000 nodes, cluster uptime SLA, and long-term support. |
| **Node Operating System**       | Pre-configured: Azure Linux | Default: Ubuntu |
|                                 |                              | Optional: Azure Linux, Windows Server containers |

## Security and Policies

Cluster authentication and authorization use Azure Role-based Access Control (RBAC) for Kubernetes authorization and applications can use features like workload identity with Microsoft Entra Workload ID and OpenID Connect (OIDC) cluster issuer to have secure communication with Azure services. Deployment safeguards enforce Kubernetes best practices through Azure Policy controls and the built-in image cleaner removes unused images with vulnerabilities, enhancing image security.

| Option                          | AKS Automatic                | AKS Standard                 |
|---------------------------------|------------------------------|------------------------------|
| **Cluster Authentication and Authorization** | Pre-configured: Azure RBAC for Kubernetes authorization for managing cluster authentication and authorization using Azure role-based access control. | Default: Local accounts. |
|                                 | Optional: Azure RBAC for Kubernetes authorization, Kubernetes RBAC with Microsoft Entra integration | |
| **Cluster Security**            | Pre-configured: API server virtual network integration enables network communication between the API server and the cluster nodes over a private network without requiring a private link or tunnel. | Optional: API server virtual network integration enables network communication between the API server and the cluster nodes over a private network without requiring a private link or tunnel. |
| **Application Security**        | Pre-configured: Workload identity with Microsoft Entra Workload ID, OpenID Connect (OIDC) cluster issuer. | Optional: Workload identity with Microsoft Entra Workload ID, OpenID Connect (OIDC) cluster issuer. |
| **Image Security**              | Pre-configured: Image cleaner to remove unused images with vulnerabilities. | Optional: Image cleaner to remove unused images with vulnerabilities. |
| **Policy Enforcement**          | Pre-configured: Deployment safeguards that enforce Kubernetes best practices in your AKS cluster through Azure Policy controls. | Optional: Deployment safeguards enforce Kubernetes best practices in your AKS cluster through Azure Policy controls. |

## Networking

AKS Automatic clusters use managed Virtual Network powered by Azure CNI Overlay with Cilium for high-performance networking and robust security. Ingress is handled by managed NGINX using the application routing add-on, integrating seamlessly with Azure DNS and Azure Key Vault. Egress uses a managed NAT gateway for scalable outbound connections. Additionally, you have the flexibility to enable Azure Service Mesh (Istio) ingress or bring your own service mesh.

| Option                          | AKS Automatic                | AKS Standard                 |
|---------------------------------|------------------------------|------------------------------|
| **Virtual Network**             | Pre-configured: Managed Virtual Network using Azure CNI Overlay powered by Cilium combines the robust control plane of Azure CNI with the data plane of Cilium to provide high-performance networking and security. | Default: Managed Virtual Network with kubenet. |
| **Ingress**                     | Pre-configured: Managed NGINX using the application routing add-on with integrations for Azure DNS and Azure Key Vault. | Optional: Managed NGINX using the application routing add-on with integrations for Azure DNS and Azure Key Vault. |
|                                 | Optional: Azure Service Mesh (Istio) ingress gateway, Bring your own ingress or gateway. | Optional: Azure Service Mesh (Istio) ingress gateway, Bring your own ingress or gateway. |
| **Egress**                      | Pre-configured: AKS managed NAT gateway for a scalable outbound connection flow. | Default: Azure Load Balancer |
|                                 | Optional: User-assigned NAT gateway, AKS managed NAT gateway. | Optional: User-assigned NAT gateway, AKS managed NAT gateway. |
| **Service Mesh**                | Optional: Azure Service Mesh (Istio), Bring your own service mesh. | Optional: Azure Service Mesh (Istio), Bring your own service mesh. |
