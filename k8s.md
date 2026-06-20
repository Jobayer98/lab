# Kubernetes Lab Course Outline

---

## Phase 0: Prerequisites (1-2 weeks)

### Linux Basics

* Filesystem
* Processes
* Permissions
* SSH
* Systemd
* Networking basics

### Containers

* Docker architecture
* Images, containers, volumes
* Networks
* Docker Compose

### Hands-on

* Build Node.js image
* Run PostgreSQL container
* Multi-container app with Docker Compose

---

# Phase 1: Kubernetes Fundamentals (2 weeks)

### Understand

* What is Kubernetes?
* Cluster architecture
* Control Plane
* Worker Nodes
* API Server
* Scheduler
* etcd
* Kubelet
* Container Runtime

### Setup

Install:

* kubectl
* Minikube (or Kind)

### Hands-on

```bash
minikube start
kubectl get nodes
kubectl cluster-info
kubectl get all -A
```

Goal:
Understand how a cluster works.

---

# Phase 2: Pods (1 week)

### Learn

* Pod lifecycle
* Multi-container pods
* Init containers

### Labs

Create pods using YAML:

```yaml
apiVersion: v1
kind: Pod
...
```

Practice:

```bash
kubectl create
kubectl get pods
kubectl describe pod
kubectl logs
kubectl exec
kubectl delete
```

Goal:
Become comfortable with Pods.

---

# Phase 3: Deployments & ReplicaSets (1 week)

### Learn

* ReplicaSet
* Deployment
* Rolling updates
* Rollbacks

### Labs

Deploy nginx:

```yaml
kind: Deployment
replicas: 3
```

Practice:

```bash
kubectl scale
kubectl rollout status
kubectl rollout undo
```

Simulate bad deployment and rollback.

---

# Phase 4: Services & Networking (2 weeks)

### Learn

* ClusterIP
* NodePort
* LoadBalancer
* DNS
* Labels & Selectors

### Labs

Create:

* Backend Deployment
* Frontend Deployment
* Service between them

Commands:

```bash
kubectl expose
kubectl port-forward
```

Goal:
Understand pod communication.

---

# Phase 5: Configuration (1 week)

### Learn

* ConfigMaps
* Secrets
* Environment variables

### Labs

Inject configuration:

```yaml
env:
envFrom:
```

Use Secret for database password.

---

# Phase 6: Storage (1 week)

### Learn

* Volumes
* PersistentVolume
* PersistentVolumeClaim
* StorageClass

### Labs

Deploy PostgreSQL with persistent storage.

Delete pod and verify data remains.

---

# Phase 7: Advanced Workloads (1 week)

### Learn

* DaemonSet
* StatefulSet
* Jobs
* CronJobs

### Labs

* CronJob backup task
* Stateful PostgreSQL
* DaemonSet logging agent

---

# Phase 8: Ingress (1 week)

### Learn

* Ingress
* Ingress Controller
* Routing

### Labs

Install Nginx Ingress.

Create:

```
api.example.com → backend
web.example.com → frontend
```

---

# Phase 9: Scheduling (1 week)

### Learn

* Taints
* Tolerations
* Node Affinity
* Resource Requests
* Resource Limits

### Labs

Experiment with pod placement.

---

# Phase 10: Observability (1 week)

### Learn

* Logs
* Metrics
* Health checks

### Labs

Readiness Probe:

```yaml
readinessProbe:
```

Liveness Probe:

```yaml
livenessProbe:
```

Install Metrics Server:

```bash
kubectl top nodes
kubectl top pods
```

---

# Phase 11: Security (2 weeks)

### Learn

* Service Accounts
* RBAC
* Roles
* RoleBindings
* Network Policies

### Labs

Create user with limited permissions.

Test access:

```bash
kubectl auth can-i
```

---

# Phase 12: Package Management (Helm) (1 week)

### Learn

* Charts
* Values
* Templates

### Labs

Install:

* nginx
* Prometheus
* Grafana

Customize values.yaml.

---

# Phase 13: Monitoring & Logging (1 week)

### Learn

* Prometheus
* Grafana
* Loki

### Labs

Deploy monitoring stack with Helm.

Visualize CPU and memory metrics.

---

# Phase 14: CI/CD (2 weeks)

### Learn

* GitHub Actions
* Docker Hub
* Kubernetes deployment

### Labs

Pipeline:

```
GitHub
 ↓
Build Docker image
 ↓
Push image
 ↓
Deploy to Kubernetes
```

---

# Phase 15: Production Concepts (2 weeks)

### Learn

* HPA
* Vertical Scaling
* Rolling Update
* Canary Deployment
* Resource optimization

### Labs

Configure:

```yaml
HorizontalPodAutoscaler
```

Load test application.

---

# Phase 16: CKA Topics (3 weeks)

### Cluster Maintenance

* Backup etcd
* Upgrade cluster
* Drain nodes

