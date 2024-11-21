
### **Day 1-5: Introduction and Setup**
#### **Day 1**
- Learn what Kubernetes is and why it’s used.
  - Core concepts: container orchestration, scalability, self-healing.
  - Understand Kubernetes components:
    - **Master Node**: API server, Scheduler, Controller Manager, etcd.
    - **Worker Nodes**: kubelet, kube-proxy, container runtime.

#### **Day 2**
- Install Kubernetes:
  - Local setup: Use **Minikube** or **Kind (Kubernetes in Docker)**.
  - Cloud setup: Use free tiers of cloud providers like GKE (Google), AKS (Azure), or EKS (AWS).
  - Verify installation: `kubectl version`.

#### **Day 3**
- Explore `kubectl` (Kubernetes CLI):
  - `kubectl get`, `kubectl describe`, `kubectl logs`, `kubectl exec`.
- Familiarize yourself with the YAML file structure.

#### **Day 4**
- Understand Kubernetes objects:
  - Pods, Deployments, ReplicaSets, Services.

#### **Day 5**
- Run your first app in Kubernetes:
  - Deploy an NGINX pod.
  - Expose it with a service using `kubectl expose`.

---

### **Day 6-10: Pods, Deployments, and Services**
#### **Day 6**
- Dive into Pods:
  - What are Pods?
  - Create a Pod using YAML.
  - Example:
    ```yaml
    apiVersion: v1
    kind: Pod
    metadata:
      name: mypod
    spec:
      containers:
      - name: nginx
        image: nginx:latest
    ```

#### **Day 7**
- Understand Deployments:
  - Benefits of Deployments (updates, scaling).
  - Create a Deployment using YAML.
  - Scale Pods: `kubectl scale deployment <name> --replicas=3`.

#### **Day 8**
- Learn about Services:
  - Types of Services: ClusterIP, NodePort, LoadBalancer, ExternalName.
  - Expose a Deployment with a Service.

#### **Day 9**
- Play with labels and selectors:
  - Assign labels to Pods.
  - Use selectors in Services.

#### **Day 10**
- Explore namespaces:
  - Create and manage namespaces.
  - Isolate resources using namespaces.

---

### **Day 11-15: Storage and Configuration**
#### **Day 11**
- Understand Volumes:
  - Types of Volumes: emptyDir, hostPath, persistentVolume (PV), persistentVolumeClaim (PVC).
  - Mount a volume to a Pod.

#### **Day 12**
- Work with ConfigMaps:
  - Store configuration data as key-value pairs.
  - Inject configuration into Pods.

#### **Day 13**
- Use Secrets:
  - Store sensitive information (passwords, tokens).
  - Inject Secrets into Pods.

#### **Day 14**
- Manage Stateful Applications:
  - Understand StatefulSets.
  - Example use case: Deploy a database like MySQL.

#### **Day 15**
- Learn about StorageClasses:
  - Dynamically provision storage.

---

### **Day 16-20: Networking and Advanced Concepts**
#### **Day 16**
- Understand Kubernetes networking:
  - Pod-to-Pod communication.
  - Cluster networking (CNI).

#### **Day 17**
- Explore Ingress:
  - Use Ingress to expose HTTP and HTTPS routes.
  - Example with an NGINX ingress controller.

#### **Day 18**
- Play with DaemonSets:
  - Use cases: logging agents, monitoring agents.

#### **Day 19**
- Learn about Jobs and CronJobs:
  - Create a one-time Job and a recurring CronJob.

#### **Day 20**
- Understand Taints and Tolerations:
  - Restrict workloads to specific nodes.

---

### **Day 21-25: Scaling, Monitoring, and Troubleshooting**
#### **Day 21**
- Practice horizontal scaling:
  - Use HorizontalPodAutoscaler (HPA) for dynamic scaling.

#### **Day 22**
- Learn resource management:
  - Requests and Limits for CPU and memory.

#### **Day 23**
- Monitoring with Prometheus and Grafana:
  - Set up Prometheus for metrics collection.
  - Use Grafana to visualize Kubernetes metrics.

#### **Day 24**
- Explore Logging:
  - Centralized logging with Elasticsearch, Fluentd, and Kibana (EFK stack).

#### **Day 25**
- Debug and troubleshoot:
  - Common `kubectl` commands for troubleshooting (`kubectl describe`, `kubectl logs`).
  - Use tools like **Lens** or **K9s**.

---

### **Day 26-30: Projects and Advanced Topics**
#### **Day 26**
- Work with Helm:
  - Install Helm.
  - Use Helm charts to deploy applications.

#### **Day 27**
- Dive into Operators:
  - Understand Kubernetes Operators.
  - Deploy a sample operator (e.g., MongoDB Operator).

#### **Day 28**
- Learn Kubernetes security:
  - Role-Based Access Control (RBAC).
  - Secure communication with TLS.

#### **Day 29**
- Deploy an end-to-end application:
  - Example: A multi-tier web app with a frontend, backend, and database.
  - Use Deployments, Services, Ingress, and Persistent Volumes.

#### **Day 30**
- Explore Kubernetes in production:
  - Learn about GitOps (e.g., with ArgoCD).
  - Understand Kubernetes backup and disaster recovery tools (Velero).

---

### **Resources**
- **Kubernetes Documentation**: [https://kubernetes.io/docs/](https://kubernetes.io/docs/)
- **Play with Kubernetes**: [https://labs.play-with-k8s.com/](https://labs.play-with-k8s.com/)
- **Katacoda Kubernetes Scenarios**: [https://www.katacoda.com/courses/kubernetes](https://www.katacoda.com/courses/kubernetes)
- **Kubernetes for Developers** (YouTube): TechWorld with Nana.

By following this roadmap, you’ll gain practical Kubernetes experience and be well-equipped for real-world use cases!