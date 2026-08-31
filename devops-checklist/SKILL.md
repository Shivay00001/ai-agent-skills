---
name: devops-checklist
description: >
  Comprehensive DevOps & Engineering Master Skills Reference and Project Checklist.
  Covers 20+ technologies: Docker, Kubernetes, Terraform, Ansible, Jenkins, GitHub Actions,
  GitLab CI, Prometheus, Grafana, CI/CD pipelines, databases, security, cloud platforms, and more.
  Includes production-ready templates, starter configs, and a 9-phase go-live readiness checklist.
  Use this skill when setting up a new project, onboarding infrastructure, or auditing DevOps readiness.
---

# 🚀 DevOps & Engineering — Master Skills & Checklist

> A comprehensive reference for DevOps, Software Engineering, and Infrastructure skills.
> Use this as a **project readiness checklist**, **learning roadmap**, and **best-practices guide**.

---

## Table of Contents

1. [Software Engineering Fundamentals](#1-software-engineering-fundamentals)
2. [Agile & Scrum](#2-agile--scrum)
3. [Jira & Project Management](#3-jira--project-management)
4. [Git Version Control](#4-git-version-control)
5. [GitHub](#5-github)
6. [GitLab](#6-gitlab)
7. [CI/CD Pipelines](#7-cicd-pipelines)
8. [Jenkins](#8-jenkins)
9. [Docker & Containers](#9-docker--containers)
10. [Kubernetes & Orchestration](#10-kubernetes--orchestration)
11. [Terraform (IaC)](#11-terraform-infrastructure-as-code)
12. [Ansible (Configuration Management)](#12-ansible-configuration-management)
13. [Servers & Deployment](#13-servers--deployment)
14. [Database Management](#14-database-management)
15. [Prometheus (Monitoring)](#15-prometheus-monitoring)
16. [Grafana (Observability)](#16-grafana-observability)
17. [Security & Compliance](#17-security--compliance-devsecops)
18. [Cloud Platforms](#18-cloud-platforms)
19. [Networking & DNS](#19-networking--dns)
20. [Logging & Tracing](#20-logging--tracing)
21. [Project Readiness Master Checklist](#21--project-readiness-master-checklist)

---

## 1. Software Engineering Fundamentals

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Clean Code Principles | 🟢 Core | SOLID, DRY, KISS, YAGNI |
| Design Patterns | 🟢 Core | Singleton, Factory, Observer, Strategy, Adapter |
| Data Structures & Algorithms | 🟢 Core | Arrays, Trees, Graphs, Sorting, Searching |
| API Design | 🟢 Core | REST, GraphQL, gRPC, WebSockets |
| Testing Strategies | 🟢 Core | Unit, Integration, E2E, Load, Chaos |
| Code Review | 🟡 Important | PR review standards, constructive feedback |
| Documentation | 🟡 Important | ADRs, README, API docs, Runbooks |
| 12-Factor App Methodology | 🟡 Important | Config, logging, statelessness, disposability |

### Checklist

- `[ ]` Coding standards and style guide established
- `[ ]` Linter and formatter configured (ESLint, Prettier, Black, etc.)
- `[ ]` Code review process defined (min reviewers, SLA)
- `[ ]` API contracts documented (OpenAPI / Swagger)
- `[ ]` Error handling strategy defined
- `[ ]` Logging standards established (structured JSON logs)
- `[ ]` Testing strategy documented (coverage targets, test types)
- `[ ]` Architecture Decision Records (ADR) template created
- `[ ]` Technical debt tracking process in place
- `[ ]` Dependency update policy defined

---

## 2. Agile & Scrum

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Scrum Framework | 🟢 Core | Sprints, ceremonies, roles, artifacts |
| Kanban | 🟡 Important | Visual boards, WIP limits, flow metrics |
| User Stories | 🟢 Core | As a…, I want…, So that… format |
| Sprint Planning | 🟢 Core | Backlog refinement, estimation, capacity |
| Retrospectives | 🟢 Core | Continuous improvement, action items |
| Velocity Tracking | 🟡 Important | Burn-down/up charts, forecasting |
| SAFe / Scaled Agile | 🔵 Advanced | PI Planning, ARTs, solution trains |

### Checklist

- `[ ]` Sprint duration defined (1–4 weeks)
- `[ ]` Definition of Done (DoD) documented
- `[ ]` Definition of Ready (DoR) documented
- `[ ]` Estimation methodology chosen (Story Points / T-Shirt sizing)
- `[ ]` Sprint ceremonies scheduled (Planning, Daily, Review, Retro)
- `[ ]` Backlog grooming cadence established
- `[ ]` Velocity baseline established after 3+ sprints
- `[ ]` Burndown chart dashboard set up
- `[ ]` Impediment escalation process defined
- `[ ]` Cross-team dependency management process in place

---

## 3. Jira & Project Management

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Project Configuration | 🟢 Core | Boards, workflows, issue types, schemes |
| JQL (Jira Query Language) | 🟢 Core | Advanced filtering and reporting |
| Workflow Customization | 🟡 Important | Status transitions, validators, post-functions |
| Dashboards & Reporting | 🟡 Important | Gadgets, filters, burndown charts |
| Automation Rules | 🟡 Important | Auto-assign, transitions, notifications |
| Integrations | 🔵 Advanced | GitHub/GitLab, Slack, CI/CD, Confluence |

### Checklist

- `[ ]` Jira project created with appropriate project type (Scrum/Kanban)
- `[ ]` Issue types configured (Epic, Story, Task, Bug, Sub-task)
- `[ ]` Custom fields defined (Environment, Severity, Team, etc.)
- `[ ]` Workflow states defined (To Do → In Progress → Code Review → QA → Done)
- `[ ]` Board columns mapped to workflow states
- `[ ]` Sprint board configured with swimlanes
- `[ ]` Labels and components taxonomy established
- `[ ]` Automation rules set up (auto-transition, notifications)
- `[ ]` Git integration configured (smart commits, branch linking)
- `[ ]` Release management configured (Fix Version tracking)
- `[ ]` SLA and priority matrix defined
- `[ ]` Dashboard with key metrics created (velocity, cycle time, throughput)

### Useful JQL Queries

```sql
-- My open items in current sprint
assignee = currentUser() AND sprint in openSprints() AND status != Done

-- Bugs created this week
issuetype = Bug AND created >= startOfWeek()

-- Unestimated stories in backlog
issuetype = Story AND "Story Points" is EMPTY AND status = "To Do"

-- Overdue items
due < now() AND status != Done

-- Items without assignee
assignee is EMPTY AND sprint in openSprints()
```

---

## 4. Git Version Control

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Basic Commands | 🟢 Core | clone, add, commit, push, pull, fetch |
| Branching Strategies | 🟢 Core | GitFlow, GitHub Flow, Trunk-Based |
| Merge vs Rebase | 🟢 Core | When to use each, conflict resolution |
| Interactive Rebase | 🟡 Important | Squash, fixup, reorder, edit |
| Cherry-pick | 🟡 Important | Selective commit porting |
| Bisect | 🔵 Advanced | Binary search for bug-introducing commits |
| Submodules / Subtrees | 🔵 Advanced | Multi-repo management |
| Git Hooks | 🟡 Important | Pre-commit, pre-push, commit-msg |
| Signed Commits | 🔵 Advanced | GPG/SSH signing for verification |

### Checklist

- `[ ]` Branching strategy chosen and documented
- `[ ]` Branch naming convention defined (`feature/`, `bugfix/`, `hotfix/`, `release/`)
- `[ ]` Commit message convention adopted (Conventional Commits)
- `[ ]` `.gitignore` properly configured
- `[ ]` Protected branches configured (main, develop)
- `[ ]` Merge strategy defined (squash, merge commit, rebase)
- `[ ]` Pre-commit hooks installed (linting, formatting, secrets scanning)
- `[ ]` Tag strategy for releases defined (SemVer: `v1.2.3`)
- `[ ]` Git LFS configured for large files (if needed)
- `[ ]` Stale branch cleanup policy established

### Branching Strategy Reference

```
main ─────────────────────────────────────────────►
  │                        ▲
  ├── develop ─────────────┤
  │     │          ▲       │
  │     ├── feature/auth ──┘
  │     ├── feature/api ───┘
  │     └── bugfix/login ──┘
  │
  └── hotfix/critical-fix ─────────────────────────►
```

---

## 5. GitHub

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Pull Requests | 🟢 Core | Reviews, approvals, merge rules |
| GitHub Actions | 🟢 Core | CI/CD workflows, reusable actions |
| Branch Protection Rules | 🟢 Core | Required reviews, status checks |
| GitHub Packages | 🟡 Important | npm, Docker, Maven registries |
| GitHub Security | 🟡 Important | Dependabot, secret scanning, CODEOWNERS |
| GitHub Pages | 🟡 Important | Static site hosting from repos |
| GitHub Projects | 🟡 Important | Project boards, views, automation |
| GitHub Copilot | 🔵 Advanced | AI-assisted development |

### Checklist

- `[ ]` Repository created with proper visibility (Public/Private)
- `[ ]` Branch protection rules configured on `main`
- `[ ]` `CODEOWNERS` file created
- `[ ]` `README.md` with project overview, setup, and usage
- `[ ]` `CONTRIBUTING.md` guide created
- `[ ]` Issue templates configured (Bug Report, Feature Request)
- `[ ]` PR template created (`.github/pull_request_template.md`)
- `[ ]` GitHub Actions CI/CD pipeline configured
- `[ ]` Dependabot enabled for dependency updates
- `[ ]` Secret scanning enabled
- `[ ]` Repository secrets configured for CI/CD
- `[ ]` GitHub Environments set up (dev, staging, production)
- `[ ]` Release workflow with auto-generated changelogs

### GitHub Actions — Starter Workflow

```yaml
name: CI/CD Pipeline
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
          cache: 'npm'
      - run: npm ci
      - run: npm run lint
      - run: npm test
      - run: npm run build

  security-scan:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: github/codeql-action/init@v3
      - uses: github/codeql-action/analyze@v3

  deploy:
    needs: [build-and-test, security-scan]
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    environment: production
    steps:
      - uses: actions/checkout@v4
      - name: Deploy to Production
        run: echo "Deploy steps here"
```

---

## 6. GitLab

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| GitLab CI/CD | 🟢 Core | `.gitlab-ci.yml`, pipelines, stages, jobs |
| Merge Requests | 🟢 Core | Approvals, merge trains, squash |
| GitLab Runners | 🟢 Core | Shared, group, project runners |
| GitLab Container Registry | 🟡 Important | Docker image storage |
| GitLab Environments | 🟡 Important | Review apps, deployments |
| GitLab Security | 🟡 Important | SAST, DAST, dependency scanning |
| GitLab Pages | 🔵 Advanced | Static site hosting |

### Checklist

- `[ ]` GitLab project created and configured
- `[ ]` `.gitlab-ci.yml` pipeline file created
- `[ ]` GitLab Runner registered and tagged
- `[ ]` CI/CD variables configured (Settings → CI/CD → Variables)
- `[ ]` Protected branches and tags configured
- `[ ]` Merge request approvals configured
- `[ ]` Container Registry enabled
- `[ ]` Security scanning templates included
- `[ ]` Environment definitions created (dev, staging, production)
- `[ ]` Auto DevOps evaluated and configured if applicable

### GitLab CI — Starter Pipeline

```yaml
stages:
  - build
  - test
  - security
  - deploy

variables:
  DOCKER_IMAGE: $CI_REGISTRY_IMAGE:$CI_COMMIT_SHORT_SHA

build:
  stage: build
  image: docker:latest
  services:
    - docker:dind
  script:
    - docker build -t $DOCKER_IMAGE .
    - docker push $DOCKER_IMAGE

test:
  stage: test
  image: node:20
  script:
    - npm ci
    - npm run lint
    - npm test
  coverage: '/Statements\s*:\s*(\d+\.?\d*)%/'

sast:
  stage: security
  include:
    - template: Security/SAST.gitlab-ci.yml

deploy_production:
  stage: deploy
  environment:
    name: production
    url: https://app.example.com
  script:
    - kubectl set image deployment/app app=$DOCKER_IMAGE
  only:
    - main
  when: manual
```

---

## 7. CI/CD Pipelines

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Pipeline Design | 🟢 Core | Stages, gates, parallel execution |
| Build Automation | 🟢 Core | Compile, test, package, publish |
| Artifact Management | 🟡 Important | Nexus, Artifactory, GitHub Packages |
| Blue/Green Deployments | 🟡 Important | Zero-downtime deployments |
| Canary Releases | 🔵 Advanced | Progressive rollout with monitoring |
| Feature Flags | 🟡 Important | LaunchDarkly, Unleash, Flagsmith |
| Rollback Strategies | 🟢 Core | Automated and manual rollback |
| Pipeline Security | 🟡 Important | SAST, DAST, SCA, secrets scanning |

### Checklist

- `[ ]` CI/CD tool selected (GitHub Actions, GitLab CI, Jenkins, etc.)
- `[ ]` Pipeline stages defined (Build → Test → Scan → Deploy)
- `[ ]` Automated unit tests integrated
- `[ ]` Integration tests in pipeline
- `[ ]` Code quality gates configured (coverage thresholds, lint)
- `[ ]` Security scanning integrated (SAST, dependency scanning)
- `[ ]` Artifact versioning and storage configured
- `[ ]` Environment promotion strategy defined (dev → staging → prod)
- `[ ]` Deployment approval gates for production
- `[ ]` Rollback procedure documented and tested
- `[ ]` Pipeline notifications configured (Slack, email)
- `[ ]` Pipeline performance optimized (caching, parallelism)
- `[ ]` Feature flag system integrated
- `[ ]` Database migration strategy in pipeline

---

## 8. Jenkins

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Jenkinsfile (Declarative) | 🟢 Core | Pipeline as code |
| Jenkinsfile (Scripted) | 🟡 Important | Groovy-based flexible pipelines |
| Plugins Management | 🟢 Core | Install, configure, update plugins |
| Shared Libraries | 🟡 Important | Reusable pipeline code |
| Distributed Builds | 🟡 Important | Master/Agent architecture |
| Credentials Management | 🟢 Core | Secrets, tokens, SSH keys |
| Blue Ocean | 🟡 Important | Modern UI for pipeline visualization |
| Jenkins Configuration as Code (JCasC) | 🔵 Advanced | YAML-based Jenkins config |

### Checklist

- `[ ]` Jenkins server provisioned and secured (HTTPS, auth)
- `[ ]` Admin account configured with strong credentials
- `[ ]` Essential plugins installed (Git, Docker, Pipeline, Credentials)
- `[ ]` Jenkins agents configured (static or dynamic)
- `[ ]` Credentials stored securely in Jenkins Credential Store
- `[ ]` Multibranch pipeline configured
- `[ ]` Shared library repository set up
- `[ ]` Webhook triggers configured (GitHub/GitLab)
- `[ ]` Build retention policy configured (days/count)
- `[ ]` Backup strategy implemented (ThinBackup plugin or filesystem)
- `[ ]` Security matrix configured (role-based access)
- `[ ]` JCasC file created for reproducible setup

### Jenkinsfile — Declarative Template

```groovy
pipeline {
    agent any

    environment {
        DOCKER_REGISTRY = 'registry.example.com'
        APP_NAME = 'my-app'
    }

    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'npm ci'
                sh 'npm run build'
            }
        }

        stage('Test') {
            parallel {
                stage('Unit Tests') {
                    steps { sh 'npm test' }
                }
                stage('Lint') {
                    steps { sh 'npm run lint' }
                }
            }
        }

        stage('Docker Build') {
            steps {
                sh "docker build -t ${DOCKER_REGISTRY}/${APP_NAME}:${BUILD_NUMBER} ."
            }
        }

        stage('Deploy to Staging') {
            when { branch 'develop' }
            steps {
                sh "kubectl apply -f k8s/staging/"
            }
        }

        stage('Deploy to Production') {
            when { branch 'main' }
            input { message 'Deploy to production?' }
            steps {
                sh "kubectl apply -f k8s/production/"
            }
        }
    }

    post {
        success { slackSend(color: 'good', message: "✅ Build #${BUILD_NUMBER} succeeded") }
        failure { slackSend(color: 'danger', message: "❌ Build #${BUILD_NUMBER} failed") }
        always  { cleanWs() }
    }
}
```

---

## 9. Docker & Containers

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Dockerfile | 🟢 Core | Multi-stage builds, layer optimization |
| Docker Compose | 🟢 Core | Multi-container orchestration |
| Image Management | 🟢 Core | Build, tag, push, pull, prune |
| Volumes & Networking | 🟢 Core | Data persistence, container networking |
| Docker Security | 🟡 Important | Non-root, read-only, scanning |
| Registry Management | 🟡 Important | Docker Hub, ECR, GCR, ACR, Harbor |
| BuildKit & Buildx | 🟡 Important | Advanced build features, multi-arch |
| Container Runtime | 🔵 Advanced | containerd, CRI-O, Podman |

### Checklist

- `[ ]` Docker installed and configured
- `[ ]` Dockerfile created with multi-stage build
- `[ ]` `.dockerignore` file configured
- `[ ]` Base image pinned to specific version (not `latest`)
- `[ ]` Container runs as non-root user
- `[ ]` Health check defined in Dockerfile
- `[ ]` Image size optimized (< 200MB target for apps)
- `[ ]` Docker Compose file for local development
- `[ ]` Container registry configured and accessible
- `[ ]` Image scanning integrated (Trivy, Snyk, Scout)
- `[ ]` Secrets management (not baked into images)
- `[ ]` Container resource limits defined (CPU, memory)
- `[ ]` Logging driver configured
- `[ ]` Docker layer caching optimized in CI

### Dockerfile — Production Template

```dockerfile
# ── Build Stage ──────────────────────────────────
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production && \
    npm cache clean --force
COPY . .
RUN npm run build

# ── Production Stage ─────────────────────────────
FROM node:20-alpine AS production
LABEL maintainer="team@example.com"
LABEL version="1.0.0"

RUN addgroup -g 1001 appgroup && \
    adduser -u 1001 -G appgroup -s /bin/sh -D appuser

WORKDIR /app
COPY --from=builder --chown=appuser:appgroup /app/dist ./dist
COPY --from=builder --chown=appuser:appgroup /app/node_modules ./node_modules
COPY --from=builder --chown=appuser:appgroup /app/package.json ./

USER appuser
EXPOSE 3000

HEALTHCHECK --interval=30s --timeout=5s --start-period=10s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://localhost:3000/health || exit 1

CMD ["node", "dist/main.js"]
```

### Docker Compose — Development Template

```yaml
version: '3.9'

services:
  app:
    build:
      context: .
      dockerfile: Dockerfile
      target: builder
    ports:
      - "3000:3000"
    volumes:
      - ./src:/app/src
      - /app/node_modules
    environment:
      - NODE_ENV=development
      - DATABASE_URL=postgresql://postgres:password@db:5432/mydb
      - REDIS_URL=redis://redis:6379
    depends_on:
      db:
        condition: service_healthy
      redis:
        condition: service_started
    networks:
      - app-network

  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: mydb
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./init.sql:/docker-entrypoint-initdb.d/init.sql
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U postgres"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - app-network

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data
    networks:
      - app-network

volumes:
  postgres_data:
  redis_data:

networks:
  app-network:
    driver: bridge
```

---

## 10. Kubernetes & Orchestration

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Pods, Deployments, Services | 🟢 Core | Core workload resources |
| ConfigMaps & Secrets | 🟢 Core | Configuration management |
| Ingress & Load Balancing | 🟢 Core | Traffic routing, TLS termination |
| Namespaces & RBAC | 🟢 Core | Multi-tenancy, access control |
| Helm Charts | 🟡 Important | Package management for K8s |
| HPA & VPA | 🟡 Important | Horizontal/Vertical Pod Autoscaling |
| StatefulSets | 🟡 Important | Stateful workloads (databases) |
| Operators & CRDs | 🔵 Advanced | Custom resource definitions |
| Service Mesh (Istio) | 🔵 Advanced | Traffic management, mTLS |
| GitOps (ArgoCD/Flux) | 🔵 Advanced | Declarative continuous delivery |
| Network Policies | 🟡 Important | Pod-to-pod traffic control |
| Pod Security Standards | 🟡 Important | Restricted, Baseline, Privileged |

### Checklist

- `[ ]` Kubernetes cluster provisioned (EKS, GKE, AKS, or self-managed)
- `[ ]` `kubectl` configured and cluster access verified
- `[ ]` Namespace strategy defined (per-env, per-team, per-app)
- `[ ]` RBAC policies configured (least privilege)
- `[ ]` Deployment manifests created with resource requests/limits
- `[ ]` Liveness and readiness probes configured
- `[ ]` ConfigMaps created for app configuration
- `[ ]` Secrets management strategy (Sealed Secrets, Vault, External Secrets)
- `[ ]` Ingress controller installed (NGINX, Traefik, etc.)
- `[ ]` TLS certificates configured (cert-manager + Let's Encrypt)
- `[ ]` HPA configured for auto-scaling
- `[ ]` PodDisruptionBudget configured for availability
- `[ ]` Network policies defined for pod isolation
- `[ ]` Pod Security Standards enforced
- `[ ]` Helm charts created for application packaging
- `[ ]` GitOps tool configured (ArgoCD or Flux)
- `[ ]` Monitoring stack deployed (Prometheus + Grafana)
- `[ ]` Log aggregation configured (EFK/Loki stack)
- `[ ]` Backup strategy for etcd and PVs
- `[ ]` Disaster recovery plan documented

### Kubernetes Deployment Template

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: my-app
  namespace: production
  labels:
    app: my-app
    version: v1.0.0
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
        version: v1.0.0
    spec:
      serviceAccountName: my-app-sa
      securityContext:
        runAsNonRoot: true
        runAsUser: 1001
        fsGroup: 1001
      containers:
        - name: my-app
          image: registry.example.com/my-app:v1.0.0
          ports:
            - containerPort: 3000
              protocol: TCP
          resources:
            requests:
              cpu: 250m
              memory: 256Mi
            limits:
              cpu: 500m
              memory: 512Mi
          livenessProbe:
            httpGet:
              path: /health
              port: 3000
            initialDelaySeconds: 15
            periodSeconds: 20
            failureThreshold: 3
          readinessProbe:
            httpGet:
              path: /ready
              port: 3000
            initialDelaySeconds: 5
            periodSeconds: 10
          envFrom:
            - configMapRef:
                name: my-app-config
            - secretRef:
                name: my-app-secrets
          volumeMounts:
            - name: tmp
              mountPath: /tmp
      volumes:
        - name: tmp
          emptyDir: {}
      topologySpreadConstraints:
        - maxSkew: 1
          topologyKey: topology.kubernetes.io/zone
          whenUnsatisfiable: DoNotSchedule
          labelSelector:
            matchLabels:
              app: my-app
---
apiVersion: v1
kind: Service
metadata:
  name: my-app
  namespace: production
spec:
  type: ClusterIP
  selector:
    app: my-app
  ports:
    - port: 80
      targetPort: 3000
      protocol: TCP
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: my-app
  namespace: production
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: my-app
  minReplicas: 3
  maxReplicas: 10
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
    - type: Resource
      resource:
        name: memory
        target:
          type: Utilization
          averageUtilization: 80
```

---

## 11. Terraform (Infrastructure as Code)

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| HCL Syntax | 🟢 Core | Resources, variables, outputs, locals |
| State Management | 🟢 Core | Remote backend, locking, state operations |
| Modules | 🟢 Core | Reusable, composable infrastructure blocks |
| Providers | 🟢 Core | AWS, GCP, Azure, Kubernetes providers |
| Workspaces | 🟡 Important | Environment isolation (dev/staging/prod) |
| Terragrunt | 🟡 Important | DRY Terraform, multi-environment |
| Import & Migration | 🟡 Important | Importing existing infrastructure |
| Sentinel / OPA | 🔵 Advanced | Policy as code |
| Testing (Terratest) | 🔵 Advanced | Automated infrastructure testing |

### Checklist

- `[ ]` Terraform installed and version pinned
- `[ ]` Remote state backend configured (S3, GCS, Azure Blob)
- `[ ]` State locking enabled (DynamoDB, Cloud Storage)
- `[ ]` Provider versions pinned in `required_providers`
- `[ ]` Module structure defined (root + child modules)
- `[ ]` Variables properly typed with descriptions and defaults
- `[ ]` Sensitive variables marked as `sensitive = true`
- `[ ]` Output values defined for cross-module references
- `[ ]` Environment separation strategy (workspaces or separate dirs)
- `[ ]` `.tfvars` files per environment
- `[ ]` `terraform fmt` and `terraform validate` in CI
- `[ ]` `tflint` integrated for best practices
- `[ ]` Cost estimation integrated (Infracost)
- `[ ]` Plan review required before apply
- `[ ]` Drift detection scheduled

### Terraform Project Structure

```
terraform/
├── modules/
│   ├── networking/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   ├── compute/
│   │   ├── main.tf
│   │   ├── variables.tf
│   │   └── outputs.tf
│   └── database/
│       ├── main.tf
│       ├── variables.tf
│       └── outputs.tf
├── environments/
│   ├── dev/
│   │   ├── main.tf
│   │   ├── backend.tf
│   │   ├── variables.tf
│   │   └── terraform.tfvars
│   ├── staging/
│   │   └── ...
│   └── production/
│       └── ...
├── .terraform.lock.hcl
└── README.md
```

### Terraform — Main Module Template

```hcl
terraform {
  required_version = ">= 1.5.0"

  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }

  backend "s3" {
    bucket         = "my-terraform-state"
    key            = "production/terraform.tfstate"
    region         = "us-east-1"
    dynamodb_table = "terraform-locks"
    encrypt        = true
  }
}

provider "aws" {
  region = var.aws_region

  default_tags {
    tags = {
      Environment = var.environment
      ManagedBy   = "terraform"
      Project     = var.project_name
    }
  }
}

module "networking" {
  source      = "../../modules/networking"
  environment = var.environment
  vpc_cidr    = var.vpc_cidr
}

module "compute" {
  source        = "../../modules/compute"
  environment   = var.environment
  vpc_id        = module.networking.vpc_id
  subnet_ids    = module.networking.private_subnet_ids
  instance_type = var.instance_type
}

module "database" {
  source       = "../../modules/database"
  environment  = var.environment
  vpc_id       = module.networking.vpc_id
  subnet_ids   = module.networking.database_subnet_ids
  db_engine    = "postgres"
  db_version   = "16"
}
```

---

## 12. Ansible (Configuration Management)

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Playbooks | 🟢 Core | Tasks, handlers, templates, vars |
| Inventory Management | 🟢 Core | Static, dynamic, groups, host_vars |
| Roles | 🟢 Core | Reusable, shareable role structure |
| Ansible Galaxy | 🟡 Important | Community roles and collections |
| Ansible Vault | 🟢 Core | Encrypted secrets management |
| Jinja2 Templates | 🟡 Important | Dynamic configuration files |
| Ansible Tower / AWX | 🔵 Advanced | Enterprise automation platform |
| Molecule | 🔵 Advanced | Role testing framework |

### Checklist

- `[ ]` Ansible installed with version pinned
- `[ ]` Inventory file organized (static or dynamic)
- `[ ]` SSH key-based authentication configured
- `[ ]` Ansible configuration file (`ansible.cfg`) customized
- `[ ]` Role structure created using `ansible-galaxy init`
- `[ ]` Variables organized (group_vars, host_vars)
- `[ ]` Sensitive data encrypted with Ansible Vault
- `[ ]` Idempotency verified for all playbooks
- `[ ]` Handlers used for service restarts
- `[ ]` Tags defined for selective execution
- `[ ]` Molecule tests created for roles
- `[ ]` Lint checks with `ansible-lint` in CI

### Ansible Playbook — Server Setup Template

```yaml
---
- name: Configure Application Server
  hosts: app_servers
  become: true
  vars_files:
    - vars/common.yml
    - vars/{{ env }}.yml

  roles:
    - role: common
      tags: [common]
    - role: security
      tags: [security]
    - role: docker
      tags: [docker]
    - role: app
      tags: [app]

  tasks:
    - name: Ensure required packages are installed
      ansible.builtin.apt:
        name:
          - curl
          - wget
          - htop
          - vim
          - net-tools
          - unzip
        state: present
        update_cache: true

    - name: Configure firewall rules
      ansible.builtin.ufw:
        rule: allow
        port: "{{ item }}"
        proto: tcp
      loop:
        - '22'
        - '80'
        - '443'
      notify: reload firewall

    - name: Deploy application config
      ansible.builtin.template:
        src: templates/app.conf.j2
        dest: /etc/myapp/app.conf
        owner: appuser
        group: appgroup
        mode: '0640'
      notify: restart application

  handlers:
    - name: reload firewall
      ansible.builtin.ufw:
        state: reloaded

    - name: restart application
      ansible.builtin.systemd:
        name: myapp
        state: restarted
        daemon_reload: true
```

---

## 13. Servers & Deployment

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Linux Administration | 🟢 Core | systemd, cron, users, permissions |
| Nginx / Apache | 🟢 Core | Reverse proxy, load balancing, TLS |
| SSH Management | 🟢 Core | Key management, tunneling, hardening |
| Process Management | 🟡 Important | systemd, PM2, supervisord |
| SSL/TLS Certificates | 🟢 Core | Let's Encrypt, cert rotation |
| Deployment Strategies | 🟢 Core | Rolling, Blue/Green, Canary |
| Server Hardening | 🟡 Important | CIS benchmarks, fail2ban, firewall |
| CDN Configuration | 🟡 Important | CloudFront, Cloudflare, Fastly |

### Checklist

- `[ ]` Server OS hardened (CIS benchmark applied)
- `[ ]` SSH hardened (key-only auth, no root login, non-standard port)
- `[ ]` Firewall configured (UFW/iptables — allow only required ports)
- `[ ]` fail2ban installed and configured
- `[ ]` Automatic security updates enabled (unattended-upgrades)
- `[ ]` Nginx/Apache configured as reverse proxy
- `[ ]` TLS certificates installed and auto-renewal configured
- `[ ]` Application deployed with process manager (PM2/systemd)
- `[ ]` Log rotation configured (logrotate)
- `[ ]` Monitoring agent installed (node_exporter, Datadog, etc.)
- `[ ]` Backup cron jobs configured
- `[ ]` Deployment script or pipeline tested
- `[ ]` Rollback procedure tested
- `[ ]` DNS records configured (A, CNAME, MX, TXT)
- `[ ]` CDN configured for static assets

### Nginx — Reverse Proxy Template

```nginx
upstream app_backend {
    least_conn;
    server 127.0.0.1:3000 weight=5;
    server 127.0.0.1:3001 weight=3;
    keepalive 32;
}

server {
    listen 80;
    server_name app.example.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    server_name app.example.com;

    ssl_certificate     /etc/letsencrypt/live/app.example.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/app.example.com/privkey.pem;

    ssl_protocols TLSv1.2 TLSv1.3;
    ssl_ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256;
    ssl_prefer_server_ciphers off;

    # Security Headers
    add_header Strict-Transport-Security "max-age=63072000; includeSubDomains; preload" always;
    add_header X-Content-Type-Options "nosniff" always;
    add_header X-Frame-Options "SAMEORIGIN" always;
    add_header X-XSS-Protection "1; mode=block" always;
    add_header Referrer-Policy "strict-origin-when-cross-origin" always;

    # Gzip
    gzip on;
    gzip_types text/plain application/json application/javascript text/css;
    gzip_min_length 1024;

    location / {
        proxy_pass http://app_backend;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_read_timeout 90s;
        proxy_buffering off;
    }

    location /static/ {
        alias /var/www/app/static/;
        expires 1y;
        add_header Cache-Control "public, immutable";
    }

    location /health {
        access_log off;
        return 200 'OK';
        add_header Content-Type text/plain;
    }
}
```

---

## 14. Database Management

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| PostgreSQL | 🟢 Core | Queries, indexing, partitioning, replication |
| MySQL / MariaDB | 🟢 Core | InnoDB, replication, optimization |
| MongoDB | 🟡 Important | Document model, aggregation, sharding |
| Redis | 🟢 Core | Caching, pub/sub, data structures |
| Database Migrations | 🟢 Core | Flyway, Liquibase, Prisma, Alembic |
| Backup & Recovery | 🟢 Core | pg_dump, mysqldump, PITR |
| Connection Pooling | 🟡 Important | PgBouncer, ProxySQL |
| Query Optimization | 🟡 Important | EXPLAIN, indexing strategies |
| Database HA | 🔵 Advanced | Primary-replica, failover, clustering |

### Checklist

- `[ ]` Database engine selected and version pinned
- `[ ]` Database provisioned (managed service or self-hosted)
- `[ ]` Connection pooling configured (PgBouncer, HikariCP)
- `[ ]` Database user accounts created with least privilege
- `[ ]` Schema versioning tool configured (migrations)
- `[ ]` Initial migration created and tested
- `[ ]` Indexes defined for frequent query patterns
- `[ ]` Automated backup schedule configured
- `[ ]` Backup restoration tested successfully
- `[ ]` Point-in-time recovery (PITR) enabled
- `[ ]` Connection string stored securely (secrets manager)
- `[ ]` Monitoring configured (slow queries, connections, disk)
- `[ ]` Query performance baseline established
- `[ ]` Read replicas configured (if needed)
- `[ ]` Data retention / archival policy defined
- `[ ]` Encryption at rest enabled
- `[ ]` Encryption in transit (TLS) configured

### Database Backup Script Template

```bash
#!/bin/bash
set -euo pipefail

# ── Configuration ──────────────────────────────
DB_HOST="${DB_HOST:-localhost}"
DB_PORT="${DB_PORT:-5432}"
DB_NAME="${DB_NAME:-mydb}"
DB_USER="${DB_USER:-postgres}"
BACKUP_DIR="/backups/postgresql"
RETENTION_DAYS=30
TIMESTAMP=$(date +%Y%m%d_%H%M%S)
BACKUP_FILE="${BACKUP_DIR}/${DB_NAME}_${TIMESTAMP}.sql.gz"

# ── Create backup directory ───────────────────
mkdir -p "${BACKUP_DIR}"

# ── Perform backup ────────────────────────────
echo "[$(date)] Starting backup of ${DB_NAME}..."
pg_dump \
    -h "${DB_HOST}" \
    -p "${DB_PORT}" \
    -U "${DB_USER}" \
    -d "${DB_NAME}" \
    --format=custom \
    --compress=9 \
    --verbose \
    --file="${BACKUP_FILE}"

# ── Verify backup ─────────────────────────────
if [ -f "${BACKUP_FILE}" ]; then
    SIZE=$(du -h "${BACKUP_FILE}" | cut -f1)
    echo "[$(date)] ✅ Backup completed: ${BACKUP_FILE} (${SIZE})"
else
    echo "[$(date)] ❌ Backup FAILED!" >&2
    exit 1
fi

# ── Cleanup old backups ───────────────────────
find "${BACKUP_DIR}" -name "*.sql.gz" -mtime +${RETENTION_DAYS} -delete
echo "[$(date)] Cleaned up backups older than ${RETENTION_DAYS} days"
```

---

## 15. Prometheus (Monitoring)

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| PromQL | 🟢 Core | Queries, aggregations, functions |
| Scrape Configuration | 🟢 Core | Targets, labels, relabeling |
| Alert Rules | 🟢 Core | Alert definitions, severity, routing |
| Alertmanager | 🟢 Core | Routing, grouping, silencing, receivers |
| Exporters | 🟡 Important | Node, Blackbox, custom exporters |
| Service Discovery | 🟡 Important | K8s, Consul, EC2, file-based |
| Recording Rules | 🟡 Important | Pre-compute expensive queries |
| Thanos / Cortex | 🔵 Advanced | Long-term storage, HA |

### Checklist

- `[ ]` Prometheus server deployed (standalone or Kubernetes Operator)
- `[ ]` Persistent storage configured for metrics
- `[ ]` Retention period defined (15d, 30d, 90d)
- `[ ]` Scrape targets configured for all services
- `[ ]` Node Exporter deployed on all servers
- `[ ]` Service discovery configured (K8s SD, file SD)
- `[ ]` Recording rules created for frequently used queries
- `[ ]` Alert rules defined for critical metrics
- `[ ]` Alertmanager configured with notification channels
- `[ ]` Alert routing and grouping configured
- `[ ]` Silence and inhibition rules defined
- `[ ]` Grafana data source configured for Prometheus
- `[ ]` Custom application metrics instrumented

### Prometheus Config Template

```yaml
global:
  scrape_interval: 15s
  evaluation_interval: 15s
  scrape_timeout: 10s

rule_files:
  - /etc/prometheus/rules/*.yml

alerting:
  alertmanagers:
    - static_configs:
        - targets: ['alertmanager:9093']

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']

  - job_name: 'node-exporter'
    static_configs:
      - targets: ['node-exporter:9100']

  - job_name: 'application'
    metrics_path: /metrics
    static_configs:
      - targets: ['app:3000']
        labels:
          environment: production

  - job_name: 'kubernetes-pods'
    kubernetes_sd_configs:
      - role: pod
    relabel_configs:
      - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_scrape]
        action: keep
        regex: true
      - source_labels: [__meta_kubernetes_pod_annotation_prometheus_io_path]
        action: replace
        target_label: __metrics_path__
        regex: (.+)
```

### Essential Alert Rules

```yaml
groups:
  - name: infrastructure
    rules:
      - alert: HighCPUUsage
        expr: 100 - (avg by(instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100) > 85
        for: 5m
        labels:
          severity: warning
        annotations:
          summary: "High CPU usage on {{ $labels.instance }}"
          description: "CPU usage is above 85% for 5 minutes (current: {{ $value }}%)"

      - alert: HighMemoryUsage
        expr: (1 - node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100 > 90
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "High memory usage on {{ $labels.instance }}"

      - alert: DiskSpaceRunningLow
        expr: (node_filesystem_avail_bytes{fstype!="tmpfs"} / node_filesystem_size_bytes) * 100 < 15
        for: 10m
        labels:
          severity: warning
        annotations:
          summary: "Disk space below 15% on {{ $labels.instance }}"

  - name: application
    rules:
      - alert: HighErrorRate
        expr: rate(http_requests_total{status=~"5.."}[5m]) / rate(http_requests_total[5m]) > 0.05
        for: 5m
        labels:
          severity: critical
        annotations:
          summary: "Error rate above 5% on {{ $labels.job }}"

      - alert: HighLatency
        expr: histogram_quantile(0.95, rate(http_request_duration_seconds_bucket[5m])) > 1
        for: 10m
        labels:
          severity: warning
        annotations:
          summary: "P95 latency above 1s on {{ $labels.job }}"

      - alert: ServiceDown
        expr: up == 0
        for: 2m
        labels:
          severity: critical
        annotations:
          summary: "{{ $labels.job }} is down"
```

---

## 16. Grafana (Observability)

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| Dashboard Design | 🟢 Core | Panels, variables, annotations |
| Data Sources | 🟢 Core | Prometheus, Loki, Elasticsearch, etc. |
| Alerting | 🟡 Important | Alert rules, contact points, policies |
| Provisioning | 🟡 Important | Dashboards and datasources as code |
| Grafana Loki | 🟡 Important | Log aggregation and querying |
| Grafana Tempo | 🔵 Advanced | Distributed tracing |
| Grafana OnCall | 🔵 Advanced | Incident management |

### Checklist

- `[ ]` Grafana deployed and accessible (HTTPS)
- `[ ]` Authentication configured (LDAP, OAuth, SSO)
- `[ ]` Data sources connected (Prometheus, Loki, etc.)
- `[ ]` Organization and team structure set up
- `[ ]` Folder structure for dashboards defined
- `[ ]` Infrastructure dashboard created (CPU, Memory, Disk, Network)
- `[ ]` Application dashboard created (RPS, Latency, Error Rate)
- `[ ]` Business metrics dashboard created (KPIs)
- `[ ]` Alert rules configured in Grafana
- `[ ]` Notification channels configured (Slack, PagerDuty, Email)
- `[ ]` Dashboard provisioning via JSON/YAML (GitOps)
- `[ ]` Dashboard variables for environment/service filtering
- `[ ]` Annotations for deployments and incidents

### Key Dashboard Panels (RED Method)

| Panel | PromQL | Description |
|-------|--------|-------------|
| **Request Rate** | `sum(rate(http_requests_total[5m]))` | Requests per second |
| **Error Rate** | `sum(rate(http_requests_total{status=~"5.."}[5m])) / sum(rate(http_requests_total[5m]))` | % of 5xx errors |
| **Duration (P50)** | `histogram_quantile(0.50, sum(rate(http_request_duration_seconds_bucket[5m])) by (le))` | Median latency |
| **Duration (P95)** | `histogram_quantile(0.95, sum(rate(http_request_duration_seconds_bucket[5m])) by (le))` | 95th percentile |
| **Duration (P99)** | `histogram_quantile(0.99, sum(rate(http_request_duration_seconds_bucket[5m])) by (le))` | 99th percentile |
| **CPU Usage** | `100 - (avg(rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)` | Server CPU % |
| **Memory Usage** | `(1 - node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes) * 100` | Server memory % |

---

## 17. Security & Compliance (DevSecOps)

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| SAST (Static Analysis) | 🟢 Core | SonarQube, CodeQL, Semgrep |
| DAST (Dynamic Analysis) | 🟡 Important | OWASP ZAP, Burp Suite |
| SCA (Dependency Scanning) | 🟢 Core | Snyk, Dependabot, Trivy |
| Secrets Management | 🟢 Core | Vault, AWS Secrets Manager, SOPS |
| Container Scanning | 🟡 Important | Trivy, Anchore, Snyk Container |
| OWASP Top 10 | 🟢 Core | Common web vulnerabilities |
| Compliance Frameworks | 🔵 Advanced | SOC2, HIPAA, GDPR, PCI-DSS |
| Zero Trust Architecture | 🔵 Advanced | Identity-centric security model |

### Checklist

- `[ ]` Secrets scanning in CI pipeline (gitleaks, trufflehog)
- `[ ]` No secrets in source code (verified)
- `[ ]` SAST tool integrated and passing
- `[ ]` Dependency vulnerability scanning enabled
- `[ ]` Container image scanning enabled
- `[ ]` OWASP Top 10 mitigations verified
- `[ ]` Authentication & authorization implemented properly
- `[ ]` Input validation on all user inputs
- `[ ]` HTTPS enforced everywhere
- `[ ]` Security headers configured (CSP, HSTS, X-Frame-Options)
- `[ ]` Rate limiting and DDoS protection enabled
- `[ ]` Audit logging enabled for sensitive operations
- `[ ]` Secrets rotation policy defined and automated
- `[ ]` Penetration testing scheduled
- `[ ]` Incident response plan documented
- `[ ]` Data encryption at rest and in transit

---

## 18. Cloud Platforms

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| AWS (EC2, S3, RDS, Lambda, EKS) | 🟢 Core | Market leader, broadest services |
| GCP (GKE, Cloud Run, BigQuery) | 🟡 Important | Strong K8s and data analytics |
| Azure (AKS, App Service, DevOps) | 🟡 Important | Enterprise, .NET ecosystem |
| Cost Management | 🟢 Core | Budgets, alerts, right-sizing |
| IAM Best Practices | 🟢 Core | Least privilege, service accounts |
| Multi-Cloud Strategy | 🔵 Advanced | Portability, vendor lock-in mitigation |

### Checklist

- `[ ]` Cloud provider selected with justification
- `[ ]` Account/project structure defined (org, folders, projects)
- `[ ]` IAM roles and policies configured (least privilege)
- `[ ]` Service accounts created for applications
- `[ ]` VPC/network architecture designed
- `[ ]` Budget alerts configured
- `[ ]` Cost optimization review scheduled monthly
- `[ ]` Resource tagging policy enforced
- `[ ]` Multi-region strategy defined (if needed)
- `[ ]` Cloud-native services evaluated vs. self-managed

---

## 19. Networking & DNS

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| TCP/IP, HTTP/HTTPS | 🟢 Core | Protocol fundamentals |
| DNS Management | 🟢 Core | Records (A, CNAME, MX, TXT, SRV) |
| Load Balancing | 🟢 Core | L4/L7, algorithms, health checks |
| VPN & Tunneling | 🟡 Important | Site-to-site, client VPN, WireGuard |
| Firewall Rules | 🟢 Core | Inbound/outbound, security groups |
| Service Mesh | 🔵 Advanced | Istio, Linkerd, Consul Connect |

### Checklist

- `[ ]` DNS provider selected and configured
- `[ ]` Domain registered and NS records pointing correctly
- `[ ]` SSL/TLS certificates provisioned (auto-renewal)
- `[ ]` Load balancer configured with health checks
- `[ ]` Firewall rules follow least-access principle
- `[ ]` Private networking configured (VPC, subnets)
- `[ ]` CDN configured for static content
- `[ ]` Network monitoring enabled (latency, packet loss)

---

## 20. Logging & Tracing

### Skills

| Skill | Level | Description |
|-------|-------|-------------|
| ELK/EFK Stack | 🟡 Important | Elasticsearch, Logstash/Fluentd, Kibana |
| Grafana Loki | 🟡 Important | Lightweight log aggregation |
| Structured Logging | 🟢 Core | JSON logs, correlation IDs |
| Distributed Tracing | 🟡 Important | Jaeger, Zipkin, OpenTelemetry |
| OpenTelemetry | 🟡 Important | Unified observability (logs, metrics, traces) |
| Log Retention Policies | 🟢 Core | Compliance, cost, archive |

### Checklist

- `[ ]` Structured logging implemented (JSON format)
- `[ ]` Log levels used correctly (DEBUG, INFO, WARN, ERROR)
- `[ ]` Correlation / Request IDs propagated across services
- `[ ]` Log aggregation system deployed (Loki, ELK, CloudWatch)
- `[ ]` Log retention policy defined
- `[ ]` Sensitive data scrubbed from logs (PII, secrets)
- `[ ]` Distributed tracing enabled (OpenTelemetry)
- `[ ]` Error tracking integrated (Sentry, Rollbar)
- `[ ]` Log-based alerts configured for critical errors
- `[ ]` Dashboard for log analysis created

---

## 21. ✅ Project Readiness Master Checklist

> Use this as a final checklist before launching any project.

### Phase 1: Foundation

- `[ ]` Repository created with README, CONTRIBUTING, LICENSE
- `[ ]` Git branching strategy documented
- `[ ]` Jira/project board configured with backlog
- `[ ]` Agile ceremonies scheduled
- `[ ]` Architecture Decision Records (ADRs) started
- `[ ]` Tech stack documented and approved

### Phase 2: Development Environment

- `[ ]` Docker Compose for local development
- `[ ]` Pre-commit hooks installed (lint, format, secrets)
- `[ ]` IDE configuration shared (`.editorconfig`, extensions)
- `[ ]` Environment variables documented (`.env.example`)
- `[ ]` Database migrations working locally
- `[ ]` API documentation auto-generated

### Phase 3: CI/CD Pipeline

- `[ ]` CI pipeline: build, lint, test, security scan
- `[ ]` CD pipeline: deploy to staging automatically
- `[ ]` Production deployment requires manual approval
- `[ ]` Rollback procedure documented and tested
- `[ ]` Pipeline notifications configured (Slack/Teams)
- `[ ]` Artifact versioning with SemVer

### Phase 4: Infrastructure

- `[ ]` Infrastructure as Code (Terraform) created
- `[ ]` Environments provisioned (dev, staging, production)
- `[ ]` Kubernetes manifests / Helm charts ready
- `[ ]` Secrets stored in vault / secrets manager
- `[ ]` TLS certificates auto-renewing
- `[ ]` DNS records configured
- `[ ]` CDN and caching configured

### Phase 5: Database

- `[ ]` Database provisioned with HA
- `[ ]` Schema migrations versioned and tested
- `[ ]` Backup automation configured
- `[ ]` Backup restore tested successfully
- `[ ]` Connection pooling configured
- `[ ]` Monitoring for slow queries enabled

### Phase 6: Observability

- `[ ]` Prometheus metrics collection active
- `[ ]` Grafana dashboards created (infra + app)
- `[ ]` Alert rules defined with escalation paths
- `[ ]` Log aggregation configured (Loki/ELK)
- `[ ]` Distributed tracing enabled
- `[ ]` On-call rotation established

### Phase 7: Security

- `[ ]` SAST + DAST scanning in pipeline
- `[ ]` Dependency vulnerability scanning active
- `[ ]` Container image scanning active
- `[ ]` Secrets rotation policy in place
- `[ ]` OWASP Top 10 addressed
- `[ ]` Incident response plan documented
- `[ ]` Security headers configured

### Phase 8: Documentation

- `[ ]` Architecture diagram (C4 model or similar)
- `[ ]` API documentation (OpenAPI/Swagger)
- `[ ]` Runbook for common operations
- `[ ]` Disaster recovery plan
- `[ ]` Onboarding guide for new developers
- `[ ]` Incident response playbook

### Phase 9: Go-Live

- `[ ]` Load testing completed
- `[ ]` Chaos engineering tests passed
- `[ ]` Penetration testing completed
- `[ ]` Performance baseline established
- `[ ]` SLOs/SLAs defined (availability, latency)
- `[ ]` Error budgets defined
- `[ ]` Go/No-Go review completed
- `[ ]` Stakeholders notified

---

## 📊 Skill Proficiency Legend

| Icon | Level | Meaning |
|------|-------|---------|
| 🟢 | Core | Must-have — required for every project |
| 🟡 | Important | Should-have — needed for production systems |
| 🔵 | Advanced | Nice-to-have — for complex/enterprise systems |

---

## 🔖 Quick Reference Commands

### Docker

```bash
docker build -t myapp:v1 .                   # Build image
docker run -d -p 3000:3000 myapp:v1           # Run container
docker compose up -d                          # Start all services
docker system prune -af                       # Clean up everything
docker scout cves myapp:v1                    # Scan for vulnerabilities
```

### Kubernetes

```bash
kubectl get pods -A                           # All pods, all namespaces
kubectl describe pod <pod-name>               # Pod details
kubectl logs -f <pod-name>                    # Stream logs
kubectl rollout status deployment/myapp       # Deployment status
kubectl rollout undo deployment/myapp         # Rollback
kubectl top pods                              # Resource usage
```

### Terraform

```bash
terraform init                                # Initialize
terraform plan -out=plan.tfplan               # Preview changes
terraform apply plan.tfplan                   # Apply changes
terraform destroy                             # Tear down
terraform state list                          # List managed resources
terraform import aws_instance.web i-12345     # Import existing
```

### Ansible

```bash
ansible-playbook -i inventory site.yml        # Run playbook
ansible-playbook site.yml --check --diff      # Dry run
ansible-vault encrypt secrets.yml             # Encrypt file
ansible all -m ping                           # Test connectivity
```

### Prometheus / Grafana

```bash
# Test PromQL in CLI
curl 'http://prometheus:9090/api/v1/query?query=up'

# Check targets
curl 'http://prometheus:9090/api/v1/targets'

# Grafana API — export dashboard
curl -H "Authorization: Bearer $TOKEN" \
  http://grafana:3000/api/dashboards/uid/my-dashboard
```