### Networking

* Troubleshooting

### Scheduling

### Security

### Storage

### Labs

Practice entirely with kubectl.

---

# Phase 17: Real Projects

### Project 1

Node.js + PostgreSQL

Components:

* Deployment
* Service
* ConfigMap
* Secret
* PVC
* Ingress

---

### Project 2

Microservices App

```
Frontend
API
Auth
Redis
PostgreSQL
```

Deploy everything on Kubernetes.

---

### Project 3

Monitoring Stack

```
Prometheus
Grafana
Loki
AlertManager
```

---

### Project 4

GitHub Actions + Kubernetes

Auto deployment pipeline.

---

# Recommended Tools

### Local Cluster

1. Minikube (beginner)
2. Kind (Docker-based, preferred later)

### CLI

* kubectl
* k9s
* stern
* kubectx
* kubens

### YAML Editor

VSCode + Kubernetes extension

---

# Certification Path

```
Docker
 ↓
Kubernetes Fundamentals
 ↓
CKAD (Application Developer)
 ↓
Helm
 ↓
Monitoring
 ↓
CI/CD
 ↓
Security
 ↓
CKA (Administrator)
 ↓
EKS (AWS)
 ↓
Production Kubernetes
```

---

### My recommendation as your mentor:

**Don't rush to CKA.**

Follow:

```
Docker
↓
Minikube
↓
Pods
↓
Deployments
↓
Services
↓
Storage
↓
Ingress
↓
Security
↓
Helm
↓
Monitoring
↓
CI/CD
↓
CKAD
↓
CKA
↓
AWS EKS
```

Yes, but **not deeply enough** if your goal is **DevOps and troubleshooting**. Linux automation deserves its own phase because much of a DevOps engineer's work is automating repetitive tasks.

I'd expand the roadmap like this:

# Phase 9: Shell Scripting (Basic Automation)

Learn:

* Variables
* Conditionals
* Loops
* Functions
* Exit codes
* Arguments
* Error handling

### Labs

* Backup script
* Disk usage checker
* Log analyzer
* User creation script

---

# Phase 10: Linux Automation (Intermediate)

## Cron Jobs

```bash
crontab -e
```

Learn:

* Schedule syntax
* Environment variables
* Logging cron jobs

### Lab

Daily backup at midnight.

---

## systemd Timers

Modern replacement for cron.

### Lab

Run cleanup script every hour.

---

## File Synchronization

```bash
rsync
```

### Lab

Backup `/home` to another directory.

---

## Text Automation

Tools:

* grep
* awk
* sed
* xargs

### Lab

Find and compress old logs:

```bash
find /var/log -name "*.log" | xargs gzip
```

---

## Batch Operations

Create 100 users:

```bash
for i in {1..100}; do
    useradd user$i
done
```

---

## Monitoring Scripts

Write scripts to check:

* CPU
* Memory
* Disk
* Services

### Lab

If nginx is down:

```bash
systemctl restart nginx
```

---

## Log Rotation

Learn:

```bash
logrotate
```

### Lab

Rotate logs daily.

---

# Phase 16: Advanced Automation

## SSH Automation

```bash
ssh
scp
rsync
```

Run commands remotely:

```bash
ssh server "uptime"
```

---

## Parallel Execution

```bash
xargs -P
```

---

## Expect Scripts

Automate interactive commands.

---

## Configuration Management (Very Important)

After Linux basics:

* Bash automation
* Then **Ansible** ⭐⭐⭐⭐⭐

Learn:

* Inventory
* Playbooks
* Variables
* Roles
* Templates

### Labs

Automate:

* User creation
* Package installation
* Nginx deployment
* Multiple servers

---

# Real DevOps Automation Projects

### Server Health Monitor

Checks:

* CPU
* RAM
* Disk

Writes logs and sends alerts.

---

### Auto Backup System

Daily backup with cron.

---

### Log Cleanup Service

Delete logs older than 30 days.

---

### Auto-Heal Nginx

If nginx crashes:

* Restart service
* Write log
* Send notification

---

### Provision New Servers

Using Ansible:

```yaml
Install nginx
Create users
Configure firewall
Deploy app
```

---

For a **DevOps engineer**, I would consider these skills mandatory:

1. Linux fundamentals
2. Troubleshooting
3. Bash scripting
4. Cron/systemd timers
5. Text processing (grep, awk, sed)
6. SSH and rsync
7. Ansible ⭐⭐⭐⭐⭐
8. Containers (Docker)
9. Kubernetes
10. CI/CD

So yes, automation should be a major part of the roadmap, not just a small section.


If we're doing this together, I would teach it as a **20-week lab-driven course**, where every topic includes:

1. Theory (20%)
2. YAML writing (30%)
3. Hands-on labs (40%)
4. Troubleshooting exercises (10%)

This approach aligns well with DevOps jobs and Kubernetes certifications.
