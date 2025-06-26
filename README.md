# Voting App - Kubernetes Architecture

Este projeto demonstra uma aplicação de votação em contêineres orquestrada com **Kubernetes**, composta por múltiplos pods e serviços.

## 🧩 Arquitetura

A aplicação é composta pelos seguintes componentes:

### 🎯 Frontend
- **voting-app (Python)**
  - Exibe a interface de votação ao usuário.
  - Envia votos para o Redis.

### 🧠 Backend
- **worker (Python)**
  - Escuta eventos no Redis.
  - Processa os votos e grava os resultados no banco de dados PostgreSQL.

### 💾 Banco de dados
- **db (PostgreSQL)**
  - Armazena os resultados dos votos.

### ⚙️ Armazenamento de estado
- **redis**
  - Armazena temporariamente os votos em memória.

### 📊 Resultado
- **result-app (Node.js)**
  - Exibe os resultados atuais da votação.

---

## 🚀 Comunicação entre os Pods

Cada componente roda em seu próprio **Pod** e é exposto por um **Service**, permitindo comunicação interna no cluster:

```plaintext
[voting-app] --> [redis] --> [worker] --> [db]
                          ↓
                    [result-app]
