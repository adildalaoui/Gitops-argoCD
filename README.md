# 🚀 Projet GitOps End-to-End sur AWS EKS avec Jenkins, SonarQube, Nexus et ArgoCD

## 📋 Présentation

Ce projet met en œuvre une plateforme DevOps complète basée sur les principes GitOps afin d'automatiser l'intégralité du cycle de vie d'une application conteneurisée déployée sur Kubernetes. L'objectif principal était de concevoir une architecture moderne, scalable et sécurisée permettant d'automatiser l'infrastructure, l'intégration continue, les contrôles qualité, la gestion des artefacts et le déploiement continu sur AWS EKS.

---

## 🎯 Objectifs

- Automatiser le provisionnement de l'infrastructure avec Terraform.
- Déployer un cluster Kubernetes managé sur AWS EKS.
- Mettre en place une chaîne CI/CD complète avec Jenkins.
- Intégrer des contrôles qualité et sécurité dans le pipeline.
- Gérer les artefacts Maven avec Nexus Repository.
- Construire et publier des images Docker automatiquement.
- Implémenter une approche GitOps avec ArgoCD.
- Assurer le déploiement automatique des applications sur Kubernetes.
- Garantir la traçabilité, la reproductibilité et la fiabilité des déploiements.

---

## 🏗️ Architecture

```text
Developer
    │
    ▼
GitHub (Repository CI)
    │
    ▼
Jenkins Pipeline
    │
    ├── Maven Build
    ├── Unit Tests
    ├── SonarQube Analysis
    ├── Trivy Security Scan
    ├── Nexus Artifact Publishing
    └── Docker Build & Push
                │
                ▼
GitHub (Repository CD)
                │
                ▼
ArgoCD
                │
                ▼
AWS EKS Cluster
                │
                ▼
Application Kubernetes
```

---

## 🛠️ Stack Technique

### Cloud & Infrastructure
- AWS EC2
- AWS EKS
- AWS IAM
- AWS Load Balancer
- Terraform
- EKSCTL

### CI/CD
- Jenkins
  

### Conteneurisation & Orchestration
- Docker
- Kubernetes
- Amazon EKS

### GitOps
- ArgoCD

### Qualité & Sécurité
- SonarQube
- Trivy

### Gestion des Artefacts
- Nexus Repository

### Système
- Linux Ubuntu

### DNS
- Hostinger

---

## ⚙️ Réalisations

### Provisionnement de l'infrastructure

- Création d'une machine EC2 d'administration.
- Installation et configuration de Terraform, AWS CLI, Kubectl et EKSCTL.
- Provisionnement automatisé de l'infrastructure AWS.
- Création d'un cluster Amazon EKS.
- Configuration d'OpenID Connect (OIDC).
- Création d'un Managed Node Group avec Auto Scaling.

### Mise en place de la plateforme DevOps

Déploiement d'une machine dédiée hébergeant :

- Jenkins
- SonarQube
- Nexus Repository
- Docker Engine

### Sécurisation de Kubernetes

Mise en œuvre des bonnes pratiques Kubernetes :

- Service Accounts dédiés
- RBAC
- Roles et RoleBindings
- ClusterRoles
- Gestion sécurisée des accès Jenkins → Kubernetes

---

## 🔄 Pipeline CI/CD

Le pipeline Jenkins automatise l'intégralité du processus de livraison.

### Étapes automatisées

#### 1. Nettoyage de l'environnement

```bash
cleanWs()
```

#### 2. Récupération du code source

```bash
git checkout
```

#### 3. Compilation

```bash
mvn compile
```

#### 4. Exécution des tests unitaires

```bash
mvn test
```

#### 5. Analyse de sécurité

```bash
trivy fs .
```

Analyse des vulnérabilités et dépendances du projet.

#### 6. Analyse de qualité du code

```text
SonarQube Analysis
```

Contrôle automatique du Quality Gate avant validation.

#### 7. Packaging de l'application

```bash
mvn package
```

#### 8. Publication des artefacts

```bash
mvn deploy
```

Publication automatique dans Nexus Repository.

#### 9. Construction de l'image Docker

```bash
docker build
```

#### 10. Publication de l'image Docker

```bash
docker push
```

#### 11. Déclenchement GitOps

Le pipeline :

- Clone le repository GitOps.
- Met à jour automatiquement le tag de l'image Docker dans les manifests Kubernetes.
- Commit et Push les modifications dans GitHub.

Cette modification devient alors la source de vérité pour le déploiement.

---

## 🚀 Déploiement GitOps avec ArgoCD

ArgoCD assure la synchronisation continue entre GitHub et Kubernetes.

### Fonctionnement

1. Surveillance permanente du repository GitOps.
2. Détection automatique des changements.
3. Synchronisation avec le cluster EKS.
4. Réconciliation automatique de l'état réel avec l'état désiré.

### Bénéfices

- Déploiement Pull-Based.
- Historique complet des changements via Git.
- Rollback simplifié.
- Sécurité renforcée.
- Suppression des accès directs Jenkins → Kubernetes.

---

## 📊 Qualité et Sécurité

### SonarQube

Analyse automatique :

- Bugs
- Vulnerabilités
- Code Smells
- Dette technique
- Couverture des tests

### Trivy

Détection des :

- Vulnérabilités système
- Dépendances vulnérables
- Risques de sécurité

---

## 🌐 Exposition de l'application

L'application est accessible via :

- AWS Load Balancer
- Kubernetes Services
- Nom de domaine personnalisé Hostinger

Flux réseau :

```text
Utilisateur
      │
      ▼
Nom de domaine
      │
      ▼
AWS Load Balancer
      │
      ▼
Ingress Kubernetes
      │
      ▼
Pods Applicatifs
```

---

## 📈 Compétences démontrées

### DevOps

- CI/CD
- GitOps
- Infrastructure as Code
- Automatisation
- Continuous Delivery

### Cloud

- AWS EKS
- EC2
- IAM
- Networking

### Kubernetes

- Cluster Administration
- RBAC
- Services
- Deployments
- Namespaces

### Sécurité

- Trivy
- SonarQube
- Gestion des Credentials
- Contrôle des accès

### Outils

- Jenkins
- ArgoCD
- Terraform
- Docker
- Nexus
- GitHub
- Linux

---

## ✅ Résultats

- Infrastructure AWS entièrement automatisée.
- Déploiement Kubernetes industrialisé.
- Pipeline CI/CD complet et sécurisé.
- Contrôles qualité et sécurité intégrés.
- Gestion centralisée des artefacts.
- Déploiement GitOps automatisé avec ArgoCD.
- Synchronisation continue entre GitHub et Kubernetes.
- Réduction des interventions manuelles.
- Déploiements fiables, reproductibles et traçables.

---

## 🎓 Ce que j'ai appris

Ce projet m'a permis d'approfondir les concepts avancés de GitOps, Kubernetes, AWS et CI/CD tout en mettant en œuvre une architecture proche des standards utilisés en environnement de production. J'ai acquis une expérience pratique dans l'automatisation complète du cycle de livraison logicielle, la sécurisation des pipelines DevOps et la gestion d'infrastructures Cloud Native à l'aide d'outils reconnus du marché.

---

## 👨‍💻 Auteur

**DALAOUI Adil**

DevOps Engineer | Cloud Engineer | Platform Engineer

**Compétences :** AWS • Kubernetes • Docker • Terraform • Jenkins • ArgoCD • GitOps • SonarQube • Nexus • Linux • CI/CD
