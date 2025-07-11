# 📦 Projeto Booking — API Test Automation

Este repositório contém a automação de testes da API do projeto **Booking** utilizando o **Postman** e o **Newman**, com integração ao **GitHub Actions** para execução automática dos testes.

## 🚀 Tecnologias Utilizadas
- [Postman](https://www.postman.com/) — Criação e execução de coleções de testes API.
- [Newman](https://www.npmjs.com/package/newman) — CLI para rodar coleções Postman.
- [GitHub Actions](https://docs.github.com/en/actions) — Pipeline de integração contínua (CI/CD).
- [Node.js](https://nodejs.org/) — Ambiente de execução para o Newman.

---

## 🔧 Estrutura do Repositório
```plaintext
📂 .github/workflows/
│ └── postman-tests.yml → Workflow GitHub Actions
📂 postman/
│ ├── API_Booking.postman_collection.json → Coleção de testes Postman
│ └── environment-dev.json → Ambiente de testes
📄 README.md → Documentação do projeto
```
---

## ⚙️ Como Funciona o Pipeline
O pipeline é executado automaticamente quando:
- Recebe um evento `repository_dispatch` (via integração com outros repositórios).
- Recebe um Pull Request.

### Etapas do Workflow:
1. Checkout do código;
2. Instalação do Node.js e do Newman;
3. Execução dos testes Postman;
4. Geração e upload do relatório de testes.

---

## 🔗 Integração com Outros Repositórios
Este repositório é configurado para ser acionado automaticamente por outros repositórios via **GitHub Repository Dispatch**.

> 💡 Exemplo: Integrado ao repositório [CI-CD-API](https://github.com/JonasSousa/CI-CD-API) para disparo automático de testes.

---

## 📝 Como Rodar Localmente
1. Instale o Newman:
```bash
npm install -g newman

newman run postman/API_Booking.postman_collection.json \
  --environment postman/environment-dev.json \
  --reporters cli,junit \
  --reporter-junit-export results.xml



