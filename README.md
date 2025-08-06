## ⚙️ CI/CD com GitHub Actions

Este projeto utiliza **GitHub Actions** para automatizar tarefas de integração contínua (CI), como instalação de dependências, build e testes automatizados.

### 📁 Local do workflow

O pipeline está configurado no arquivo:

.github/workflows/ci.yml
.github/workflows/cd.yaml


### 🚀 O que o pipeline faz?

Este pipeline é executado automaticamente **toda vez que um push ou pull request é feito para o branch `main`**. Ele realiza os seguintes passos:

1. **Clona o repositório**
2. **Configura o ambiente de um código simples com Go**
3. **Executa os testes**
4. **Build do projeto**
5. **Deploy do projeto**
