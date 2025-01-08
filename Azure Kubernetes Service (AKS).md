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
