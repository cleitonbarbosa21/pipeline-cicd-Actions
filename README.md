## 🚀 CI/CD com GitHub Actions + Kubernetes na DigitalOcean

Este projeto utiliza uma pipeline de **CI/CD automatizada com GitHub Actions**, integrada a um **cluster Kubernetes hospedado na DigitalOcean.

📁 Estrutura do projeto
.
├── Dockerfile
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
└── .github/
    └── workflows/
        └── CI.yml
        └── CD.yaml

        
### 📦 O que está automatizado?

A cada **push no branch `main`**, o GitHub Actions executa as seguintes etapas:

1. **Build da imagem Docker**
2. **Push da imagem para o Docker Hub**
3. **Atualização automática da aplicação no cluster Kubernetes (DOKS)**

---

### ☁️ Cluster Kubernetes (DOKS)

- O cluster foi provisionado usando o [DigitalOcean Kubernetes Service (DOKS)](https://www.digitalocean.com/products/kubernetes)
- O acesso é feito via `kubectl` usando um **kubeconfig** armazenado com segurança no GitHub Secrets
- A aplicação é implantada com um **Deployment + Service** padrão do Kubernetes
- O cluster expõe a aplicação via LoadBalancer (ou Ingress Controller, se aplicável)

---

### 🔐 Secrets utilizados

Os seguintes segredos foram configurados no GitHub (`Settings > Secrets and variables > Actions`):

| Nome do Secret            | Descrição                                              |
|---------------------------|--------------------------------------------------------|
| `DOCKERHUB_USERNAME`      | Nome de usuário do Docker Hub                          |
| `DOCKERHUB_TOKEN`         | Token de acesso com permissão de push                  |
| `KUBE_CONFIG`             | Kubeconfig do cluster Kubernetes (DOKS)                |

---

### 🛠️ Ferramentas e Ações utilizadas

- `docker/login-action`: autenticação no Docker Hub
- `docker/build-push-action`: build e push da imagem Docker
- `azure/setup-kubectl`: instalação do `kubectl`
- `kubernetes/kubectl`: para aplicar arquivos YAML no cluster

---

